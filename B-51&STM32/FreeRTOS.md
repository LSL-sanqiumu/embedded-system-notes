# FreeRTOS

FreeRTOS相关网站：

- 官方：[FreeRTOS - Market leading RTOS (Real Time Operating System) for embedded systems with Internet of Things extensions](https://www.freertos.org/zh-cn-cmn-s/)
- 源代码托管：[FreeRTOS Real Time Kernel (RTOS) - Browse /FreeRTOS at SourceForge.net](https://sourceforge.net/projects/freertos/files/FreeRTOS/)
- 野火教程：[RTOS-实时操作系统 — 野火产品资料下载中心 文档 (embedfire.com)](https://doc.embedfire.com/products/link/zh/latest/tutorial/index-rtos.html?highlight=rtos)

FreeRTOS：面向微控制器和小型微处理器的实时操作系统。

> 历史：由美国的Richard Barry于2003年发布，后于2018年被亚马逊收购，改名为AWS FreeRTOS，版本号升级为V10，且开源协议也由原来的GPLv2+ 修改为 MIT，与 GPLv2+ 相比，MIT更加开放。V9以前的版本还是维持原样，V10版本相 比于V9就是加入了一些物联网相关的组件，内核基本不变。

实时操作系统：[什么是实时操作系统（RTOS） - 知乎 (zhihu.com)](https://zhuanlan.zhihu.com/p/86861756)

为何发展处实时操作系统，相对于轮询来说，有什么优缺点呢？

# 文件下载和说明

FreeRTOS的源代码托管网址：[FreeRTOS Real Time Kernel (RTOS) - Browse /FreeRTOS at SourceForge.net](https://sourceforge.net/projects/freertos/files/FreeRTOS/)

**1、下载：**

进入到源代码托管网站，找到需要的版本进行下载 —— 下载V9.0.0版本，下载`FreeRTOSv9.0.0.zip`文件。

**2、目录说明：**

解压文件，找到FreeRTOS目录，里面的Demo和Source目录：（FreeRTOS-Plus目录可不了解，一般不用）

- Demo目录：FreeRTOS 官方为各个单片机移植好的工程代码，一些评估板的完整的工程文件，里面包含了不同开发平台、不同芯片的工程文件，可以参考这些文件来进行开发。
- Source目录：内核源代码。

关于Source目录：

- include目录下的文件和Source目录下的直接子文件：FreeRTOS 的通用的头文件和 C 文件，适用于各种编译器和处理器。
- portable目录：里面是需要情况进行移植的文件，需要移植的头文件和 C文件都在该目录下。

关于portable目录：对于不同编译器的支持文件

- Keil目录和RVDS目录：两个目录内的文件是一样的，因此官方只将文件放在了RVDS目录里。RVDS 目录里包含了各种处理器相关的文件目录，根据目录名称可以指定是哪个内核（STM32的M0、M3、M4等内核）的支持文件，里面提供了 cortex-m0、m3、m4 和 m7 等内核的单片机的接口文件。**RVDS目录里的文件就是用来将FreeRTOS和MCU联系起来的接口文件。**
- MemMang目录： 存放的是跟内存管理相关的，总共有五个 heap 文件以及一个 readme 说明文件，这五个 heap 文件在移植的时候必须使用一个，因为 **FreeRTOS 在创建内核对象的时候使用的是动态分配内存**，而这些动态内存分配的函数则在这几个文件里面实现，不同的分配算法会导致不同的效率与结果。（初学，选用heap_4.c即可）

> FreeRTOS 是一个软件，单片机是一个硬件，FreeRTOS 要想运行在一个单片机上面，它们就必须关联在一起，如何关联？还是得通过写代码来关联，这部分关联的文件叫接口文件，通常由汇编和 C 联合编写。这些接口文件都是跟硬件密切相关的，不同的硬件接口文件是不一样的，但都大同小异。**编写这些接口文件的过程我们就叫移植**，移植的过程通常由 FreeRTOS 和 mcu 原厂 的人来负责，移植好的这些接口文件就放在 RVDS 这个文件夹的目录下。FreeRTOS 为我们提供了 cortex-m0、m3、m4 和 m7 等内核的单片机的接口文件，只要 是使用了这些内核的 mcu 都可以使用里面的接口文件。
>
> 这里使用FreeRTOS，准确来说是使用官方的移植，而不是移植FreeRTOS到xxxMCU。

关于RVDS目录里只有“port.c”与“portmacro.h”两个文件，以里面的ARM_CM3目录为例：

- port.c：里面的内容是由 FreeRTOS 官方的技术人员为 Cortex-M3 内核的处理器写的接口文件，里面核心的上下文切换代码是由汇编语言编写而成。
- portmacro.h： 则是 port.c 文件对应的头文件，主要是一些数据类型和宏定义

此外还需要一个FreeRTOS的配置头文件，该文件见Demo目录里的STM32相关的demo中文件名为`FreeRTOSConfig.h`的文件。

**3、总结：**

使用官方的FreeRTOS的移植时，涉及的文件如下：

1. FreeRTOS源代码文件：include目录下的文件和Source目录下的直接子文件。
2. 软件、硬件之间的接口文件：如果是STM32，那就是portable目录下的RVDS目录下的文件。
3. 内存管理文件：MemMang目录下的文件，一般使用heap_4.c即可。
4. 配置文件：`FreeRTOSConfig.h`。

移植时只将这些文件分离出来即可，目录结构也可以按照官方的FreeRTOS目录结构来设置，即分离出来的文件放到另一个FreeRTOS目录里，然后源代码文件和目录照搬，portable目录里只留需要的内存管理文件、软硬件接口文件即可。目录结构和文件示例如下：

![](imgFreeRTOS/1.目录结构和文件.png)

# 移植FreeRTOS

将FreeRTOS添加进STM32F103C8的工程里，分为两步：

1. 创建好STM32F103C8的工程：创建项目，创建好组并加载好相关文件，再搞好工程配置（）。
2. 移植FreeRTOS：将涉及的文件加入到项目组里，修改好一些文件，再搞好项目的工程配置。

## Keil

使用Keil来进行开发。

1、创建好工程项目：STM32F103C8的工程创建过程说明见`STM32.md`。

2、移植FreeRTOS：

- 工程中创建好FreeRTOS/src、FreeRTOS/portable组，将相关文件添加进去。
- 将`FreeRTOSConfig.h`文件添加到User组里，需要修改该文件。
- 编译的时候需要为FreeRTOS源文件指定头文件的路径，不然编译会报错，因此需要在C/C++的 include path 添加FreeRTOS目录下的include、portable目录。
- 修改`stm32f10x_it.c`文件。

> FreeRTOSConfig.h 是直接从 demo 文件夹中某些demo目录下面拷贝过来的，该头文件对裁剪整个 FreeRTOS 所需的功能的宏均做了定义，有些宏定义被使能，有些宏定义被失能，一开始我们只需要配置最简单的功能即可。要想随心所欲的配置 FreeRTOS 的功能，我们必须对这些宏定义的功能有所掌握。野火修改过的`FreeRTOSConfig.h`文件，里面添加了一些中文注释，并且把相关的头文件进行分类，方便查找宏定义和阅读，见《FreeRTOS 内核实现与应用开发实战指南》。

修改`FreeRTOSConfig.h`，在末尾添加以下内容：

```c
#define xPortPendSVHandler 	PendSV_Handler
#define vPortSVCHandler 	SVC_Handler
#define xPortSysTickHandler	SysTick_Handler
```

修改`stm32f10x_it.c`文件：（上面添加的内容会导致重复定义的错误，因此需要修改该文件，把重复的给注释掉）

```c
// 在stm32f10x_it.c文件中找到以下三个函数并注释掉
void SVC_Handler(void)
{
}
void PendSV_Handler(void)
{
}
void SysTick_Handler(void)
{
}
```

3、修改`main.c`，测试：（通过FreeRTOS实现流水灯）

```c
#include "stm32f10x.h"                  // Device header
#include "Delay.h"
#include "FreeRTOS.h"
#include "task.h"
#include "portmacro.h"

static TaskHandle_t led_task_handle0 = NULL;
static TaskHandle_t led_task_handle1 = NULL;
static TaskHandle_t led_task_handle2 = NULL;

void led_init(void)
{
	RCC_APB2PeriphClockCmd(RCC_APB2Periph_GPIOA, ENABLE);
	
	GPIO_InitTypeDef GPIO_InitStructure;
	GPIO_InitStructure.GPIO_Mode = GPIO_Mode_Out_PP;
	GPIO_InitStructure.GPIO_Pin = GPIO_Pin_0 | GPIO_Pin_2 | GPIO_Pin_4;
	GPIO_InitStructure.GPIO_Speed =  GPIO_Speed_50MHz;
	GPIO_Init(GPIOA, &GPIO_InitStructure);
}
void led_task0(void *arg)
{
	while(1)                            
	{
		GPIO_SetBits(GPIOA, GPIO_Pin_0);
		vTaskDelay(500/portTICK_PERIOD_MS);
		GPIO_ResetBits(GPIOA, GPIO_Pin_0);
		vTaskDelay(500/portTICK_PERIOD_MS);
	}
}
void led_task1(void *arg)
{
	while(1)                            
	{
		GPIO_SetBits(GPIOA, GPIO_Pin_2);
		vTaskDelay(1000/portTICK_PERIOD_MS);
		GPIO_ResetBits(GPIOA, GPIO_Pin_2);
		vTaskDelay(1000/portTICK_PERIOD_MS);
	}
}
void led_task2(void *arg)
{
	while(1)                            
	{
		GPIO_SetBits(GPIOA, GPIO_Pin_4);
		vTaskDelay(2000/portTICK_PERIOD_MS);
		GPIO_ResetBits(GPIOA, GPIO_Pin_4);
		vTaskDelay(2000/portTICK_PERIOD_MS);
	}
}
int main(void) 
{
	led_init();
	xTaskCreate(led_task0, "led_task0", 1024, NULL, 20, &led_task_handle0);
	xTaskCreate(led_task1, "led_task1", 1024, NULL, 20, &led_task_handle1);
	xTaskCreate(led_task2, "led_task2", 1024, NULL, 20, &led_task_handle2);
	vTaskStartScheduler();
	while(1);
}
```


















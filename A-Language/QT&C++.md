# QT开发环境

安装最后一个开源离线版：[Index of /archive/qt/5.14/5.14.2](https://download.qt.io/archive/qt/5.14/5.14.2/)，里面自带QTCreator。（编译器选择，按需选择）

# Qt Widgets Application

Qt Widgets Application，支持桌面平台的有图形用户界面（Graphic User Interface，GUI）界面的应用程序。  

创建Qt Widgets Application项目：New File or Project → Qt Widgets Application → choose... → Location，项目命名与项目目录选择 → Build System选择，qmake → Details，设计主窗体 → Translation，默认 → Kits，32和64位都选上吧 → Summary，项目目录确认与更改 → Finished。

Qt Widgets Application项目目录说明：

![](imgQT/1.界面应用程序.png)

编译与调试：

![](imgQT/2.编译与调试工具.png)

# GUI应用设计基础

## UI文件设计与运行机制

### 文件组成

Qt Widgets Application项目的基本组成：

![](imgQT/1.界面应用程序.png)

目录：

1. Headers：用于存放所有的头文件。
2. Sources：用于存放项目所有C++源代码文件。
3. Forms：用于存放所有窗口的界面文件。

文件：

1. .pro文件：项目管理文件，用于存储项目设置的文件。
2. main.cpp：程序入口。
3. mainwindow.ui：主窗口界面文件，是一个用XML格式来存储窗体上的元件及其布局信息的文件。
4. mainwindow.h：所设计的窗口类的头文件。
5. mainwindow.cpp：是mainwindow.h里定义的类的实现文件；（在C++里，任何窗体或界面组件都是用类封装的，一个类一般有一个头文件(.h文件)和一个源程序文件(.cpp文件)，一个用于类定义（类定义及类成员的声明），一个用于类行为（功能函数）具体实现）

当编译后，会根据每个窗体上的组件及其属性、信号与槽的关联等会自动生成的一个类的定义文件。上面只有一个主窗口，会生成一个类的定义文件ui_mainwindow.h，类名Ui_MainWindow。

![](imgQT/3.生成.png)



### 运行机制

通过分析各个窗体文件的内容及功能，就可以知道它们是如何一起工作来实现界面的创建与显示的。以上面图中创建的项目为例。

**1、mainwindow.h和mainwindow.cpp：**

mainwindow.h：窗体类头文件，创建项目时选的窗体基类是哪个，该头文件就会定义一个继承该基类的类；该文件内容如下：

```c++
#ifndef MAINWINDOW_H
#define MAINWINDOW_H

#include <QMainWindow>
/*  声明了一个命名空间——Ui，里面包含一个类MainWindow，
	注意这个类是ui_mainwindow.h文件里定义的类 
*/
QT_BEGIN_NAMESPACE
namespace Ui { class MainWindow; }
QT_END_NAMESPACE
/* 窗体类定义，继承于QMainWindow的类的定义 */
class MainWindow : public QMainWindow
{
    //  Q_OBJECT，是使用Qt的信号与槽（signal和slot）机制的类都必须加入的一个宏
    Q_OBJECT         

public:
    MainWindow(QWidget *parent = nullptr);  // 构造函数
    ~MainWindow();  // 析构函数

private:
    /*
    用前面声明的namespace Ui里的Widget类定义的，
    所以指针ui是指向可视化设计的界面，
    后面会看到要访问界面上的组件，都需要通过这个指针ui
    */
    Ui::MainWindow *ui; 
};
#endif // MAINWINDOW_H
```

mainwindow.cpp：用于mainwindow.h中定义的窗体类的功能的具体实现。

```c++
#include "mainwindow.h"
#include "ui_mainwindow.h"   //  注意这里编译后自动加入了生成的与UI文件mainwindow.ui对应的类定义文件
/*
	构造函数，意为执行父类QMainWindow的构造函数，创建一个Ui::MainWindow类的对象——ui。
	这个ui就是MainWindow类的private部分定义的指针变量ui。
*/
MainWindow::MainWindow(QWidget *parent)
    : QMainWindow(parent)
    , ui(new Ui::MainWindow)
{
    // 执行Ui::MainWindow类的setupUi()函数，这个函数实现窗口的生成与各种属性的设置、信号与槽的关联
    ui->setupUi(this);  

}

MainWindow::~MainWindow()
{
    // 删除用new创建的指针ui
    delete ui;
}
```

总结：Ui::MainWindow类 是用于描述可视化设计的窗体的一个类，用于描述整个窗体；而  MainWindow类 则是对可视化设计窗体的功能延伸的描述，是功能描述的集合。（一个用于窗体描述和基本功能实现，一个用于功能拓展）

Ui::MainWindow类的行为如下。

**2、mainwindow.ui和ui_mainwindow.h：**

mainwindow.ui：

- 窗体界面定义文件，是一个XML文件，定义了窗口上的所有组件的属性设置、布局，及其信号与槽函数的关联等。
- 用UI设计器可视化设计的界面都由Qt自动解析，并以XML文件的形式保存下来。
- 在设计界面时，只需在UI设计器里进行可视化设计即可，而不用管widget.ui文件是怎么生成的  。

ui_mainwindow.h：对mainwindow.ui文件编译后生成的一个文件，通过UI设计器更改界面，编译后这个文件也会随之改变。它主要做以下工作：

1. 定义了一个Ui_MainWindow类，用于封装可视化设计的界面。
2. 自动生成了界面各个组件的类成员变量定义，在public部分为窗口界面上每个组件定义了一个指针变量，指针变量的名称就是在UI设计器里设置的objectName。
3. 定义并实现了setupUi()函数，这个函数实现分为三部分：
   - 1.根据可视化设计的界面内容，用C++代码创建界面上各个组件，并设置各个组件的位置、大小、文字内容、字体等属性。
   - 2.调用了函数retranslateUi(Widget)  ，用来设置界面各组件的文字内容属性，如标签的文字、按键的文字、窗体的标题等。将界面上的文字设置的内容独立出来作为一个函数retranslateUi()，在设计多语言界面时会用到这个函数。  
   - 3.设置信号与槽的关联。  
   - 因此在MainWindow的构造函数里调用 ui->setupUI(this)，就实现了窗体上组件的创建、属性设置、信号与槽的关联。  
4. 定义namespace Ui，并定义了一个从Ui_MainWindow继承的类MainWindow。

```c++
/* 信号与槽的关联 */
// 将pushButton按钮的clicked()信号与窗体MainWindow的槽函数close()关联起来
// 当点击按钮时，就会执行MainWindow的close()
QObject::connect(pushButton, SIGNAL(clicked()), MainWindow, SLOT(close()));
// 设置槽函数的关联方式，用于将UI设计器自动生成的组件信号的槽函数与组件信号相关联
QMetaObject::connectSlotsByName(MainWindow);
```



## 可视化UI设计

### 访问组件



### 组件布局



### 信号与槽


















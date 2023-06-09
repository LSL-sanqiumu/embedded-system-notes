# 外行想学嵌入式软件开发最快需要多久？

> 作者：秃然的自我
> 链接：https://www.zhihu.com/question/368730083/answer/3082306089
> 来源：知乎
> 著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。

看你想学到什么程度，我们暂且以找到工作为目标。

目标定了，还要看你走哪个方向，嵌入式软件开发也分几个职业方向的，比如单片机工程师、Linux驱动工程师、Linux应用工程师。

三个方向，学习的内容和周期都不一样。

我身边有学几个月，也有跟我说学了2年的。

拿我自己做案例，我主要走的是单片机方向，因为学历不高、也不是相关专业。

现在我也是快奔4的人了，之前是电气工程毕业，后面自学转行单片机开发，做了10几年研发。

从事研发越久，我越发现这个行业的知识真是永远学不完。

但也不代表你要花好几年时间，才能达到就业水平。

我具体花了几个月，记不清楚了，10几年前了，不过我能确定的是半年内。

那时候也没经验，瞎学的，在模电数电上浪费了很多时间，还买了一本贼厚的[电子元器件](https://www.zhihu.com/search?q=电子元器件&search_source=Entity&hybrid_search_source=Entity&hybrid_search_extra={"sourceType"%3A"answer"%2C"sourceId"%3A3082306089})手册一页一页地看，这种就是属于走了弯路。

如果你走软件方向，电路这块只需要学习常用的元器件原理和作用即可，不需要学太深。

学完电子元器件，就跟着教程学开发板上面的电路，能看懂就行，不需要会设计的程度。

主要精力用于学C语言，学单片机这些基础知识，学这些基础内容，最快的方式就是买个[开发板](https://www.zhihu.com/search?q=开发板&search_source=Entity&hybrid_search_source=Entity&hybrid_search_extra={"sourceType"%3A"answer"%2C"sourceId"%3A3082306089})，按着教程玩一遍。

学完一个开发板以后，就开始找项目做。

为什么要找项目做？

为了后面给找工作做铺垫，如果你只会c语言、单片机这种基础内容，企业看不上。

项目去哪里找？

可以到某宝找，但是某宝的项目我看了一圈，真正有含金量的项目，没有！

也可以网上找一些开源的，自己慢慢摸索，但是周期太长。

也可以跟[无际单片机](https://www.zhihu.com/search?q=无际单片机&search_source=Entity&hybrid_search_source=Entity&hybrid_search_extra={"sourceType"%3A"answer"%2C"sourceId"%3A3082306089})的做项目，无缝对接实际产品开发，效率高，但需要付费。

如何取舍，看自己的认知和条件。

但是做项目这一步，肯定不能少。

很多工程师，包括我，为什么工作以后技术提升得最快？

就是因为工作以后一直在做各种项目，项目是做锻炼人的，没有之一。

如果你想快速提升，不断做项目就是捷径，开发板这玩意，一般我们用来辅助项目学习、调试。

最后我建议：

学习，很多人是做加法，什么都想学，而我是喜欢做减法，只学最刚需的。

不要在不应该的阶段，去学你理解成本过高的东西。

比如说新手不适合死磕模电，不适合死磕RTOS。

如果你能理解以上，完全能够在4-6个月时间，从零基础到就业。



# 怎么学嵌入式单片机？学习路线是什么？

我属于半路出家，之前专业是电气，到目前为止，做单片机开发有12年时间了，做过的行业和技术涉及比较杂，智能楼宇、智能家居、智能安防、电表、车载产品、Lora、WiFi、4G、GSM、蓝牙等等，大大小小产品做过几十个。

做过单片机开发的，相对纯软件程序员，最有意思的是，我能搞出来一个实实在在的东西，而且这个东西，自己从硬件到软件都很通透，不像做纯软件做应用的，底层全部现成的，你只是个调库侠。

如果你经常阅读嵌入式怎么学的文章，你会有一种错觉，这个行业要学得东西太多了，觉得门槛很高，收入和付出不成正比。

从事行业越久，我越发现这个行业涉及的知识确实无穷无尽，一辈子也学不完。

但是如果你的目标仅仅是找份工作，并不需要学很多东西，4-6个月左右完全可以达到找工作水平。

很多东西，你前期的时候并不需要深入学习，甚至都不需要学。

下面根据我从业多年经验，给大家总结一个比较靠谱的学习路线，让你少看几十G教程。

## 一、硬件需要学习的内容

1.做嵌入式开发，需要对硬件有一定了解，能看得懂电路图就可以了，不需要会设计的程度。

特别是不要纠结模拟电路，否则你会死得很惨，这个不是新手阶段能学得懂的。

以前我就是在模拟电路上浪费了很多时间，学不懂、工作以后才发现模电的知识实际用得也很少。

2.先学习常用的元器件，比如电阻、电容、电感、二极管、三极管、MOS管原理及作用。
可以参照无际单片机编程的硬件基础课目录学习：xxx

这些内容，基本上就是刚需中的刚需，产品中最常用的了。


3.学完常用元器件，再通过开发板或者项目学单片机最小系统电路和功能性模块电路（LED驱动、按键检测、数码管显示、屏显示、蜂鸣器驱动、存储电路等），不断积累。

4.学完这个再学1个画图工具，我最开始学的是Protel99se，不过现在已经过时了，目前一般用AD、Allegro、Pads、Cadence等等，学会其中一款，能用它看原理图就可以了，先别学PCB，这是硬件工程师干的活。



## 二、软件学习

做嵌入式单片机开发，软件是我们学习的主力，也是花费时间最多的地方。

### 1.C语言

单片机支持C语言和汇编两种语言，目前产品开发主流是C语言，所以先学C语言就可以了。

前期学学基本语法就够了，可以参考这个课程目录：

1. 单片机是什么？
2. 单片机资源有哪些？
3. 二进制和十六进制。
4. C51点亮LED灯。
5. 变量的定义和应用。
6. C语言算术运算符。
7. C语言关系运算符。
8. C语言位运算符。
9. if语句、while语句、switch语句、for语句、break、continue、goto语句。
10. C语言逻辑运算符。
11. C语言赋值运算符。
12. C语言函数定义和调用。
13. include、sfr、sbit关键字的用法。
14. C语言条件编译命令。
15. 数组定义和赋值。
16. 多维数组定义和赋值。

不用学得太深，这个阶段甚至指针都可以先不学。

> 书籍：《C Programming Language》；《C和指针》、《C专家编程》、《C陷阱与缺陷》这三本的内容挑着看，研究哪部分内容就看哪部分。
>
> 啥叫会编程？**会编程，是指在应对各种不同的业务需求时，都能很快的将业务逻辑转化成编程逻辑，并且编码实现的能力。**
>
> 编程能力提升：阅读开源代码、做项目、写算法。
>
> 比如Linux系统的源码，举例：
>
> ```c
> // 对比两数大小，一个宏实现，一个函数实现
> #define MAX( a, b) ( (a) > (b)?(a) : (b) )  
> int max( int a, int b)
> {
> 　　return ((a > b)? a : b);
> }
> ```
>
> 



ANSI C 、POSIX C、GNU C到底是啥？之间到底有啥关系？

### 2.51单片机

我是先学了STC89C51单片机，我也建议零基础的从51单片机开始学习，比较好上手，直接淘个开发板跟着教程学，基本没什么技巧。

C语言和单片机可以同时学习，正好边学边实操，实操才是重点，这个技术光看是学不会的。

### 3.做小项目

学完51单片机以后，先不要急着学STM32或者性能更高的单片机，不然你后面会学得很吃力，问题比你学得知识还多。

先用51单片机做几个小项目，比如智能小车、电子时钟、温湿度智控之类的。

这一步很关键，也是最多人跳过的一步，为什么？

**单片机只是工具，更高端的单片机，只能代表这个工具能做更复杂的项目，但是能不能把项目做出来，不在于工具本身，而是用工具的人，取决于你的编程思路和编程水平，这两东西只能通过项目去锻炼出来。**

### 4.学习C语言高阶用法

这个阶段深入学指针、结构体、枚举，以及它们的实际应用是最佳时机。

后面STM32的库，会大量使用这些玩意。

### 5.学STM32

STM32对于初学者来说就是噩梦，我在学STM32的时候已经工作了大概半年了，用过STC15系列和NXP的单片机改过项目程序。

即便如此，研究起来还是会有点吃力，STM32主要就是学库的使用，如果你深入寄存器去学习，虽然学得比较透彻，但会遥遥无期。

其实STM32很多外设可以先不用学习，除了给初学者学习的开发板，大多数项目只会用到它部分外设资源，并非全部。

所以，我们前期只需要学一些常用的外设就可以了，比如说GPIO、Systick、Timer、USART、NVIC、EXTI、DMA、ADC、SPI、IIC。

这些外设基本上是产品的刚需。

### 6.持续做项目

前面学得那些就是基础技能，接下来就需要不断做项目提升，成长速度和高度由项目数量和质量决定。

如果你从事开发很多年，会发现，真正让你成长最大的就是工作以后，因为工作内容基本就是做项目，做项目，做项目，还有一点很关键，就是身边有领导或同事能指导你。

如果你学完STM32，找工作处处碰壁，也是正常的，毕竟光会基础技能毫无竞争力，就是看运气。

**解决办法就是可以自己去网上找些项目做**，如果自己摸索太慢，想办法找人指导，这样成长快点。

### 7.RTOS

实时操作系统，我认为在你没碰到需求之前，可以先不用学，毕竟不是刚需，当然，你学了也可以作为一个加分项。

不过我建议在你没做过任何基于STM32项目的时候，不要去学，不然可能会耗费你1-2个时间。

因为你的经验和编程底子太薄，去理解RTOS的知识占用时间太长，而且RTOS的很多东西，你不知道它们到底用在哪里，学得云里雾里。

核心还是先通过项目不断提升编程思维和代码水平，干它3-4个项目以后，RTOS对你来说就是水到渠成的事情，可能1-2周就上手了。



# 初学者怎样提高C/C++编程能力？

    	首先、什么算你所谓的编程能力？
    	我们对一项技能的掌握程度往往很难量化，对于编程能力的考量可能比较抽象，我们来类比比较直观的其他技能。比如说什么叫会弹吉他？我们说一个人吉他玩的好，这个人会弹吉他，是指他会弹《小星星》？还是会弹岸部真明的《time travel》？（力荐，好听！）恐怕都不是，我们对于会弹吉他的认知，应当是随手给他一个不熟悉的谱子，你也能很快的用吉他精彩的演奏，我们才说这个人吉他玩的真6。那编程也是，我们所希望的编程能力，指的是会写双向链表还是会写二叉树？恐怕都不是，我们所指的会编程，是指他在应对各种不同的业务需求时，都能很快的将业务逻辑转化成编程逻辑，并且编码实现的能力。
    
        那么、如何来锻炼这种能力？
    
        前段时间在罗胖的《得到app》上听的一篇精品课，非常受启发。一位老师讲如何高效地学习一项技能，他用两年的时间就从零基础达到了专业级的弹指吉他大师的水平，他所使用的方法很值得借鉴。内容大概是这样：他一开始接触吉他，没有从基础开始练，而是直接挑战难度极高的世界名曲开始演奏。可想而知这难度是极大的，没有任何基础的他，很多和弦都压不住。尤其对与刚玩吉他的人，十指连心啊，压弦的那只手是钻心的疼。一开始一句完整的都弹不下来，更别提什么扫弹，闷音，切音的技巧。就这样一节一节地弹，经过不懈的努力，他把这首曲子拿了下来。
    
         巨大的成就感是自然的，但对于优秀的渴望使得这位大佬感到仍然不能满足。怎么办呢？请教名师！这时候老师告诉他：“一禅呐！所谓知之者不如好之者、好之者不如乐之者，你现在已经能够从弹奏吉他中获得喜悦，现在，请再回过头，从基础开始学起。”这下子他才开始从最基础的乐理开始，什么叫节奏、什么叫旋律、什么叫音阶、什么C调G调F调。原来之前练到手指快疼死的的指法叫F和弦？原来之前的曲子里变调是这个意思？
    
       和上去就啃吉他基础教学不一样，这波儿基础的学习让他任督二脉蹭的一下就通了，仿佛杨过一身雄厚的内劲得黄药师点化一番，实力大增。不但能将那首世界名曲演绎的更加纯熟，对于其他没有演奏过乐曲，只要稍加练习，就能够德芙般顺滑地弹奏下来。
    
        同样的方法，映射到编程上，就是我想说的学习方法。我很不建议一开始就从基础开始啃，有多少人从大一刚入学立志将来做一个IT大佬，抱着一本《C++ Primer》开始啃，最后啃不到200页就去LOL上分冲段位了。所以我的建议是，一开始只要会点儿基础语法，就定一个小目标去实现就好了，不必强求每一行代码都是亲自手写。遇到问题就查，百度也可以查书也可以，我一开始写个五子棋小游戏的时候，连数组的声明语法都是查书的。把你遇到的问题从业务逻辑定位成代码逻辑，然后知道从哪儿可以找到想要的答案，这个能力在未来的工作、编程和面试中非常重要。
    
        一两个完整的程序做下来之后，再回过头来从变量、语法、表达式、流程控制、函数....重新去学习这门编程语言，这时候你会不断地发现原来这个地方这么写的原因是这样？原来这个地方是这么实现的，那个地方我还可以这么写。一本枯燥的语法书籍你会很流畅地读下来，甚至还可能读出快感和兴趣，这样一顿操作之后，你可以算真正掌握了一门编程语言，有了自己的理解在里面，并且有对应的应用经验，未来的面试中也可以讲的头头是道。
————————————————
版权声明：本文为CSDN博主「CodingPs」的原创文章，遵循CC 4.0 BY-SA版权协议，转载请附上原文出处链接及本声明。
原文链接：https://blog.csdn.net/CodingPs/article/details/103460891

# C艹

作者：Skiiii
链接：https://www.zhihu.com/question/390717188/answer/1184954255
来源：知乎
著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。



算了吧，过来人告诉你，大学里面那堆项目，99%是没有任何技术含量的廉价劳动力，我觉得只有毫无目标且焦虑的人才会觉得做点大学的项目是在锻炼你。

我自己读研的时候只想推掉所有分给我的实验室的项目，避免让这些东西占我自己瞎搞的时间。

后来工作面试遇到过各种做大学导师垃圾C艹项目的人，结果你问他一个C艹虚函数怎么实现的（没有标准答案，你能说出来可行的方案就行），一无所知。反而背了一大堆 mfc 的 API，简直不忍直视。

说真的，找对路线，进互联网公司做个平凡的码农(BAT级别)简直太简单了，随便列举一个有脑子就行的弱鸡路线:

1.  大一大二打好基础，操作系统，网络，任意一门C系带面向对象的语言吃透(基本的底层实现，一般一本语法，3本进阶就够了)，基本的算法数据结构(真的很基本)，Linux 基本 API 和机制。
2. 大三去看看开源项目，有感兴趣的研究研究，吃透一两个开源库的源码（要我推荐就是 leveldb，不仅学习 lsm tree，顺便看看人家怎么设计 C++ 模块的）。
3. 跟 1、2 并行的，每天刷一道 leetcode，学完什么数据结构/算法，就去刷什么题，这样三年下来，怎么也刷了4、500道题了。

上面的按部就班做完，还找不到工作的话你可以上知乎发简历给我，我帮你内推啊 。

# 硬件

一个实际电路的原理图是怎样设计出来的？ - HANs的回答 - 知乎 https://www.zhihu.com/question/358059963/answer/920402590



# 通识

> 为什么现在年轻人很迷茫？是选择太多了吗？ - 墨苍离的回答 - 知乎 https://www.zhihu.com/question/574649845/answer/3038668155

多数人离开做例题不会思考。

通识教育弄出来各种解决问题的范式，而范式训练的关键是要有例题。

说白点，要有具体的案例可以参考，可以抄袭思路。

之前之所以年轻人没觉得迷茫，是因为在经济上升周期有大把的前人的案例可以抄袭，比如转CS就能高薪，比如XXX行业能赚钱。

经济周期有其惯性，因而这种抄袭思路的做题逻辑，在惯性期间仍然看上去是有效的，所以冒出来各种报专业的咨询、各种总结如何抄袭的所谓攻略。

但经济周期变成停滞或者下行的时候（这是无法避免的）。这些有效的“攻略”突然失效了。

这时候，人们会由于无法抄袭成功案例而变得无所适从。

或者抄袭了成功案例，发现失效了，而悔恨不已。

在他们没有被逻辑和视野污染的认知中，穷举所有的选择性都变成了一种奢望。

甚至，他们的思维的基础，词汇符号已经被腐蚀到了很精简的程度，以至于，无法支撑清晰的逻辑思考，自动带有各种被忽悠或者逻辑归因错误的debuff。

他们会去拥挤的参与那些目前看起来，貌似不会差的赛道。然后几百万人去寻求几万个岗位，或者把仅有的翻本资源投入那些过度宣传的所谓机会。

然后在极度养蛊的这些赛道和机会上，被毒打。

即使找到了工作，也会继续用范式去进行与社会的交互，而这些范式又是原生环境给予的，装满了各种奇特的刚性的思想钢印的，于是潜意识拒绝改变，继续在交互中被毒打。

毒打的多了，就习得性无助。

那么迷茫就变成了唯二解，还有一个解，是污名化环境。

我很想告诉这些人们：

1，经济周期的波动是常态，现在难，代表经济周期在谷底附近，它总会上升，奔向下一个高峰；

2，在功利化的寻求出路之前，请先用功利化的目光好好审视自己的真正优势和真正爱好，如果没有，经济低谷期去建立优势和爱好，性价比最高；

3，**好好整理和充实一下自己的思维底层，不要为了对冲当前的郁闷和迷茫，去看太多奶头乐，这会把脑子搞得逻辑上更单纯、更简约，其结果是词汇符号越来越模糊、逻辑越来越被情绪控制。**

4，要实践，用实践来暴露自身的问题，而不是用空想和道听途说去寻求成长，更不是用呻吟和唾骂社会来获得自我慰藉。

5，少看短视频，少看畅销书，读点纪实文学，读点经典书籍，读点大学教材。

以上。

供参考。






















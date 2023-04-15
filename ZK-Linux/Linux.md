# Linux

# 熟悉常用目录

|         常用目录         | 描述                                                         |
| :----------------------: | :----------------------------------------------------------- |
| /usr/bin、/usr/local/bin | bin是Binary的缩写，存放经常使用的命令                        |
|          /root           | 该目录为系统管理员，也称为超级权限者的用户主目录             |
|          /boot           | 存放的是启动Linux时使用的一些核心文件，包括一些连接文件以及镜像文件 |
|          /media          | linux系统会自动识别一些设备，例如U盘光驱等等，当识别后，linux会把识别的设备挂载到这个目录下 |
|           /mnt           | 系统提供该目录是为了让用户临时挂载别的文件系统的，我们可以将外部的存储挂载在/mnt/上， 然后进入该目录就可以查看里面的内容了，例如用虚拟机创建的共享文件D:/myshare |
|           /etc           | **配置：**所有的系统管理所需要的**配置文件**和子目录，比如安装mysql数据库的my.conf配置文件 |
|          /home           | **用户：**存放普通用户的主目录，在Linux中每个用户都有一个自己的目录， 一般该目录名是以账户的账号名命名 |
|         **/usr**         | **应用：**这是一个非常重要的目录，用户的很多应用程序和文件都放在这个目录下， 类似与windows下的program files目录 |
|      **/usr/local**      | **应用：**这是另一个给主机额外安装软件的目录，一般是通过编译源码的方式安装的程序 |
|         **/var**         | **日志：**这个目录中存放着会不断扩充着的东西，习惯将经常被修改的目录放在这个目录下，包括各种**日志文件** |
|         **/opt**         | **软件包：**这是给主机额外安装软件所存放的目录，如安装ORACLE数据库就可放到该目录下。默认为空； - 约定俗成，要安装的软件下载好先拷贝到该目录。 |

# 熟悉常用命令

## vim & vi

Linux会内置vi文本编辑器；Vim具有程序编辑的能力，可以看为vi的增强版，其可以主动地以字体的颜色辨别语法的正确性，方便程序设计，其代码补全、编译、及错误跳转等方面编程的功能特别丰富，被程序员广泛使用。

安装 vim：`yum install vim`。

**vi和vim常用的三种模式：**

- **正常模式：**打开文件的默认模式，可以使用上下控制光标，可以进行删除字符、删除整行、复制、粘贴等操作来处理档案内容、文件数据；可以使用快捷键。
- **插入模式/编辑模式：**按下i（或者I、o、O、a、A、r）就可以进入，然后就可以进行内容的输入。
- **命令行模式：**输入`:`就会进入命令行模式，在这个模式中，可以执行相关指令来完成读取、存盘、替换、离开vim、显示行号等操作。

<img src="img/模式切换.png" style="zoom: 67%;" />

vi或vim模式切换：（`:wq`（保存并退出）、`:q`（退出）、`:!q`（强制退出，不保存））。

**快捷键使用：**

1. yy：拷贝当前行，5yy：拷贝当前行向下的5行（从当前行开始复制）。（一般模式）
2. p：粘贴。（一般模式）
3. dd：删除当前行，5dd：删除当前行向下的5行（从当前行开始删除）。（一般模式）
4. u：撤销操作。（一般模式）
5. 跳转到指定行：（一般模式）
   1. gg：跳到首行；`5 + gg`跳到第五行；G：光标跳到末行。
   2. `shift + h`：跳到首行；`shift + g`：跳到尾行。输入要到达的行数然后再执行`shift+g` ，就会调到指定行（可以先显示行号：`:set nu`，然后退回到一般模式，输入行号这个数，再输入`shift+g`即可定位到指定行数）。

6. 设置文件行号：`set nu`；取消文件行号：`set nonu`。（命令行模式）
7. `/查找内容`：查找内容， 然后按n可以继续下一个。（命令行模式）



## 用户管理

| 命令            | 说明                                                         |
| --------------- | ------------------------------------------------------------ |
| useradd  用户名 | 添加用户，添加后自动创建用户家目录：/home/用户名<br>`useradd -d /home/test usertest`—自定义用户家目录 |
| userdel  用户名 | 删除用户，`userdel -r 用户名`：删除用户并且删除用户的家目录  |
| id 用户名       | 查询有无此用户                                               |
| su - 用户名     | 切换到指定用户，从权限高的用户切换到权限低的用户不需要密码<br>**返回原来的用户使用exit或logout命令** |
| whoami          | 查询当前登陆到的用户的用户名，切换到哪个就是哪个             |
| who am i        | 最开始是用哪个登陆的就显示哪个                               |
| passwd          | 修改当前登录的用户的密码                                     |
| passwd  用户名  | root用户下修改其他用户的密码                                 |

用户相关文件：

![](img/group.png)

可用`vim xxx`查看这三个文件。（`vim /etc/passwd`）



## 重启与关机

| 命令            | 说明                                                         |
| --------------- | ------------------------------------------------------------ |
| shutdown -h now | 立刻关机                                                     |
| shutdown -h 1   | 1分钟后关机                                                  |
| shutdown -r now | 立刻重启                                                     |
| shutdown -r 1   | 1分钟后重启                                                  |
| sync            | 将内存中的数据同步到磁盘<br>建议，无论重启或关闭系统，都要先执行`sync`命令<br>即使shutdown/reboot/halt等命令均会在关机前进行sync操作 |
| halt            | 立刻关机                                                     |
| reboot          | 立刻重启                                                     |



## 帮助

| 命令         | 说明                                            |
| ------------ | ----------------------------------------------- |
| man  xx命令  | 查询该命令的使用信息                            |
| imfo  xx命令 | 与 man 命令相似，能够显示出命令的相关资料和信息 |



## 文件 & 目录

| 命令                                                         | 说明                                                         |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| pwd                                                          | 显示当前所在目录的绝对路径                                   |
| `ls [选项] [目录或文件]`：`ls -al`、`ls -lh`<br>选项有a、l、h | 显示目录下的文件或文件的相关信息                             |
| cd xxxx：                                                    | 切换到指定目录，`cd ~`回到家目录，`cd ..`回到上一层目录      |
| mkdir [选项] 要创建的目录名                                  | 不加选项则只能创建单个目录，加上选项`-p`则是用来创建单个或多级目录 |
| touch 文件名称                                               | 该命令只用来创建空文件<br>Linux系统是没有后缀的定义的，后缀可看成是一个可有可无的标记 |
| cp 文件 目录/                                                | 拷贝文件到指定目录下（`cp hello.txt text/`）                 |
| \cp 文件 目标目录                                            | 复制到目标目录并强制覆盖                                     |
| cp -r 目录 目标目录                                          | 递归复制整个目录，把指定目录拷贝到目标目录                   |
| \cp -r 目录 目标目录                                         | 递归复制并强制覆盖目标目录里同名的文件                       |
| rm [选项] 文件：`rm -rf xxx`                                 | 强制删除且不再提示是否删除                                   |
| mv xx文件或目录   xx                                         | 移动或重命名文件或目录（剪切、重命名）                       |
| cat [选项] 要查看的文件                                      | 查看文件                                                     |
| more                                                         | 查看文件                                                     |
| less                                                         | 查看文件                                                     |
| head                                                         | 查看文件头10行                                               |
| tail                                                         | 查看文件尾10行                                               |
| tail -f 文件                                                 | 实时追踪文件的所有更新，会占有屏幕、实时显示更新的内容       |
| >                                                            | 追加                                                         |
|                                                              |                                                              |
|                                                              |                                                              |
|                                                              |                                                              |

### 显示：

1. `pwd`：显示当前工作目录的绝对路径。
2. `ls [选项] [目录或文文件]`：
   - 选项是`-a`（all的缩写），则显示当前目录的所有文件和目录（包括隐藏的）。
   - 选项是`-l`（list的缩写）则以列表的形式显示非隐藏文件。
3. `ls -lh`：以更人性化的方式显示当前目录下的内容。
4. `ll`，相当于`ls -l`。

### 切换：

- `cd [参数]`：切换到指定目录，`cd ~`回到家目录，`cd ..`回到上一层目录。

### 创建：

1. `mkdir [选项] 要创建的目录名`：不加选项则只能创建单个目录，加上选项`-p`则是用来创建单个或多级目录（p是parents）。
2. `touch 文件名称`：该命令只用来创建空文件（Linux系统下是没有后缀的定义的，后缀可看成是一个可有可无的标记）。

### 拷贝：

1. 复制文件到目录：
   - `cp 文件 目录/`：拷贝文件到指定目录下（`cp hello.txt text/`）（会提示是否要覆盖同名文件）。
   - `\cp 文件 目标目录`：复制到目标目录并强制覆盖。
2. 目录的复制：
   - `cp -r 目录 目标目录`：递归复制整个文件夹，把指定目录拷贝到目标目录（`cp -r /home/text/ /opt/`）（会提示是否覆盖同名文件）。
   - `\cp -r 目录 目标目录`：递归复制并强制覆盖目标目录里同名的文件。

### 删除：

1. 删除文件：

   - `rm [选项] 文件`：例如`rm test/hello.txt`，删除test目录下的hello.txt文件（选项为-r、-f、-rf）。

2. 删除目录：

   - `rm 选项 要删除目录`：选项用`-r`则是递归删除整个文件夹，用`-f`则是强制删除且不再提示，`rm -rf 要删除的目录`。
   - `rmdir [选项] 要删除的空目录`：只能删除空目录，删除非空目录要使用该命令：`rm -rf 要删除的目录`。

3. 使rm命令失效的一个思路：利用mv来替代掉rm——把文件移到到回收站中，然后再执行清除回收站的命令，完成删除。

   1. `vim ~/.bashrc`，在该文件下加入以下代码，然后保存并退出：

      ```bash
      mkdir -p ~/.trash   #在家目录下创建一个.trash文件夹
      alias rm=del        #使用别名del代替rm   
      del()               #函数del，作用：将rm命令修改为mv命令
      {  
      mv $@ ~/.trash/  
      }  
      cleardel()          #函数cleardel，作用：清空回收站.trash文件夹，y或Y表示确认，n表示取消
      {  
      read -p "clear sure?[Input 'y' or 'Y' to confirm. && Input 'n' to cancel.]" confirm   
      [ $confirm == 'y' ] || [ $confirm == 'Y' ]  && /bin/rm -rf ~/.trash/*   
      }  
      ```

   2. 最后实现的删除文件命令：`del 文件`、`rm 文件`、`del *`、`rm *`；然后清除回收站`cleardel`。（注意自己系统下的回收站是哪个文件夹）


### 移动：

- `mv xx xx`：重命名文件或目录（`mv 旧文件/目录 新文件/新目录`）；移动文件、目录（`mv 文件或目录地址 目标目录`）（相当于剪切并粘贴）。
- 如果某目录下有同名目录且非空，则会移动失败。

### 查看文件：

1. `cat [选项] 要查看的文件`：选项为`-n`则是显示行号，该命令只能查看文件，一般使用`cat -n 文件 | more`来查看文件。（`|`：管道命令）

2. `more 文件`：查看文件。
3. `less 文件`：查看文件。
4. `head 文件`：默认查看文件内容的头十行；`head -n 5 文件`用于指定显示头几行。
5. `tail 文件`：默认查看文件最后十行的内容；`tail -n 5 文件`（指定显示最后5行）。
   - `tail -f 文件`：实时追踪文件的所有更新，会占有屏幕、实时显示内容。


![](img/more.png)

![](img/less.png)

### 重定向和追加：

![](img/echo.png)

追加和重定向的区别：追加是在原文件内容下另开一行开始添加内容，而重定向是将文件原内容去除完再添加进去。

### 输出内容到控制台：

1. `echo xx`：`echo $PATH,$HOSTNAME`（输出环境变量），`echo hello`（输出hello）。
2. `echo 'hello' > hello.txt`：将在控制台输出的文本`hello`重定向到该文件，会将该文件原来的内容覆盖。
3. `cal >> xxx`：追加日期到xxx文件。



## 时间日期

![](img/date.png)

1. `cal`是显示日历的指令，显示的是当月的日历；如果是`cal 2020`则是显示2020年的整个日历。

## 搜索查找

**文件查找指令：**

1. find指令：

   - `find /home -name hello.txt`：在/home目录下按文件名查找（注意Linux里面没有后缀概念）；其他的选项都是类似的查找方式。
   - `find xxxx文件或目录`，在当前所在目录下寻找文件或目录，不会进当前目录下的目录里寻找。
   - 如果查找到的文件过多，可以在最后使用`| more`进行分页查看。
   - `find /home -size -100M`（查找小于100M的），按文件大小进行查找，+、-、=分别表示大于、小于、等于，单位有k、M、G。
2. locate指令：

   - `locate 要搜索的文件`：该指令可快速定位文件路径。（第一次使用该命令前需先执行`updatedb`）
   - 安装locate指令：`yum install mlocate`。

**指令查找指令：**

1. which指令：

   - `which 指令`：查看指令在哪个目录下。

**grep指令和管道符：**

- `|`：管道符，表示将前一个命令的处理结果传递给后面的命令处理。

- `grep [选项] 查找内容 文件`：过滤查找，将指定的内容从文件中过滤出来；选项有`-n`（显示查找到的内容的所在行及行号）和`-i`（忽略字母大小写）。

- 示例（最终结果都一样）：`cat /home/hello.txt | grep -n "yes"`、`grep -n "yes" /home/hello.txt`，文件中查找到`"yes"`所在行并显示到控制台上。

- `grep -ni "yes" /home/hello.txt`：忽略大小写并显示行号的过滤查询，查询到`"yes"`在文件中的哪个段落。



## 压缩与解压

| 命令                              | 说明                                                         |
| --------------------------------- | ------------------------------------------------------------ |
| `zip [选项] xxx.zip 要压缩的内容` | 压缩文件或目录，常用的选项是`-r`，即递归压缩（压缩目录）     |
| `unzip [选项] xxx.zip`            | 解压缩文件，常用的选项是`-d`，即指定解压后文件的存放目录<br>`unzip -d /home xxx.zip`：解压到/home目录 |
| `gzip 文件`                       | 只能压缩文件，不会保留原始文件，执行后获得以`.gz`结尾的压缩文件（`文件名.gz`） |
| gunzip 文件.gz                    | 解压缩以`.gz`结尾的压缩包文件，不会保留原始的压缩包文件      |

**tar指令：**（打包成.tar文件再使用gzip压缩成.gz压缩包）

![](img/tar.png)

1. 打包压缩文件或目录：（格式：`tar -zcvf 打包压缩后的文件名 被压缩文件1 被压缩文件2 ...`）

   - `tar -zcvf xxx.tar.gz xxx文件 xxx文件`：可打包压缩多个文件并产生`.tar.gz`打包压缩文件。
   - `tar -zcvf xxx.tar.gz xxx目录`：打包并压缩目录。
   - `tar -cvf xxx.tar xxx文件或目录`：仅打包但不压缩。


2. 解压：（解压结包后原压缩包不会被丢失）

   - `tar -zxvf xxx.tar.gz`：解包解压到当前目录。
   - `tar -zxvf xxx.tar.gz -C 目标目录`：将某目录下的压缩打包文件解包解压缩到目标目录。
   - `tar -xvf xxx.tar.gz`：解包。



## 软链接-符号链接

1. `ln -s [原文件或目录] 软链接名`：在当前目录下创建文件或目录的软链接，使用rm相关指令即可删除。
2. 软连接类似Windows里的快捷方式，是文件或目录的代表，可通过软连接来访问其代表的文件或目录。

## 历史命令

1. 查看你曾执行过的命令：
   - `history`：查看已经执行过的命令（该history也会包含在内）。
   - `history 数字`：查看距离现在最近已执行的n条指令（该history也会包含在内）。
   - 查询出来的指令前都带有一个序号，该序号可配合`!`来执行序号所代表的指令。

2. `!指令前的数字`：使用history查看到历史指令后使用该指令可以执行指定的历史指令。

## 环境变量设置





## else

### 重启与关机

1. `shutdown -h now`、`halt`：立刻关机。
2. `shutdown -h 1`：1分钟后关机
3. `shutdown -r now`、`reboot`：立刻重启。
4. `sync`：将内存中的数据同步到磁盘。
   - 建议，无论重启或关闭系统，都要先执行`sync`命令，即使shutdown/reboot/halt等命令均会在关机前进行sync操作。

### 运行级别

运行级别：常用的是3和5	

- 0：关机。
- 1：单用户（找回丢失密码）。
- 2：多用户状态没有网络服务。
- 3：多用户状态有网络服务。（multi-user.target）
- 4：系统未使用保留给用户。
- 5：图形界面。（graphical.target）
- 6：系统重启。

运行级别的操作：

1. `init 运行级别`：切换到指定运行级别，0-6。
2. CentOS7后运行级别：

   - `systemctl get-default`：显示当前是什么运行级别。

   - `systemctl set-default TARGET.target`：切换运行级别（`systemctl set-default multi-user.target`，切换到3级别）。

   - `graphical.target`是图形界面级别，`multi-user.target`是运行级别3。


3. 如果重启，会是切换后的运行级别。

### root密码

找回root用户密码，CentOS7.6：

![](img/linuxroot.png)

1.重启进入该页面，按上下光标停止倒计时，再按e键进入到下面的页面并通过下向下的箭头键移动光标，找到linux16开头的：

![](img/e.png)

2.在linux16开头的后面，即UTF-8后面，先输入一个空格再输入`init=/bin/sh`。

3.然后按`Ctrl + X`，进入单用户模式。

进入单用户模式后，在光标闪烁位置输入`mount -o remount,rw / `（逗号两边不要有空格，rw后加空格后再加`/`）；如下：

![](img/单用户模式.png)

4.然后按回车，再在新一行输入`passwd`，输入后再按回车，输入密码后回车，再次输入确认密码后，按回车，密码设置完成；

![](img/passwd.png)

5.再输入`touch /.autorelabel`，回车。

6.再在新的一行输入`exec /sbin/init`，按回车后等待系统自动修改密码（可能时间有点长，耐心等待），完成后系统重启，新密码就会生效。

### 帮助指令

1. man：`man xx命令`，查询该命令的使用信息。
2. help：`help <command>`，在控制台打印出指定的命令的帮助信息。
3. info：与 man 命令相似，能够显示出命令的相关资料和信息。

# 熟悉磁盘管理

### 概述

Linux的每个分区都是组成整个文件系统的一部分，Linux的整个文件系统中包含了一整套的文件和目录；

Linux采用“载入”的处理方法，Linux将一个分区和一个目录联系起来，分区与某个目录对应。

![](img/sda.png)

### 查看挂载状况

- `lsblk`、`lsblk -f`：查看所有设备的挂载状况；

### 新磁盘分区

为新硬盘分区并挂载：

1. 对新硬盘分区：
   - `fdisk /dev/硬盘名`：硬盘名就像上面的sda，新硬盘一般是sdb，执行该命令后进入分区操作；
   - 进入后输入命令（`m`：显示命令列表；`p`：显示磁盘分区；`n`：新增分区；`d`：删除分区；`w`：写入并退出；`q`：不保存退出；）；
   - （开始分区后输入n，然后选择p，两次回车默认剩余全部空间，最后w写入并退出）。
2. 格式化磁盘：`mkfs -t ext4 /dev/分区名`；
3. 挂载，将磁盘和分区联系起来
   - `mount 设备名称 挂载目录`，例如`mount /dev/sdb1 /newdisk`；（【注意】用命令行挂载，重启后会失效）
   - 如果要实现永久挂载，就得通过修改`/etc/fstab`实现（`vim /etc/fstab`，添加，如下图，保存后退出执行`mount -a`立即生效，重启也会生效）；
   - 取消挂载（要切换到外面）：`umount 设备名称(或挂载目录)`，例如`umount /dev/sdb1`、`umount /newdisk`。

![](img/f.png)

### 查看磁盘情况

`df -h`：查看磁盘使用情况，如果使用达80%以上就得考虑清理空间或扩容；

![](img/查询.png)

- 例如`du -h --max-depth=1 /opt`、`du -ha --max-depth=1 /opt`；

### 实用指令

- `ls -l /opt | grep "^-" |wc -l`：统计/opt文件夹下文件的个数（不包括子文件夹的）；
- `ls -l /opt | grep "^d" |wc -l`：统计/opt文件夹下目录的个数；
- `ls -lR /opt | grep "^-" |wc -l`：统计/opt文件夹下全部文件的总数（递归统计）；
- `ls -lR /opt | grep "^d" |wc -l`：统计/opt文件夹下全部目录的总数（递归统计）；
- `tree 目录名`：以树状显示目录结构（如果没有tree，使用`yum install tree`安装）。

# 熟悉GCC命令







# 熟悉网络配置

## NAT网络原理

<img src="img/11.NAT.png" style="zoom:67%;" />

1. Linux虚拟机的IP地址为192.168.2.131。
2. Windows的以太网适配器 VMware Network Adapter VMnet8的IPv4 地址是192.168.2.1。
3. Linux虚拟机和VMnet8的IP相似，在linux虚拟机`ping 192.168.2.1`可以通，在Windows上ping Linux的也会通。
4. Windows的无线局域网适配器 WLAN的IPv4 地址是192.168.101.8，以太网适配器通过无线局域网适配器，然后再走网关、路由器等，就可以访问外网了。

## 查看虚拟机ip配置

1. Windows下：`ipconfig`。
2. Linux下：`ifconfig`。查看云服务器公网：`curl ifconfig.me`、`curl cip.cc`。

![](img/10.ens33.png)

网卡名称ens33，指自动被援模式，ens33下`inet 192.168.137.131`即为主机地址，远程连接就是通过该IP地址，不联网是不会显示该地址的。

- en：标识ethernet。
- o：主板板载网卡，集成是的设备索引号。
- p：独立网卡，PCI网卡。
- s：热插拔网卡，USB之类的扩展槽索引号。
- nnn（数字）：MAC地址+主板信息计算得出唯一序列。

ping用于测试主机之间的网络连通性：`ping 目的主机`，例如`ping www.baidu.com`。

## 虚拟机静态ip配置

CentOS为例：

1. 自动配置，会自动获取到IP地址，避免IP冲突（IP可能会变化，系统界面的网络连接设置可设置为自动）

2. 手动配置：`vim /etc/sysconfig/network-scripts/ifcfg-ens33`（程序员使用）

   <img src="img/12.config.png" style="zoom: 67%;" />

`vim /etc/sysconfig/network-scripts/ifcfg-ens33`，进入该文件后进行设置：

1. 需要设置的是BOOTPROTO以及最后的IP地址、网关、域名解析器，如下：

   ```bash
   TYPE=Ethernet
   PROXY_METHOD=none
   BROWSER_ONLY=no
   BOOTPROTO=static
   DEFROUTE=yes
   IPV4_FAILURE_FATAL=no
   IPV6INIT=yes
   IPV6_AUTOCONF=yes
   IPV6_DEFROUTE=yes
   IPV6_FAILURE_FATAL=no
   IPV6_ADDR_GEN_MODE=stable-privacy
   NAME=ens33
   UUID=f05d1f02-2a4c-4dd5-b886-0b594f5c7c79
   DEVICE=ens33
   ONBOOT=yes
   #IP地址
   IPADDR=192.168.137.130
   #网关
   GATEWAY=192.168.137.2
   #域名解析器
   DNS1=192.168.137.2
   ```

2. 虚拟机：设置好后，还需要在虚拟网络编辑器里设置：子网IP的前三个和上面设置的IP地址的前三个一样，网关和上面的GATEWAY一样。

   <img src="img/13.changeNetWork.png" style="zoom: 67%;" />

3. 要使设置生效：重启网络服务（`service network restart`）或重启系统（`reboot`）。

4. `ifconfig`再查看IP。

## 主机名和映射

为了记忆方便，或根据需要设置主机名：

- 查看主机名：`hostname`。
- 修改主机名：`vim etc/hostname`，进入该文件进行修改；修改后需要重启。

设置host映射，这样就可以通过主机名来ping某个系统：

- Windows下设置的方法：在`C:\Windows\System32\drivers\ect\hosts`文件中指定，指定格式`192.168.200.130 lsl`。
- Linux下设置分方法：在`/etc/hosts`文件中指定，例如`192.168.137.130 lsl`。

主机名解析：

- hosts文件：是用来存放IP与主机名的映射关系的文件。
- DNS（Domain Name System），域名系统，互联网上域名与IP地址相互映射的一个分布式数据库。

浏览器输入请求地址后的域名解析过程：

1. 浏览器先查缓存中有没有该域名解析后的IP地址，有就调用；如果没有就检测DNS缓存器，如果有就返回。（本地解析器缓存）
2. 一般情况下，电脑成功访问某个网页，在一定时间内浏览器或操作系统会缓存DNS解析记录（IP地址），
   - cmd：`ipconfig /displaydns`——查看DNS域名解析缓存；`ipconfig /flushdns`——手动清除dns缓存。
3. 没有在缓存中找到，就检查系统中的hosts文件，有就返回，没有就去访问域名服务器进行解析。

# 熟悉进程与服务

## 进程管理命令

在Linux中，每个执行的程序都是一个进程，每一个进程都有一个ID号（pid，进程号）；进程分为前台进程和后台进程。一般系统服务都以后台进程存在，并常驻。

**ps指令查看进程**

ps指令，用来参考系统中进程的执行状况、是否在执行等，可不加任何参数：

- `ps [选项]`：`-a`，显示所有进程；`-u`：以用户的格式显示进程；`-x`：显示后台进程运行参数。
- `ps -aux | grep xxx`：查看进程（服务）。

![](img/14.psall.png)

**查看父进程**

- `ps -ef | grep redis`：以全格式查看redis进程（-e：显示所有；-f：全格式），查看进程的父进程。

![](img/15.ps_ef.png)

**终止进程**

1. `kill [选项] 进程号`：通过进程号杀死进程；常用选项是`-9`，表示立刻杀死进程。
2. `killall 进程名称`：通过进程名称杀死进程，也支持通配符，在系统负载过大而变得很慢的时候有用。

案例：

1. 踢掉某个非法登录的用户：先查出用户通过ssh登录的进程号，然后执行`kill 进程号`。
   - `root 29024  0.0  0.0 112728   988 pts/0    R+   11:46   0:00 grep --color=auto ssh`。
   - `kill 29024`。

2. 终止远程登录服务，并在适当时候再次重启sshd服务：
   - 通过进程号kill掉sshd的服务。
   - 启动服务：`/bin/ststemctl start sshd.service`。
3. 终止多个gedit：`killall grdit`。
4. 强制杀掉终端：查看到进程的终端号，然后`kill -9 进程号`。

**查看进程树**

`pstree [选项]`：查看进程树；选项`-p`：显示进程的PID；`-u`：显示进程的所属用户。

- 树状形式显示进程的PID：`pstree -p`。
- 树状形式显示进程的用户名：`pstree -u`。



## 服务管理指令

service——服务是运行在后台的进程，通常都会监听端口来等待其它程序的请求，例如mysqld、sshd、防火墙等，因此又称为守护进程。

**systemctl指令：**（CentOS7后很多指令都使用这个管理）

1. 状态管理：`systemctl [start | stop | restart | status] 服务名`，对服务进行管理(立即生效但只是暂时的)，用于开启服务、停止服务、重启服务、查看服务状态等。

2. 服务查看：其管理的服务在`/usr/lib/systemd/system`目录中查看。

3. 自启动服务的查看与设置：
   1. `systemctl list-unit-files | grep enabled`：查看所有开机自启动的服务。
      
      `systemctl list-unit-files | grep 服务名`：查看服务是不是开机自启动（enabled）。
   2. `systemctl enable 服务名`：设置服务开机自启动（永久生效）。
   3. `systemctl disable 服务名`：停止服务开机自启动（永久生效）。

## 防火墙

### CentOS的

**关闭防火墙服务**：（firewalld.service）

- `systemctl disable firewalld.service`：从开机自启动中移除。（服务名可不加.service）

- `systemctl stop firewalld.service`：关闭防火墙服务。

- `systemctl start firewalld.service`：开启防火墙服务。

**firewall——用于设置防火墙服务：**（防火墙未关闭时才能设置防火墙）

1. 打开端口：`firewall-cmd --permanent --add-port=端口号/协议`。（一般都是tcp协议）
2. 关闭端口：`firewall-cmd --permanent --remove-port=端口号/协议`。
3. 防火墙重新载入（使打开或关闭端口生效）：`firewall-cmd --reload`。
4. 查询端口开发状态：`firewall-cmd --query-port=端口/协议`。

![](img/firewalld.png)

Windows的telnet需要在Windows功能里开启 Telnet Client。

1. `firewall-cmd --reload`：重载规则。
2. `firewall-cmd --list-all`：查看已配置规则。
3. `firewall-cmd --permanent --add-rich-rule="rule family="ipv4" source address="192.168.44.101" port protocol="tcp" port="8080" accept"`：允许该ip（192.168.44.101）访问指定端口。
4. `firewall-cmd --permanent --remove-rich-rule="rule family="ipv4" source address="192.168.44.101" port port="8080" protocol="tcp" accept"`：移除规则。

### Ubuntu的

Ubuntu的防火墙是ufw：

- 安装：`sudo apt install ufw`。
- 查看是否开启：`sudo ufw status verbose`，显示状态为不活动则是未开启防火墙，同时也会显示出设置了的允许外部访问的端口。
- 开启：`sudo ufw enable`。
- 关闭：`sudo ufw disable`。
- 默认配置：`sudo ufw default deny`，设置默认的 incoming 策略更改为 deny（表示关闭所有外部对本机的访问，安装防火墙开启后的默认策略也是这个）。

打开或关闭端口：

```c
sudo ufw allow 53   // 允许外部访问53端口(tcp/udp)

sudo ufw allow 3690 // 允许外部访问3690端口(svn)

sudo ufw allow from 192.168.1.111   // 允许此IP访问所有的本机端口

sudo ufw allow proto tcp from 192.168.0.0/24 to any port 22  // 允许指定的IP段访问特定端口

sudo ufw delete allow smtp // 删除上面建立的某条规则，比如删除svn端口就是 sudo ufw delete allow 3690 
```



## 动态监控进程

`top [选项]`：

- 用来显示正在执行的线程，执行一段时间可以更新正在运行的进程（与ps命令的区别），执行后按q可以退出。
- 选项：`-d 秒数`：指定top命令每隔几秒更新，默认是3秒；`-i`：不显示任何闲置或僵死进程；`-p`：通过指定监控进程ID来监控某个进程。

进入top后的交互：

1. 输入P：以CPU使用率排序（默认的）。
2. 输入M：以内存的使用率排序。
3. 输入N：以PID排序。
4. 输入q：退出top。
5. 输入u后回车再输入用户名：监视特定用户。
6. 输入k回车再输入要结束的进程的ID号：终止指定的进程。

## 监控网络状态

1. `netstat [选项]`：用来查看网络情况；（`-an`：按一定顺序排列输出；`-p`：显示哪个进程在调用）。
2. `ping 对方的ip地址`：检测远程主机是否正常，检测两部主机间的网线或网卡故障。

# 软件包管理

## CentOS下

### rpm

RPM  是Red-Hat Package Manager（红帽软件包管理器）的缩写，用于互联网下载包的打包及安装，rpm生成具有.rpm拓展名的文件；（这一文件格式名称虽然打上了RedHat的标志，但是其原始设计理念是开放式的，包括OpenLinux、S.u.S.E.以及Turbo Linux等Linux的分发版本都有采用，可以算是公认的行业标准了）。

![](img/rpm.png)

rpm包查询：

1. `rpm -qa [| grep/more xx]`：查询已安装的rmp包。（query all）
2. `rpm -qi 软件包名`：查询软件包的信息，例如`rpm -qi firefox`。（query info）
3. `rpm -ql 软件包名`：显示软件包中的全部文件。（query list）
4. `rpm -qf 文件全路径名`：查询某目录下文件所属的软件包。

rpm包卸载：

1. `rpm -e RMP包的名称(名称可以不写全)`：卸载rpm包，如果该包被依赖则删除会失败。
2. `rpm -e --nodsps RMP包的名称`：忽略依赖强制删除rpm包（不推荐）。

安装rpm包：

1. `rpm -ivh RPM包的全路径名称`：i是install，v是verbose（提示），h是hash（进度条）。
2. 例如：`rpm -ivh /opt/firefox-60.2.2-1.el7.centos.x86_64.rpm `，安装火狐（输入rpm包所在目录后输入头部的一些信息再按tab键可快速补全）。

### yum

yum：一个shell前端软件包管理器，基于rpm包管理，能够从指定的服务器自动下载rpm包并安装，可以自动处理依赖性关系，并且一次安装所有依赖的软件包。

1. `yum list | grep xxx软件(或软件列表)`：用于查询yum服务器是否有该软件的软件包，如果已经安装了会在显示信息后面标有“installed”（已安装）。（`yum list | grep mysql`）

2. `yum install xxx`：用于从服务器下载并安装指定的软件。

| 命令                           | 说明                     |
| ------------------------------ | ------------------------ |
| **yum check-update**           | 列出所有可更新的软件清单 |
| **yum update**                 | 更新所有软件             |
| **yum install <package_name>** | 仅安装指定的软件         |
| **yum update <package_name>**  | 仅更新指定的软件         |
| **yum list**                   | 列出所有可安裝的软件清单 |
| **yum remove <package_name>**  | 删除软件包               |
| **yum search < keyword >**     | 查找软件包               |

 清除缓存命令：

- **yum clean packages**：清除缓存目录下的软件包
- **yum clean headers**：清除缓存目录下的 headers
- **yum clean oldheaders**：清除缓存目录下旧的 headers
- **yum clean, yum clean all (= yum clean packages; yum clean oldheaders)** ：清除缓存目录下的软件包及旧的 headers

## Ubuntu下

摘自：[Ubuntu安装软件有这5种方法 - 知乎 (zhihu.com)](https://zhuanlan.zhihu.com/p/270908077)。

### apt

不只Ubuntu，其实Debian系统的系统（Debian，Ubuntu，Deepin，Raspbian等）都可以使用apt命令安装软件。

在Ubuntu 16 之前要使用`apt-get install 软件包`来安装，**在Ubuntu 16 之后官方建议直接使用`apt install 软件包`来安装。**

`apt` 命令用法：

1. 更新软件列表：`apt update -y`
2. 搜索软件: `apt search 关键字`
3. 显示软件包详情：`apt show 软件包名`
4. 安装软件：`apt install 软件包名`
5. 升级指定软件：`apt upgrade 软件包名`
6. 升级所有可以升级的软件：`apt upgrade`
7. 卸载软件：`apt remove 软件包名`
8. 卸载软件并移除软件依赖：`apt autoremove 软件包名`
9. 卸载软件并删除配置文件：`apt remove 软件包名 --purge`

示例——安装gimp：

```c
sudo apt install gimp -y
```

### snap

`snap`是在Ubuntu 16 新添加的一种软件包格式。这种格式把软件运行所需的依赖全部打包到软件包里面， 运行的时候持载到一个虚拟的环境里面运行。所有这种格式的软件包**安装时不会破坏系统现有的软件包依赖**。

`snap`命令用法：

1. 搜索软件包：`snap find 关键字`
2. 显示软件包详情：`snap info 软件包名`
3. 安装软件包：`snap install 软件包名`
4. 升级指定软件：`snap refresh 软件包名`
5. 升级所有可以升级的软件：`snap refresh`
6. 卸载软件：`snap remove 软件包名`

也是直接在终端运行命令就可以安装，比如使用下面的命令安装wps:

```bash
sudo snap install wps-2019-snap
```

### dpkg命令

上面3种方法都只能安装已经添加的软件源里面的软件。但像网易云音乐、百度网盘这些并没有在软件源里面，而是在官网提供deb后缀的软件包下载，这种软件我们就要用到dpkg命令来安装了。

```bash
sudo dpkg -i 文件名.deb
```

### 源码编译安装





# 熟悉CentOS的日志

**日志管理**

![](img/日志.png)

日志管理服务：

![](img/日志管理服务配置.png)

![](img/日志类型.png)

rsyslogd服务：

- `ps aux | grep "rsyslogd" | grep -v "grep" `：查询服务是否启动。
- `systemctl list-unit-files | grep rsyslog`：查询服务自启动状态。

自定义日志服务：

1. /var/log目录下新建日志文件。
2. 配置rsyslogd。

日志轮替：

![](img/日志轮替.png)

![](img/日志轮替配置.png)

自定义日志轮替：

![](img/日志轮替参数.png)

![](img/日志轮替加入.png)

日志轮替机制：

依赖系统定时任务，/rtc/cron.daily/目录下有一个可执行的logrotate文件，日志轮替通过这个可执行文件定时执行任务。

内存日志：

![](img/内存日志.png)

# 熟悉应用部署

## Web服务环境配置

### 安装JDK

在Linux下，只需解压并配置好环境变量即可。

![](img/installJDK.png)



1. vim /etc/profile
2. export JAVA_HOME=/usr/local/java/jdk1.8.0_xxx
3. export CLASSPATH=.:$JAVA_HOME/lib/dt.jar:$JAVA_HOME/lib/tools.jar
4. exoprt PATH=$JAVA_HOME/bin:$PATH
5. source /etc/profile

### 安装Tomcat

1. 安装好JDK并配置好环境变量。
2. 解压压缩包，移动：`mv xx /usr/local/tomcat`。
3. 进入Tomcat的bin目录，`vim setclasspath.sh`配置JAVA_HOME。
4. 进入Tomcat的bin目录，执行`sudo ./startup.sh`。
5. 确保端口开放。
6. 设置开机重启：`systemctl enable 服务名称`。
7. 关闭Tomcat：进入Tomcat的bin目录，执行`sudo ./shutdown.sh`。

### 安装配置MySQL

1. 下载地址：[MySQL :: Download MySQL Community Server (Archived Versions)](https://downloads.mysql.com/archives/community/)；
2. 解压到/opt/mysql目录下；
3. 卸载centos7.6自带的类MySQL数据库mariadb：
   - `rpm -qa | grep mari`：查询相关安装包；
   - `rpm -e --nodeps mariadb-libs`：卸载相关安装包；
4. 安装MySQL5.7：
   1. `npm -ivh mysql-community-common-5.7.26-1.el7.x86_64.rpm`。
   2. `npm -ivh mysql-community-libs-5.7.26-1.el7.x86_64.rpm`。
   3. `npm -ivh mysql-community-client-5.7.26-1.el7.x86_64.rpm`。
   4. `npm -ivh mysql-community-server-5.7.26-1.el7.x86_64.rpm`。
5. 启动MySQL：`systemctl start mysqld.service`。
6. 设置root密码，MySQL自动给root用户设置随机密码，`grep "password" /var/log/mysqld.log`——查看密码。



## 应用部署





## 代码更新



# 了解目录结构

**Linux目录结构**

Linux的文件系统：采用层级式的树状目录结构，最上层是根目录`/`，然后在此目录下再创建其它的目录。

Linux世界里，一切皆文件！（Linux把硬件都当作文件来处理）。

**具体的目录结构（不用背，知道即可，要记住呗。。）：**

1. `/bin`：**常用**，是Binary的缩写，存放经常使用的命令。（/usr/bin、/usr/local/bin）
2. `/sbin`：s就是Super User的意思，存放的是系统管理员使用的系统管理程序。(/usr/sbin、/usr/local/sbin) 
3. `/home`：**常用**，存放普通用户的主目录，在Linux中每个用户都有一个自己的目录，一般该目录名是以账户的账号名命名。
4. `/root`：**常用**，该目录为系统管理员，也称为超级权限者的用户主目录。
5. `/lib`：系统开机所需要的最基本的动态连接共享库，作用类似于Windows里的DLL文件，几乎所有的应用程序都需要用到这些共享库。
6. `/lost+foubd`：该目录一般是空的，被隐藏起来的，当系统非法关机后，这里就存放了一些文件。
7. `/etc`：**常用**，所有的系统管理所需要的配置文件和子目录my.conf。
8. **`/usr`**：**常用**，这是一个非常重要的目录，用户的很多应用程序和文件都放在这个目录下，类似与windows下的program files目录。
9. `/boot`：**常用**，存放的是启动Linux时使用的一些核心文件，包括一些连接文件以及镜像文件。
10. `/proc`：**不能动**，动的话可能会造成系统崩溃，这个目录是一个虚拟的目录，它是系统内存的映射，访问这个目录来获取系统信息。
11. `/srv`：**不能动**，service的缩写，该目录存放一些服务启动之后需要提取的数据。
12. `/sys`：**不能动**，这是linux2.6内核的一个很大的变化。该目录下安装了2.6内核中新出现的一个文件系统sysfs。
13. `/tmp`：这个目录是用来存放一些临时文件的。
14. `/dev`：类似windows的设备管理器，把所有的硬件用文件的形式存储。
15. `/media`：**常用**，linux系统会自动识别一些设备，例如U盘光驱等等，当识别后，linux会把识别的设备挂载到这个目录下。
16. `/mnt`：**常用**，系统提供该目录是为了让用户临时挂载别的文件系统的，我们可以将外部的存储挂载在/mnt/上，然后进入该目录就可以查看里面的内容了。
17. **`/opt`**：
    - 这是给主机额外安装软件所存放的目录，如安装ORACLE数据库就可放到该目录下。默认为空；
    - 约定俗成，要安装的软件下载好先拷贝到该目录。
18. **`/usr/local`**：**常用**，这是一个给主机额外安装软件的目录，用于安装额外的软件，一般是通过编译源码的方式安装的程序。
19. **`/var`**：**常用**，这个目录中存放着在不断扩充着的东西，习惯将经常被修改的目录放在这个目录下，包括各种日志文件。
20. `/selinux`：security-ehhanced Linux，SELinux是一种安全子系统，它能控制程序只能访问特定文件，有三种工作模式，可以自行设置，不启用则看不到该目录。

**总结：**

1. Linux的目录中有且只有一个根目录。
2. Linux的各个目录存放的内容是规划好，不用乱放文件。
3. Linux是以文件的形式管理我们的设备，因此linux系统，一切皆为文件。
4. 对Linux的各个文件目录下存放什么内容，必须有一个认识。

|         常用目录         |                             描述                             |
| :----------------------: | :----------------------------------------------------------: |
| /usr/bin、/usr/local/bin |            bin是Binary的缩写，存放经常使用的命令             |
|          /home           | 存放普通用户的主目录，在Linux中每个用户都有一个自己的目录，<br/>一般该目录名是以账户的账号名命名 |
|          /root           |       该目录为系统管理员，也称为超级权限者的用户主目录       |
|           /etc           | 所有的系统管理所需要的配置文件和子目录，比如安装mysql数据库的my.conf配置文件 |
|         **/usr**         | 这是一个非常重要的目录，用户的很多应用程序和文件都放在这个目录下，<br/>类似与windows下的program files目录 |
|          /boot           | 存放的是启动Linux时使用的一些核心文件，包括一些连接文件以及镜像文件 |
|          /media          | linux系统会自动识别一些设备，例如U盘光驱等等，当识别后，linux会把识别的设备挂载到这个目录下 |
|           /mnt           | 系统提供该目录是为了让用户临时挂载别的文件系统的，我们可以将外部的存储挂载在/mnt/上，<br/>然后进入该目录就可以查看里面的内容了，例如用虚拟机创建的共享文件D:/myshare |
|      **/usr/local**      | 这是另一个给主机额外安装软件所安装的目录，一般是通过编译源码的方式安装的程序 |
|         **/var**         | 这个目录中存放着会不断扩充着的东西，习惯将经常被修改的目录放在这个目录下，包括各种日志文件 |
|         **/opt**         | - 这是给主机额外安装软件所存放的目录，如安装ORACLE数据库就可放到该目录下。默认为空；<br/>- 约定俗成，要安装的软件下载好先拷贝到该目录。 |

# 用户组、权限、任务调度

## 用户组管理

每个用户都属于某一个组。

对于文件（或目录）：所有者（该文件的所有者是哪个用户），所在组（文件所有者属于的组），其它组（文件所有者所属的组外的组）。

**组设置与查看：**

| 命令                                        | 说明                                             |
| ------------------------------------------- | ------------------------------------------------ |
| groupadd 组名                               | 新增组                                           |
| groupdel 组名                               | 删除组                                           |
| cat /etc/group、`cat /etc/group |grep 组名` | 查看组信息，一般来说，新创建的组在显示结果的最后 |
| ls -ahl                                     | 可查看到文件或用户的所有者、所在组               |

**更改：**

| 命令                       | 说明                                                         |
| -------------------------- | ------------------------------------------------------------ |
| usermod -g 用户组 用户名   | 修改用户所属组                                               |
| `useradd -g 用户组 用户名` | 新建用户并指定用户所在组                                     |
| chgrp 组名 文件名或目录    | 修改文件所在组（chgrp后加`-R`可以递归修改目录及目录下文件所属的组） |
| `usermod -d 目录名 用户名` | 改变用户所在组并指定用户登录后所在的工作目录（前提要有访问此目录的权限） |

![](img/16.ls-lah.png)

## 权限管理

**权限说明：**

![](img/rwx.png)

- `-`：在第0位的时的`-`，表示这是个普通文件。
- 第2、3、4点表示的位置需要用`rwx`和`-`表示，如果某位置用`-`则表示没有该权限；关于rwx权限的解释如下：
- ![](img/grouprwx.png)

**权限与权限数：**

![](img/ls.png)

**变更权限的方式：**（chmod：change mode，改变状态）

![](img/chmod.png)

- `=`表示赋予权限（可同时赋予多个），`+`表示给某个对象添加某个权限（单个赋予），`-`表示收回、去除某个权限。

还可以通过数字变更权限：

- `r`是4、`w`是2、`x`是1，组合成1-7表示7个权限搭配，rwx = 4 + 2 + 1 = 7。
- `chmod 751 文件或目录`：给u（所有者）7、给g（所有组）5、给o（其它组）1的权限，相当于`chmod u=rwx,g=rx,o=x`。
- `chmod 75 文件或目录`：当只指定一个或两个数字时，默认前面的为0（没有权限）来补满三个数。

**修改文件所有者：**（change owner）

- `chown 新的所有者(用户) 文件/目录`：改变所有者。
- `chown -r 新的所有者(用户) 目录`：递归修改目录及目录下的文件的所有者。
- `chown 新的所有者(用户):新的组 文件/目录`：改变文件或目录的所有者和所在组，也可以使用`-R`来更改目录下所有文件或目录的所有者、所在组。



## 任务调度

Linux后台运行着一个用于管理任务调度的程序，可以利用其执行特定时间段的命令（任务调度就是指某个时间执行的特定命令或程序）。

### crontab（计时器）

- `crontab [选项]`：常用选项`-e`（编辑crontab 定时任务）、`-l`（查询crontab 任务）、`-r`（删除当前用户所有的crontab任务）。
- 执行的任务是命令或.sh脚本。

![](img/crontab.png)

![](img/特殊符号.png)

**任务调度的用处：**

- 用来定时执行某些指令：执行`crontab -e`后进入任务调度设置界面，`i`切换到插入模式，然后就可以写任务调度指令（例如 `*/10 * * * * date >> /home/mydate.txt`），然后`:wq`保存并退出。
- 用来定时执行脚本：
  1. 编写脚本，例如`vim /home/my.sh`进入脚本编写可执行指令（例如`date >> /home/mycal.txt`和 `cal >> /home/mycal.txt`）；
  2. 给脚本增加执行权限（主要是给root用户），`chomd u+x /home/my.sh`；
  3. 执行`crontab -e`进入任务调度设置界面，增加`*/1 * * * * /home/my.sh`即可。

3. 用来定时数据库备份：`mysqldump -u root -p密码 数据库 >> /home/db.bak`；

### at

![](img/at.png)

- 执行完作业后作业会被移出。
- `at [选项] [时间]`，执行此命令后进入任务编辑，按Ctrl + D退出作业编辑（连按两次d（Ctrl + DD））。
- `atq`：查询要执行的工作任务。

![](img/at选项.png)

![](img/attime.png)

实例：

- 先执行`at 5pm + 2 days`用来添加该规则下的一次性定时任务，然后就添加任务，例如`/bin/ls /home`；
- `at now + 2 minutes`，`date >> /home/mydate.txt`；

# 熟悉shell编程

## 概述

shell负责接收用户输入，然后根据输入来找到其他程序并运行。

![](img/shellcode.png)

![](img/shell.png)

1、shell脚本一般以.sh结尾（Linux没有后缀的概念）。

2、shell脚本文件的格式：固定开头`#!/bin/bash`

  ```shell
#!/bin/bash 
脚本程序
  ```

3、shell脚本的注释：单行注释`#`，多行注释`:<<!  !`，多行注释开头和结束符要单独一行。

4、要赋予脚本权限，`chmod u+o hello.sh`。

5、脚本执行方式：

- 给予了脚本可执行权限：直接在终端输入脚本文件相对路径或绝对路径，然后回车即可执行。
- `sh 脚本`：这种情况可以不加权限就可以执行。

## shell变量

系统变量和用户自定义变量：

1、系统变量：$HOME、$PATH、$SHELL、$USER等，可使用`echo 系统变量`输出变量值；`set`命令可查看shell中所有的变量。

2、自定义变量：

  - ```bash
    #!/bin/bash 
    A=100   # 定义变量A
    unset A # 撤销变量A
    readonly B=2 # 定义静态变量B，静态变量不能被撤销
    ```

  - 定义变量规则：名称可由数字、字母、下划线组成，但不能以数字开头；变量名一般大写；等号两侧不能有空格。

  - 命令返回值返回给变量：`A=$(date)`或用反单引号``包住命令。

环境变量设置（环境变量可简单理解为全局变量）：

1. `export 变量名=变量值`：将shell变量设置为环境变量或全局变量。
2. `source 配置文件`：让修改后的配置文件立即生效。
3. `echo $变量`：查看变量的值。

位置参数变量：

1、执行脚本时可以从命令行传入参数给脚本：例如`./myshell.sh 100 200 300 ...`，可传入多个变量值。

2、脚本内接收传入变量：

  - `$n`：拿到某个传入参数，n为自然数，$0是命令本身，$1-$9代表参数1-9，如果10个以上，则使用大括号：`${10}`等。
  - `$*`：拿到所有传入的参数，把传入的参数看作是一个整体。
  - `$@`：拿到所有传入的参数，把传入的参数区分对待。
  - `$#`：拿到传入参数个数。

预定义变量：shell设计者预先定义好的变量

1. `$$`：代表当前进程进程号，可获得当前进程号（PID）。
2. `$!`：最后一个后台运行的进程号PID。
3. `$?`：最后一次命令返回的值，是0代表上一个命令执行正确，如果上一个命令执行不正确，具体的返回值由命令来绝定。

## shell运算符

1. 运算操作表达式：`$((运算式))`或`$[运算式]`、或`expr m + n`（expression：表达式，使用expr要注意运算符之间要有空格）。
2. expr相对于一个指令，要返回指令的结果使用反引号``包住指令。
3. 运算符：乘法：`\*`（使用expr才需要转义）；除：/；取余：%。
4. 推荐使用`$[运算式]`。
5. 判断符：

![](img/判断符.png)

## shell语句

if判断语句：

- `if [ condition ] then 判断后要执行的 fi`：condition前后要有空格（`[]也会出错，[ ]不会），非空返回true，0返回true，大于1返回false，fi表示语句结束；

- ```bash
  if [ "ok" = "ok" ] # 单分支
  then 
  	echo "OK"
  fi
  # 多分支
  if [ 条件判断语句 ] 
  then 
  	echo "OK"
  elif [ 条件判断语句 ] # 相对于elseif的简写
  	执行语句
  fi
  ```

case语句：

```bash
case $变量名 in # 变量值对于以下某个值就执行)下的语句，;;为一条case语句结束；*表示如果没有对应的值就执行该条语句
"1")
echo "周一"
;;
"2")
echo "周二"
;;
"3")
echo "周三"
;;
*)
echo "other..."
;;
esac # case结束
```

for循环语法1：

```bash
for 变量 in 值1 值2 值3 ...
do
程序
done # 结束
# 例子 可体会$@ $*的区别
for i in "$*"
do
echo "num is $i"
done
for i in "$@"
do
echo "num is $i"
done
```

for循环语法2：

```bash
for (( 初始值; 循环控制条件; 变量变化 )) # 支持 ++ --
do
程序
done
```

while循环：

```bash
while [ 条件判断式 ]
do
程序
done
```

read语句读取控制台的输入：

- `read [选项] [参数]`：选项有`-p`：读取值是的提示符；`-t`：读取时等待的时间；

- ```bash
  read -p "请输入一个数NUM=" num
  read -t 10 -p "请输入一个数NUMS=" nums
  echo "num="$num
  echo "nums="$nums
  ```



## shell函数

系统函数：`basename [pathname] [suffix]`  `dirname 文件绝对路径`

```bash
basename /home/mytext.txt # 会返回mytext.txt 获取路径下最后的/后面的字符
basename /home/mytext.txt .txt # 会返回mytext 获取路径下最后的/后面的字符并删除指定字符
```

```bash
dirname /home/mytext.txt # 返回最后一个/前的字符，相当于获取指定文件所在目录
```

自定义函数：

```bash
# 语法
[ function ] funname[()]
{
	action;
	[return int;] # 可以有返回值
}
# 例子
function getSum() {
	SUM=$[$n1+$n2]
	echo "和为$SUM"
}
read -p "请输入第一个数"n1
read -p "请输入第二个数"n2
# 调用
getSUM $n1 $n2
```

## shell编程案例

1. 凌晨2、3点备份数据库到`/data/backup/db`；
2. 备份开始、备份结束要有提示信息
3. 备份后文件要求以备份时间为文件名，并打包成`.tar.gz`的形式
4. 备份的同时检查是否有十天前备份的数据库文件，如果有就删除

```bash
#!/bin/bash
BACKUP=/data/backup/db
DATETIME=$(date +%Y-%m-%d_%H%M%S)
HOST=localhost
DB_USER=root
DB_PW=123456
DATABASE=mysqltest
# 创建备份目录
[ ! -d "${BACKUP}/${DATETIME}" ] && mkdir -p "${BACKUP}/$DATETIME"
# 备份数据库
mysqldump -u${DB_USER} -p${DB_PW} --host=${HOST} -q -R --databases ${DATABASE} | gzip > ${BACKUP}/$DATETIME.sql.gz
cd ${BACKUP}
tar -zcvf $DATETIME.tar.gz ${DATABASE}
# 删除备份目录
rm -rf ${BACKUP}/$DATETIME
# 删除十天前备份的数据
find ${BACKUP} -atime +10 -name ".tar.gz"
echo "备份数据库${DATABASE}成功"
```

# 记一次扩容虚拟机根目录

在VMware界面右键点击你创建的计算机进入设置，将硬盘新增到25GB，要先挂机再操作：

![](img/2.设置.png)

再启动虚拟机，使用`lsblk`查看磁盘环境：

![](img/1.新增虚拟内存.png)

看到硬盘sda有25GB内存了，然后创建一个分区sd3，操作如下：

1. 执行`fdisk /dev/sda`，进入分区操作界面；

2. 进入界面后执行`n`，开始分区；

3. 然后选择`p`，回车后再回车两次，最后执行`w`写入并退出；

4. 使用`lsblk`查看磁盘环境：（如果没出现sd3就重启一下）

   ![](img/3.分区sd3.png)

**开始扩容：**

创建物理卷，如下图操作：

![](img/4.创建物理卷.png)

查看物理卷和卷组，如下操作：

- 查看物理卷：（查看到创建的物理卷名为 /dev/sda3）

![](img/5.查看1.png)

查看卷组：（查看到卷组名为 centos）

![](img/6.查看2.png)

将物理卷加入到卷组：

![](img/7.add.png)

最后将卷组剩余空间添加到逻辑卷 /dev/centos/root ：

![](img/8.addP.png)

同步到文件系统：（之前只是对逻辑卷扩容，还要同步到文件系统，实现对根目录的扩容）

- `resize2fs /dev/mapper/centos-root`。
- `xfs_growfs /dev/centos/root`、`xfs_growfs /`。

（注意：**resize2fs 命令。针对的是ext2、ext3、ext4文件系统；xfs_growfs 命令，针对的是xfs文件系统**）

查看文件系统命令`df -hT`，如下图：

![](img/9.查看文件类型.png)

﻿#Description
The distributed operation layer (DOL) is a software development framework to program parallel applications. The DOL allows to specify applications based on the Kahn process network model of computation and features a simulation engine based on SystemC. Moreover, the DOL provides an XML-based specification format to describe the implementation of a parallel application on a multi-processor systems, including binding and mapping.

#How to install
##  1. 安装linux系统
### 用虚拟机安装ubuntu
##  2. 安装一些必要的环境
```
$ sudo apt-get update
$ sudo apt-get install ant
$ sudo apt-get install openjdk-7-jdk
$ sudo apt-get install unzip
```
## 3. 下载文件
```
$ sudo wget http://www.accellera.org/images/downloads/standards/systemc/systemc-2.3.1.tgz
$ sudo wget http://www.tik.ee.ethz.ch/~shapes/downloads/dol_ethz.zip
```
## 4. 解压文件
### 新建dol的文件夹 
```
$ mkdir dol
```
### 将dolethz.zip解压到 dol文件夹中
```
$ unzip dol_ethz.zip -d dol
```
### 解压systemc
```
$ tar -zxvf systemc-2.3.1.tgz
```
## 5. 编译systemc
### 解压后进入systemc-2.3.1的目录下
```
$ cd systemc-2.3.1
```
### 新建一个临时文件夹objdir
```
$ mkdir objdir
```
###进入该文件夹objdir
```
$ cd objdir
```
###运行configure(能根据系统的环境设置一下参数，用于编译)
```
$ ../configure CXX=g++ --disable-async-updates
```
###编译
```
$ sudo make install
```
###记录当前的工作路径(会输出当前所在路径，记下来，待会有用)
```
$ pwd
```
##6. 编译dol
###进入刚刚dol的文件夹
```
$ cd ../dol
```
###修改build_zip.xml文件,找到下面这段话，就是说上面编译的systemc位置在哪里，
```
<property name="systemc.inc" value="YYY/include"/>
<property name="systemc.lib" value="YYY/lib-linux/libsystemc.a"/>
```
###把YYY改成上页pwd的结果（注意，对于  64位 系统的机器，lib-linux要改成lib-linux64）
###然后是编译
```
$ ant -f build_zip.xml all
```
###若成功会显示build successful
###接着可以试试运行第一个例子
进入build/bin/mian路径下
```
$ cd build/bin/main
```
###然后运行第一个例子
```
$ ant -f runexample.xml -Dnumber=1
```

#实验感想
### 1. 因为这一次实验是直接下载QQ群里的Ubuntu，所以整个配置环境只能通过看实验课件和别人的问题来了解，所以配置的过程在这里就不写了；
### 2. 在进行Github的文件上传的时候，遇到了md文件无法识别中文的问题，将其保存为UTF-8格式即可；
### 3. 最后就是实验教程需要认真阅读，不要漏掉每一句关键的话，不然就有可能导致最终结果的错误。

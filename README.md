# NachOS
Operating Systems (2015 NTU EE 5173/921 U9580, Homework only)<br/>
Professor: Farn Wang<br/>
http://cc.ee.ntu.edu.tw/~farn/courses/OS/OS2015/index.htm

* Project 1: Thread Management
* Project 2: System Call & CPU Scheduling
* Project 3: Memory management


## Installation and Configuration<br/>
VMware Workstation Player<br/>
https://www.vmware.com/tw/products/workstation-player.html<br/>
Ubuntu 32-bit 16.04.6<br/>
https://releases.ubuntu.com/16.04/<br/>


## Setup<br/>
Install g++ and csh
```
sudo apt-get install g++
sudo apt-get install csh
```
Download NachOS & Cross Compiler
```
wget -d http://cc.ee.ntu.edu.tw/~farn/courses/OS/OS2015/projects/project.1/nachos-4.0.tar.gz
wget -d http://cc.ee.ntu.edu.tw/~farn/courses/OS/OS2015/projects/project.1/mips-x86.linux-xgcc.tar.gz
```
untar **nachos-4.0.tar.gz**
```
tar -xvf nachos-4.0.tar.gz
```
move **mips-x86.linux-xgcc.tar.gz** to root and untar
```
sudo mv mips-x86.linux-xgcc.tar.gz /
cd /
sudo tar -zxvf mips-x86.linux-xgcc.tar.gz
```
Change directory reference of cross compiler in ~/nachos-4.0/code/test/Makefile
```
...
GCCDIR = /mips-x86.linux-xgcc/
...
CPP = /mips-x86.linux-xgcc/cpp0
...
CFLAGS = -G 0 -c $(INCDIR) -B/mips-x86.linux-xgcc/
...
```
Make NachOS-4.0
```
cd ~/nachos-4.0/code
make
```

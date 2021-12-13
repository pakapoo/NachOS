# NachOS
Operating Systems (2015 NTU EE 5173/921 U9580, Homework only)<br/>
Professor: Farn Wang<br/>
http://cc.ee.ntu.edu.tw/~farn/courses/OS/OS2015/index.htm

* Project 1: Thread Management
* Project 2: System Call & CPU Scheduling
* Project 3: Memory management


## Software version<br/>
VMware Workstation Player<br/>
https://www.vmware.com/tw/products/workstation-player.html<br/>
Ubuntu 32-bit 16.04.6<br/>
https://releases.ubuntu.com/16.04/<br/>


## Installation and Configuration<br/>
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
tar -zxvf nachos-4.0.tar.gz
```
move **mips-x86.linux-xgcc.tar.gz** from home to root and untar
```
sudo mv mips-x86.linux-xgcc.tar.gz /
cd /
sudo tar -zxvf mips-x86.linux-xgcc.tar.gz
```
## Trouble shooting
error: /usr/local/nachos/decstation-ultrix/bin/gcc: Command not found<br/>
solution: Tracing back the code, error generated in ~/nachos-4.0/code/test/Makefile. As nachOS is referring to the incorrect directory for gcc, we need to modify the gcc directory in ~/nachos-4.0/code/test to find the one we untarred in root.
```
...
#GCCDIR = /usr/local/nachos/decstation-ultrix/bin/gcc
GCCDIR = /mips-x86.linux-xgcc/
...
```
error: gcc: installation problem, cannot exec 'cc1': No such file or directory<br/>
solution: Tracing back the code, error generated in ~/nachos-4.0/code/test/Makefile. When generating halt.o, cc1 has to be used
```
...
#CFLAGS = -G 0 -c $(INCDIR)
CFLAGS = -G 0 -c $(INCDIR) -B/mips-x86.linux-xgcc/
...
```
Also modify the cpp directory to find the one we untarred
```
...
#CPP = /lib/cpp
CPP = /mips-x86.linux-xgcc/cpp0
...
```
## Make NachOS-4.0
```
cd ~/nachos-4.0/code
make
```

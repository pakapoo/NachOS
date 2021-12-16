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
**error:** /usr/local/nachos/decstation-ultrix/bin/gcc: Command not found<br/>
**solution:** Tracing back the code, error generated in ~/nachos-4.0/code/test/Makefile. Change GCC directory to the one we untarred in root.
```
...
#GCCDIR = /usr/local/nachos/decstation-ultrix/bin/gcc
GCCDIR = /mips-x86.linux-xgcc/
...
```
**error:** gcc: installation problem, cannot exec 'cc1': No such file or directory<br/>
**solution:** Tracing back the code, error generated in ~/nachos-4.0/code/test/Makefile from the C compilation command of halt.o. cc1 is one of the gcc compiler's subprogram. Because that cc1 is not in /usr/lib/gcc/ or /usr/local/lib/gcc/, compiler is not able find it. Thus, we specified the directory with -B directory search option.
```
...
#CFLAGS = -G 0 -c $(INCDIR)
CFLAGS = -G 0 -c $(INCDIR) -B/mips-x86.linux-xgcc/
...
```
To prevent future error, make sure all subprograms that compiler driver program runs have the correct directory, including cpp, cc1, as and ld.
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
## Reference
Course website: http://cc.ee.ntu.edu.tw/~farn/courses/OS/OS2015/index.htm
GCC manual_3.16 Options for Directory Search: https://gcc.gnu.org/onlinedocs/gcc/Directory-Options.html<br/>
跟我一起写 Makefile: https://seisman.github.io/how-to-write-makefile/Makefile.pdf

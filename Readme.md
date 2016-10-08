#Distributed Operation Layer#
##Description##
The **distributed operation layer** (DOL) is a software development framework to program parallel applications. The DOL allows to specify applications based on the Kahn process network model of computation and features a simulation engine based on SystemC. Moreover, the DOL provides an XML-based specification format to describe the implementation of a parallel application on a multi-processor systems, including binding and mapping.

![DOL_1](https://cl.ly/0E1P2Q1H1s0z/DOL.jpg)



##How to install##
###Based on Linux Operating system###
The following that I use is the Ubuntu in the VMware Workstation
####Steps:
**1.Install some neccessary condition**<br>

>`$	sudo apt-get update`<br>
`$	sudo apt-get install ant`<br>
`$ 	sudo apt-get install openjdk-7-jdk`<br>
`$	sudo apt-get install unzip`<br>

**2.Download files**<br>
I just copy them into Ubuntu in the VMware,and you also can use the command line as follows

>`$	sudo wget http://www.accellera.org/images/downloads/standards/systemc/systemc-2.3.1.tgz`<br>
`$	sudo wget http://www.tik.ee.ethz.ch/~shapes/downloads/dol_ethz.zip`

**3.Unzip files into folder**<br>
At the begin with,we should new a DOL folder;Then unzip the *dolethz.zip* into the dol folder,and the same with *systemc*<br>
>`$	mkdir dol`<br>
`$	unzip dol_ethz.zip -d dol`<br>
`$	tar -zxvf systemc-2.3.1.tgz`<br>


**4.Compile the *systemc* file**<br>
Firstly,get access into the content of *systemc-2.3.1*,and new a folder *objdir* and get into it;Then use the command of *configure* to compile
>`$	cd systemc-2.3.1`<br>
`$	mkdir objdir`<br>
`$	cd objdir`<br>
`$	../configure CXX=g++ --disable-async-updates`<br>

![DOL_1](https://cl.ly/1d3Y0k384042/DOL_1.jpg)

After the compile,the content and the path are as follows:<br>
>`$	sudo make install`<br>
`$	pwd`

![DOL_2](https://cl.ly/2C183Z0n2L3c/DOL_2.jpg)
<br>
That shows my current work path is **/xinxin/systemc-2.3.1**

**5.Compile the DOL**<br>
At the beginning,modify the *build_zip.xml*<br>
find these:<br>
`<property name="systemc.inc" value="YYY/include"/>`
`<property name="systemc.lib" value="YYY/lib-linux/libsystemc.a"/>`<br>
And change the **YYY** into **YOUR** current work path

**Special Remind:** If your machine is 64-bits,Please change the *lib-linux* into *lib_linux64* !

>`$	ant -f build_zip.xml all`<br>

If it succeed,it will show *build successful* as follows


![DOL_0](https://cl.ly/0d1O2x2w1S1D/download/DOL_0.jpg)


**6.Try an example**<br>
Get into the path of *build/bin/main*, and run the first example:
`$	cd build/bin/main`<br>
`$ ant -f runexample.xml -Dnumber=1`

![DOL_3](https://cl.ly/2x3R380i0v3v/DOL_3.jpg)

The process can be show in the flow chart:
![DOL_3](https://cl.ly/180w1Y052A19/Ex_1.png)


##Experimental experience##
In general, The process of this experiment——the Installation configuration about DOL, is relatively smoothly.

Onething that I have to mention is that I met the problem of JDK downloaded incompletely.Then after **changing the cloud platform** into the Ali's,I solved this problem.

Finally,I hope my experience can help you~
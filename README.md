# Yocto

Four elements of embedded Linux
--------------------------------

Toolchain: toolchain is a compiler and other tools (like assembler, linker and loader) which is needed to create code for your target device. Everything else depends on the toolchain.

Bootloader: The program that initializes the board and loads the Linux kernel.

Kernel: This is the heart of the system, managing system resources and interfacing with hardware.

Root filesystem: Contains the libraries and programs that are run once the kernel has completed its initialization.

One more element can be collection of programs specific to your embedded application which make the device do whatever it is supposed to do, be it weigh groceries, display movies, control a robot, or fly a drone.


Poky
------------------
yocto project uses poky to build images (kernel, system and application) for targeted hardware.  

At technical level it is a combined repository of the components:  

  • Bitbake  
	• OpenEmbedded Core  
	• meta-yocto-bsp  
	• Documentation  
  
  Note: Poky does not contain binary files,it is a working example of how to build your own custom Linux distribution from source.

Metadata  
----------------
Non yocto: A set of data that describe and gives information about other data  

Yocto world:  
  Metadata refers to the build indturctions
  refers to the commands and data used to indicate what versions of software are used  
  where they are obtained from  
  what are the patches we need to apply  
  changes or additions to the software itself (patches) which are used bugs or customize the software for use in a particular situation  
  
Metadata for kernel
--------------------

How to build kernel, have to ise make commands, make conf, make modules install  
In kernel metadata, we have to which hardware we have to use, which version of kernel we have to install

Metadata is collection of  
----------------------  
	• Configuration files (.conf)  
	• Recipes (.bb and .bbappend)  
	• Classes (.bbclass)  
	• Includes (.inc)  

OpenEmbedded Project
----------------------
OpenEmbedded offers a best cross-compiler environment. it allows developers to create a complete linux distribution for embedded systems.  

See both Yocto & OpenEmbedded allows developers to create a complete linux distribution for embedded systems.  

What is the difference between OpenEmbedded and the Yocto Project?
------------------------------------------------------------------

The Yocto Project and OpenEmbedded share a core collection of metadata called openembedded-core. 

However, the two organizations remain separate, each with its own focus

OpenEmbedded provides a comprehensive set of metadata for a wide variety of architectures, features, and applications  

	Not a reference distribution  
	the mian focus of OpenEmbedded is "Designed to be the foundation for others"  

The Yocto Project focuses on providing powerful, easy-to-use, interoperable, well-tested tools, metadata, and board support packages (BSPs) for a core set of architectures and specific boards.

OpenEmbedded-Core(oe-core)
---------------------------

The Yocto Project and OpenEmbedded have agreed to work together and share a common core set of metadata(recipes, classes and associated files): oe-core

What is bitbake
----------
bitbake is a core component of the yocto project and poky  
It basically performs the same functionality as of make  
It's a task scheduler that parses python and shell script mixed code  
when tis code is parsed it generates and run the tasks, which are basically a set of steps ordered according to code's dependencies.   

steps:
1- fetch the source  
2- extract the source  
3- conf the source  

It reads recipes and follows them by fetching packages, building them and incorporating the results into bootable images.  

It keeps track of all tasks being processed in order to ensure completion, maximizing the use of processing resources to reduce build time and being predictable.  

meta-yocto-bsp
--------------
A Board Support Package (BSP) is a collection of information that defines how to support a particular hardware device, set of devices, or hardware platform

The BSP includes information about the hardware features present on the device and kernel configuration information along with any additional hardware drivers required.

The BSP also lists any additional software components required in addition to a generic Linux software stack for both essential and optional platform features.

The meta-yocto-bsp layer in Poky maintains several BSPs such as the Beaglebone, EdgeRouter, and generic versions of both 32-bit and 64-bit IA machines.

Machines supported (poky has supported for these particular machines)
-------------------
Texas Instruments BeagleBone (beaglebone)
Freescale MPC8315E-RDB (mpc8315e-rdb)
Intel x86-based PCs and devices (genericx86 and genericx86-64)
Ubiquiti Networks EdgeRouter Lite (edgerouter)

Note: To develop on different hardware, you will need to complement Poky with hardware-specific Yocto layers.

 ![poky-reference-distribution](https://user-images.githubusercontent.com/89451747/203954025-4920f117-a683-4bf2-b828-a43622ab8af0.png)




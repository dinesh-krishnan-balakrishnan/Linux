# Basic Terminology and The Linux Boot Process

**Kernel:** Considered to be the brain of the operating system, the kernel is a computer program that handles the interaction between hardware and software, as well as certain startup procedures.
>EX: Linux Kernel


**Distribution:** Also known as a *Distro*, a distribution is a collection of programs combined with a kernel to make an operating system. This includes packages, utilities, configuration, updates/patches, documentation, and support services.
>EX: Ubuntu, CentOS

**Boot Loader:** A program that sets up a minimal environment for the OS and runs its startup procedure. 
>EX: GRUB (GRand Unified Bootloader)

**Service:** A program that runs as a background process.
>EX: httpd (Listens for incoming server requests.)

**Filesystem:** A method for storing and organizing files.
>EX: NTFS (New Technology File System)

**X Window System:** Provides the framework for graphical user interfaces (GUIs), such as window movement, keyboard input, and mouse movements.

**Desktop Environment:** The GUI for the OS. All programs are part of the Desktop Environment, greatly improving user access.
>EX: GNOME 

**Command Line:** An interface for typing commands to the OS.

**Shell:** Interprets command line input and instructs the OS to perform any necessary tasks or commands.
>EX: bash

# Linux Boot Process

1. **BIOS:** The Basic Input/Output System initializes hardware and runs POST. It will then execute a partition in the 
    hard drive that contains the boot loader.
   
    * **POST:** Known as the Power On Self Test, it tests the computer's main memory. 
  
    * The BIOS is stored on a ROM chip on the motherboard. The OS controls the rest of the boot process.

2. **Boot Loader:** The first stage boot loader finds a bootable partition, searches for the 2nd stage boot loader, and launches it in the partition. The second stage boot loader (EX: GRUB) is located under */boot* and loads the kernel of the OS into RAM.
  
    * **MBR:** Known as Master Boot Record, it is the first sector of the hard disk in BIOS systems and stores the first stage boot loader in 512 bytes. 
  
    * **UEFI:** The Unified Extensible Firmware Interface is the modern version of BIOS with more features. It is referred to as the BIOS to prevent confusion. UEFI devices don't have an MBR, but know the specific location of the first stage boot loader.

3. **initramfs:** Stands for Initial RAM Filesystem,  consisting of modules needed for kernel functionality. This file system is a compressed version of an unchanged starting root directory. It is loaded into RAM by the boot loader.

4. **/sbin/init:** Mounts and pivots over to the current, real file system being used, starting system and network services. It is also responsible for keeping the system running by acting as a manager for non-kernel processes and shutting it down cleanly.
    * The current init process being used in Linux is systemd. It was created in 2011 and replaced Upstart.

5. **getty:** Stands for "Get TTY," a TTY being a text terminal. getty launches these text terminals and the command shell. 

6. **X Windows System:** The graphical user interface is finally booted as the last part of the boot process.

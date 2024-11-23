---
title: "Day-4 of DevOps"
datePublished: Fri May 03 2024 04:26:17 GMT+0000 (Coordinated Universal Time)
cuid: clvq6ab8a00010ajt6woa5w71
slug: day-4-of-devops
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1714712282257/59d8fccc-f86b-4a24-9b7c-ca88d17f68c9.jpeg
tags: linux

---

## **File System Hierarchy**

The File System Hierarchy Standard (FHS) is a way to organize files and directories on Unix-like operating systems. Here's a brief overview of the typical hierarchy:

1. **/ (Root)**: The root directory, which contains all other directories and files in the system.
    
2. **/bin (Binaries)**: Contains essential command binaries that are needed for system boot and repair. Common commands like ls, cp, mv are found here.
    
3. **/boot**: Contains files needed for booting the system, such as the kernel, bootloader configuration, and initial ramdisk (initrd).
    
4. **/dev (Devices)**: Contains device files, which are special files that represent physical or virtual devices.
    
5. **/etc (Configuration)**: Contains system-wide configuration files. This directory often includes configuration files for various services and daemons.
    
6. **/home**: Contains user home directories. Each user typically has a subdirectory here where they can store their personal files and configurations.
    
7. **/lib (Libraries)**: Contains shared libraries needed by the essential binaries in /bin and /sbin.
    
8. **/media**: Mount point for removable media such as USB drives, CDs, etc.
    
9. **/mnt (Mount)**: Mount point for temporary filesystems or mounting external filesystems.
    
10. **/opt (Optional)**: Contains optional software packages. Some third-party software may be installed here.
    
11. **/proc (Process)**: A virtual filesystem that provides information about processes and system resources.
    
12. **/root**: Home directory for the root user (superuser/administrator).
    
13. **/run**: A temporary filesystem containing runtime information such as process IDs (PIDs) and Unix domain sockets.
    
14. **/sbin (System Binaries)**: Contains essential system administration binaries, typically used by the root user.
    
15. **/srv (Service)**: Contains site-specific data served by the system.
    
16. **/sys**: A virtual filesystem that exposes information about kernel data structures.
    
17. **/tmp (Temporary)**: A directory for temporary files. Files here are typically deleted upon system reboot.
    
18. **/usr (User)**: Contains user applications and files that are not required for the system to boot or repair.
    
19. **/var (Variable)**: Contains variable data files, such as logs, spool files, and temporary files created by users or programs.
    

This hierarchy provides a standardized structure that allows different Unix-like systems to maintain consistency and compatibility. However, there may be variations between different distributions and implementations.

##   
**Linux Booting Process**

Ever pondered what transpires between pressing your system's power button and witnessing the login screen appear? Every operating system follows a boot process, a sequential series of steps leading up to the presentation of the login screen.

Let's embark on a journey through the Linux boot process, unraveling each step along the way:

![diagram.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1656719207394/-HhDhEvBu.png?auto=compress,format&format=webp align="left")

1. **BIOS (Basic Input/Output System)**: Upon system startup, the BIOS initializes hardware components and executes the Master Boot Record (MBR) located on the boot device.
    
2. **MBR (Master Boot Record)**: The MBR contains the initial boot loader code. It executes the Grand Unified Bootloader (GRUB) stored in the boot partition.
    
3. **GRUB (Grand Unified Bootloader)**: GRUB loads the Linux kernel into memory and provides a selection menu if multiple operating systems are installed. Once the kernel is loaded, control is transferred to it.
    
4. **Kernel**: The Linux kernel initializes essential hardware and mounts the root filesystem. It then executes the first user-space process, usually /sbin/init or systemd.
    
5. **Init**: The init process, or systemd on modern systems, is responsible for initializing the system and launching system services according to the configured runlevel or target.
    
6. **Runlevel**: Runlevel programs are executed from directories such as /etc/rc.d/rc\*.d/. These scripts and services are responsible for setting up the environment and running various tasks based on the system's runlevel or target.
    

![Linux: Understanding the boot process - EnableGeek](https://lh6.googleusercontent.com/xhBJETBvBAsyi1TBTf4hubzIL1l7MEdi0wDsPPqzDWWwi2Znh6RLM52aDTPPtGmQBHQ6mDQPpiggIF3AJXrpVEt5IvQvuH5KDjeQvBetAJBluuZ7GYOIgB7Lzs35DhCnAuGYWaFts_AHhk9PiiNjM1Shqksvm6yrgGg3GFu98VwSGMHY31tNukSpPw align="left")
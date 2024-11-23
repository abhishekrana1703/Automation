---
title: "How to check OS version in Linux command line"
datePublished: Thu May 09 2024 06:12:59 GMT+0000 (Coordinated Universal Time)
cuid: clvyuqmvn000m09l58s41c6jr
slug: how-to-check-os-version-in-linux-command-line
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1715235161211/cf48c1cf-af7e-4de1-9b1b-d4ea7484e82d.jpeg
tags: linux

---

Linux, an open-source operating system, comes in various distributions, each tailored to different needs. These distributions, often referred to as "distros," include popular names like SUSE, OpenSUSE, Debian, Ubuntu, CentOS, Arch, Fedora, and RHEL. Understanding your Linux distribution and its version is crucial for timely security updates, ensuring the security of your system.

## Check os version in Linux

The procedure to find os name and version on Linux:

1. Open the terminal application (bash shell)
    
2. For remote server login using the ssh: **<kbd>ssh user@server-name</kbd>**
    
3. Type any one of the following command to find os name and version in Linux:`$ cat /etc/os-release   $ lsb_release -a   $ hostnamectl`
    
4. Type the following command to find Linux kernel version:`$ uname -r`
    

Let us see all examples in details for common Linux distros.

### The /etc/os-release file

Type the following cat command to view the /etc/os-release file:[  
`$`](https://www.cyberciti.biz/faq/linux-unix-appleosx-bsd-cat-command-examples/) `cat /etc/os-release`  
Here is what I see:  
Sample outputs:

`test-server@testserver-VirtualBox:~$ cat /etc/os-release NAME="Ubuntu" VERSION="20.04.6 LTS (Focal Fossa)" ID=ubuntu ID_LIKE=debian PRETTY_NAME="Ubuntu 20.04.6 LTS" VERSION_ID="20.04" HOME_URL="`[`https://www.ubuntu.com/`](https://www.ubuntu.com/)`" SUPPORT_URL="`[`https://help.ubuntu.com/`](https://help.ubuntu.com/)`" BUG_REPORT_URL="`[`https://bugs.launchpad.net/ubuntu/`](https://bugs.launchpad.net/ubuntu/)`" PRIVACY_POLICY_URL="`[`https://www.ubuntu.com/legal/terms-and-policies/privacy-policy`](https://www.ubuntu.com/legal/terms-and-policies/privacy-policy)`" VERSION_CODENAME=focal UBUNTU_CODENAME=focal`

We can filter out information such as OS version and name using the `grep command/egrep` command as follows:[  
`$`](https://www.cyberciti.biz/faq/grep-regular-expressions/) `grep '^VERSION' /etc/os-release   $ grep -E '^(VERSION|NAME)=' /etc/os-release`  
Here is what we see:

`test-server@testserver-VirtualBox:~$ grep -E '^(VERSION|NAME)=' /etc/os-release NAME="Ubuntu" VERSION="20.04.6 LTS (Focal Fossa)" test-server@testserver-VirtualBox:~$`

Even tiny Linux distro such as Alpine Linux provide the required OS (Operating system) information, including version:

`PRETTY_NAME="Ubuntu 20.04.6 LTS" VERSION_ID="20.04" HOME_URL="`[`https://www.ubuntu.com/`](https://www.ubuntu.com/)`" SUPPORT_URL="`[`https://help.ubuntu.com/`](https://help.ubuntu.com/)`" BUG_REPORT_URL="`[`https://bugs.launchpad.net/ubuntu/`](https://bugs.launchpad.net/ubuntu/)`"`

### Checking OS version on Linux using the lsb\_release command

**Prerequisite**  
By default, `lsb_releas`e command may not be installed on your system. Hence, use the apk command on Alpine Linux, dnf command/yum command on RHEL & co, apt command/apt-get command on Debian, Ubuntu & co, zypper command on SUSE/OpenSUSE, pacman command on Arch Linux to install the `lsb_release.`

The lsb\_release command gives [LSB](https://en.wikipedia.org/wiki/Linux_Standard_Base) [(Li](https://en.wikipedia.org/wiki/Linux_Standard_Base)nux Standard Base) and distribution-specific information on the CLI. The syntax is:  
`$ lsb_release -a`

Sample outputs:

`test-server@testserver-VirtualBox:~$ lsb_release -a No LSB modules are available. Distributor ID: Ubuntu Description: Ubuntu 20.04.6 LTS Release: 20.04 Codename: focal test-server@testserver-VirtualBox:~$`

### hostnamectl command

Use the `hostnamectl` command to query and change the system hostname and related settings. Just type the following command to check OS name and Linux kernel version. For example:  
`$ hostnamectl`  
And it will give info as follows. Look out for “Operating System” and “Kernel“:

`test-server@testserver-VirtualBox:~$ hostnamectl Static hostname: testserver-VirtualBox Icon name: computer-vm Chassis: vm Machine ID: a5746980b66d448cb2b99d1faa593b16 Boot ID: 7fb7f5dde1aa408bb0882ede0e5977d9 Virtualization: oracle Operating System: Ubuntu 20.04.6 LTS Kernel: Linux 5.15.0-105-generic Architecture: x86-64 test-server@testserver-VirtualBox:~$`

### uname command

Just print Linux kernel version, run the following uname command:  
`$ uname -r`

Sample outputs:

`test-server@testserver-VirtualBox:~$ uname -r 5.15.0-105-generic test-server@testserver-VirtualBox:~$`

Another option is to type the following `cat/more` or `less`:

`cat /proc/version`

`test-server@testserver-VirtualBox:~$ cat /proc/version Linux version 5.15.0-105-generic (buildd@lcy02-amd64-054) (gcc (Ubuntu 9.4.0 1ubuntu1~20.04.2) 9.4.0, GNU ld (GNU Binutils for Ubuntu) 2.34) #115~20.04.1-Ubuntu SMP Mon Apr 15 17:33:04 UTC 2024 test-server@testserver-VirtualBox:~$`

### The /etc/issue file

Use more command/less command as follows to display the contains of the `/etc/issue`:[  
`$ cat /et`](https://www.cyberciti.biz/faq/howto-change-login-message/)`c/issue   $ more /etc/issue   $ less /etc/issue`  
Some distros like Debian can show minor version using the `/etc/debian_version` file:  
`$ cat /etc/debian_version`

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1715234743188/695421db-1606-49de-a1b2-dd777d40dbb3.png align="center")

### Getting help

You can also view the manual page on uname using the following man command:  
`$ man hostnamectl   $ man lsb_release   $ man uname   $ man cat`
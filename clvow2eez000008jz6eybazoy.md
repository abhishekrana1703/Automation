---
title: "Day-2 of DevOps"
datePublished: Thu May 02 2024 06:52:26 GMT+0000 (Coordinated Universal Time)
cuid: clvow2eez000008jz6eybazoy
slug: day-2-of-devops
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1714632714567/fdcdaf39-dfb5-4ae3-90bf-47466344f1df.jpeg
tags: linux

---

### **Listing commands**

### **File Management:**

1. **ls**: List directory contents.
    
    * Example: `ls`, `ls -l`, `ls -a`
        
2. **cd**: Change directory.
    
    * Example: `cd /path/to/directory`
        
3. **pwd**: Print name of current/working directory.
    
    * Example: `pwd`
        
4. **mkdir**: Make directories.
    
    * Example: `mkdir new_directory`
        
5. **rmdir**: Remove empty directories.
    
    * Example: `rmdir directory_name`
        
6. **rm**: Remove files or directories.
    
    * Example: `rm file.txt`, `rm -rf directory`
        
7. **cp**: Copy files and directories.
    
    * Example: `cp file.txt /path/to/destination`, `cp -r directory /path/to/destination`
        
8. **mv**: Move or rename files and directories.
    
    * Example: `mv file.txt new_location`, `mv old_name new_name`
        
9. **touch**: Create an empty file or update timestamp.
    
    * Example: `touch file.txt`
        
10. **cat**: Concatenate and display files.
    
    * Example: `cat file.txt`
        
11. **head**: Output the first part of files.
    
    * Example: `head file.txt`, `head -n 10 file.txt` (display first 10 lines)
        
12. **tail**: Output the last part of files.
    
    * Example: `tail file.txt`, `tail -n 10 file.txt` (display last 10 lines)
        
13. **more**: File perusal filter for crt viewing.
    
    * Example: `more file.txt`
        
14. **less**: Opposite of more.
    
    * Example: `less file.txt`
        
15. **ln**: Create soft or hard links.
    
    * Example: `ln -s /path/to/file link_name`
        
16. **find**: Search for files and directories.
    
    * Example: `find /path/to/search -name "*.txt"`
        
17. **locate**: Find files by name.
    
    * Example: `locate filename`
        
18. **grep**: Print lines matching a pattern.
    
    * Example: `grep "pattern" file.txt`
        
19. **sed**: Stream editor for filtering and transforming text.
    
    * Example: `sed 's/old/new/' file.txt`
        
20. **awk**: Pattern scanning and processing language.
    
    * Example: `awk '{print $1}' file.txt` (print first column)
        
21. **sort**: Sort lines of text files.
    
    * Example: `sort file.txt`
        
22. **cut**: Remove sections from each line of files.
    
    * Example: `cut -d',' -f1 file.csv` (cut first column from CSV file)
        
23. **wc**: Print newline, word, and byte counts for each file.
    
    * Example: `wc file.txt`
        
24. **tar**: Tape archive utility.
    
    * Example: `tar -czvf archive.tar.gz /path/to/directory`
        
25. **zip/unzip**: Package and compress (uncompress) files.
    
    * Example: `zip -r` [`archive.zip`](http://archive.zip) `directory`, `unzip` [`archive.zip`](http://archive.zip)
        

### **Process Management:**

26. **ps**: Report a snapshot of the current processes.
    
    * Example: `ps aux`
        
27. **top**: Display and update sorted information about processes.
    
    * Example: `top`
        
28. **kill**: Send a signal to a process.
    
    * Example: `kill PID`
        
29. **killall**: Kill processes by name.
    
    * Example: `killall process_name`
        
30. **pkill**: Send a signal to a process by name.
    
    * Example: `pkill -9 process_name`
        
31. **nice**: Set the priority of a command or job.
    
    * Example: `nice -n 10 command`
        
32. **renice**: Alter priority of running processes.
    
    * Example: `renice +10 -p PID`
        
33. **bg**: Put a process in the background.
    
    * Example: `bg`
        
34. **fg**: Bring a process to the foreground.
    
    * Example: `fg`
        
35. **jobs**: List active jobs.
    
    * Example: `jobs`
        

### **System Information:**

36. **uname**: Print system information.
    
    * Example: `uname -a`
        
37. **hostname**: Print or set the system's host name.
    
    * Example: `hostname`
        
38. **whoami**: Print effective user ID.
    
    * Example: `whoami`
        
39. **w**: Show who is logged on and what they are doing.
    
    * Example: `w`
        
40. **last**: Show last logged in users.
    
    * Example: `last`
        
41. **uptime**: Show how long the system has been running.
    
    * Example: `uptime`
        
42. **free**: Display amount of free and used memory in the system.
    
    * Example: `free -m`
        
43. **df**: Report file system disk space usage.
    
    * Example: `df -h`
        
44. **du**: Estimate file space usage.
    
    * Example: `du -sh /path/to/directory`
        
45. **lscpu**: Display CPU information.
    
    * Example: `lscpu`
        
46. **lsusb**: Display USB information.
    
    * Example: `lsusb`
        
47. **lspci**: Display PCI information.
    
    * Example: `lspci`
        
48. **lsblk**: List information about all available block devices.
    
    * Example: `lsblk`
        

### **Network:**

49. **ifconfig**: Configure a network interface.
    
    * Example: `ifconfig`
        
50. **ip**: Show or manipulate routing, devices, policy routing, and tunnels.
    
    * Example: `ip addr show`
        
51. **ping**: Send ICMP ECHO\_REQUEST to network hosts.
    
    * Example: `ping` [`google.com`](http://google.com)
        
52. **traceroute**: Print the route packets trace to network host.
    
    * Example: `traceroute` [`google.com`](http://google.com)
        
53. **netstat**: Print network connections, routing tables, interface statistics, masquerade connections, and multicast memberships.
    
    * Example: `netstat -tuln`
        
54. **nslookup/dig**: Query Internet name servers interactively or non-interactively.
    
    * Example: `dig` [`example.com`](http://example.com)
        
55. **host**: DNS lookup utility.
    
    * Example: `host` [`google.com`](http://google.com)
        
56. **wget/curl**: Non-interactive network downloader.
    
    * Example: `wget` [`https://example.com/file`](https://example.com/file), `curl -O` [`https://example.com/file`](https://example.com/file)
        
57. **ssh**: OpenSSH SSH client (remote login program).
    
    * Example: `ssh user@host`
        
58. **scp**: Secure copy (remote file copy program).
    
    * Example: `scp file.txt user@host:/path/to/destination`
        
59. **ftp/sftp**: File Transfer Protocol (FTP/SFTP) client.
    
    * Example: `ftp` [`ftp.example.com`](http://ftp.example.com), `sftp user@host`
        
60. **telnet**: User interface to the TELNET protocol.
    
    * Example: `telnet` [`example.com`](http://example.com)
        
61. **nc**: Netcat - networking utility for reading/writing network connections.
    
    * Example: `nc -l 1234` (listen on port 1234)
        

### **System Configuration:**

62. **sudo**: Execute a command as another user.
    
    * Example: `sudo command`
        
63. **su**: Run a shell with substitute user and group IDs.
    
    * Example: `su - username`
        
64. **useradd**: Create a new user or update default new user information.
    
    * Example: `useradd newuser`
        
65. **userdel**: Delete a user account and related files.
    
    * Example: `userdel username`
        
66. **usermod**: Modify a user account.
    
    * Example: `usermod -aG groupname username`
        
67. **groupadd**: Create a new group.
    
    * Example: `groupadd newgroup`
        
68. **groupdel**: Delete a group.
    
    * Example: `groupdel groupname`
        
69. **groupmod**: Modify a group.
    
    * Example: `groupmod -n newname oldname`
        
70. **passwd**: Update a user's authentication tokens.
    
    * Example: `passwd username`
        
71. **chown**: Change file owner and group.
    
    * Example: `chown user:group file.txt`
        
72. **chgrp**: Change group ownership.
    
    * Example: `chgrp groupname file.txt`
        
73. **chmod**: Change file mode bits.
    
    * Example: `chmod 755 file.txt`
        
74. **ulimit**: Set or display process resource limits.
    
    * Example: `ulimit -n 1024`
        
75. **sysctl**: Configure kernel parameters at runtime.
    
    * Example: `sysctl -a`
        

### **Text Processing:**

76. **grep**: Print lines matching a pattern.
    
    * Example: `grep "pattern" file.txt`
        
77. **sed**: Stream editor for filtering and transforming text.
    
    * Example: `sed 's/old/new/g' file.txt`
        
78. **awk**: Pattern scanning and processing language.
    
    * Example: `awk '{print $1}' file.txt`
        
79. **sort**: Sort lines of text files.
    
    * Example: `sort file.txt`
        
80. **uniq**: Report or omit repeated lines.
    
    * Example: `uniq file.txt`
        
81. **tr**: Translate or delete characters.
    
    * Example: `echo "hello" | tr "[:lower:]" "[:upper:]"`
        
82. **wc**: Print newline, word, and byte counts for each file.
    
    * Example: `wc -l file.txt`
        
83. **head**: Output the first part of files.
    
    * Example: `head file.txt`
        
84. **tail**: Output the last part of files.
    
    * Example: `tail file.txt`
        
85. **paste**: Merge lines of files.
    
    * Example: `paste file1.txt file2.txt`
        
86. **join**: Join lines of two files on a common field.
    
    * Example: `join file1.txt file2.txt`
        

### **Compression/Archiving:**

87. **tar**: Tape archive utility.
    
    * Example: `tar -czvf archive.tar.gz /path/to/directory`
        
88. **gzip/gunzip**: Compress or expand files.
    
    * Example: `gzip file.txt`, `gunzip file.txt.gz`
        
89. **bzip2/bunzip2**: A block-sorting file compressor.
    
    * Example: `bzip2 file.txt`, `bunzip2` [`file.txt.bz`](http://file.txt.bz)`2`
        
90. **zip/unzip**: Package and compress (uncompress) files.
    
    * Example: `zip -r` [`archive.zip`](http://archive.zip) `directory`, `unzip` [`archive.zip`](http://archive.zip)
        

### **Security:**

91. **chmod**: Change file mode bits.
    
    * Example: `chmod 755 file.txt`
        
92. **chown**: Change file owner and group.
    
    * Example: `chown user:group file.txt`
        
93. **chgrp**: Change group ownership.
    
    * Example: `chgrp groupname file.txt`
        
94. **passwd**: Update a user's authentication tokens.
    
    * Example: `passwd username`
        
95. **ssh**: OpenSSH SSH client (remote login program).
    
    * Example: `ssh user@host`
        
96. **iptables**: Administration tool for IPv4 packet filtering and NAT.
    
    * Example: `iptables -A INPUT -p tcp --dport 22 -j ACCEPT`
        
97. **ufw**: Uncomplicated Firewall.
    
    * Example: `ufw allow 22`
        
98. **fail2ban**: Intrusion prevention software framework.
    
    * Example: `fail2ban-client status`
        
99. **openssl**: OpenSSL command line tool.
    
    * Example: `openssl genrsa -out key.pem 2048`
        
100. **htpasswd**: Create and update password file for basic authentication.
    
    * Example: `htpasswd -c /etc/apache2/.htpasswd username`
        

These examples cover a wide range of tasks and functionalities in Linux systems.
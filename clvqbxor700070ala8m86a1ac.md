---
title: "Polling source code"
datePublished: Fri May 03 2024 07:04:26 GMT+0000 (Coordinated Universal Time)
cuid: clvqbxor700070ala8m86a1ac
slug: polling-source-code
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1714719789143/2eb22dd8-c6a7-4a6c-8069-c364a2bf43e8.png
tags: polling-source-code

---

This option will enable Jenkins to monitor GitHub repository and as soon as some changes are committed on GitHub, Jenkins will initiate project build for project.

Under project click Configure

![Capture.PNG](https://geekdudes.files.wordpress.com/2018/09/capture1.png?w=614 align="left")

Under Source Code Management click Git-paste Git Repo URL

![6.PNG](https://geekdudes.files.wordpress.com/2018/09/63.png?w=614 align="left")

Under Build Triggers click Poll SCM and specify time interval for checking GitHub repository for changes

![2.PNG](https://geekdudes.files.wordpress.com/2018/09/24.png?w=614 align="left")

Schedule uses crontab format

![3.PNG](https://geekdudes.files.wordpress.com/2018/09/34.png?w=614 align="left")

Click on Git Polling log to see changes

![4.png](https://geekdudes.files.wordpress.com/2018/09/45.png?w=614 align="left")

In case i changed something in code, project build will start/

![5.PNG](https://geekdudes.files.wordpress.com/2018/09/54.png?w=614 align="left")

![7.PNG](https://geekdudes.files.wordpress.com/2018/09/72.png?w=614 align="left")
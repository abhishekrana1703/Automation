---
title: "Check Code quality"
datePublished: Fri May 03 2024 07:11:28 GMT+0000 (Coordinated Universal Time)
cuid: clvqc6qk5000109kzg2npaylh
slug: check-code-quality
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1714720212203/78fb7903-785d-4069-9e17-a030bbcde4ea.png
tags: jenkins-devops

---

With Jenkins Checkstyle plugin generates the trend report for [Checkstyle](http://checkstyle.sourceforge.net/), an open source static code analysis program.

Install plugin by going to Manage Jenkins-Manage plugins-click on Available-in filter type checkstyle and click on Checkstyle checkbox to install plugin.

![1.PNG](https://geekdudes.files.wordpress.com/2018/09/15.png?w=614 align="left")

![2.PNG](https://geekdudes.files.wordpress.com/2018/09/25.png?w=614 align="left")

Once plug-in is installed click on project-Configure

![3.png](https://geekdudes.files.wordpress.com/2018/09/35.png?w=614 align="left")

Under Build-Goals add checkstyle:checkstyle at the end of goal line

![2-1.PNG](https://geekdudes.files.wordpress.com/2018/09/2-1.png?w=614 align="left")

In Post-build Actions add Publish Checkstyle analysis results

Your pom file have to be configured to user this checkstyle report

![Capture.PNG](https://geekdudes.files.wordpress.com/2018/09/capture3.png?w=614 align="left")

Build the project

![4.png](https://geekdudes.files.wordpress.com/2018/09/46.png?w=614 align="left")

If there are any errors/warnings, it will be shown and categorized

![5.png](https://geekdudes.files.wordpress.com/2018/09/55.png?w=614 align="left")
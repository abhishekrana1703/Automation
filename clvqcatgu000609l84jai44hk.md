---
title: "Continuous deployment"
datePublished: Fri May 03 2024 07:14:39 GMT+0000 (Coordinated Universal Time)
cuid: clvqcatgu000609l84jai44hk
slug: continuous-deployment
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1714720499120/95744771-3def-408b-a2e3-b998f86a3eeb.png
tags: jenkins

---

In this example we’ll copy war file from Jenkins project to Tomcat using Jenkins.

[Install Tomcat](https://tomcat.apache.org/download-80.cgi)

configure tomcat credentials:edit file conf\\tomcat-users.xml

&lt;role rolename=”manager-script”/&gt;  
&lt;role rolename=”admin-gui”/&gt;  
&lt;user username=”tomcat” password=”tomcat” roles=”manager-script,admin-gui”/&gt;  
&lt;/tomcat-users&gt;

If tomcat port needs to be changed, edit file conf\\server.xml

&lt;Connector port=”8081″ protocol=”HTTP/1.1″  
connectionTimeout=”20000″  
redirectPort=”8443″ /&gt;

Install copy artifact and deploy to container plugins:

Manage Jenkins-Manage Plugins

![7.png](https://geekdudes.files.wordpress.com/2018/09/73.png?w=614 align="left")

![8.PNG](https://geekdudes.files.wordpress.com/2018/09/82.png?w=614 align="left")

![9.PNG](https://geekdudes.files.wordpress.com/2018/09/9.png?w=614 align="left")

Create Jenkins job for compiling war file and to invoke other job for copying war files to tommcat (job name:packer)

![1.PNG](https://geekdudes.files.wordpress.com/2018/09/16.png?w=614 align="left")

In build step add Invoke top-level Maven targets

select Maven Version and Goals:clean package

![2.PNG](https://geekdudes.files.wordpress.com/2018/09/26.png?w=614 align="left")

In Post-build Action add Archive the artifacts

Files to archive \*\*/\*.war (archive all war file)

Add Post-build Action to run other job after this one is executed (deploy\_staging)

![3.PNG](https://geekdudes.files.wordpress.com/2018/09/36.png?w=614 align="left")

 **Creating job for copying war file to tomcat (deploy\_staging)**

Build action:pecify project name (one we created in previous step)

Artifacts to copy:\*\*/\*.war

![4.PNG](https://geekdudes.files.wordpress.com/2018/09/48.png?w=614 align="left")

Post-build Actions:

Deploy war/ear to a container:\*\*/\*.war

Specify tomcat credentials-click Add to add credentials and Tomcat URL

![5.png](https://geekdudes.files.wordpress.com/2018/09/56.png?w=614 align="left")

![6.PNG](https://geekdudes.files.wordpress.com/2018/09/64.png?w=614 align="left")

Now run first job (packer), it should compile war file and copy it to Tomcat directory
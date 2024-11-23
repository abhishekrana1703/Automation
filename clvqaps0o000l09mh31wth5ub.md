---
title: "Installing Maven on Ubuntu 20.04 and configure with Jenkins"
datePublished: Fri May 03 2024 06:30:17 GMT+0000 (Coordinated Universal Time)
cuid: clvqaps0o000l09mh31wth5ub
slug: installing-maven-on-ubuntu-2004-and-configure-with-jenkins
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1714717804187/63a25a71-711c-4dbd-b9c2-783e753f7e6d.png
tags: jenkins

---

To install Maven on Ubuntu 20.04 and configure it with Jenkins, you can follow these steps:

1. **Install Maven**:
    
    * Open a terminal window.
        
    * Update the package index:
        
        ```bash
        sqlCopy codesudo apt update
        ```
        
    * Install Maven:
        
        ```bash
        Copy codesudo apt install maven
        ```
        
2. **Verify Installation**:
    
    * Once the installation is complete, you can verify it by checking the version:
        
        ```bash
        Copy codemvn -version
        ```
        
3. **Configure Maven with Jenkins**:
    
    * Open Jenkins in your web browser.
        
    * Go to "Manage Jenkins" &gt; "Global Tool Configuration".
        
    
    ![1](https://geekdudes.files.wordpress.com/2018/09/1-1.png?w=614 align="left")
    
    * Scroll down to the "Maven" section and click on "Add Maven".
        
    
    ![4](https://geekdudes.files.wordpress.com/2018/09/43.png?w=614 align="left")
    
    * Provide a name for the Maven installation and select "Install automatically".
        
    * Save the configuration.
        
4. **Create or Configure Jenkins Job**:
    
    * Create a new Jenkins job or configure an existing one.
        
    * In the job configuration, specify the Maven installation you configured earlier.
        
    * Set up the build steps according to your project requirements. Typically, this would involve specifying Maven goals like `clean`, `compile`, `test`, etc.
        
    * Save the job configuration.
        
5. **Run Jenkins Job**:
    
    * Trigger the Jenkins job manually or set up a trigger (e.g., periodic, webhook, SCM change) based on your project needs.
        
    * Jenkins will automatically use the Maven installation you configured to build your project.
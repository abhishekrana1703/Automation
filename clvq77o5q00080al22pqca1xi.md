---
title: "How To Install Jenkins on Ubuntu 20.04"
datePublished: Fri May 03 2024 04:52:14 GMT+0000 (Coordinated Universal Time)
cuid: clvq77o5q00080al22pqca1xi
slug: how-to-install-jenkins-on-ubuntu-2004
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1714710745679/715ca064-5cbf-4292-9e21-8b923d992ada.png
tags: jenkins

---

Preparing for installing Jenkins on Ubuntu 20.04 involves ensuring that your system meets certain prerequisites. These prerequisites are essential to ensure a smooth installation process and the proper functioning of Jenkins once it's installed. Let's delve into what you need before embarking on the Jenkins installation journey.

### Prerequisites

Before installing Jenkins on Ubuntu 20.04, ensure you have the following prerequisites:

1. **Ubuntu 20.04**: Ensure that you have a clean installation of Ubuntu 20.04 LTS (Long Term Support) version.
    
2. **Java Development Kit (JDK)**: Jenkins requires Java to run. Install the default JDK using the following command:
    
    ```bash
    bashCopy codesudo apt install default-jdk
    ```
    
3. **Administrative Privileges**: You'll need sudo privileges to install packages and perform system-level configurations.
    
4. **Internet Connection**: Ensure your Ubuntu system has access to the internet to download packages and dependencies during the installation process.
    

Once you've verified these prerequisites, you're ready to proceed with the installation of Jenkins on Ubuntu 20.04.

### Step 1 — Installing Jenkins

The version of Jenkins included with the default Ubuntu packages is often behind the latest available version from the project itself. To ensure you have the latest fixes and features, use the project-maintained packages to install Jenkins.

First, add the repository key to the system:

```bash
wget -q -O - https://pkg.jenkins.io/debian-stable/jenkins.io.key | sudo apt-key add -
```

After the key is added the system will return with `OK`.

Next, let’s append the Debian package repository address to the server’s `sources.list`:

```bash
sudo sh -c 'echo deb http://pkg.jenkins.io/debian-stable binary/ > /etc/apt/sources.list.d/jenkins.list'
```

After both commands have been entered, we’ll run `update` so that `apt` will use the new repository.

```bash
sudo apt update
```

Finally, we’ll install Jenkins and its dependencies.

```bash
sudo apt install jenkins
```

Now that Jenkins and its dependencies are in place, we’ll start the Jenkins server.

### Step 2 — Starting Jenkins

Let’s start Jenkins by using [`systemctl`](https://www.digitalocean.com/community/tutorials/how-to-use-systemctl-to-manage-systemd-services-and-units):

```bash
sudo systemctl start jenkins
```

Since `systemctl` doesn’t display status output, we’ll use the `status` command to verify that Jenkins started successfully:

```bash
sudo systemctl status jenkins
```

If everything went well, the beginning of the status output shows that the service is active and configured to start at boot:

```bash
Output● jenkins.service - LSB: Start Jenkins at boot time
   Loaded: loaded (/etc/init.d/jenkins; generated)
   Active: active (exited) since Fri 2020-06-05 21:21:46 UTC; 45s ago
     Docs: man:systemd-sysv-generator(8)
    Tasks: 0 (limit: 1137)
   CGroup: /system.slice/jenkins.service
```

Now that Jenkins is up and running, let’s adjust our firewall rules so that we can reach it from a web browser to complete the initial setup.

### Step 3 — Opening the Firewall

To set up a UFW firewall, visit Initial Server Setup with Ubuntu 20.04, Step 4- Setting up a Basic Firewall. By default, Jenkins runs on port `8080`. We’ll open that port using `ufw`:

```bash
sudo ufw allow 8080
```

**Note:** If the firewall is inactive, the following commands will allow OpenSSH and enable the firewall:

```bash
sudo ufw allow OpenSSH
sudo ufw enable
```

Check `ufw`’s status to confirm the new rules:

```bash
sudo ufw status
```

You’ll notice that traffic is allowed to port `8080` from anywhere:

```bash
OutputStatus: active

To                         Action      From
--                         ------      ----
OpenSSH                    ALLOW       Anywhere
8080                       ALLOW       Anywhere
OpenSSH (v6)               ALLOW       Anywhere (v6)
8080 (v6)                  ALLOW       Anywhere (v6)
```

With Jenkins installed and our firewall configured, we can complete the installation stage and dive into Jenkins setup.

### Step 4 — Setting Up Jenkins

To set up your installation, visit Jenkins on its default port, `8080`, using your server domain name or IP address: `http://your_server_ip_or_domain:8080`

You should receive the **Unlock Jenkins** screen, which displays the location of the initial password:

![Unlock Jenkins screen](https://assets.digitalocean.com/articles/jenkins-install-ubuntu-1604/unlock-jenkins.png align="left")

In the terminal window, use the `cat` command to display the password:

```bash
sudo cat /var/lib/jenkins/secrets/initialAdminPassword
```

Copy the 32-character alphanumeric password from the terminal and paste it into the **Administrator password** field, then click **Continue**.

The next screen presents the option of installing suggested plugins or selecting specific plugins:

![Customize Jenkins Screen](https://assets.digitalocean.com/articles/jenkins-install-ubuntu-1804/customize_jenkins_screen_two.png align="left")

We’ll click the **Install suggested plugins** option, which will immediately begin the installation process.

![Jenkins Getting Started Install Plugins Screen](https://assets.digitalocean.com/articles/jenkins-install-ubuntu-1804/jenkins_plugin_install_two.png align="left")

When the installation is complete, you’ll be prompted to set up the first administrative user. It’s possible to skip this step and continue as `admin` using the initial password we used above, but we’ll take a moment to create the user.

![Jenkins Create First Admin User Screen](https://assets.digitalocean.com/articles/jenkins-install-ubuntu-1804/jenkins_create_user.png align="left")

Enter the name and password for your user:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1714711581420/86d9c884-1dc8-4203-87e1-676c900bb115.png align="center")

You’ll receive an **Instance Configuration** page that will ask you to confirm the preferred URL for your Jenkins instance. Confirm either the domain name for your server or your server’s IP address:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1714711673327/3b21809d-ebcc-4ffe-8d10-9cc071f2b4d8.png align="center")

After confirming the appropriate information, click **Save and Finish**. You’ll receive a confirmation page confirming that **“Jenkins is Ready!”**:

![Jenkins is ready screen](https://assets.digitalocean.com/articles/jenkins-install-ubuntu-1804/jenkins_ready_page_two.png align="left")

Click **Start using Jenkins** to visit the main Jenkins dashboard:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1714711842058/62b61b0f-6799-434d-ac2b-75f4c1a8b941.png align="center")

At this point, you have completed a successful installation of Jenkins.

### Conclusion

In this article, you installed Jenkins using the project-provided packages, started the server, opened the firewall, and created an administrative user. At this point, you can start exploring Jenkins.
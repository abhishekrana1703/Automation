---
title: "GitHub Actions"
datePublished: Sat May 04 2024 06:51:40 GMT+0000 (Coordinated Universal Time)
cuid: clvrqx49s000109lahy5d3bqj
slug: github-actions
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1714805470060/9a78075d-8dd9-466b-b95d-333f21d40b4f.png
tags: github-actions-1

---

Continuous Integration and Delivery (CI/CD) has revolutionized the software development process, enabling teams to deliver high-quality products efficiently and frequently. Automation testers play a crucial role in this process by ensuring that every code change is thoroughly tested before deployment. GitHub Actions, integrated seamlessly with GitHub repositories, provides a powerful platform for automating these testing processes. In this blog, we'll explore how automation testers can leverage GitHub Actions to configure CI/CD pipelines effectively.=

**In this article, I will cover the following topics**

* What is GitHub Actions?
    
* The components of GitHub Actions
    
* How to set up GitHub Actions in a GitHub repository
    
* How to view GitHub Actions activity
    

## What is GitHub Actions

GitHub Actions is a continuous integration (build, test, merge) and continuous delivery(automatically release to the repository) **(CI/CD)** platform. It automates and executes the software development workflows right from GitHub. It helps to customize how actions work and automate tasks all along in the software development lifecycle.

With GitHub Actions, you can build, test, and publish across multiple platforms, operating systems, and languages all within the same workflow and then see the status checks displayed within the pull request.

GitHub Actions works with various languages and frameworks, and its configurations are in YAML.

**One example of GitHub Actions is** :

If you’ve configured GitHub Actions in your Git repository and you push code to the remote branch, the GitHub Action will automatically trigger the predefined workflow.

It supports various events such as opening pull requests, merging code, or pushing to a branch, making it a powerful and flexible tool for different scenarios. GitHub Actions, being event-driven, responds to these events by executing the specified workflows.

![](https://media.licdn.com/dms/image/D5612AQH3pHbR0UhJ1w/article-inline_image-shrink_1500_2232/0/1711886027263?e=1720051200&v=beta&t=UE64-aQgGcMUqDLgE7NHLOEB6CM3ICToTZY6k2wzZK4 align="left")

![](https://media.licdn.com/dms/image/D5612AQHXT0o-Etf4bQ/article-inline_image-shrink_1500_2232/0/1711886227495?e=1720051200&v=beta&t=dRyYHpmB6av_7JpPEipx5z_5CfSIlSnLHtrAKAHa_fY align="left")

![](https://media.licdn.com/dms/image/D5612AQHINyEW5WoL9g/article-inline_image-shrink_1500_2232/0/1711886631872?e=1720051200&v=beta&t=_JJSA12Nj15bsVuq4qL_58WBXRgztafJ69c_k7zrzdA align="left")

Github Actions uses .yml syntax to define the events, jobs, and steps.

## Components Of GitHub Actions:

Components of GitHub Actions include workflows, events, and actions. These components enable the creation of powerful automation pipelines for building, testing, and deploying projects on GitHub.

Below is a detailed explanation of the components of GitHub Actions:

1**.Events** :

Events is an activity that triggers a workflow to run. Events can be triggered by opening a pull request, merging a pull request, etc. It can be configured to run on schedule.

2. **Workflows** (Jobs, Runner, Steps) :

![](https://media.licdn.com/dms/image/D5612AQHNKaeo26Kezg/article-inline_image-shrink_1500_2232/0/1711886676923?e=1720051200&v=beta&t=-2NhN8MJow2ukvvl6lVwn2FhOGR4ykXIkCeSM7F86E8 align="left")

Job is a set of *steps* in a workflow that execute on the same runner

Runner is a server that runs your workflows when they’re triggered. Each runner can run a single job at a time.

3\. **Actions**:

It is a custom application/command for the GitHub Actions platform that performs a complex but frequently repeated task that automates the workflow process.

## How to set up GitHub action in GitHub repository:

**Pre-Requisite:** GitHub Account, to create and run a GitHub Actions workflow. GitHub Actions uses YAML syntax to define the workflow.

In the below section, I have discussed, how we can add GitHub Action to the GitHub repository. I have taken an example of my GitHub repository which already has some code pushed in to master branch.

In the GitHub repository, one needs to create.github/workflows/directory and add a .yml file.

There are two ways to create a \*.yml file

1. **Through Web Application (Github) directly**
    

a. Go to repository

b. Click on Add File &gt; Create New File

![](https://media.licdn.com/dms/image/D5612AQFYUqATAXL-8Q/article-inline_image-shrink_1500_2232/0/1711887374428?e=1720051200&v=beta&t=rYhWmQo-QuxQIdWr54Ti487TXLwWip5hkv_datC97ss align="left")

c. Enter .github/workflows/maven.yml ( It has to be in the same sequence. You can pass any name of your choice for .ym file)

![](https://media.licdn.com/dms/image/D5612AQEDaNeQAkz-Fw/article-inline_image-shrink_1500_2232/0/1711889288639?e=1720051200&v=beta&t=VcDHv4Q1JI86EdmU7oVzF0aA-2MOb4e_Vlmz3MtU1Gs align="left")

d. Now, you can add the code to the maven.yml file and commit changes to your GitHub repository

Sample Code :

```bash
# This workflow will build a Java project with Maven and cache/restore any dependencies to improve the workflow execution time
name: GitHub Actions Demo Test Execution

on:
  push:
    branches: [ master ]
  pull_request:
    branches: [ master ]
  schedule:
    - cron: '*/15 * * * *'

jobs:
  build:

    runs-on: ubuntu-latest

    steps:
      - uses: actions/checkout@v2
      - name: Set up JDK 11
        uses: actions/setup-java@v2
        with:
          java-version: '11'
          distribution: 'adopt'
          cache: maven
      - name: Build with Maven
        run: mvn clean install
```

![](https://media.licdn.com/dms/image/D5612AQFNDnkuBNhulg/article-inline_image-shrink_1500_2232/0/1711889382542?e=1720051200&v=beta&t=n30YlroA012g_pV0oZ80fjD0NhMs0izmlBiLZJP1gRE align="left")

**2\. Through Terminal:**

a. Clone your GitHub repository into your system **(git clone \[Githubrepo\])**

b. Navigate to your GitHub repo (cd githubactions). Create a directory **.github** (command: mkdir .github)

***\*githubactions is the repository name used here***

c. Go to .github (cd .github)

d. Create a folder **workflow** (command: mkdir workflows)

e. Go to workflows (cd workflows)

f. Create \*.yml file (command: vi main.yml). You can give any name. I have created a file as main.yml

```bash
# This workflow will build a Java project with Maven and cache/restore any dependencies to improve the workflow execution time
name: GitHub Actions Demo Test Execution

on:
  push:
    branches: [ master ]
  pull_request:
    branches: [ master ]
  schedule:
    - cron: '*/15 * * * *'

jobs:
  build:

    runs-on: ubuntu-latest

    steps:
      - uses: actions/checkout@v2
      - name: Set up JDK 11
        uses: actions/setup-java@v2
        with:
          java-version: '11'
          distribution: 'adopt'
          cache: maven
      - name: Build with Maven
        run: mvn clean install
```

![](https://media.licdn.com/dms/image/D5612AQEnr-W7n-oLZA/article-inline_image-shrink_1500_2232/0/1711889343978?e=1720051200&v=beta&t=wylRXN5IYp7S59gTv-zsSuPjR5wI3WyK11KS_1TvD_k align="left")

## How to view GitHub action activity:

Once the GitHub actions are configured and start running, you can view each step’s activity on GitHub.

* Go to your repository on [Github.com](http://github.com/)
    
* Under the repository name, click on the **Actions** tab
    

![](https://media.licdn.com/dms/image/D5612AQEtr8Dlp-OP2Q/article-inline_image-shrink_1500_2232/0/1711888449792?e=1720051200&v=beta&t=9JDuLcR1FipkWH-gYn4Lv39lj9FiqAw5n-PNj1Ah3nI align="left")

* Select the workflow you want to see from the left sidebar.
    

![](https://media.licdn.com/dms/image/D5612AQFYLSvoP7zBYQ/article-inline_image-shrink_1500_2232/0/1711888566719?e=1720051200&v=beta&t=Z_u6ap9zS7xiw0JgOgY7bzi3f02JSxtRPMPpULCREnw align="left")

Under “**Workflow runs”**, click the name of the run you want to see.

![](https://media.licdn.com/dms/image/D5612AQGIlFzp3ENFlw/article-inline_image-shrink_1500_2232/0/1711888638035?e=1720051200&v=beta&t=BoVwgBZGuwc-RG8LawtTbdhx-5FeRCCVk5qSx8PtdFo align="left")

One can view the result of each step by clicking on the workflow

![](https://media.licdn.com/dms/image/D5612AQHWge8TsXL3fg/article-inline_image-shrink_1500_2232/0/1711888662189?e=1720051200&v=beta&t=cwW0chB1tS2NWZQI9N7Or4824BdHLiLeoukaWYLciFQ align="left")

![](https://media.licdn.com/dms/image/D5612AQEdRXH0I5qx_w/article-inline_image-shrink_1500_2232/0/1711888929591?e=1720051200&v=beta&t=6l4T9yC5GnhgoHpWyVrV79Xd6E3dhwQrc3i1lppRvx8 align="left")

I hope you have enjoyed the article. Thanks for reading !!
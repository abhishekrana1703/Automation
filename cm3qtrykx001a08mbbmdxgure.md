---
title: "Super Linter"
seoTitle: "Code Quality Assurance Tool"
seoDescription: "Super Linter ensures code quality with GitHub Actions, streamlining CI, enhancing collaboration, and saving time"
datePublished: Thu Nov 21 2024 04:41:31 GMT+0000 (Coordinated Universal Time)
cuid: cm3qtrykx001a08mbbmdxgure
slug: super-linter
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1732163998878/42900cb3-9b5d-45d1-89d9-f7a288fd25a3.webp
tags: super-linter

---

Super Linter is a GitHub Action that helps enforce standards for code quality and consistency across multiple languages and frameworks. It can be used in your GitHub workflows to automatically check your code whenever changes are made.

### Key Uses and Benefits of Super Linter

* **Automated Code Quality Checks**
    
* **Multi-Language Support**
    

Super Linter supports a wide range of programming languages, including but not limited to JavaScript, Python, Go, C++, HTML, CSS, YAML, JSON, Markdown, and more. This allows developers to maintain a single, unified linting process for projects with multiple languages.

* **Ease of Setup**
    

Integrating Super Linter into a GitHub repository is straightforward with minimal configuration needed. Pre-configured rules for popular linters can be used out-of-the-box, or you can customize the rules as needed.

* **Continuous Integration (CI) Integration**
    

Super Linter can be seamlessly integrated into your CI/CD pipeline using GitHub Actions. It automatically runs on events like push, pull request, or schedule, providing immediate feedback on code quality.

* **Customizability**
    

Allows for custom configurations to meet the specific needs of your project. You can include or exclude specific linters, adjust the rules, and set environment variables to fine-tune its behavior.

* **Improved Collaboration**
    

Enforces coding standards across the team, reducing discrepancies and ensuring all team members adhere to the same coding practices. Helps in maintaining a clean and consistent codebase, making it easier for team members to review and understand each other’s code.

* **Visibility and Reporting**
    

Provides detailed reports on linting issues directly in the GitHub Actions workflow logs. Makes it easy to track and address issues without leaving the GitHub interface.

* **Time and Cost Efficiency**
    

Automating the linting process saves time and reduces the manual effort required for code reviews. Helps catch issues early, potentially saving costs associated with fixing bugs at later stages of development.

### Where to Use Super Linter

* Open-Source Projects: Enforce coding standards across contributions from multiple developers. Ensure a consistent codebase quality.
    
* Corporate Development: Maintain code quality across teams and projects. Automate code reviews to save time and resources.
    
* Educational Projects: Teach best practices by enforcing coding standards. Automatically provide feedback on code quality.
    
* Personal Projects: Maintain high code quality standards. Catch and fix errors early in the development process.
    
* CI/CD Pipelines: Integrate into continuous integration and continuous deployment workflows. Ensure that only high-quality code is deployed to production.
    

### Best Practices for Using Super Linter

* Start with a Default Configuration
    
* Customize Configuration as Needed
    
* Run Linting on Key GitHub Events
    

Example configuration

```python
name: Super Linter
on: 
  push:
    branches: [ main ]
  pull_request:
    branches: [ main ]
jobs:
  lint:
    runs-on: arc-k8s-rs
    steps:
    - name: Checkout code
      uses: actions/checkout@v3
    - name: Run Super Linter
      uses: github/super-linter@v5
      env:
        DEFAULT_BRANCH: main
        GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
```

Use Environment Variables for Customization:

* Configure behavior through environment variables in the GitHub Actions workflow file.
    
* Examples: VALIDATE\_ALL\_CODEBASE: Set to true to lint the entire codebase, not just changed files.VALIDATE\_PYTHON\_PYLINT: Set to true to enable
    
* ython linting with pylint.
    

Exclude Unnecessary Files:

* Use FILTER\_REGEX\_EXCLUDE to exclude files or directories that do not need linting.
    
* Example
    

```python
env:
  FILTER_REGEX_EXCLUDE: '.*\.md$'
```

Fail Fast on Errors:

* Configure the workflow to fail if linting errors are detected, enforcing code quality before merging.
    
* Example
    

```python
jobs:
  lint:
    runs-on: ubuntu-latest
    steps:
    - name: Checkout code
      uses: actions/checkout@v3

    - name: Run Super Linter
      uses: github/super-linter@v5
      env:
        DEFAULT_BRANCH: main
        GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
    continue-on-error: false
```

Monitor and Address Linting Issues:

* Regularly review linting results in the GitHub Actions tab.
    
* Address and fix linting issues promptly to maintain code quality.
    

Educate Team Members:

* Ensure all team members understand the linting rules and their importance.
    
* Provide resources and training on how to fix common linting issues.
    
* Regularly Update Linter Configurations:
    
* Keep linter configurations up to date with the latest best practices.
    
* Review and adjust rules periodically to match evolving project needs.
    

Document Linting Rules:

* Document the linting rules and configurations in your project's README or a dedicated documentation file.
    
* Make it easy for new contributors to understand and follow the coding standards.
    

### Example Workflow File with Custom Configurations

example workflow file with custom configurations:

```python
name: Super Linter

on: 
  push:
    branches: [ main ]
  pull_request:
    branches: [ main ]

jobs:
  lint:
    runs-on: ubuntu-latest
    steps:
    - name: Checkout code
      uses: actions/checkout@v3

    - name: Run Super Linter
      uses: github/super-linter@v5
      env:
        DEFAULT_BRANCH: main
        GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
        VALIDATE_ALL_CODEBASE: true
        VALIDATE_PYTHON_PYLINT: true
        FILTER_REGEX_EXCLUDE: '.*\.md$'
```

### How Super Linter Works

Initialization:

When a specified event occurs in your GitHub repository (such as a push or pull request), the GitHub Actions runner initializes and sets up the environment.

Checkout Code:

The first step in the Super Linter workflow is to check out the repository code. This is typically done using the actions/checkout action, which pulls the code from the repository into the runner.

```python
name: Checkout code
uses: actions/checkout@v3
```

Run Super Linter:

* The next step is to execute the Super Linter action. This is done by specifying the github/super-linter action in your workflow file.
    

```python
- name: Run Super Linter
  uses: github/super-linter@v5
  env:
    DEFAULT_BRANCH: main
    GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
```

Environment Variables:

* Super Linter uses environment variables to customize its behavior. For example, DEFAULT\_BRANCH sets the default branch to compare against, and GITHUB\_TOKEN provides the necessary authentication.
    

```python
env:
  DEFAULT_BRANCH: main
  GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
```

```python
name: Super Linter

on: 
  push:
    branches: [ main ]
  pull_request:
    branches: [ main ]

jobs:
  lint:
    runs-on: ubuntu-latest
    steps:
    - name: Checkout code
      uses: actions/checkout@v3

    - name: Run Super Linter
      uses: github/super-linter@v5
      env:
        DEFAULT_BRANCH: main
        GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
```

> Example of a complete workflow file for running Super Linter on push and pull request events

### Customizing Super Linter

You can customize Super Linter by setting various environment variables and adding configuration files for specific linters. Here are a few customization options:

Lint Entire Codebase

```python
env:
  VALIDATE_ALL_CODEBASE: true
```

### Environment variables and their purpose

```python
DEFAULT_BRANCH: main
```

> Purpose: This variable specifies the default branch of your repository that Super Linter will use for comparison.

```python
GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
```

> Purpose: This variable provides Super Linter with the necessary authentication token to access the GitHub API and perform operations such as fetching repository details and posting comments on pull requests.

```python
VALIDATE_ALL_CODEBASE: true
```

> Purpose: This variable tells Super Linter to run linters on the entire codebase, not just the files that have been changed in the current commit or pull request.

```python
VALIDATE_PYTHON_PYLINT: true
```

> Purpose: This variable enables the Pylint linter for Python files.

```python
FILTER_REGEX_EXCLUDE: '.*\.md$'
```

> Purpose: This variable specifies a regular expression pattern to exclude certain files from being linted.

Here's an example of a GitHub Actions workflow file that includes these environment variables to configure Super Linter

```python
name: Super Linter

on: 
  push:
    branches: [ main ]
  pull_request:
    branches: [ main ]

jobs:
  lint:
    runs-on: ubuntu-latest
    steps:
    - name: Checkout code
      uses: actions/checkout@v3

    - name: Run Super Linter
      uses: github/super-linter@v5
      env:
        DEFAULT_BRANCH: main
        GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
        VALIDATE_ALL_CODEBASE: true
        VALIDATE_PYTHON_PYLINT: true
        FILTER_REGEX_EXCLUDE: '.*\.md$'
```
---
title: "Transfer Ownership of All GitHub Repositories in an Organization Using Python"
datePublished: Sun Nov 03 2024 09:09:30 GMT+0000 (Coordinated Universal Time)
cuid: cm31df9wx001009l5dvx29njq
slug: transfer-ownership-of-all-github-repositories-in-an-organization-using-python
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1730624963908/d145ea00-e47e-4189-b691-b46cbf46b92d.jpeg
tags: transfer-ownership-of-all-github-repositories-in-an-organization-using-python

---

Managing a GitHub organization with numerous repositories can sometimes require large-scale changes, such as transferring repository ownership to another user or organization. Doing this manually through GitHub's web interface can be time-consuming, especially if you're dealing with dozens or even hundreds of repositories.

In this article , I’ll show you how to automate the process of transferring all repositories from one organization to a new owner using Python and GitHub's API. This solution is perfect for developers or DevOps engineers looking to automate repository transfers with minimal effort.

### Why Automate Repository Transfers?

Manually transferring repositories, especially when dealing with multiple projects, can be tedious. Automating this process helps ensure that:

1. Time is Saved: Instead of manually transferring each repository, a script can handle it in one go.
    
2. Consistency: Automation reduces the chances of human error when performing repetitive tasks.
    
3. Scalability: Whether you have 10 repositories or 1,000, the process is the same. The script can handle as many repositories as needed without additional effort.
    

**Prerequisites**

Before we dive into the code, make sure you have the following:

* GitHub API Token: You'll need a personal access token (PAT) with sufficient permissions to list and transfer repositories. You can generate one from your GitHub account settings with the following scopes:
    
* Python: Make sure Python is installed on your machine. You can download it from the [official Python website](https://www.python.org/downloads/).
    
* requests Library: This Python library is used to make HTTP requests to the GitHub API. You can install it using pip:
    

```bash
pip install requests 
```

### Step 1: Set Up the Python Script

The first step is to create a Python script that will interact with GitHub’s API to list and transfer repositories.

```python
import requests
import time

# GitHub API token and org details
GITHUB_TOKEN = "your_github_token_here"
OLD_ORG = "your_old_org_name"
NEW_OWNER = "new_owner_username"
API_URL = "https://api.github.com"
HEADERS = {
    "Authorization": f"Bearer {GITHUB_TOKEN}",
    "Accept": "application/vnd.github.v3+json"
}

def get_org_repos(org):
    url = f"{API_URL}/orgs/{org}/repos"
    repos = []
    page = 1
    while True:
        response = requests.get(url, headers=HEADERS, params={"per_page": 100, "page": page})
        if response.status_code != 200:
            raise Exception(f"Error fetching repos: {response.status_code}, {response.text}")
        
        repo_data = response.json()
        if not repo_data:
            break
        
        repos.extend(repo_data)
        page += 1
    
    return repos

def transfer_repo(repo_name, new_owner):
    url = f"{API_URL}/repos/{OLD_ORG}/{repo_name}/transfer"
    data = {
        "new_owner": new_owner
    }
    
    response = requests.post(url, headers=HEADERS, json=data)
    if response.status_code == 202:
        print(f"Transfer initiated for repo: {repo_name}")
    else:
        print(f"Failed to transfer repo {repo_name}: {response.status_code} - {response.text}")

def main():
    repos = get_org_repos(OLD_ORG)
    
    for repo in repos:
        repo_name = repo['name']
        print(f"Transferring {repo_name} to {NEW_OWNER}...")
        transfer_repo(repo_name, NEW_OWNER)
        time.sleep(2)  # To avoid rate limiting

if __name__ == "__main__":
    main() 
```

### Step 2: Customize the Script

1. API Token: Replace your\_github\_token\_here with your GitHub API token. Ensure that your token has the required permissions to access and transfer repositories.
    
2. Old Organization Name: Update your\_old\_org\_name with the name of the organization from which you want to transfer repositories.
    
3. New Owner Username: Replace new\_owner\_username with the GitHub username of the new owner to whom the repositories will be transferred.
    
4. Adjust Rate Limiting (if necessary): Depending on the number of repositories, you may hit GitHub's API rate limits. The script includes a time.sleep(2) after each transfer to help prevent this. Adjust the sleep duration as needed based on your API usage limits.
    

**Step 3: Run the Script**

Once you’ve customized the script, you can run it from your terminal or command line:

```python
python transfer_repos.py 
```

This script will:

1. Fetch all repositories from the specified organization.
    
2. Initiate a transfer of each repository to the new owner.
    
3. Print status messages for each transfer, so you know which repositories were successfully transferred or if any errors occurred.
    

**Handling Errors**

If the script encounters an error (e.g., insufficient permissions or rate limiting), it will print the error details, allowing you to troubleshoot the issue. Here are a few common errors and how to resolve them:

* **403 Forbidden**: Ensure that your API token has the necessary permissions to transfer repositories.
    
* **404 Not Found**: Double-check that the organization name and repository name are correct.
    
* **API Rate Limiting**: If you hit GitHub’s rate limits, consider increasing the time. Sleep value or breaking the script into smaller batches of repository transfers.
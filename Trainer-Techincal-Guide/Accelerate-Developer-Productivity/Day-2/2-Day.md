# Solution Guide: 

# 1 Day

# Challenge 01: Continuous Integration and Deployment for Contoso Traders using GitHub Actions

## Introduction
This challenge is designed to evaluate the attendee/user skills in creating a robust CI/CD pipeline leveraging GitHub Actions. It aims to assess your capability to not only establish a seamless pipeline but also to guarantee the successful deployment of the application. Through this challenge, the attendee/user will set up a GitHub repository, implement a CI/CD workflow using GitHub Actions, deploy a .NET application to Azure, and make rolling updates to the application.

Here's the solution guide, which includes detailed step-by-step instructions required to complete the challenge.

## Accessing GitHub

1. To access and log into GitHub, open the edge browser from inside the environment and navigate to **[GitHub](https://github.com/)**.

2. Sign in to GitHub by clicking on the **Sign in** button in the top right corner of the GitHub home page.

3. On the **Sign into GitHub tab**, you will see a login screen. Enter the following email/username, and then click on **Next**.

   - **Email/Username:** <inject key="GitHubUsername"></inject>

1. Now enter the following password and click on **Sign in**.

   - **Password:** <inject key="GitHubPassword"></inject>

## Accessing the Azure Portal

1. To access the Azure Portal, open the Edge browser from inside the environment and navigate to the **[Azure Portal](https://portal.azure.com)**.

1. On the **Sign in to Microsoft Azure** tab, you will see a login screen. Enter the following email/username, and then click on **Next**. 
   * **Email/Username**: <inject key="AzureAdUserEmail"></inject>
        
1. Now enter the following password and click on **Sign in**.
   * **Password**: <inject key="AzureAdUserPassword"></inject>
     
1. If you see the pop-up **Stay Signed in?**, click No.

1. If you see the pop-up **You have free Azure Advisor recommendations!**, close the window to continue the lab.

1. If a **Welcome to Microsoft Azure** pop-up window appears, click **Cancel** to skip the tour.

## Solution Guide 

### Task 1: Setup a GitHub repository

In this task, you will login to an account on [GitHub](https://github.com) and use `git` to add lab files to a new repository.

1. In a new browser tab, open ```https://www.github.com/login```. From the **Environment** page **(1)**, navigate to **Licenses** **(2)** tab and **copy** **(3)** the credentials. Use the same username and password to log into GitHub.

   ![](../media/devops-devsecops-new-1.png) 
   
1. For **Device Verification Code**, use the same credentials as in the previous step, open `http://outlook.office.com/` in a private window, and enter the same username and password used for the GitHub Account login. Copy the verification code and Paste it into Device verification.

   ![](../media/2dgn154.png) 
    
1. In the upper-right corner, expand the user **drop-down menu** **(1)** and select **Your repositories** **(2)**.

   ![The `New Repository` creation form in GitHub.](../media/2dg1.png "New Repository Creation Form")

1. Next to the search criteria, locate and select the **New** button.

   ![The `New Repository` creation form in GitHub.](../media/ex2-t3-3-git.png "New Repository Creation Form")

1. On the **Create a new repository** screen, name the repository ```devsecops``` **(1)**, select **Public** **(2)**, and click on the **Create repository** **(3)** button.

   ![The `New Repository` creation form in GitHub.](../media/cl1-t1-s5.png "New Repository Creation Form")
   
   >**Note**: If you observe any repository existing with the same name, please make sure you delete the Repo and create a new one. Please follow steps 6 to 10. Otherwise, skip to step 11.

1. In the upper-right corner, expand the user **drop-down menu** **(1)** and select **Your repositories** **(2)**.

   ![The `New Repository` creation form in GitHub.](../media/2dg1.png "New Repository Creation Form")

1. Using the search bar, search for ```devsecops``` **(1)** and open it.

   ![The `New Repository` creation form in GitHub.](../media/cl1-t1-s7.png "New Repository Creation Form")

1. From the GitHub repository, click on the **Settings** tab.

   ![The `New Repository` creation form in GitHub.](../media/cl1-t1-s8.png "New Repository Creation Form")

1. In the settings page, scroll to the bottom of the page to select **Delete this repository**, and then click on **I want to delete this repository**.

   ![The `New Repository` creation form in GitHub.](../media/2dg120.png "New Repository Creation Form")

1. Within the following pop-up window, click on **I have read and understand these effects**.

   ![](../media/cl1-t1-s10.png)

1. In the succeeding pop-up window, copy the **repository name** **(1)**, paste it in the **box** **(2)**, and click on **Delete this repository** **(3)**.

   ![The `New Repository` creation form in GitHub.](../media/cl1-t1-s11.png "New Repository Creation Form")

1. On the **Quick setup** screen, copy the **HTTPS** GitHub URL for your new repository and **save it** in a notepad for future use.

   ![](../media/cl1-t1-s12.png)
   
1. From the GitHub username, note down the **Unique-ID** present in the Username. You'll need this in the upcoming steps.

   ![](../media/cl1-t1-s13.png) 
   
1. Navigate back to the **Visual Studio Code** application in which the terminal is already open. In the terminal, click on the **drop-down** button and select **PowerShell** to open a fresh PowerShell terminal tab.

   ![Quick setup screen is displayed with the copy button next to the GitHub URL textbox selected.](../media/2dg4.png "Quick setup screen")

   >**Note**: If the terminal is not open by default, please navigate to the terminal and click on new terminal.

1. In Visual Studio Code, run the below commands in the terminal to set your **email** and **username**, which Git uses for commits. Make sure to replace the GitHub account email and username.
   
     ```pwsh
     cd C:\Workspaces\lab\DevOps-DevSecOps-Hackathon-lab-files
     git config --global user.email "you@example.com"
     git config --global user.name "Your UserName"
     ```
     
   ![](../media/cl1-t1-s15.png) 
     
    Run the below-mentioned command in the terminal. Make sure to replace `your_github_repository-url` with the value you copied in step 12 and `Unique-ID` in step 13.

    Note: This step is done to initialize the folder as a Git repository, commit, and submit contents to the remote GitHub branch “main” in the lab files repository created in Step 1. 

      ```pwsh
      git init
      git add .
      git commit -m "Initial commit"
      git branch -M main
      git remote add origin<Unique-ID> <your_github_repository-url>
      git push -u origin<Unique-ID> main
      ```
     
   - If you are asked to authenticate your GitHub account, select **Sign in with your browser**, and you will be prompted with a pop-up window to authorize Git Credential Manager. Click on **Authorize git-ecosystem** to provide access.

       ![](../media/ex2-t3.png)
       
   - After you are prompted with the message **Authorization Succeeded**, close the tab and continue with the next task.

### Task 2: Deploy Infrastructure


2. To create GitHub secrets, in your GitHub lab files repository, click on the **Settings** tab.

      ![](../media/cl1-t2-s2.png)

 3. Navigate to **Environment** **(1)**, click on **Service Principal Details** **(2)**, and copy the **Subscription ID**, **Tenant ID (Directory ID)**, **Application ID (Client ID)**, and **Secret Key (Client Secret)**.

      ![](../media/devops-devsecops-new-2.png)
   
      - Replace the values that you copied in the below JSON. You will be using them in this step.
      
         ```json
         {
            "clientId": "zzzzzzzz-zzzz-zzzz-zzzz-zzzzzzzzzzzz",
            "clientSecret": "zzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzz",
            "tenantId": "zzzzzzzz-zzzz-zzzz-zzzz-zzzzzzzzzzzz",
            "subscriptionId": "zzzzzzzz-zzzz-zzzz-zzzz-zzzzzzzzzzzz"
         }
         ```

4. Under **Security**, expand **Secrets and variables** **(1)** by clicking the drop-down and select **Actions** **(2)** blade from the left navigation bar. Select the **New repository secret** **(3)** button.

   ![](../media/exe2-task4-step6-action-setup.png)

5. Under the **Actions Secrets/New secret** page, enter the below-mentioned details and click on **Add secret** **(3)**.

   - **Name** : Enter **SERVICEPRINCIPAL** **(1)**
   - **Value** : Paste the service principal details in JSON format **(2)**
   
      ![](../media/2dgn36.png)

6. To create another secret, under the **Actions Secrets/New secret** page, enter the below-mentioned details and click on **Add secret** ***(3)***.

   - **Name**: Enter **SQLPASSWORD** ***(1)***
   - **Value**: You need to enter any unique password with combination of Alphanumeric letters. Your password must contain characters from three of the following categories – English uppercase letters, English lowercase letters, numbers (0-9), and non-alphanumeric characters (!, $, #, %, etc.).

      ![](../media/sqlpass.png)

7. Under the **Actions Secrets/New variable** page, enter the below-mentioned details and click on **Add variable** ***(3)***.

   - **Name** : Enter **SUFFIX** ***(1)***
   - **Value** : **<inject key="DeploymentID" enableCopy="false" />** (Copy the Deployment ID from the environment details tab) ***(2)***
   
       
8. Same as above create a new variable called **DEPLOYMENTREGION** and enter the region where you want to deploy your infrastructure. 


10. To run a workflow, perform the following steps and wait for the resources to be deployed within your Azure Portal:
      - Click on **Actions (1)** within your GitHub repository.
      - Select the workflow named **contoso-traders-provisioning-deployment (2)**.
      - Click on **Run workflow (3)**.
      - Finally, click on **Run workflow (4)**. Ensure that the branch is selected as **main**.

         ![](../media/cl1-t2-s10.png)


11. Navigate to `.github/workflow/update-contoso-traders-App.yml` path, ensure to update the `AKS_NODES_RESOURCE_GROUP_NAME` and`RESOURCE_GROUP_NAME` environment variable by replacing `<deployment-id>` with **<inject key="DeploymentID" enableCopy="false" />**, once updated click commit changes to save the file:

    ![](../media/dso1.png) 

12. To run a workflow, perform the following steps and wait for the resources to be deployed within your azure portal:
      - Click on **Actions (1)** within your GitHub repository.
      - Select on the workflow named **update contoso traders app (2)**.
      - Click on **Run workflow (3)**.
      - Finally click on **Run workflow (4)**. Ensure that the branch is select as **main**.

         ![](../media/dso2.png) 

### Task 3: Setup CI/CD Workflow

1. From the Azure Portal Dashboard, click on Resource Groups from the Navigate panel to see the resource groups.

   ![](../media/2dgn9.png) 
   
1. Select the **contosotraders-rg<Deployment-ID>** resource group from the list.

   ![](../media/cl1-t3-s2.png)  
   
1. Select the **productsdb** SQL database from the list of resources.

   ![](../media/cl1-t3-s3.png) 
   
1. Under the Settings side blade, select **Connection strings** ***(1)*** and copy the **ADO.NET (SQL authentication)** ***(2)*** connection string from the ADO.NET tab. 

   ![](../media/ado-sql-database.png)  
 
1. In your GitHub lab files repository, select the **Settings** tab from the lab files repository.

   ![](../media/cl1-t1-s8.png)
   
1. Under **Security**, expand **Secrets and variables** ***(1)*** by clicking the drop-down and selecting **Actions** ***(2)*** from the left navigation bar. Select the edit button for the created secret named **SQL_PASSWORD** ***(3)***.

   ![](../media/cl1-t3-s6.png)
    
1. Under the **Actions Secrets/Update secret** page, enter the below-mentioned details, and click on **Update secret** ***(3)***.

   - **Value**: Paste the **ADO.NET (SQL authentication)** that you  have copied in the previous step.
   
      ![](../media/cl1-t3-s7.png)
   
   >**Note**: Replace `{your_password}` with the password that you have used initially
   
   
1. From your GitHub repository, select the **Actions** ***(1)*** tab. Select the **contoso-traders-app-deployment** ***(2)*** workflow from the side blade, Click on the  **drop-down** ***(3)*** next Run workflow button, and select **Run workflow** ***(4)***.

   ![](../media/2dgn159.png)
   
1. Navigate back to the Actions tab and select the **contoso-traders-app-deployment** workflow. This workflow builds the Docker image, which is pushed to the container registry. The same image is pushed to the Azure container application.

   ![](../media/2dgn124.png)
   

   
   **Note**: If the workflow **fails** due to the **npm install** job, follow steps 13 to 15. Otherwise, continue from step 16. 
   
1. From the GitHub browser tab, follow the steps given below and click on **Create codespace on main** ***(3)***.

   - Click on **Code** ***(1)***, 
   - Select the **Codespace** ***(2)*** tab

      ![](../media/ex2-kc-codespace.png)
   
1. Run the below-mentioned commands in the **Terminal**. You'll set the node version to node 14.

   ```pwsh
   cd src
   cd ContosoTraders.Ui.Website
   nvm install 14
   nvm use 14
   npm i
   git add . 
   git commit -m "updated node version"
   git push
   ```
    
1. From your GitHub repository, select the **Actions** ***(1)*** tab. You'll see an Action named **Updated node version** ***(2)*** executing. Please wait until the execution is complete.

   ![](../media/2dgn160.png)
   
   ![](../media/2dgn161.png)      

## Task 4: Test the application and perform rolling updates

1. Navigate to Azure Portal, and click on Resource Groups from the Navigate panel to see the resource groups.

   ![](../media/2dgn9.png) 
   
2. Select the **contosotraders-<inject key="DeploymentID" enableCopy="false" />** resource group from the list.

   ![](../media/2dgn135.png) 
   
3. Select the **contosotraders-ui2<inject key="DeploymentID" enableCopy="false" />** endpoint from the list of resources.

   ![](../media/2dgn127.png) 
   
4. Click on the **Endpoint hostname**. It'll open a browser tab where you will be able to verify that the Contoso Traders app has been hosted successfully.

   ![](../media/2dgn128.png) 
    
   ![](../media/2dgn162.png) 
    
   The last task automated building and updating only one of the Docker images. In this task, we will update the workflow file with a more appropriate workflow for the structure of our repository. This task will end with    a file named `docker-publish.yml` that will rebuild and publish Docker images as their respective code is updated.

5. From the GitHub browser tab, follow the steps given below and click on **Create codespace on main** ***(3)***.

   - Click on **Code** ***(1)***, 
   - Select the **Codespace** ***(2)*** tab

      ![](../media/ex2-kc-codespace.png)
   
      >**Note**: In case you have created a codespace in a previous task. Click on the **+** button to create a new codespace.
   
6. You'll be redirected to a new codespace tab in the browser. Please wait until the codespace is configured.

   ![](../media/2dg33.png)
   
7. From the explorer side blade, navigate to **.github (1)** > **workflows** **(2)** and select the **contoso-traders-provisioning-deployment.yml** **(3)** file.

   ![](../media/contosoprovision.png) 
   
8. Remove the commands from lines 7 to 14 from the workflow file.

   ![](../media/2dgn163.png) 
   
9. Using the terminal from codespace, run the following commands to commit this change to your repo and push the change to GitHub.

   ```pwsh
   git add .
   git commit -m "Updating app deployment"
   git push
   ```
   ![](../media/2dgn133.png) 
    
   > **Note**: This will update the workflow and will **not** run the "Update the ... Docker image" jobs.

10. Navigate back to the GitHub browser, select the **Actions** ***(1)*** tab, and review the **workflow** ***(2)*** created automatically for the changes made. 

      ![](../media/2dgn164.png)

11. Click on the **Next** button present in the bottom-right corner of this lab guide.

## Success criteria:
To complete this challenge successfully:

- The application must be deployed using VS Code, which supports GitHub Actions.
- A new repository must have been created.
- **CI/CD Implementation**: The CI/CD pipeline should be established using GitHub Actions, encompassing build, test, and deployment stages effectively.
- **Deployment Accuracy**: The application must be successfully deployed using GitHub Actions, and the chosen deployment strategy should align with the project's requirements.

## Additional Resources:

- Refer to [GitHub Actions and .NET](https://learn.microsoft.com/en-us/dotnet/devops/github-actions-overview) for reference.
- [Building and testing .NET](https://docs.github.com/en/actions/automating-builds-and-tests/building-and-testing-net).
- [Why CI/CD](https://resources.github.com/ci-cd/).
- [Continuous Deployment with Github Actions: An Example](https://www.dolthub.com/blog/2020-11-23-continous-deployment-with-github-actions/).
- [How to build a CI/CD pipeline with GitHub Actions in four simple steps](https://github.blog/2022-02-02-build-ci-cd-pipeline-github-actions-four-steps/).


# Challenge 02: GitHub Advanced Security - Implement Code Security Enhancements

## Introduction
In this challenge, the user will focus on implementing security features such as Code scanning, CodeQL alerts, and repository security advisories to their GitHub repository using GitHub Advance security features.

Here's the solution guide, which includes detailed step-by-step instructions required to complete this challenge.

## Accessing GitHub

1. To access and log into GitHub, open the edge browser from inside the environment and navigate to **[GitHub](https://github.com/)**.

2. Sign in to GitHub by clicking on the **Sign in** button in the top right corner of the GitHub home page.

3. On the **Sign into GitHub tab**, you will see a login screen. Enter the following email/username and click on **Next**.

   - **Email/Username:** <inject key="GitHubUsername"></inject>

1. Now enter the following password and click on **Sign in**.

   - **Password:** <inject key="GitHubPassword"></inject>

## Solution Guide

## Task 1: Implement Code Scanning and CodeQL:

In this task, you'll configure Code scanning and explore CodeQL alerts. Code scanning is a feature that you use to analyze the code in a GitHub repository to find security vulnerabilities and coding errors. Any problems identified by the analysis are shown on GitHub.

**Note**: To perform this task, the GitHub repository should be public. If the repository visibility is private, please go to the settings of the repository and change the visibility to public.
   
1. Select the **Settings** ***(1)*** tab from the GitHub browser tab. Click on **Code security** ***(2)*** under the security side blade.

   ![](../media/devops-devsecops-new-4.png)  
   
1. Click on the **Set up** **(1)** button to enable CodeQL analysis, and select the **Advanced** **(2)** option for creating a CodeQL Analysis YAML file.

   ![](../media/devops-devsecops-new-5.png)      

1. Update the workflow name to **codeql-analysis.yml** ***(1)*** and review the yaml file. Select **Commit changes** ***(2)***, then select **Commit directly to the main branch** ***(3)***, and click on **Commit changes** ***(4)***.
  
   ![](../media/cl2-t1-s3.png)

   ![](../media/ex5-task1-step3b.png) 
  
1. Navigate to the **Actions** ***(1)*** tab, here you can review the **workflow** ***(2)*** run.
    
   ![](../media/cl2-t1-s4.png) 
  
1. Navigate to the **Security** ***(1)*** tab and click on **View alerts** ***(2)***.
   
   ![](../media/cl2-t1-s5.png)
  
1. You will be navigated to the **Code scanning** section. You'll be able to visualize the **No code scanning alerts here!**.
   
   ![](../media/cl2-t1-s6.png)
    
## Task 2: Implement Repository security advisories:
 
In this task, you'll enable Repository security advisories. You can use GitHub Security Advisories to privately discuss, fix, and publish information about security vulnerabilities in your repository.  Anyone with admin permissions to a repository can create a security advisory.
 
1. Navigate to the **Security** ***(1)*** tab, select **Advisories** ***(2)*** from the side blade, and click on **New draft security advisory** ***(3)***.

   ![](../media/cl2-t2-s1.png)  
     
1. In the Open a draft security advisory tab, under the Advisory Details section, provide the following details:

   - Title: **Improper Access Control in devsecops/src/TailwindTraders.Ui.Website/src/App.js** ***(1)***
   - CVE identifier: **Request CVE ID later** ***(2)***
   - Description: **Add** ***(3)*** the below-mentioned details in the description section.
   
   ```
   Impact
   What kind of vulnerability is it? Who is impacted?

   HTTP request handlers should not perform expensive operations such as accessing the file system, executing an operating system command, or interacting with a database without limiting the rate at which requests are accepted. Otherwise, the application becomes vulnerable to denial-of-service attacks where an attacker can cause the application to crash or become unresponsive by issuing a large number of requests at the same time.

   Patches
   Has the problem been patched? What versions should users upgrade to?

   It is patched and rectified the error. Please use 1.2 version

   Workarounds
   Is there a way for users to fix or re../mediate the vulnerability without upgrading?

   // set up rate limiter: maximum of five requests per minute
   var RateLimit = require('express-rate-limit');
   var limiter = new RateLimit({
   windowMs: 1601000, // 1 minute
   max: 5
   });

   // apply rate limiter to all requests
   app.use(limiter);

   Added the above code in app.js

   References
   Are there any links users can visit to find out more?

   https://github.com/OWASP/API-Security/blob/master/2019/en/src/0xa4-lack-of-resources-and-rate-limiting.md
   https://codeql.github.com/codeql-query-help/javascript/js-missing-rate-limiting/
   ```
    
   ![](../media/cl2-t2-s2.png)
   
1. In the **Affected products** section, provide the following details and click on **Create draft security advisory** ***(7)***   
 
   - Ecosystem: **composer** ***(1)***
   - Package name: **devsecops/src/TailwindTraders.Ui.Website/src/App.js** ***(2)***
   - Affected version: **<1.2** ***(3)***
   - Patched version: **1.2** ***(4)***
   - Severity: **High** ***(5)***
   - Common Weakness Enumerator (CWE): **Improper Access Control (CWE-284)** ***(6)***
  
   ![](../media/cl2-t2-s3.png)
   
 1. Once the security advisory is created, scroll down and click on **start a temporary private fork**. It is used to collaborate on a patch for this advisory.

    ![](../media/cl2-t2-s4-a.png)
    
    ![](../media/cl2-t2-s4-b.png)
  
 1. After having the temporary fork, you can request a CVE. It is used for GitHub reviews and published security advisories. Upon review, we may use this advisory to send Dependabot alerts to affected repositories and redistribute the advisory through our API and Atom feed.

 ## Success criteria:
To complete this challenge successfully:

   - Verify the implementation of Implement Code Scanning and CodeQL.
   - Configure the Repository security advisories feature and create temporary private fork.

## Additional Resources:

- Refer to [About GitHub's Advanced Security](https://docs.github.com/en/code-security/getting-started/github-security-features) for reference.
- Refer to [About GitHub's Advanced Security](https://docs.github.com/en/code-security/code-scanning/introduction-to-code-scanning/about-code-scanning-with-codeql) for reference.
- Refer to [Code Scanning with GitHub CodeQL](https://learn.microsoft.com/en-us/training/modules/code-scanning-with-github-codeql/) for reference.

# Challenge 03: GitHub Advanced Security - Dependency Management and Secret Scanning

## Introduction

In this challenge, attendee/user will continue to focus on implementing crucial GitHub Advanced security features like GitHub Dependabots and Secret Scanning.

This is the solution guide, which provides all the specific, step-by-step directions needed to do the task.

## Solution Guide

### Task 1: Configure Dependabot Alerts:

In this task, you will use Dependabot to track the versions of the packages we use in our GitHub repository and create pull requests to update packages for us.

1. In your lab files GitHub repository, navigate to the **Settings** ***(1)*** tab and select the **Code security** ***(2)*** under Security from the side blade. Make sure **Dependabot alerts** is **Enabled** ***(3)***, if not, click on **Enable** to Enable Dependabot alerts. Click on **Enable** ***(4)*** to Enable Dependabot security updates.

   > **Note**: Enabling the `Dependabot security updates` will also automatically enable `Dependency graph` and `Dependabot alerts`.

   ![The GitHub Repository Security Overview tab.](../media/devops-devsecops-new-6.png "GitHub Repository Security Overview")

   > **Note**: The alerts for the repository may take some time to appear. The rest of the steps for this task rely on the alerts being present. You can continue with the next exercise, as this is an independent task and doesn't affect the lab. Please visit this task later and complete it.

1. To observe Dependabot issues, navigate to the **Security** ***(1)*** tab and select the **View Dependabot alerts** ***(2)*** link.

   ![GitHub Dependabot alerts in the Security tab.](../media/devops-devsecops-new-7.png "GitHub Dependabot alerts")

1. You should arrive at the `Dependabot alerts` blade in the `Security` tab.

   ![GitHub Dependabot alerts in the Security tab.](../media/devops-devsecops-new-8.png "GitHub Dependabot alerts")

1. Sort the Dependabot alerts by `Package name`. Under the **Package** ***(1)*** dropdown menu, search for **node-forge** ***(2)*** by typing in the search box and selecting **node-forge** ***(3)*** vulnerability.

   ![Summary of the `handlebars` Dependabot alert in the list of Dependabot alerts.](../media/ex5-t3-node-forge.png "`handlebars` Dependabot alert")

1. Select any of the `node-forge` Dependabot alert entries to see the alert details. After reviewing the alert, select **Review security update**.

   ![The `handlebars` Dependabot alert detail.](../media/ex5-t3-reviewsu.png "Dependabot alert detail")
   
   **Note:** If you see the Create Dependabot Security Update option, click on it. After it is created, select Review security update. 

1. Navigate to the **Pull Requests** ***(1)*** tab, find the Dependabot security patch pull request ***(2)***, and merge it to your main branch.

   ![List of Pull Requests.](../media/cl3-t1-s6.png "Pull Requests")
   
1. Click on **Merge pull request**, followed by **Confirm merge**. 

   ![The Pull Request Merge Button in the Pull Request detail.](../media/ex5-t3-merge-pr.png "Pull Request Merge Button")
    
   >**Note**: In case you see any errors with the merge request, retry steps 4 to 6 by selecting any other Dependabot alert.

1. Pull the latest changes from your GitHub repository to your local GitHub folder.

   ```pwsh
   cd C:\Workspaces\lab\DevOps-DevSecOps-Hackathon-lab-files  # This path may vary depending on how you set up your lab files repository
   git pull
   ```
   
## Task 2: Implement Secret Scanning:

In this task, you'll explore how secret scanning works and how it generates alerts. GitHub scans repositories for known types of secrets to prevent fraudulent use of secrets that were accidentally committed.

1. From your GitHub repository, click on the **Settings** tab.

   ![](../media/2dg110.png)
    
1. Select **Code security** from the sidebar and make sure **Secret scanning is enabled (1)**.

   ![](../media/devops-devsecops-new-9.png)   
    
1. Navigate back to **Code (1)** and click on the **src (2)** folder.

   ![](../media/2dg112.png)    
   
1. Click on **Add file** and select the **create new file** option.

   ![](../media/2dg113.png)    
   
1. Add a new file with the name **build.docker-compose.yml (1)**, add the code mentioned below **commit** the file. Here, you'll expose the **application ID** of a service principal.

   ```
   version: "3.4"
   services:
   api:
      build: ./ContosoTraders.Ui.Website/
      app id: 36540dcd-7bc3-4e16-90ca-4decb9ff8c36
      app secret: i1R8Q~Hn8dHn86VlWE7xJtLR4FKTIcQBXcebqcv4
   web:
      build: ./ContosoTraders.Api.Products
   ```
   
   ![](../media/devops-devsecops-new-10.png)   

1. You will get a pop up window of Secret scanning found Azure Active Directory Application secret found alert. You can either **Allow secret** by selecting the options available i.e It's used in tests, It's a false positive or I'll fix it later or **Cancel** it.

   ![](../media/devops-devsecops-new-11.png) 

1. Select the **Security (1)** tab and click on **Secret scanning (2)** from the sidebar. Here, you'll notice that an alert is generated referring to the same **Application ID** that was exposed in the `build.docker-compose.yml` file. This is how the Secret scanning feature works and generates alerts to notify you.

   ![](../media/devops-devsecops-new-13.png) 

## Success criteria:
To complete this challenge successfully:

- Successful implementation of GitHub Dependabots for identifying and addressing security vulnerabilities.
- Setup secreting scanning and updated the code base to resolve the alerts.

## Additional Resources:

- Refer to [Secret Scanning](https://docs.github.com/en/code-security/secret-scanning/about-secret-scanning) for reference.
- Refer to [GitHub Dependabot](https://docs.github.com/en/code-security/dependabot/dependabot-alerts/about-dependabot-alerts) for reference.


# Challenge 04: Integrate 'About Us' Page with GitHub Copilot in React Application

## Introduction

Contoso Traders is an e-commerce web application. In this challenge, as a DevOps engineer, your focus is to seamlessly implement and test new features with Copilot, ensuring accuracy and alignment. Conduct a thorough code review and enhance security using GitHub Advanced Security's CodeQL. Streamline development with a GitHub Actions CI/CD pipeline for Contoso Traders, ensuring efficient and secure deployment.

This is the solution guide that contains all of the comprehensive, step-by-step directions needed to finish the challenge.

## Accessing the Azure Portal

1. To access the Azure Portal, open the Edge browser from inside the environment and navigate to the **[Azure Portal](https://portal.azure.com)**.

1. On the **Sign in to Microsoft Azure** tab, you will see a login screen. Enter the following email/username, and then click on **Next**. 

   * **Email/Username**: <inject key="AzureAdUserEmail"></inject>
        
1. Now enter the following password and click on **Sign in**.
   * **Password**: <inject key="AzureAdUserPassword"></inject>
     
1. If you see the pop-up **Stay Signed in?**, click No.

1. If you see the pop-up **You have free Azure Advisor recommendations!**, close the window to continue the lab.

1. If a **Welcome to Microsoft Azure** pop-up window appears, click **Cancel** to skip the tour.

## Solution Guide

## Exercise 1: Integrate an 'About Us' app component in React using GitHub Copilot

### Task 1: Sign in to GitHub Copilot in Visual Studio Code

1. Open **Visual Studio Code** from the desktop screen. 

   ![Picture1](../media/cl7-ex1-t1-s1.png)
   
1. At the left pane , click on **Extensions**. 

   ![Picture1](../media/ex7-1.png)

1. At the search bar of the Extensions type **Github (1)**, select the **Github Copilot (2)** Extension and then click on **install (3).**

   ![Picture1](../media/ex7-task1-0.1.png)
   
1. Once the installation is successfull, a pop appears to sign-in. Click on **Sign in to GitHub**

   ![Picture1](../media/ex7-task1-0.2.png)

1. Next, once you get the popup, click on **Allow**.

   ![Picture1](../media/cl7-ex1-t1-s3.png)

1. On the **select user to authorize** page in the edge browser, click on **Continue**

   ![Picture1](../media/ex7-task1-0.3.png)

1. You will encounter a pop-up prompt. Click **Open** to proceed.

   ![Picture1](../media/ex7-task1-0.4.png)

   >**Note:** If you get another pop-up stating **Allow an extension to open this URI**, please click on **Open**.

1. You will be able to see in the bottom right corner that GitHub Copilot has been activated.

   ![Picture1](../media/cl7-ex1-t1-s8.png)

   >**Note:** If the activation status of Github Copilot in the bottom right corner is not visible, try restarting Visual Studio Code to ensure that the activation status becomes visible in that location.

1. Verify if **GitHub Copilot Chat** is installed. If its installed, chat window will open as shown below.
   
    ![Picture1](../media/copilotchat.png)
   
### Task 2: Integrate an 'About Us' app component in React using GitHub Copilot

  >**NOTE:** It should be noted that the code suggestions offered by GitHub Copilot might not exactly match the screenshots shown within the labguide. GitHub Copilot is an AI-powered tool that generates code based on context and patterns, and its suggestions can be influenced by various factors. It is also important that you have the knowledge on operating and running React Applications which may be needed as you proceed with this exercise.

1. In a new Visual Studio Code window, click on **File (1)** at the top left corner and then select **Open Folder (2)**.

    ![](../media/ex4-task1-1.png)

3. Navigate to **C:\Workspaces\lab\DevOps-DevSecOps-Hackathon-lab-files-2/ (1)** within the file explorer, and then select the **ContosoTraders.Ui.Website.V2.Raw (2)** folder, and then click on **Select folder (3)**

    ![Picture1](../media/ex7-task1-1.png) 

4. Ensure to click on **Yes, I trust the authors** within the pop-up to successfully import the CloudLabs folder into VS Code.

   ![Picture1](../media/trust-authors.png)

5. Once the project has loaded, within the explorer pane of VS Code, navigate to `Contosotraders.Ui.Website.V2\src` folder to view the `App.js` file.

   ![Picture1](../media/CL7-EX1-T2-S3.png)

6. Within the **CHAT: GITHUB COPILOT** pane, type: `Help me create the new About Us" page in ContosoTraders.Ui.Website.V2\src` and observe the AI response. You can follow the instructions provided by GitHub Copilot towards successfully adding the About Us page as a part of the sample React application that you have imported into VS Code.

   ![Picture1](../media/CL7-EX1-T2-S4.png)

  >**Disclaimer:** It should be noted that the code suggestions offered by GitHub Copilot might not exactly match the screenshots shown within the labguide. GitHub Copilot is an AI-powered tool that generates code based on context and patterns, and its suggestions can be influenced by various factors. It is also important that you have the knowledge on operating and running React Applications which may be needed as you proceed with this exercise.

  >**Note:** However the ease of executability of this challenge, you can open a new folder within VS Code and import the solution folder from the Windows file explorer with path, `C:\Workspaces\lab\DevOps-DevSecOps-Hackathon-lab-files-2\`. Select the **src** folder. This solution project has integrated "About Us" page and unit test cases for the same.

  >**Note:** If you wish to continue to manually edit the raw project, follow the steps from step 5.

5. Create a new file named `AboutUs.css` **(1)** in your `src` directory ie., within the path `ContosoTraders.Ui.Website.V2\src` and then add the following code **(2)**:

   ```
   .about-us {
       padding: 20px;
       font-size: 1.2em;
       line-height: 1.6;
       color: #333;
   }
   
   .about-us h1 {
       font-size: 2em;
       margin-bottom: 0.5em;
   }
   ```

   >**Note:** This `AboutUs.css` file contains CSS (Cascading Style Sheets) rules that are used to style HTML elements on a webpage. The specific code you've selected defines styles for elements with the class `about-us` and `h1` elements within elements with the class `about-us`.

   ![Picture1](../media/CL7-EX1-T2-S5.png)

6. Save the newly created `AboutUs.css` file.

7. Now let's build a new component for the application. Create a new file named `AboutUs.js` **(1)** in your `src` directory i.e., within the path `ContosoTraders.Ui.Website.V2\src` and then add the following code **(2)**:

   ```
   import React from "react";
   import "./AboutUs.css";
   
   function AboutUs() {
     return (
       <div className="container">
         <div className="about-us">
           <h1 className="text-center">About Us</h1>
           <p>
             Contoso Traders is a leading company in the trading industry. We have
             been serving our customers for over 20 years with high-quality
             products and excellent customer service.
           </p>
           <p>
             Our team is dedicated to providing the best service possible. We value
             our customers and strive to meet their needs.
           </p>
         </div>
       </div>
     );
   }
   
   export default AboutUs;
   ```

   >**Note:** Feel free to make changes in the above code snippet as per your use case scenario.

   >**Note:** Notice that the css rules have been imported into the `AboutUs.js` file using the code, `import "./AboutUs.css";`.
   
   >**Note:** The `AboutUs.js` file is a React component that renders an "About Us" section on a webpage based on the CSS rules that have been defined in `AboutUs.css` file.

8. Save the newly created `AboutUs.js` file.

9. Now navigate to the `App.js` file to integrate the "About Us" page that was created in the previous steps.

10. Within the `App.js` file, enter the following code.

     ```
     import AboutUs from "./AboutUs";
     import "./App.css";
     ```

11. Your `App.js` should look similar like the below screenshot:

     ![Picture1](../media/CL7-EX1-T2-S11.png)

12. Scroll down to the end of the code within the `App.js` file and then add the following code to include the newly created `About Us` component.

     ```
     <AboutUs />
     ```
13. Your `App.js` should now look similar like the below screenshot:

     ![Picture1](../media/CL7-EX1-T2-S13.png)

14. To run your React application, you typically use the command line (also known as the terminal). Here are the steps:
      - Within Visual Studio Code, you can open the terminal by going to the top menu to click on **Terminal** **(1)** and then select **New Termimal (2)**.
      - Navigate to your project directory. You can do this with the `cd` command followed by the path to your project. You can use the below command to navigate to the React application's working directory **(3)**:
      ```
      cd C:\Workspaces\lab\DevOps-DevSecOps-Hackathon-lab-files-2\src\ContosoTraders.Ui.Website.V2
      ``` 
      - Once you're in your project directory, you can start the application with the `npm start` **(3)** because we need npm to create the Contoso Traders Application. After running the following command within the terminal, your application should start, and you can view it in your web browser at http://localhost:3000.   
      ```
      npm run start
      ```
      
     ![Picture1](../media/CL7-EX1-T2-S14.png)

    >**Note:** If the above command fails, you might need to run the following command :

     ```powershell
     npm i
     ```
   
     - The command `npm i` is a shorthand version of `npm install`. It is used in Node.js environments to install all the dependencies listed in the `package.json` file. These dependencies are libraries or packages that your project needs to run correctly. The installed packages will be placed in a folder named `node_modules` in your project directory.

     - After the installation of all the dependencies, execute the command - `npm run start` to start the application. This open a new browser tab over the url path, `http://localhost:3000/`.

15. Observe that the new "About Us" component has been added at the end of the webpage.

     ![Picture1](../media/CL7-EX1-T2-S15.png)

## Exercise 2: Generate and run Unit Test cases using GitHub Coplilot:

### Task 1: Create and run test cases:

1. In Visual Studio Code, go to **Explorer** and navigate to path `ContosoTraders.Ui.Website.V2\src\components` and open the `WelcomePopup.js` file.

   ![Picture1](../media/CL7-EX2-T1-S1.png)

2. Select all code lines `[CTRL+A]` of `WelcomePopup.js` file **(1)** and then paste the following prompt **(2)** within the GitHub Copilot Chat Panel and press enter:
   ```
   /tests
   ```

   ![Picture1](../media/CL7-EX2-T1-S2.png)

3. Now create a new file named `WelcomePopup.test.js` under the path `ContosoTraders.Ui.Website.V2\src\components`.

   ![Picture1](../media/CL7-EX2-T1-S3.png)

4. Navigate back to the GitHub Copilot chat panel and copy the unit test that has been generated using Copilot for the `WelcomePopup` component. Ensure to paste these unit test cases within the newly created file - `WelcomePopup.test.js` under the `components` folder and save the file.

   **Disclaimer:** Please be aware that the unit test cases produced by GitHub Copilot may not be accurate. There could be issues within the test cases, such as lacking code logic. It's advisable to thoroughly review the generated code before integrating it into your project.

   **Note:** Below is an example unit test cases generated by GitHub Copilot which upon running leads to successful test case passes. This following unit test file is being provided for the easy execution using the `react-app/jest` framework.
   
   ![Picture1](../media/CL7-EX2-T1-S4-a.png)

   ![Picture1](../media/CL7-EX2-T1-S4-b.png)

5. Once ready with the test cases, open a new terminal within Visual Studio Code, and navigate to the following path/directory by running the below command within the terminal:

   ```
   cd C:\Workspaces\lab\DevOps-DevSecOps-Hackathon-lab-files-2\src\ContosoTraders.Ui.Website.V2\src\components
   ```

   >**Note:** Ensure that your current working directory within the terminal has the `components` folder in its present path. In this scenario, the `components` folder is present inside the `/src` directory. 

6. To execute the unit test cases genereated by GitHub Copilot, we need to run the `WelcomePopup.test.js` file using the following command within the terminal:

   ```
   npm run test
   ```

7. Post execution of the above unit test, you must ensure to have a successful - `PASS` test runs with no errors. If you are produced with errors, please understand the intricacies of the error as mentioned within the terminal and work towards a successful unit test run.

   ![Picture1](../media/CL7-EX2-T1-S7.png)

## Exercise 3: Code Review and Security Check

### Task 1: Submit Codebase Modifications to GitHub Repository

1. In a new browser tab, open ```https://www.github.com/login```. From the **Environment Details** page **(1)**, navigate to **License** **(2)** tab and **copy** **(3)** the credentials. Use the same username and password to log into GitHub.

   ![](../media/dev2.png) 

2. once logged-in, on the upper-right corner, expand the user **drop-down menu** **(1)** and select **Your repositories** **(2)**.

   ![The `New Repository` creation form in GitHub.](../media/2dg1.png "New Repository Creation Form")

3. Next to the search criteria, locate and select the **New** button.

   ![The `New Repository` creation form in GitHub.](../media/ex2-t3-3-git.png "New Repository Creation Form")

4. On the **Create a new repository** screen, name the repository ```devsecops-2``` **(1)**, select **Public** **(2)**, and click on the **Create repository** **(3)** button.

   ![](../media/CL7-EX3-T1-S4.png) 

5. On the **Quick setup** screen, copy the **HTTPS** GitHub URL for your new repository and **save it** in a notepad for future use.

   ![](../media/ex7-task1-3.png)

6. From the GitHub username, note down the **Unique-ID** present in the Username. You'll need this in the upcoming steps.

   ![](../media/cl1-t1-s13.png)

7. Navigate back to the **Visual Studio Code** application in which the terminal is already open. In the terminal, click on the **drop-down** button and select **PowerShell** to open a fresh PowerShell terminal tab.

   ![imported-Quick setup screen is displayed with the copy button next to the GitHub URL textbox selected.](../media/2dg4.png "Quick setup screen")

8. In Visual Studio Code, run the below commands in the terminal to set your **email** and **username**, which Git uses for commits. Make sure to replace the GitHub account email and username.
   
     ```pwsh
     cd C:\Workspaces\lab\DevOps-DevSecOps-Hackathon-lab-files-2\src\ContosoTraders.Ui.Website.V2
     git config --global user.email "you@example.com"
     git config --global user.name "Your UserName"
     ```
     
   ![](../media/ex7-task1-4.png) 
     
    Run the below-mentioned command in the terminal. Make sure to replace `your_github_repository-url` with the value you copied in step 5 and `Unique-ID` in step 6.

    Note: This step is done to initialize the folder as a Git repository, commit, and submit contents to the remote GitHub branch “main” in the lab files repository created named `devsecops`. 

      ```pwsh
      git init
      git add .
      git commit -m "Initial commit"
      git branch -M main
      git remote add origin-<Unique-ID> <your_github_repository-url>
      git push -u origin-<Unique-ID> main
      ```
     
   - If you are asked to authenticate your GitHub account, select **Sign in with your browser**, and you will be prompted with a pop-up window to authorize Git Credential Manager. Click on **Authorize git-ecosystem** to provide access.

       ![](../media/ex2-t3.png)
       
   - After you are prompted with the message **Authorization Succeeded**, close the tab and continue with the next task.

### Task 2: Implement Code Scanning and CodeQL

In this task, you'll configure Code scanning and explore CodeQL alerts. Code scanning is a feature that you use to analyze the code in a GitHub repository to find security vulnerabilities and coding errors. Any problems identified by the analysis are shown on GitHub.

**Note**: To perform this task, the GitHub repository should be public. If the repository visibility is private, please go to the settings of the repository and change the visibility to public.

1. Login to GitHub where the `devsecops-2` repository was created.

2. Select the **settings** ***(1)*** tab from the GitHub browser tab. Click on **Code security** ***(2)*** under the security side blade.

   ![](../media/ex2-task1-1.png) 

3. Click on the **Set up** **(1)** button to enable CodeQL analysis, and select the **Advanced** **(2)** option for creating a CodeQL Analysis YAML file.

   ![](../media/ex2-task1-2.png)     

4. Update the workflow name to **codeql-analysis.yml** ***(1)*** and review the yaml file. Select **Commit changes** ***(2)***, then select **Commit directly to the main branch** ***(3)***, and click on **Commit changes** ***(4)***.
  
   ![](../media/cl2-t1-s3.png)

   ![](../media/c2-1.png) 

5. Navigate to the **Actions** ***(1)*** tab, here you can review the **workflow** ***(2)*** run.
    
   ![](../media/cl2-t1-s4.png) 

6. Navigate to the **Security** ***(1)*** tab and click on **View alerts** ***(2)***.
   
   ![](../media/cl2-t1-s5.png)

7. You will be navigated to the **Code scanning** section. You'll be able to visualize the **No code scanning alerts here!**.
   
   ![](../media/ex7-task1-5.png)

### Task 3: Implement Repository security advisories

In this task, you'll enable Repository security advisories. You can use GitHub Security Advisories to privately discuss, fix, and publish information about security vulnerabilities in your repository. Anyone with admin permissions to a repository can create a security advisory.

1. Navigate to the **Security** ***(1)*** tab, select **Advisories** ***(2)*** from the side blade, and click on **New draft security advisory** ***(3)***.

   ![](../media/cl2-t2-s1.png)

2. In the Open a draft security advisory tab, under the Advisory Details section, provide the following details:

   - Title: **Improper Access Control in devsecops-2/src/App.js** ***(1)***
   - CVE identifier: **Request CVE ID later** ***(2)***
   - Description: **Add** ***(3)*** the below-mentioned details in the description section.
   
   ```
   Impact
   What kind of vulnerability is it? Who is impacted?

   HTTP request handlers should not perform expensive operations such as accessing the file system, executing an operating system command, or interacting with a database without limiting the rate at which requests are accepted. Otherwise, the application becomes vulnerable to denial-of-service attacks where an attacker can cause the application to crash or become unresponsive by issuing a large number of requests at the same time.

   Patches
   Has the problem been patched? What versions should users upgrade to?

   It is patched and rectified the error. Please use 1.2 version

   Workarounds
   Is there a way for users to fix or re../mediate the vulnerability without upgrading?

   // set up rate limiter: maximum of five requests per minute
   var RateLimit = require('express-rate-limit');
   var limiter = new RateLimit({
   windowMs: 1601000, // 1 minute
   max: 5
   });

   // apply rate limiter to all requests
   app.use(limiter);

   Added the above code in app.js

   References
   Are there any links users can visit to find out more?

   https://github.com/OWASP/API-Security/blob/master/2019/en/src/0xa4-lack-of-resources-and-rate-limiting.md
   https://codeql.github.com/codeql-query-help/javascript/js-missing-rate-limiting/
   ```
    
   ![](../media/CL7-EX3-T3-S2.png)

3. In the **Affected products** section, provide the following details and click on **Create draft security advisory** ***(7)***   
 
   - Ecosystem: **composer** ***(1)***
   - Package name: **devsecops-2/src/App.js** ***(2)***
   - Affected version: **<1.2** ***(3)***
   - Patched version: **1.2** ***(4)***
   - Severity: **High** ***(5)***
   - Common Weakness Enumerator (CWE): **Improper Access Control (CWE-284)** ***(6)***
  
     ![](../media/CL7-EX3-T3-S3.png)

4. Once the security advisory is created, scroll down and click on **start a temporary private fork**. It is used to collaborate on a patch for this advisory.

    ![](../media/CL7-EX3-T3-S4-a.png)
    
    ![](../media/cl2-t2-s4-b.png)

5. After having the temporary fork, you can request a CVE. It is used for GitHub reviews and published security advisories. Upon review, we may use this advisory to send Dependabot alerts to affected repositories and redistribute the advisory through our API and Atom feed.

## Exercise 4: CI/CD Pipeline Setup and Infrastrucure Deployment

### Task 1: Deploy Infrastructure

1. Login to your Azure portal with the credentials provided in the **Environment Details** tab of the integrated CloudLabs Environment.

2. In the global search bar, search for and select **Static Web Apps**

3. Click on **+ Create** to create a new Static Web Apps.

4. In the **Basics tab** of the **Create Static Web App** page, enter the following details:
   - **Subscription:** Select the available subscription **(1)**.
   - **Resource Group:** Create a new resource group named - **Static-Web-App (2)**.
   - **Name:** `React-Static-Web-App` **(3)**.
   - **Plan type:** Select **Free (4)**.
   - **Source:** Select **GitHub (5)**
   - **GitHub account:** Connect to your GitHub account which has the `devsecops-2` repository with the React application files **(6)**.
   - **Organization:** Select your assigned Github organization **(7)**.
   - **Repository:** Select `devsecops-2` **(8)**.
   - **Branch:** `Main` **(9)**.
   - **Build presets:** Search for and select **React (detected) (10)**.
   - **App location:** `/` **(11)**.

      >**Note:** `/` refers to the root directory of the GitHub repository. Ensure that the location is specified appropriately as per your GitHub file structure.
   
   - Leave the other fields at default and then click on **Review + Create (12)**.
   - Finally, click on **Create** on the **Review + create** page to create the static web app.

     ![](../media/ex7-task1-6.png)
   
     ![](../media/ex7-task1-8.png)

     ![](../media/ex7-task1-7.png)

6. Once the deployment is successful, click on **Go to resource**.

    ![](../media/CL7-EX4-T1-S5.png)

7. Navigate back to your `devsecops-2` repository on the GitHub portal and click on the **Actions** tab.

    ![](../media/CL7-EX4-T1-S6.png)

8. Ensure that your **Azure Static Web Apps CI/CD** workflow has a successful run status.

    ![](../media/CL7-EX4-T1-S7.png)

9. Navigate back to your Azure portal on the overview page of the recently created Static Web App and click on the **URL**

    ![](../media/CL7-EX4-T1-S8.png)

10. The URL redirects you to a new browser tab with the React Application up and running.

    ![](../media/CL7-EX4-T1-S9.png)

11. Click on **Get Started** and scroll down within your static web app to view the integrated **About Us** page.

    ![](../media/CL7-EX4-T1-S10.png)

## Success criteria:
To complete this challenge successfully:

- Successful implementation of the new feature.
- Accuracy and completeness of the generated unit tests with all successful passes.
- Successful setup and execution of the CI/CD pipeline.

## Additional Resources:

- Refer to [About GitHub Copilot Chat](https://docs.github.com/en/copilot/github-copilot-chat/about-github-copilot-chat) for reference.
- Refer to [Copilot Chat writes Unit Tests](https://dev.to/this-is-learning/copilot-chat-writes-unit-tests-for-you-1c82) for reference.
- Refer to [Using GitHub Copilot Chat in your IDE](https://docs.github.com/en/copilot/github-copilot-chat/using-github-copilot-chat-in-your-ide) for reference.

# Challenge 05: Implementing Monitoring Solutions for Contoso Traders

## Introduction

In this challenge, the user/attendee will integrate Azure's monitoring tools—Azure Monitor and Application Insights—into their Azure-based application. Monitoring is vital for maintaining efficiency and resilience in cloud applications, enabling proactive issue identification and seamless user experiences.

This is the solution guide that contains all of the comprehensive, step-by-step directions needed to finish the challenge.

## Solution Guide

### Task 1: Deploy Monitoring Infrastructure

1. You will deploy the complete monitoring infrastructure using the Bicep template named `monitoringinfra.bicep`. The monitoring infrastructure includes Application Insights, a secret created for Application Insights, and a monitoring dashboard.

1. Open VS Code within the Vm, and then click on **File (1)** at the top left corner and then select **Open Folder (2)**.

    ![](../media/ex4-task1-1.png)

1. Navigate to **C:\Workspaces\lab\DevOps-DevSecOps-Hackathon-lab-files\iac (1)** path ,  select **iac (2)** and click on **Open folder (3)**.

    ![](../media/ex4-task1-2.png)

1. Open the **monitoringinfra.parameters.json (1)** file. Locate the env parameter in the JSON file and update its value with the **deployment ID (2).** and then save. 

   >**Note**: You can find the deployment ID within the environment details tab of your integrated lab guide.

   ![](../media/ex4-task1-3.png)
   
1. In the VS Code Terminal, run the following command to log in to your Azure account:

   ```
   Connect-AzAccount
   ```
   >**Note**: Please use the below-mentioned credentials to login to Azure.
   
      - **Email/Username:** <inject key="AzureAdUserEmail"></inject>
      - **Password:** <inject key="AzureAdUserPassword"></inject>
      
1. Set the Resource Group Name before running the deployment command. set the  **$RGname** as **contoso-traders-rg<inject key="Deploymentid" enableCopy="false" />**

   ```
   $RGname = '<update the RG name mentioned above>'
   ```
   
   >**Note:** Make sure you are in the directory where the Bicep template and parameters file resides. If not switch to the directory cd C:\Workspaces\lab\DevOps-DevSecOps-Hackathon-lab-files\iac
   
1. Run the following command to initiate the deployment using the Bicep template and parameters file:

   ```
   New-AzResourceGroupDeployment -Name "createresource" -TemplateFile "monitoringinfra.bicep" -TemplateParameterFile "monitoringinfra.parameters.json" -ResourceGroup $RGname
   ```
1. Monitor the output in the terminal , and wait for until the deployment is succeeded.

   ![](../media/ex4-task1-5.png)
   
### Task 2: Monitoring using Application Insights

1. In the Azure Portal, navigate to the **contoso-traders-rg<inject key="Deploymentid" enableCopy="false" />** **(1)** resource group and select the **Application Insights** resource with the name  **contoso-traders-ai<inject key="Deploymentid" enableCopy="false" />** **(2)**.

   ![](../media/ex4-task1-6.png)
   
1. From the **Overview (1)** of **contoso-traders-ai<inject key="Deploymentid" enableCopy="false" />** Application Insights resource, you can set the **Show data for last (2)** as per your requirement of monitoring insights.

   ![](../media/ex4-task1-7.png)
   
1. In the first graph, you can see the number of failed requests for Application access.

   ![](../media/upd-ex6-t1-failedrequests.png)
   
1. In the next graph, you can see the average server response time.

   ![](../media/upd-ex6-t1-server-response-time.png)
   
1. In the next graph, you can see the number of server requests.

   ![](../media/upd-ex6-t1-server-requests.png)
   
1. In the last graph, you can see the average availability.

   ![](../media/upd-ex6-t1-availability.png)  

## Success criteria:
To complete this challenge successfully:

- Successful integration of Azure Monitor and Application Insights within the application environment, ensuring seamless data collection and monitoring capabilities.
- Selection and configuration of key performance metrics relevant to the application's functionality and performance goals.
- Establishment of effective alerting mechanisms with well-defined thresholds, ensuring timely notifications for potential issues or deviations in monitored metrics.

## Additional Resources:

- Refer to [Application Insights Overview](https://learn.microsoft.com/en-us/azure/azure-monitor/app/app-insights-overview) for reference.
- [Application Insights for ASP.NET Core applications](https://learn.microsoft.com/en-us/azure/azure-monitor/app/asp-net-core?tabs=netcorenew%2Cnetcore6).
- Refer to [Azure Monitor vs. Application Insights](https://azurelib.com/azure-monitor-vs-application-insights/) for reference.

---
page_type: sample
languages: Java
products: GitHub
description: "Deploy Spring Petclinic application using GitHub Actions"
urlFragment: "https://github.com/agoncal/agoncal-application-petstore-ee7"
---

# Deploying a Java Web App using GitHub actions

Learn to deploy a Java Spring app to Azure App Service and set up a CI/CD workflow using GitHub Actions

## Overview

**GitHub Actions** gives you the flexibility to build an automated software development lifecycle workflow. You can write individual tasks ("Actions") and combine them to create a custom workflow. Workflows are configurable automated processes that you can set up in your repository to build, test, package, release, or deploy any project on GitHub.

With **GitHub Actions** you can build end-to-end continuous integration (CI) and continuous deployment (CD) capabilities directly in your repository. 

### Prerequisites

1. You will need a **GitHub** account. If you do not have one, you can sign up for free [here](https://github.com/join)

1. **Microsoft Azure Account**: You will need a valid and active Azure account for this lab. If you do not have one, you can sign up for a [free trial](https://azure.microsoft.com/en-us/free/).


### Setting up the GitHub repository

Fork this repo and open the sample app code in VS Code to get started.

## Create an Azure App Service

Create a web app hosted in Azure with a unique name, **Linux** as the OS and **Java 8** as the runtime. 

## Set up CI/CD workflow with GitHub Actions 

We'll use GitHub actions to automate our deployment workflow for this web app. 

1. Navigate to the sample CI/CD workflow file `workflow.yml` in your GitHub repo under `.github/workflows/` folder path

1. Modify the values of the environment variables based on your Azure app:
```yaml
env:
  AZURE_WEBAPP_NAME: your-app-name    # set this to your application's name
  AZURE_WEBAPP_PACKAGE_PATH: '.'      # set this to the path to your web app project, defaults to the repository root
  JAVA_VERSION: '1.8'                # set this to the Java version to use
  AZURE_WEBAPP_PUBLISH_PROFILE: ${{ secrets.AZURE_WEBAPP_PUBLISH_PROFILE }}     # set GH repo secret with the publish profile of the web app
```

1. In the portal, Overview page, click on "Get publish profile". A publish profile is a kind of deployment credential, useful when you don't own the Azure subscription. Open the downloaded settings file in VS Code and copy the contents of the file.

   ![](https://github.com/Azure/actions-workflow-samples/blob/master/assets/images/get-publish-profile.png)


1. We will now add the publish profile as a secret associated with this repo. On the GitHub repository, click on the "Settings" tab.

   ![](https://github.com/Azure/actions-workflow-samples/blob/master/assets/images/github-settings.png)


1. Go to "Secrets". Create a new secret called "AZURE_WEBAPP_PUBLISH_PROFILE" and paste the contents from the settings file.

   ![](https://github.com/Azure/actions-workflow-samples/blob/master/assets/images/create-secret.png)

1. Once you're done editing the workflow by configuring the required environment variables, click on "Start commit". Committing the file will trigger the workflow.

1. You can go back to the Actions tab, click on your workflow, and see that the workflow is queued or being deployed. Wait for the job to complete successfully.

1. Browse your app by pasting the URL of your Azure web app: https://AZURE_WEBAPP_NAME.azurewebsites.net

1. Make any changes by editing the app contents and commit the changes. Browse to the **Actions** tab in GitHub to view the live logs of your Action workflow which got triggered with the push of the commit.

1.  Once the workflow successfully completes execution, browse back to your website to visualise the new changes you introduced!

## Contributing

This project welcomes contributions and suggestions.  Most contributions require you to agree to a
Contributor License Agreement (CLA) declaring that you have the right to, and actually do, grant us
the rights to use your contribution. For details, visit https://cla.opensource.microsoft.com.

When you submit a pull request, a CLA bot will automatically determine whether you need to provide
a CLA and decorate the PR appropriately (e.g., status check, comment). Simply follow the instructions
provided by the bot. You will only need to do this once across all repos using our CLA.

This project has adopted the [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/).
For more information see the [Code of Conduct FAQ](https://opensource.microsoft.com/codeofconduct/faq/) or
contact [opencode@microsoft.com](mailto:opencode@microsoft.com) with any additional questions or comments.

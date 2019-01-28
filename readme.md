---
title: Create Azure ARM Template deployment using Azure Pipelines
layout: page
sidebar: vsts
permalink: /labs/azuredevops/armtemplatedeployment/
folder: /labs/azuredevops/armtemplatedeployment/
---
<div class="rw-ui-container"></div>
<a name="Overview"></a>

## Overview ##

In this lab, you will learn how to configure Azure ARM Template deployment using Build and Release in Azure Pipelines.

<a name="Prerequisites"></a>
### Prerequisites ###

- This lab requires you to complete task 1 from the <a href="https://www.azuredevopslabs.com/labs/azuredevops/prereq/">prerequisite</a> instructions.

<a name="Exercise1"></a>
## Exercise 1: Create new repository for ARM template ##

1. Create new repository

1. Create azuredeploy.json file to the repository and copy content from [here](https://raw.githubusercontent.com/Azure/azure-quickstart-templates/master/201-aci-wordpress/azuredeploy.json) to the file

1. Commit changes

<a name="Exercise2"></a>
## Exercise 2: Introduction to Azure DevOps Build ##

<a name="Ex1Task1"></a>
### Task 1: Creating a basic build pipeline from a template ###

1. Navigate to your team project on Azure DevOps.

1. Navigate to **Pipelines \| Builds**.

    ![](images/000.png)

1. Select **New \| New build pipeline** to create a new build pipeline.

    ![](images/001.png)

1. The default option for build pipelines involves using YAML to define the process. If you are interested in that, please check out that lab. For this lab, click **use the visual designer**.

    ![](images/002.png)

1. The first thing you'll need to do is to configure the source repository. Every major platform is available, but the default options are all we need here. This build will use the **master** branch of the repo you created earlier. Leave the defaults and click **Continue**.

    ![](images/003.png)

1. Locate the **Empty Job** and click it. Note that there are many options that should cover all of our mainstream scenarios. For our purposes here, we'll just build the pipeline from scratch.

    ![](images/004.png)

1. Click the **+** sign on **Agent Job 1** bar

    ![](images/005.png)

1. search for **Azure Resource Group Deployment** and click **add**

    ![](images/006.png)

1. Select **Azure Deployment: Create or Update Resource** from left side

    ![](images/007.png)

1. Select Azure Subscription

    ![](images/008.png)
    
1. Select Resource Group from dropdown. If you don't have an existing resource group go and create one on azure portal. Come back to this step and click the refresh sign on right.

    ![](images/009.png)
    
1. Select Location (Recommended **West Europe**)

1. Choose Template location by clicking the **...*** on the right side

    ![](images/010.png)
    
1. View parameters that you can override by clicking **...*** on the right side. Add MySQL Password

    ![](images/011.png)

1. Accept the default options by clicking **Save & queue**.

    ![](images/012.png)

<a name="Ex1Task2"></a>
### Task 2: Tracking and reviewing a build ###

1. Click the link to the newly created build.

    ![](images/013.png)

1. Depending on load, the build may need to wait in the queue for a moment.

    ![](images/014.png)

1. Once the build begins, you'll be able to track the console output. If you want to review an earlier task, you can click to review its logs.

    ![](images/015.png)

1. The build should eventually succeed, which you can review in the **Summary** tab.

    ![](images/016.png)

1. Select the **Logs** tab to see each step and how long it took.

    ![](images/017.png)


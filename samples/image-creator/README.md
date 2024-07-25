# Image Creator / Generator

<!--
This is how you want the sample to appear in the samples browser.
When naming your sample, try to give it a friendly name that describes what it does. Avoid using terms like `Power Apps` and `Power Automate` -- because that's what all the samples in this repo is all about.
GOOD 👍:
  Kitten Videos
BAD 👎:
  power-apps-kittenvideos
  Kitten Videos App for Power Platform using Creator Kit
-->

## Summary

TODO: Short summary on functionality and used technologies and pictures of the solution.

<!--
Please provide a high-quality screenshot of your solution below. It should be stored in a folder called `assets`. 

If possible, use a resolution of 1920x1080.

If your solution uses a placeholder screen and requires the user to configure it, please use a screenshot of the solution as it appears **after** it has been configured.

You can add as many screen shots as you'd like to help users understand your solution without having to download it and install it.
-->

![Example of a good preview](assets/goodpreview.png)

![Also a good preview](assets/alsogoodpreview.png)

![Not so good](assets/notsogood.gif)

## Applies to

![Power Apps](https://img.shields.io/badge/Power%20Apps-No-red "No")
![Power Automate](https://img.shields.io/badge/Power%20Automate-Yes-green "Yes")
![Power BI](https://img.shields.io/badge/Power%20BI-No-red "No")
![Power Pages](https://img.shields.io/badge/Power%20Pages-No-red "No")
![Copilot Studio](https://img.shields.io/badge/Copilot%20Studio-Yes-green "Yes")
![Dataverse](https://img.shields.io/badge/Dataverse-No-red "No")
![AI Builder](https://img.shields.io/badge/AI%20Builder-No-red "No")
![Custom Connectors](https://img.shields.io/badge/Custom%20Connectors-Yes-green "Yes")
![Power Fx](https://img.shields.io/badge/Power%20Fx-No-red "No")

## Compatibility

![Premium License](https://img.shields.io/badge/Premium%20License-Required-green.svg "Premium license required")
![Experimental Features](https://img.shields.io/badge/Experimental%20Features-Yes-green.svg "Does rely on experimental features")

## Contributors
<!--
We use this section to recognize and promote your contributions. Please provide one author per line -- even if you worked together on it.

We'll only use the info you provided here. Make sure to include your full name, not just your GitHub username.

Provide a link to your GitHub profile to help others find more cool things you have done. The only link we'll accept is a link to your GitHub profile.

If you want to provide links to your social media, blog, and employer name, make sure to update your GitHub profile.
-->

* [Gomolemo Mohapi](https://github.com/gomomohapi)

## Version history

Version|Date|Comments
-------|----|--------
1.0|July 25, 2024|Initial release

## Prerequisites

* Make sure you have access to Power Automate and Copilot Studio.
* Create an [Azure account](https://azure.microsoft.com/free/) and select **Start Free** and then fill in profile details to complete the sign up process.

    ![Azure account start free page](assets/azure-start-free.png)

* To use any of the Azure OpenAI Service AI models, you'll need to request access by completing [this form](https://aka.ms/oai/access).

* Once you have an Azure account and access to Azure OpenAI Service, go to [portal.azure.com](https://aka.ms/PowerPodcast/AzurePortal) and login with your Azure account to create a resource group.
    
    * Search for and select **Resource Groups**.
    * Click on **+ Create**.

        ![Create Azure Resource Group](assets/create-resource-group.png)

    * Name it `ImageCreator` and click on **Review + Create**. Then click on **Create**.

* Create a new Azure OpenAI Service resource (for image generating) by clicking [here](https://ms.portal.azure.com/#create/Microsoft.CognitiveServicesOpenAI) and set the following parameters:

    * **Subscription**: Select your Azure subscription
    * **Resource Group**: Select the `ImageCreator` resource group you created in the previous step
    * **Region**: `Sweden Central`
    * **Name**: `imagecreatorcopilot-{your initials}` (e.g. `imagecreatorcopilot-jd` to make it unique)
    * **Pricing Tier**: Select the `Standard S0` pricing tier

        ![Create Azure OpenAI Service resource](assets/create-openai-resource.png)

    * Click on **Next** until you get to the **Review + Submit** page and then click on **Create** to create the resource.

* Create a model deployment in Azure OpenAI Studio

    * Open up your `ImageCreator` resource group in the Azure portal
    * Select the `imagecreatorcopilot-{your initials}` resource
    * Click on **Go to Azure OpenAI Studio**

        ![Go to Azure OpenAI Studio](assets/go-to-openai-studio.png)

    * In the Azure OpenAI Studio, click on **Deployments** on the left menu.
    * Click on **+ Create New Deployment** and set the following parameters:
        * **Select a model**: `dall-e-3`
        * **Model version**: `Auto-update to default`
        * **Deployment name**: `dalle3`
    * Click **Create** to create the deployment.
    * Select the **dalle3** deployment and click on **Open in Playground**.
    * Select **View Code** and note down the endpoint and the key somewhere safe

        ![Azure OpenAI Studio Playground](assets/openai-studio-playground.png)

* Set up local environment variables to store the Azure OpenAI Service endpoint and key. Open up a command prompt on your computer and run this command:

    ```bash
    setx AZURE_OPENAI_KEY "REPLACE_WITH_YOUR_KEY_VALUE_HERE"
    ```

    Then run this command:

    ```bash
    setx AZURE_OPENAI_ENDPOINT "https://imagecreatorcopilot-{your initials}.openai.azure.com/" 
    ```

<!--
Any special pre-requisites? Include any lists, permissions, offerings to the demo gods, or whatever else needs to be done for this sample to work.

Please describe the steps to configure the pre-requisites. Feel free to add screen shots, but make sure that there is a text description of the steps to perform.
 
-->

## Minimal path to awesome

<!-- 
PRO TIP:

For commands, use the `code syntax`

For button labels, page names, dialog names, etc. as they appear on the screen, use **Bold**

Don't use "click", use "select" or "use"

As tempting as it may be, don't just use images to describe the steps. Let's be as inclusive as possible and think about accessibility.

-->

### Using the solution zip

* [Download](./solution/solution.zip) the `.zip` from the `solution` folder
* Within **Power Apps Studio**, import the solution `.zip` file using **Solutions** > **Import Solution** and select the `.zip` file you just packed.
* Open the app in edit mode and make sure the data source **Data source name** is connected correctly.

### Using the source code

You can also use the [Power Apps CLI](https://docs.microsoft.com/powerapps/developer/data-platform/powerapps-cli) to pack the source code by following these steps:

* Clone the repository to a local drive
* Pack the source files back into a solution `.zip` file:

  ```bash
  pac solution pack --zipfile pathtodestinationfile --folder pathtosourcefolder --processCanvasApps
  ```

  Making sure to replace `pathtosourcefolder` to point to the path to this sample's `sourcecode` folder, and `pathtodestinationfile` to point to the path of this solution's `.zip` file (located under the `solution` folder)
* Within **Power Apps Studio**, import the solution `.zip` file using **Solutions** > **Import Solution** and select the `.zip` file you just packed.

## Features

Description of the solution with possible additional details than in short summary.
This solution illustrates the following concepts on top of the Power Platform:

* topic 1
* topic 2
* topic 3

<!--
Note that better pictures and documentation will increase the sample usage and the value you are providing for others. Thanks for your submissions in advance! You rock ❤.
-->

<!--
RESERVED FOR REPO MAINTAINERS

We'll add the video from the community call recording here

## Video

[![YouTube video title](./assets/video-thumbnail.jpg)](https://www.youtube.com/watch?v=XXXXX "YouTube video title")
-->

## Help

<!--
You can just search and replace this page with the following values:

Search for:
YOUR-SOLUTION-NAME

Replace with your sample folder name. E.g.: my-cool-sample

Search for:
@YOURGITHUBUSERNAME

Replace with your GitHub username, prefixed with an "@". If you have more than one author, use %20 to separate them, making sure to prefix everyone's username individually with an "@".

Example:
@hugoabernier

Or:
@hugoabernier%20@VesaJuvonen%20@PopWarner
-->

> Note: don't worry about this section, we'll update the links.

We do not support samples, but this community is always willing to help, and we want to improve these samples. We use GitHub to track issues, which makes it easy for  community members to volunteer their time and help resolve issues.

If you encounter any issues while using this sample, you can [create a new issue](https://github.com/pnp/powerapps-samples/issues/new?assignees=&labels=Needs%3A+Triage+%3Amag%3A%2Ctype%3Abug-suspected&template=bug-report.yml&sample=YOUR-SOLUTION-NAME&authors=@YOURGITHUBUSERNAME&title=YOUR-SOLUTION-NAME%20-%20).

For questions regarding this sample, [create a new question](https://github.com/pnp/powerapps-samples/issues/new?assignees=&labels=Needs%3A+Triage+%3Amag%3A%2Ctype%3Abug-suspected&template=question.yml&sample=YOUR-SOLUTION-NAME&authors=@YOURGITHUBUSERNAME&title=YOUR-SOLUTION-NAME%20-%20).

Finally, if you have an idea for improvement, [make a suggestion](https://github.com/pnp/powerapps-samples/issues/new?assignees=&labels=Needs%3A+Triage+%3Amag%3A%2Ctype%3Abug-suspected&template=suggestion.yml&sample=YOUR-SOLUTION-NAME&authors=@YOURGITHUBUSERNAME&title=YOUR-SOLUTION-NAME%20-%20).

## Disclaimer

**THIS CODE IS PROVIDED *AS IS* WITHOUT WARRANTY OF ANY KIND, EITHER EXPRESS OR IMPLIED, INCLUDING ANY IMPLIED WARRANTIES OF FITNESS FOR A PARTICULAR PURPOSE, MERCHANTABILITY, OR NON-INFRINGEMENT.**

<img src="https://m365-visitor-stats.azurewebsites.net/powerplatform-samples/samples/YOUR-SOLUTION-NAME"  aria-hidden="true" />
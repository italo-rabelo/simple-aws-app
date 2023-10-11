# Simple AWS Web application tutorial
## Overview

In this tutorial, you will create a simple Web application. First, you will create a static web app that display "Hello World". Then, you will learn how to add functionality to the web application so that the displayed text is based on custom input you provide.

## What you will accomplish

- Create web application.
- Connect the web application to a serverless backend.
- Add interactivity to the web application using an API and a database.

## Pre-requisites

Before starting this tutorial, you will need:

- An AWS account: If you don't already have an account, follow the AWS' basics guide for a brief overview.

## Application Architecture

The following diagram provides a visual representation of the services used in this tutorial and how they are interconnected. The application uses AWS Amplify, Amazon API Gateway, AWS Lambda, Amazon DynamoDB, and AWS Identity and Access Management (IAM).

As we progress through the tutorial, we will delve into these services in detail and point out which resources will help you learn more about them.

![architectureaws](https://github.com/italo-rabelo/simple-aws-app/assets/107402049/2ededf4a-8f95-4f8a-b072-f0a79d71c8d0)


## Modules

This tutorial is divided into six small modules. Please complete each module in the correct order before proceeding to the next one.

1. Create a Web App (5 minutes): Deploy static resources for the web application using the AWS Amplify console.
2. Create a Serverless Function (5 minutes): Use AWS Lambda to create a serverless function.
3. Link the Serverless Function to the Web App (5 minutes): Deploy the serverless function with the API Gateway.
4. Create a Data Table (10 minutes): Store data in an Amazon DynamoDB table.
5. Add Interactivity to Your Web App (5 minutes): Modify the web application to invoke the API.
6. Clean Up Resources (5 minutes): Clean up the resources used in this tutorial.

You will create this web application using the AWS Management Console, which can be accessed directly in your web browser.

# Module 1: Create a Web App
### In this module, you will deploy static resources for your web applications using the AWS Amplify console.
 
**Overview**

In this module, you will use the <a href = "https://aws.amazon.com/pt/amplify/hosting/">AWS Amplify</a> console to deploy the static resources for your web application. In subsequent modules, you will add dynamic functionality to these pages using AWS Lambda and Amazon API Gateway to call remote RESTful APIs.

All of your static web content—including HTML, CSS, JavaScript, images, and other files—will be hosted by AWS Amplify. We selected the Amplify service because it makes it straightforward to host and deploy static websites. Your end users will access your site using the URL exposed by Amplify.

The website will be an extremely simple "Hello World" page, and we will add more functionality in later modules.



**What you will accomplish**

In this module, you will:

- Create an Amplify app
- Upload files for a website directly to Amplify
- Deploy new versions of a webpage with Amplify



**Key concepts**

Static website – A static website has fixed content, unlike dynamic websites. Static websites are the most basic type of website and are the easiest to create. All that is required is creating a few HTML pages and publishing them to a web server.

Web hosting – Provides the technologies/services needed for the website to be viewed on the internet.

AWS Regions – Separate geographic areas that AWS uses to house its infrastructure. These are distributed around the world so that customers can choose a Region closest to them to host their cloud infrastructure there.



## Implementation
**Create a web app with amplify console**
1. Open your favorite text editor on your computer. Create a new file and **paste** the following HTML in it:
```html
<!DOCTYPE html>
<html>
<head>
    <meta charset="UTF-8">
    <title>Hello World</title>
</head>

<body>
    Hello World
</body>
</html>
```
2. **Save** the file as index.html.

3. **ZIP (compress)** only the HTML file.

4. In a new browser window, log into the <a href = "https://us-west-2.console.aws.amazon.com/amplify/home?region=us-west-2#/">Amplify console</a>. **Note:** We will be using the Oregon (us-west-2) Region for this tutorial.

5. In the **Get Started** section, under **Host your web app**, choose the orange **Get started** button.

6. Select **Deploy without Git provider**. This is what you should see on the screen:

![apagardps](https://github.com/italo-rabelo/simple-aws-app/assets/107402049/51cbc1c1-df9a-445e-8c74-6e74edc8b2cd)


7. Choose the **Continue** button.

8. In the **App name** field, enter GettingStarted.

9. For **Environment name**, enter dev.

10. Select the **Drag and drop method**. This is what you should see on your screen:


![sein](https://d1.awsstatic.com/webteam/getting_started/GSRC%202020%20updates/full-stack%20amplify%20console%20module%20one%20AmplifyManualDeploy.67d826d04e7a85a3fdd70be0027dae84e28c4909.png)




11. Choose the **Choose files** button.

12. Select the **ZIP file** you created in Step 3.

13. Choose the **Save and deploy** button.

14. After a few seconds, you should see the message *Deployment successfully completed*.

**Test your web app**
1. Select Domain Management in the left navigation menu.

2. Copy and paste the URL displayed in the form into your browser.

Your web app will load in a new browser tab and render "Hello World." Congratulations!





# How to create a Simple Static Website on AWS
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


## Application Architecture
**Here is what our architecture looks like right now:**

![sera](https://d1.awsstatic.com/webteam/getting_started/GSRC%202020%20updates/full-stack%20amplify%20console%20arch%20diagram%20module%201.598e9f417bcbb955c0de96c9c2ae4183a3e1b41a.png)


It is pretty minimal right now because we are only using the AWS Amplify console. We now have a live web app users can interact with. Next, we will create a Lambda function.

# Module 2: Build a serverless function
### In this module, you will deploy static resources for your web applications using the AWS Amplify console.
 
**Overview**
In this module, you will be writing a small piece of code, in Python, JavaScript, or Java, to be used in a later module to add interactivity to your web page. You will use AWS Lambda, a compute service that lets you create serverless functions, eliminating the need for you to manage software and hardware. Instead, applications are broken up into individual functions that can be invoked and scaled individually.

These serverless functions are triggered based on a specific event you will define in the code. It is also a very affordable service, because you are only charged for the number of events you process, not the idle time. Best of all, you do not have to worry about managing any servers.


**What you will accomplish**

In this module, you will:

Create a Lambda function from scratch using the AWS console (in Python, JavaScript, or Java)
Create (JSON) events in the AWS console to test your function


**Key concepts**

Compute service – A service that provides computational processing power.

Serverless function – Piece of code that will be executed by a compute service, on demand.

Lambda trigger – The type of event that will make a Lambda (serverless) function run. This can be another AWS service or an external input.


## Implementation
**Create and configure your lambda function**

1. In a new browser tab, log in to the <a href= "https://us-east-2.console.aws.amazon.com/lambda/home?region=us-east-2#
">AWS Lambda console</a>.
2. Make sure you create your **function in the same Region in which you created the web app in the previous module**. You can see this at the very top of the page, next to your account name.
3. Choose the orange **Create function** button.
4. Under **Function name**, enter HelloWorldFunction.
5. Select **Python 3.8** from the **runtime** dropdown and leave the rest of the defaults unchanged.
    
   ![a](https://d1.awsstatic.com/webteam/getting_started/GSRC%202020%20updates/Full%20Stack%20tutorial%20CreateFunction%20Python.cfe5da9cc8bd900c55ed8e7a9e024c219e5d8f0a.png)
   
6. Choose the orange **Create function** button.
7. You should see a green message box at the top of your screen with the following message "Successfully created the function **HelloWorldFunction**"

8. Under **Code source**, replace the code in **lambda_function.py** with the following:

```python
# import the JSON utility package since we will be working with a JSON object
import json
# define the handler function that the Lambda service will use as an entry point
def lambda_handler(event, context):
# extract values from the event object we got from the Lambda service
    name = event['firstName'] +' '+ event['lastName']
# return a properly formatted JSON object
    return {
    'statusCode': 200,
    'body': json.dumps('Hello from Lambda, ' + name)
    }
```


9. Save by going to the file menu and selecting **Save** to save the changes.

10. Choose **Deploy** to deploy the changes.

11. Let's test our new function. Choose the orange **Test** button to create a test event by selecting **Configure test event.**

![esim](https://d1.awsstatic.com/webteam/getting_started/GSRC%202020%20updates/Full%20Stack%20tutorial%20Code%20Source.d62a65fc78fe0a829cca91ceeceb7af64af22bfa.png)


12. Under **Event name**, enter *HelloWorldTestEvent*.

13. Copy and paste the following JSON object to replace the default one:

```json
{
"firstName": "Ada",
"lastName": "Lovelace"
}
```

14. Choose the **Save** button at the bottom of the page.


**Test your lambda function**
1. Under the **HelloWorldFunction** section at the top of the page, select **Test** tab.
2. You should see a light green box at the top of the page with the following text: Execution result: succeeded. You can choose **Details** to see the event the function returned.
3. Well done! You now have a working Lambda function.

## Application Architecture
**Now that we are done with this module, our architecture will look like this:**

![def](https://d1.awsstatic.com/webteam/getting_started/GSRC%202020%20updates/full-stack%20amplify%20console%20arch%20diagram%20module%202.6567ede33b4c8fa82c4d6ee2760475ed815b5612.png)


# Module 3: Link a Serverless Function to a Web App
### In this module, you will deploy your serverless function using Amazon API Gateway.
 
**Overview**

In this module, we will use <a href = "https://aws.amazon.com/api-gateway/?e=gs2020&p=build-a-web-app-three">Amazon API Gateway</a> to create a RESTful API that will allow us to make calls to our Lambda function from a web client (typically refers to a user's web browser). API Gateway will act as a middle layer between the HTML client we created in module one and the serverless backend we created in module two.


**What you will accomplish**


In this module, you will:

Create a new API using API Gateway
Define HTTP methods on your API
Trigger a Lambda function from an API
Enable cross-origin resource sharing (CORS) on an API so you can consume resources from a different origin (domain)
Test an API created with API Gateway from the AWS Management Console



**Key concepts**

**RESTful API** – REST stands for "Representational State Transfer" and is an architectural pattern for creating web services. API stands for "application programming interface." Thus, a RESTful API is one that implements the REST architectural pattern.

**HTTP request methods** – HTTP methods are designed to enable communications between clients and servers. Methods, like GET or PUT defined by the HTTP protocol, are used to indicate what action to take on a resource.

**CORS** – The CORS browser security feature uses HTTP headers to tell a browser to allow a given web application running at one origin (domain) to access selected resources from a server at a different origin.

**Edge optimized** – A resource that uses AWS global infrastructure to better serve geographically diverse clients.


## Implementation

**Create a new REST API**
1. Log in to the <a href = "https://console.aws.amazon.com/apigateway/main/">API Gateway Console</a>.
2. In the **Choose an API type** section, find the REST API card and choose **Build** button on the card.
3. Under **Choose the protocol**, select **REST**.
4. Under **Create new API**, select **New API**.
5. In the **API name** field, enter *HelloWorldAPI*.
6. Select **Edge optimized** from the **Endpoint Type** dropdown. (Note: Edge-optimized endpoints are best for geographically distributed clients. This makes them a good choice for public services being accessed from the internet. Regional endpoints are typically used for APIs that are accessed primarily from within the same AWS Region.)
7. Choose the blue **Create API** button. Your settings should look like the accompanying screenshot.


![tlvz](https://d1.awsstatic.com/webteam/getting_started/GSRC%202020%20updates/Full%20Stack%20tutorial%20API%20settings.00fc97f8ce54af56f304927323b49a4247ac2299.png)


**Create and new resource and method**

1. In the left navigation pane, select **Resources** under **API: HelloWorldAPI**.

2. Ensure the "/" resource is selected.

3. From the **Actions** dropdown menu, select **Create Method**.

4. Select **POST** from the new dropdown that appears, then select the checkmark.

5. Select **Lambda Function** for the **Integration type**.

6. Select the **Lambda Region** you used when making the function (or else you will see a warning box reading "You do not have any Lambda Functions in...").

7. Enter *HelloWorldFunction* in the **Lambda Function** field.

8. Choose the blue **Save** button.

9. You should see a message letting you know you are giving the API you are creating permission to call your Lambda function. Choose the **OK** button.

10. With the newly created POST method selected, select **Enable CORS** from the **Action** dropdown menu.

11. Leave the POST checkbox selected and choose the blue **Enable CORS and replace existing CORS headers** button.


![a](https://d1.awsstatic.com/webteam/getting_started/GSRC%202020%20updates/Full%20Stack%20tutorial%20EnableCORS.5bd0a1c5540ba714abe44a6ffa0c80a3dd58ce16.png)


12. You should see a message asking you to confirm method changes. Choose the blue **Yes, replace existing values** button.



**Deploy API**

1. In the **Actions** dropdown list, select **Deploy API**.

2. Select **[New Stage]** in the **Deployment stage** dropdown list.

3. Enter *dev* for the **Stage Name**.

4. Choose **Deploy**.

5. Copy and save the URL next to **Invoke URL** (you will need it in module five).



**Validate API**

1. In the left navigation pane, select **Resources**.

2. The methods for our API will now be listed on the right. Choose **POST**.

3. Choose the small blue lightning bolt.

4. Paste the following into the **Request Body** field:

```js
{
    "firstName":"Grace",
    "lastName":"Hopper"
}
```

5. Choose the blue **Test** button.

6. On the right side, you should see a response with **Code 200**.

7. Great! We have built and tested an API that calls our Lambda function.

## Application Architecture
**Module three is complete. Time to review our architecture:**


![def](https://d1.awsstatic.com/getting-started-guides/build-a-basic-web-app/Image2.6f40a854d1708df0a4025aac3f64e767e8891ee2.jpeg)


We added API Gateway and connected it to our existing Lambda function. Now, we can trigger our function with an API call. We are still missing the ability to generate this call from our web client. We will add our data table first in module four and connect everything together in module five.

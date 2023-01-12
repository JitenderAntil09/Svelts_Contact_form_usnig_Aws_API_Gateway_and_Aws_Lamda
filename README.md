# Create Dynamic Contact Forms for S3 Static Websites Using AWS Lambda, Amazon API Gateway, and Amazon SES
These are the Following Steps for creating Create Dynamic Contact Forms for S3 Static Websites Using AWS Lambda, Amazon API Gateway, and Amazon SES.

# Architecture Flow
Following is the architecture flow with detailed guidance.

<img width="527" alt="archi" src="https://user-images.githubusercontent.com/122258630/211975574-c57359d5-c117-4806-a1d9-11df29144957.PNG">

In the above diagram, the customer is submitting their inquiry through a “contact us” form, which is hosted in an Amazon S3 bucket as a static website. Information will flow in three simple steps:

1. Your “contact us” form will collect all user information and post to Amazon API Gateway restful service.
2. Amazon API Gateway will pass collected user information to an AWS lambda function.
3. AWS Lambda function will auto generate an e-mail and forward it to your mail server using Amazon SES.

# The Problem:

Having Contact Me like the one below is an integral part of most of the personal and small business websites that are built.

<img width="843" alt="contact_form" src="https://user-images.githubusercontent.com/122258630/211976634-644461e6-8676-49a8-95ee-561fba4e054c.PNG">

I was building one such website, as the entire website is static, I honestly do not want to set up a server just to expose a single endpoint.

# The solution:

I know that cloud functions are something that solves my problem of having an endpoint without actually setting up the server. I chose AWS Lambda as it was much popular. But, the resources and blogs were not enough to give me a step by step guideline.

# What are we building? 

We are going to build a node emailer service that accepts a message in our POST request body and triggers an email to the predefined set of recipients from your Gmail account.
Setup Amazon SES
# Table Of Contents

1. AWS Account Setup.
2. Setting up Lambda.
3. Uploading the emailer code to your lambda.
4. Setup Amazon SES.
5. Creating AWS API Gateway
6. Intigrate API Gateway with lambda.


# 1.AWS Account Setup:

Create an AWS account here. Your account setup will be complete with you entering your Credit card details and verifying your email. Charges are usage-based.

# 2.Setting up Lambda:

1. Naviagte to AWS Console.
2. Choose Lambda under the Find Services input field.
3. You should now be on the lambda functions dashboard which shows the list of your available lambda functions.
4. You should now be on the lambda functions dashboard which shows the list of your available lambda functions.
5. In the next screen, fill in your Function name - emailer and choose Nodejs runtime as we are implementing this using node.

<img width="947" alt="aws_lambda" src="https://user-images.githubusercontent.com/122258630/211990086-5a2727fd-e4ff-4cf1-8467-7b0df89f55c2.PNG">

6. Now you can execute and test your AWS lambda function as directed in the AWS developer guide. Make sure to update the Lambda execution role and follow the steps provided in the Lambda developer guide to create a basic execution role.
7. Add following code under policy to allow Amazon SES access to AWS lambda function:

<img width="946" alt="aws_ses_policy" src="https://user-images.githubusercontent.com/122258630/211991024-55132130-5569-46ff-a03f-af4bed49d1e2.PNG">

8. On Clicking the Create function button you should see Successfully created the function emailer message on the next screen.
9. On scrolling down the page, you will see a sample nodeJS code with index.js.
10. Create a new test with any name of your choice and click on the Test button, you should be getting the response in the Execution Result tab.

# 3.Uploading the emailer code to your lambda:

The Aws lambda IDE for nodeJS does not allow us to install our npm packages on the go. Due to this, we have to get this set up locally in our machine and then upload the code to lambda by zipping it.

1. Download the Zip. It contains the code to be uploaded to your lambda function.
2. If you want to create the zip, the content is present inside this repo where there are a nodemailer dependency and some code to send an email. Make sure to npm install and create a zip from the root directory including your node_modules folder.
3. Once you got the Zip, upload it to the AWS lambda using Actions -> Upload a .zip file option.

<img width="957" alt="lambda_upload" src="https://user-images.githubusercontent.com/122258630/211993167-b0281330-93f2-47c3-8bc2-a62fee567e43.PNG">

4. If you open index.js you should be able to see the code where we have given our Email credentials and sending an email.
5. Headers are set to handle CORS errors if you try hitting your lambda from another origin.














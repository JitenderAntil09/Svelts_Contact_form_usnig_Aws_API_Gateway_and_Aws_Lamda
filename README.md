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





# Build and Deploy Serverless webapplication on AWS using Lambda Function, API gateway and DynamoDB


## Introduction

Lambda is the serverless computing solution provided by AWS.
According to official AWS documentation,

“AWS Lambda is a compute service that lets you run code without provisioning or managing servers.”

Lambda follows the principles of serverless computing. In serverless computing, you don’t have to worry about server and operating system maintenance, capacity provisioning, automatic scaling, and logging.

AWS Lambda takes care of the provisioning of the underlying infrastructure. It ensures the code is run on a high-availability computing infrastructure and administers the solution.
The developer only needs to provide the codebase in one of the languages supported by AWS Lambda.


## Application Architecture 

In this project, I created a serverless REST API that trigger a lambda function which generates a contact form and user can fill the form and save data to DynamoDB. 


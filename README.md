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

![](https://github.com/AbiVavilala/Serverless-webapp/blob/main/Architecture-diagram.png)


## Create required IAM role

We will create an IAM role for AWS lambda function to call AWS services on  your behalf.

Open AWS Management Console and search for IAM then click on create role.
![](https://github.com/AbiVavilala/Serverless-webapp/blob/main/diagrams/IAMRole.PNG)

click on AWS services this will allow lambda function to perform actions in this account.

In use case, select lambda function and click next

![](https://github.com/AbiVavilala/Serverless-webapp/blob/main/diagrams/AWSRole2.PNG)

In Add permissions, add AWS lambdBasicexecutionRole and DynamoDB full access role 

![](https://github.com/AbiVavilala/Serverless-webapp/blob/main/diagrams/IAMRole2.PNG)

and add DynamoDB permission too and click on  next
![](https://github.com/AbiVavilala/Serverless-webapp/blob/main/diagrams/IAMroledynamodbfullaccess.PNG)

give name to the role you are creating. I am calling this role as lambdafunctionIAMrole. and click next. this will craete the IAM role needed for this project.

![](https://github.com/AbiVavilala/Serverless-webapp/blob/main/diagrams/IAMrole5.PNG)


## Create Lambda funtion 

search for lambda in AWS management console then click on create function

![](https://github.com/AbiVavilala/Serverless-webapp/blob/main/diagrams/lambda.PNG)

give your function a name and select Python runtime for this project.
![](https://github.com/AbiVavilala/Serverless-webapp/blob/main/diagrams/lambda1.PNG)

for executuon role please add lambdafunctionIAMrole to this function. and click on create functin.
![](https://github.com/AbiVavilala/Serverless-webapp/blob/main/diagrams/lambda2.PNG)

## create DynamoDB table
we need a DynamoDb to store data from our function.

Open AWS Managemnt console and search for DynamoDB. Click on create table.
![](https://github.com/AbiVavilala/Serverless-webapp/blob/main/diagrams/dynamodb.PNG)


give a table name. my table name is called serverlesstable. then write partition key. I will select partition key as email and type as string. leave all the settings as default.

![](https://github.com/AbiVavilala/Serverless-webapp/blob/main/diagrams/dynamodb1.PNG)


## Create a Rest API

we need to create an API gateway to trigger our Lambda function. click on Create API

![](https://github.com/AbiVavilala/Serverless-webapp/blob/main/diagrams/API1.PNG)

Select RestAPI and click on Build
![](https://github.com/AbiVavilala/Serverless-webapp/blob/main/diagrams/restapi1.PNG)


give API name as serverlessAPI and API endpoint as Regional and click on create API

![](https://github.com/AbiVavilala/Serverless-webapp/blob/main/diagrams/restapi2.PNG)


click on create method
![](https://github.com/AbiVavilala/Serverless-webapp/blob/main/diagrams/restapi3.PNG)

select method type as Any, lambda function as integration type and enable lambda proxy integration and select serverlessapp lambda function.
![](https://github.com/AbiVavilala/Serverless-webapp/blob/main/diagrams/restapi4.PNG)

##  Package our lambda function

Open your lambda function by clicking on serverlessapp

![](https://github.com/AbiVavilala/Serverless-webapp/blob/main/diagrams/packagelambda.PNG)

upload the zip file to lambda function and click on API gateway endpoint.

![](https://github.com/AbiVavilala/Serverless-webapp/blob/main/diagrams/package%20our%20lambda%20function.PNG)

## Test the application

lets test our Application. we will click on API Gateway and that will trigger our lambda function and open our Contact form. 




# Task description

You get a Node.js application from the Engineering team and your task is to deploy that application to the Cloud (AWS, Azure or GCP) in a
scalable fashion.
For this exercise, you may choose any non-trivial Node.js application that implements a REST API.
For example: https://github.com/digitalocean/sample-nodejs
Task:
You can use any Cloud technology/service to create a scalable deployment: please explain why you chose that technology!
Your infrastructure should be defined as code
Briefly explain how to deploy and update your infrastructure (in your Readme)
Assume that your Node.js application is stateless, it does not need a database or similar to store data. But your application might
perform complex calculations or other longer operations.
Assume that your application will get a few million HTTP requests every day, but the exact load shape is unpredictable, there might be
usage spikes during peak hours
Try to optimize for overall cost and maintainability


Solution

deployTemplate.yaml 
Template to Cloudformation stack to launch & connect to EC2 instance, set parameters, deploy node.js application 

asg.yaml
Template to Cloudformation stack to create&update Auto Sacling Group with Launch template 

You can use any Cloud technology/service to create a scalable deployment: please explain why you chose that technology!
  -> I choose AWS because my original plan was utilize Elastik Beanstalk with cloudformation templates. With a Load balancer and asg it would met the requirements of scaleability, and also cost efficiency 
  In the end I ran out of time, so I created a cloudformation template to deploy the application on a single ic, and another to create an asg. 
  To avoid going over my free account I set the asg limits to pretty low. 

Briefly explain how to deploy and update your infrastructure
  The infrastructure is located in a Github Repository. This repo can be added to the CloudFormation stack in the Git sync option. It is of course also possible to update the templete on the GUI interface. 
  To automatize the deployment of the node.js application a simple CodeDeploy application with a corresponding pipeline could dynamically push the application if we put it into an S3 bucket 
  

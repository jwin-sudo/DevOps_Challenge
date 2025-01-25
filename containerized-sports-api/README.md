Sports API Management System
Project Overview

This project demonstrates the development of a containerized API management system for querying real-time sports data. It utilizes Amazon ECS (Fargate) to run containerized applications, Amazon API Gateway for managing REST endpoints, and an external Sports API for live sports data. The project highlights modern cloud computing techniques such as API management, container orchestration, and secure integrations on AWS.

Key Features

REST API for querying live sports data.
Backend containerized using Amazon ECS with Fargate.
Scalable, serverless architecture.
API management and routing with Amazon API Gateway.
Prerequisites

Sports API Key: Sign up at serpapi.com and obtain an API key.
AWS Account: Basic understanding of ECS, API Gateway, Docker, and Python.
AWS CLI: Installed and configured for AWS interactions.
Serpapi Library: Install using pip install google-search-results.
Docker CLI and Desktop: For building and pushing container images.
Technical Architecture

Cloud Provider: AWS
Core Services: Amazon ECS (Fargate), API Gateway, CloudWatch
Programming Language: Python 3.x
Containerization: Docker
Security: IAM with custom least-privilege policies
Project Structure

sports-api-management/
├── app.py           # Flask app querying sports data  
├── Dockerfile       # Dockerfile for containerization  
├── requirements.txt # Python dependencies  
├── .gitignore       # Ignore untracked files  
└── README.md        # Project documentation  
Setup Instructions

Clone the Repository
git clone https://github.com/ifeanyiro9/containerized-sports-api.git  
cd containerized-sports-api  
Create ECR Repository
aws ecr create-repository --repository-name sports-api --region us-east-1  
Build and Push Docker Image
aws ecr get-login-password --region us-east-1 | docker login --username AWS --password-stdin <AWS_ACCOUNT_ID>.dkr.ecr.us-east-1.amazonaws.com  

docker build --platform linux/amd64 -t sports-api .  
docker tag sports-api:latest <AWS_ACCOUNT_ID>.dkr.ecr.us-east-1.amazonaws.com/sports-api:sports-api-latest  
docker push <AWS_ACCOUNT_ID>.dkr.ecr.us-east-1.amazonaws.com/sports-api:sports-api-latest  
Set Up ECS Cluster and Task Definition
ECS Cluster
Create an ECS cluster named sports-api-cluster with Fargate as the infrastructure type.
Task Definition
Create a task definition (sports-api-task) and add a container:
Container Name: sports-api-container
Image URI: <AWS_ACCOUNT_ID>.dkr.ecr.us-east-1.amazonaws.com/sports-api:sports-api-latest
Container Port: 8080
Environment Variables:
Key: SPORTS_API_KEY
Value: <YOUR_SPORTSDATA.IO_API_KEY>
Run ECS Service with an Application Load Balancer (ALB)
Create an ALB (sports-api-alb) with health check path /sports.
Deploy the ECS service (sports-api-service) with desired tasks set to 2.
Note the ALB DNS name (e.g., sports-api-alb-<AWS_ACCOUNT_ID>.us-east-1.elb.amazonaws.com).
Set Up API Gateway
Create a REST API named Sports API Gateway.
Create a resource /sports with a GET method using HTTP Proxy integration.
Use the ALB DNS name as the endpoint.
Deploy the API and note the public endpoint URL.
Test the System
Use curl or a browser:
curl https://<api-gateway-id>.execute-api.us-east-1.amazonaws.com/prod/sports  
What We Learned

Building a scalable containerized application using ECS.
Exposing public APIs using API Gateway.
Future Enhancements

Add caching for frequent requests using Amazon ElastiCache.
Integrate DynamoDB for storing user-specific queries and preferences.
Secure API Gateway with API keys or IAM-based authentication.
Implement CI/CD pipelines for automated deployments.

Sports Alerts System: NBA Game Day Notifications

Overview

This project delivers real-time NBA game score updates to subscribed users through SMS or email. By utilizing Amazon SNS, AWS Lambda and Python, Amazon EventBridge, and NBA APIs, the system ensures sports enthusiasts stay informed about ongoing games. It showcases cloud computing principles and efficient notification delivery methods.

Key Features    

Retrieves live NBA game scores via an external API.
Sends SMS or email notifications using Amazon SNS with formatted score details.
Automates notifications through scheduled events using Amazon EventBridge.
Implements secure practices with IAM roles designed for least privilege.

Requirements     

An account on SportsData.io with an active subscription and API key.
A personal AWS account with basic knowledge of AWS and Python.

Technologies Used

Cloud Provider: AWS
Core Services: SNS, Lambda, EventBridge
External API: NBA Game API (SportsData.io)
Programming Language: Python 3.x
Security:
IAM roles configured with least privilege policies for Lambda, SNS, and EventBridge.
Project File Structure

game-day-notifications/  
├── src/  
│   ├── gd_notifications.py          # Core Lambda function  
├── policies/  
│   ├── gb_sns_policy.json           # Policy for SNS permissions  
│   ├── gd_eventbridge_policy.json   # EventBridge-Lambda permissions  
│   └── gd_lambda_policy.json        # Lambda execution role policy  
├── .gitignore  
└── README.md                        # Documentation  

Setup Guide

1. Clone the Repository
git clone https://github.com/ifeanyiro9/game-day-notifications.git  
cd game-day-notifications 

2. Create an SNS Topic
Access Amazon SNS from the AWS Management Console.
Select Create Topic → Choose Standard type.
Assign a name (e.g., gd_topic) and save the ARN.

3. Add Subscriptions
Go to the topic's Subscriptions tab.
Choose Create subscription → Select the protocol (Email or SMS).
Provide the email address or phone number (use international format for SMS).
Confirm the email subscription via inbox, if applicable.

4. Define an SNS Publish Policy
In IAM, go to Policies → Create Policy.
Paste the content from gd_sns_policy.json in JSON mode.
Replace placeholders for REGION and ACCOUNT_ID with your AWS details.
Save the policy as gd_sns_policy.

5. Configure an IAM Role for Lambda
Navigate to IAM Roles → Create Role.
Attach the following policies:
gd_sns_policy
AWSLambdaBasicExecutionRole
Save the role (e.g., gd_role) and copy its ARN.

6. Deploy the Lambda Function
Open AWS Lambda → Create Function.
Use Python 3.x, assign the role (gd_role), and name it gd_notifications.
Copy the src/gd_notifications.py file content into the code editor.
Add environment variables:
NBA_API_KEY (API key from SportsData.io)
SNS_TOPIC_ARN (ARN of the SNS topic).

7. Automate with EventBridge
Go to EventBridge Rules → Create Rule.
Choose Schedule as the event source.
Set the desired cron schedule (e.g., hourly updates).
Assign the target Lambda function (gd_notifications).

Testing

Simulate function execution using a test event in AWS Lambda.
Check CloudWatch logs for any errors.
Verify notifications are delivered to the subscribers.

Key Takeaways - 

Built a sports alert system leveraging AWS Lambda and SNS.
Applied security best practices with IAM least privilege policies.
Automated workflows with EventBridge.
Integrated external APIs for cloud-based solutions.
30 Days DevOps Challenge - Weather Dashboard

Day 1: Weather Data Collection System with AWS S3 and OpenWeather API

Project Overview
This project is part of the 30 Days DevOps Challenge and focuses on building a Weather Data Collection System that incorporates essential DevOps principles. The system integrates:

External API Integration: OpenWeather API for real-time weather data.
Cloud Storage: AWS S3 for secure and scalable data storage.
Infrastructure as Code: Automating resource provisioning.
Version Control: Git for tracking and managing changes.
Python Development: Scripted workflows and API interaction.
Error Handling: Robust handling of edge cases and failures.
Environment Management: Secure handling of sensitive credentials.

Features           
Fetches real-time weather data for multiple cities.
Displays key metrics: temperature (°F), humidity, and weather conditions.
Automatically uploads weather data to an AWS S3 bucket.
Supports tracking for multiple cities.
Includes timestamps for historical data tracking.

Technical Architecture
Programming Language: Python 3.x
Cloud Provider: AWS (S3 for storage)
External API: OpenWeather API
Key Dependencies:
boto3: AWS SDK for Python
python-dotenv: Manage environment variables
requests: Simplify API calls

Project Structure
weather-dashboard/
  ├── src/
  │   ├── __init__.py
  │   └── weather_dashboard.py
  ├── tests/
  ├── data/
  ├── .env
  ├── .gitignore
  ├── requirements.txt

Setup Instructions
Clone the Repository:
git clone git@github.com:jwin-sudo/DevOps_Challenge.git
cd weather-dashboard-demo

Install Dependencies:
pip install -r requirements.txt

Set Up Environment Variables:
Create a .env file in the project root and configure it with:
OPENWEATHER_API_KEY=your_api_key
AWS_BUCKET_NAME=your_bucket_name

Configure AWS Credentials:
Use the AWS CLI to set up your credentials:
aws configure

Run the Application:
Execute the main script to start collecting weather data:
python src/weather_dashboard.py

What I Learned - 
Setting up and managing AWS S3 buckets.
Securely handling API keys and environment variables.
Best practices for Python-based API integrations.
Using Git for project version control and collaboration.
Effective error handling in distributed systems.
Managing cloud resources in a cost-efficient way.
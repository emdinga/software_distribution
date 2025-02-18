**Project Overview**
This project is a simple web application designed to allow users to select software and initiate its installation on a remote EC2 instance using AWS Systems Manager (SSM). The website allows users to:

Choose the software they want to install.
Enter the hostname of the target EC2 instance.
Proceed with the installation process.
The application utilizes AWS services such as S3 for software storage, Lambda for backend processing, API Gateway for the API endpoint, and SSM for executing installation commands on EC2 instances.

**Key Features**
Software selection via a user-friendly interface.
Hostname validation to ensure installation is triggered on the correct Host instance.
Real-time communication between the frontend, API Gateway, Lambda, and Host instances.
AWS Architecture
The project leverages various AWS services to deliver a seamless and automated software installation process:

S3: Stores the software packages that will be installed on the Host instances.
API Gateway: Handles the user requests and triggers Lambda functions for backend processing.
Lambda: Responsible for fetching the correct software from S3 and sending installation commands to the Host instances using SSM.
SSM (Systems Manager): Facilitates software installation on Host instances by executing shell scripts or commands.
EC2: Hosts the application and runs the software installations.
IAM: Manages the necessary permissions for Lambda, SSM, and EC2 instances.
Project Structure
plaintext
Copy
Edit
software-installation-web-app/
│
├── aws/                     # AWS-specific infrastructure and configurations
│   ├── lambda/              # Lambda functions
│   ├── api-gateway/         # API Gateway configurations
│   ├── s3/                  # S3 bucket for software storage
│   └── ssm/                 # SSM commands and scripts for installation
│
├── frontend/                # Frontend code (HTML, CSS, JavaScript)
│   └── index.html           # Main webpage for software selection and hostname input
│
└── README.md                # Project documentation
Getting Started
Prerequisites
AWS account with appropriate permissions to create and manage EC2, S3, Lambda, API Gateway, and SSM.
Node.js (for any backend integrations or further extensions you may want to add).
A basic understanding of how to configure AWS services.
Setting Up
Clone this repository:

bash
Copy
Edit
git clone https://github.com/Emdinga/software_distribution.git
cd software-installation-web-app
Set up AWS services:

Create an S3 bucket to store your software packages.
Set up an API Gateway endpoint to trigger the Lambda function.
Deploy your Lambda function to handle software installation logic.
Ensure your EC2 instances are configured with SSM Agent and the correct IAM role to execute SSM commands.
Frontend:

Open frontend/index.html and modify any specific details related to your website (like available software options or layout).
Host the static website (using S3, CloudFront, or another hosting service).
Backend (Lambda and API Gateway):

Create a Lambda function based on the provided code to fetch software from S3 and install it using SSM.
Configure API Gateway to trigger the Lambda function when the user submits the software and hostname.
Deploying the Software
Once everything is set up, the process is as follows:

The user selects a software and enters the hostname in the frontend.
The form is submitted to the API Gateway.
The API Gateway triggers the Lambda function.
Lambda verifies the hostname, retrieves the software from S3, and sends the installation command to the Host instance using SSM.
The installation begins on the target Host instance.
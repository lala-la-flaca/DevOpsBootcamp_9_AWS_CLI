# <img src="https://github.com/user-attachments/assets/56192d5e-c2a7-4584-8b58-d6c8951e2ae4" width="250" /> AWS CLI

## Description

This demo project is part of **Module 9**: **AWS Services** from **Nana DevOps Bootcamp**. It focuses on using the **AWS Command Line Interface (CLI)** to manage AWS resources directly from the terminal.
<br />


## 🚀 Technologies Used

- **AWS CLI**: Command-line interface for managing AWS services.
- **AWS EC2**: AWS compute resources.
- **AWS IAM**: AWS service to manage users, groups, and roles.
- **Linux**: Ubuntu is used for server configuration and management.

  

## 🎯 Features

- **Install and configure AWS CLI**
- **Create and manage IAM Users, groups, and Policies using CLI**
- **Create and configure EC2 using CLI**.
- **Generate and Manage SSH key pairs using CLI**.
- **Security Group Configuration**.
- **Browse and list AWS resources using CLI**


## 🏗 Project Architecture

<img src=""/>

## 📝  Prerequisites
-  An active AWS account with admin privileges.

## ⚙️ Project Configuration

### Installing AWS CLI
1. Follow the instructions from the link below to install AWS CLI.
   
   [AWS CLI](https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html)
   
2. Configure the AWS CLI to access AWS, using the access keys created in the previous demo.

   ```bash
   aws configure
   ```

   <img src="https://github.com/lala-la-flaca/DevOpsBootcamp_7_docker_ECR/blob/main/Img/02%20Configuring%20Credentials%20to%20access%20CLI.png" width=800 />
   
3. Verify that the credentials were successfully created by navigating to the .aws directory and reviewing the credentials file.

   ```bash
   cd /.aws
   ls
   cat credentials
   ```
   
   <img src="https://github.com/lala-la-flaca/DevOpsBootcamp_7_docker_ECR/blob/main/Img/03%20To%20double%20check%20credentials.png" width=800 />

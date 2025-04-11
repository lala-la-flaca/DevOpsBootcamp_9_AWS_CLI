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
- **Create and configure EC2 using CLI**.
- **Create and manage IAM Users, groups, and Policies using CLI**
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

### Creating an EC2 Instance Using CLI
1. List existing security groups.

   ```bash
   
   ```
   <img src="" width=800 />
   
3. List current VPCs.
   
   ```bash
   
   ```
   <img src="" width=800 />
   
5. Create a new security group named my-sg.
   
   ```bash
   
   ```
   <img src="" width=800 />
   
7. Verify the configuration of the newly created security group.
   
   ```bash
   
   ```
   <img src="" width=800 />
   
9. Update the security group’s inbound rules to allow SSH (port 22) access from your IP address.
    
   ```bash
   
   ```
   <img src="" width=800 />
   
11. Create a new key pair.

    ```bash
   
     ```

    <img src="" width=800 />
   
13. List available subnets.

    ```bash
   
     ```

    <img src="" width=800 />
   
15. Launch a new EC2 instance using the previously defined parameters.

    ```bash
   
     ```
     <img src="" width=800 />
   
17. Modify permissions for the key pair file to ensure secure access.

    ```bash
   
     ```

    <img src="" width=800 />
   
19. Display the EC2 instance using filters.

    ```bash
   
     ```
    <img src="" width=800 />
   
21. Retrieve the EC2 instance ID using filters and queries.

    ```bash
   
     ```

    <img src="" width=800 />
   

### Creating a Group, User, and policies.
1. Create a group named MyGroupCli.
   
   ```bash
   
   ```
   <img src="" width=800 />
   
3. Create a user named MyUserCli.
   
   ```bash
   
   ```
   <img src="" width=800 />
   
5. Add MyUserCli to the group MyGroupCli.
   
   ```bash
   
   ```
   <img src="" width=800 />
   
7. Verify the group configuration.
   
   ```bash
   
   ```
   <img src="" width=800 />
   
9. Retrieve the ARN for the AmazonEC2FullAccess policy:
   * From the AWS Console: Navigate to IAM > Policies, search for the policy, and view its ARN.
     

   <img src="" width=800 />
   
   * Via CLI using:
     
   ```bash
   
   ```
   <img src="" width=800 />
   
10. Attach the policy to the group.

    ```bash

    ```
    <img src="" width=800 />
   
12. Verify the policies currently attached to the group.

    ```bash

    ```

    <img src="" width=800 />
   
14. Create a login profile for MyUserCli.

    ```bash

    ```

    <img src="" width=800 />
   
16. Retrieve the ARN of the user.

    ```bash
   
     ```

    <img src="" width=800 />
   
18. Retrieve the ARN of the group.

    ```bash
   
     ```

    <img src="" width=800 />
   
20. Create a new policy to allow password changes. The JSON template can be found under IAM > Policies > IAMUserChangePassword.

    ```bash

    ```

    <img src="" width=800 />
   
22. Generate access keys for the new user.

    ```bash
   
     ````

    <img src="" width=800 />
   
24. temporarily switch AWS CLI credentials to the new user.

    ```bash

    ```

    <img src="" width=800 />
   
26. If an error occurs (e.g., due to insufficient permissions), return to the default user by opening a new terminal session or switching profiles.

    ```bash

    ```

    <img src="" width=800 />
   

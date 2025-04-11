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
   aws ec2 describe-security-groups
   ```
   <img src="https://github.com/lala-la-flaca/DevOpsBootcamp_9_AWS_CLI/blob/main/Img/1%20security%20groups.png" width=800 />
   
3. List current VPCs.
   
   ```bash
   aws ec2 describe-vpcs
   ```
   <img src="https://github.com/lala-la-flaca/DevOpsBootcamp_9_AWS_CLI/blob/main/Img/2vpc%20details.png" width=800 />
   
5. Create a new security group named my-sg.
   
   ```bash
   aws ec2 create-security-group --group-name my-sg --description "My SG" --vpc-id vpc-0275fa69931e0fb4d
   ```
   <img src="https://github.com/lala-la-flaca/DevOpsBootcamp_9_AWS_CLI/blob/main/Img/3%20creating%20segurity%20group.png" width=800 />
   
7. Verify the configuration of the newly created security group.
   
   ```bash
     aws ec2 describe-security-groups --group-ids sg-05f6b3c32295f2c27
   ```
   <img src="https://github.com/lala-la-flaca/DevOpsBootcamp_9_AWS_CLI/blob/main/Img/4%20security%20group%20info%20just%20created.png" width=800 />
   
9. Update the security group’s inbound rules to allow SSH (port 22) access from your IP address.
    
   ```bash
     aws ec2 authorize-security-group-ingress \
     --group-id sg-05f6b3c32295f2c27 \
     --protocol tcp \
     --port 22 \
     --cidr 104.153.228.34/32
   ```
   <img src="https://github.com/lala-la-flaca/DevOpsBootcamp_9_AWS_CLI/blob/main/Img/5%20configuring%20inbound%20rules%20SG.png" width=800 />
   
11. Create a new key pair.

    ```bash
       aws ec2 create-key-pais \
       --key-name MyKpCLI \
       --query 'KeyMaterial' \
       --output text>MyKpCLI.pem
     ```

    <img src="https://github.com/lala-la-flaca/DevOpsBootcamp_9_AWS_CLI/blob/main/Img/6%20creating%20a%20KeyPair.png" width=800 />
   
13. List available subnets.

    ```bash
     aws ec2 describe-subnets
     ```

    <img src="https://github.com/lala-la-flaca/DevOpsBootcamp_9_AWS_CLI/blob/main/Img/7%20subnet%20info.png" width=800 />
   
15. Launch a new EC2 instance using the previously defined parameters.

    ```bash
       aws ec2 run-instances --image-id ami-0100e595e1cc1ff7f --count 1 --instance-type t2.micro --key-name MyKpCLI --security-group-ids sg-05f6b3c32295f2c27 --subnet-id subnet-0c58dcd66a93aa5c3
     ```
     <img src="https://github.com/lala-la-flaca/DevOpsBootcamp_9_AWS_CLI/blob/main/Img/9%20Cretaing%20ec2%20instance.png" width=800 />
   
17. Modify permissions for the key pair file to ensure secure access.

    ```bash
       ls -l MyKpCLI.pem
       chmod 400 MyKpCLI.pem
       ls -l MyKpCLI.pem
     ```

    <img src="https://github.com/lala-la-flaca/DevOpsBootcamp_9_AWS_CLI/blob/main/Img/10%20permission%20to%20pem%20file%20only%20x.png" width=800 />
   
19. Display the EC2 instance using filters.

    ```bash
       aws ec2 describe-instances \
        --filters "Name=tag:Type,Values="Web-server-Docker"
     ```
    <img src="https://github.com/lala-la-flaca/DevOpsBootcamp_9_AWS_CLI/blob/main/Img/12%20displaying%20the%20ec2%20instance%20with%20filters.png" width=800 />
   
21. Retrieve the EC2 instance ID using filters and queries.

    ```bash
       aws ec2 describe-instances \
       --filters "Name=tag:Type,Values=Web-server-Docker" \
       --query "Reservations[].Instances[].InstanceId"
     ```

    <img src="https://github.com/lala-la-flaca/DevOpsBootcamp_9_AWS_CLI/blob/main/Img/13%20getting%20th%20einstance%20ID%20using%20queries.png" width=800 />
   

### Creating a Group, User, and policies.
1. Create a group named MyGroupCli.
   
   ```bash
     aws iam create-group --group-name MyGroupCli
   ```
   <img src="https://github.com/lala-la-flaca/DevOpsBootcamp_9_AWS_CLI/blob/main/Img/14%20creating%20a%20group%20CLI.png" width=800 />
   
3. Create a user named MyUserCli.
   
   ```bash
     aws iam create-user --user-name MyUserCli
   ```
   <img src="https://github.com/lala-la-flaca/DevOpsBootcamp_9_AWS_CLI/blob/main/Img/15%20Creating%20a%20USER%20CLI.png" width=800 />
   
5. Add MyUserCli to the group MyGroupCli.
   
   ```bash
     aws iam add-user-to-group --user-name MyUserCli --group-name MyGroupCli
   ```
   <img src="https://github.com/lala-la-flaca/DevOpsBootcamp_9_AWS_CLI/blob/main/Img/16%20Assigning%20the%20User%20to%20the%20group%20via%20CLI.png" width=800 />
   
7. Verify the group configuration.
   
   ```bash
     aws iam get-group --group-name MyGroupCli
   ```
   <img src="https://github.com/lala-la-flaca/DevOpsBootcamp_9_AWS_CLI/blob/main/Img/17%20Displaying%20Group%20info%20with%20user%20added.png" width=800 />
   
9. Retrieve the ARN for the AmazonEC2FullAccess policy:
   * From the AWS Console: Navigate to IAM > Policies, search for the policy, and view its ARN.
     

   <img src="https://github.com/lala-la-flaca/DevOpsBootcamp_9_AWS_CLI/blob/main/Img/18%20getting%20the%20ARN%20of%20the%20policy.png" width=800 />
   
   * Via CLI using:
     
   ```bash
         aws iam list-policies \
           --query 'Policies[?PolicyName==`AmazonEC2FullAccess`].Arn' \
           --output text
   ```

10. Attach the policy to the group.

    ```bash
      aws iam attach-group-policy --group-name MyGroupCli --policy-arn arn:aws:iam::aws:policy/AmazonEC2FullAccess
    ```
    <img src="https://github.com/lala-la-flaca/DevOpsBootcamp_9_AWS_CLI/blob/main/Img/19%20ataching%20Policy.png" width=800 />
   
12. Verify the policies currently attached to the group.

    ```bash
        aws iam list-attached-group-policies --group-name MyGroupCli
    ```

    <img src="https://github.com/lala-la-flaca/DevOpsBootcamp_9_AWS_CLI/blob/main/Img/20%20Checking%20policies%20of%20the%20group.png" width=800 />
   
14. Create a login profile for MyUserCli.

    ```bash
      aws iam create-login-profile --user-name MyUserCli --password MyP@ssword --password-reset-required
    ```

    <img src="https://github.com/lala-la-flaca/DevOpsBootcamp_9_AWS_CLI/blob/main/Img/21%20Creating%20%20a%20login%20fpr%20the%20user.png" width=800 />
   
16. Retrieve the ARN of the user.

    ```bash
       aws iam get-user --user-name MyUserCli
     ```
   
18. Retrieve the ARN of the group.

    ```bash
       aws iam get-group --group-name MyGroupCli
     ```

    <img src="https://github.com/lala-la-flaca/DevOpsBootcamp_9_AWS_CLI/blob/main/Img/22%20checking%20group.png" width=800 />
   
20. Create a new policy to allow password changes. The JSON template can be found under IAM > Policies > IAMUserChangePassword.

    ```bash
      vim changePwdPolicy.json
    ```
    policy:
    ```bash
              {
              "Version": "2012-10-17",
              "Statement": [
                  {
                      "Effect": "Allow",
                      "Action": [
                          "iam:ChangePassword"
                      ],
                      "Resource": [
                          "arn:aws:iam::734066168422:user/MyUserCli""
                      ]
                  },
                  {
                      "Effect": "Allow",
                      "Action": [
                          "iam:GetAccountPasswordPolicy"
                      ],
                      "Resource": "*"
                  }
              ]
          }
    ```
    ```bash
      cat changePwdPolicy.json
      aws iam create-policy --policy-name changePwd --policy-document file://changePwdPolicy.json
    ```

    <img src="https://github.com/lala-la-flaca/DevOpsBootcamp_9_AWS_CLI/blob/main/Img/23%20JSON%20to%20allow%20the%20user%20to%20change%20password.png" width=800 />
   
22. Attach policy to the group
    
    ```bash
      aws iam attach-group-policy --group-name MyGroupCli --policy-arn arn:aws:iam::734066168422:policy/changePwd
    ```
24. Generate access keys for the new user.

    ```bash
     aws iam create-access-key --user-name MyUserCli
     ````

    <img src="https://github.com/lala-la-flaca/DevOpsBootcamp_9_AWS_CLI/blob/main/Img/24%20creating%20access%20key%20for%20user%20new%20user.png" width=800 />
   
25. temporarily switch AWS CLI credentials to the new user.

    ```bash
      export AWS_ACCESS_KEY_ID=AKIA2V2OA2JTGFRNJHEA
      export AWS_SECRET_ACCESS_KEY=*******************
    ```

    <img src="https://github.com/lala-la-flaca/DevOpsBootcamp_9_AWS_CLI/blob/main/Img/25%20Setting%20ENV%20variables.png" width=800 />
   
26. An error occurs due to insufficient permissions, return to the default user by opening a new terminal session or switching profiles.

    ```bash
     aws iam create-user --user-name test
    ```

    <img src="https://github.com/lala-la-flaca/DevOpsBootcamp_9_AWS_CLI/blob/main/Img/26%20trying%20to%20cretae%20a%20new%20user%20after%20switching%20user%20denied.PNG" width=800 />
   

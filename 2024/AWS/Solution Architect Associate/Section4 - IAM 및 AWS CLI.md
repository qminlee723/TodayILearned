# Section4: IAM 및 AWS CLI

## IAM: Users & Groups & Policies

### Users & Groups

- IAM = Identity and Access Management, Global Service
- Root account created by default, shouldn't be used or shared
- Users are people within your organization, and can be grouped
- Users don't have to belong to a group, and user can belong to multiple groups

<img src="./assets/Screenshot 2024-07-18 at 1.00.35 AM.png" alt="Screenshot 2024-07-18 at 1.00.35 AM" style="zoom:50%;" />



### Permissions

- Users or Groups can be assigned JSON documents called policies
- These policies define the permissions of the users
- In AWS you apply **the least privilege principle**: don't give more permissions than a users needs



## IAM 사용자 및 그룹 실습

### IAM 설정

- IAM 검색 > Dashboard로 이동
- Access Management > Users



### Users

- Using a root account is not the best practice
  - for safety reasons, it's better to create other user accounts like admin user
  - that's **IAM user**



## IAM 정책

### IAM Policies inheritance

<img src="./assets/Screenshot 2024-07-19 at 11.43.13 PM.png" alt="Screenshot 2024-07-19 at 11.43.13 PM" style="zoom:50%;" />



### IAM Policies Structure

```json
{
  "Version": "2012-10-17",
  "Id": "S3-Account-Permissions",
  "Statement": [
    {
      "Sid": "1",
      "Effect": "Allow",
      "Principal": {
        "AWS": ["arn:aws:iam::123456789012:root"]
      },
      "Action": [
        "s3:GetObject",
        "s3:PutObject"
      ],
      "Resource": ["arn:aws:s3:::mybucket/*"]
    }
  ]
}
```

- Consists of 
  - Version
    - policy language version, always include "2012-10-17"
  - Id
    - an identifier for the policy (optional)
  - Statement
    - one or more individual statements(required)
- **Statements** consists of
  - Sid
    - an identifier for the statement(optional)
  - Effect
    - whether the statement allows or denies access(Allow, Deny)
  - **Principal**
    - account/user/role to which this policy applied to
  - Action
    - list of actions this policy allows or denies
  - Resource
    - list of resources to which the actions applied to
  - Condition
    - conditions for when this policy is in effect(optional)





## IAM MFA 개요

### Password Policy

- Strong passwords = higher security for your account
- In AWS, you can setup a password policy:
  - set a minimum password length
  - Require specific character types:
    - including uppercase letters
    - lowercase letters
    - numbers
    - non-alphanumeric characters
  - Allow all IAM users to change their own passwords
  - Require users to change their password after some time(password expiration)
  - Prevent password re-use



### Multi-Factor-Authentication

- Users have access to your account and can possibly change configurations or delete resources in your AWS account
- You want to protect your **Root Accounts and IAM users**

- **MFA = password you know + security device you own**

- Main benefit of MFA

  - if a password is stolen or hacked, the account is not compromised

  

### MFA devices options in AWS

- virtual MFA device
  - support for multiple tokens on a single device
    - Google Authenticator
    - Authy
- Universal 2nd Factor(U2F) Security Key
  - YubiKey by Yubico(3rd party)
    - Support for multiple root and IAM users suing a single security key
- Hardware Key Fob MFA Device
  - Provided by Gemalto (3rd party)
- Hardware Key Fob MFA Device for AWS Gov Cloud
  - Provided by SurePassID(3rd party)



## AWS 액세스 키, CLI 및 SDK

### How can users access AWS?

- To access AWS, you have 3 options
  - AWS Management Console(protected by password + MFA)
  - AWS Command Line Interface(CLI): protected by access keys
  - AWS Software Development Kit(SDK) - for code: protected by access keys
- Access Keys are generated through the AWS Console
- Users manage their own access keys
- Access Keys are secret, just like a password - DONT SHARE
- Access Key ID ~= username
- Secret Access Key ~= password



### What's the AWS CLI?

- A tool that enables you to interact with AWS services using commands in your command-line shell
- Direct access to the public APIs of AWS services
- You can develop scripts to manage your resources
- It's open-source https://github.com/aws/aws-cli
- Alternative to using AWS Management Console


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





## IAM


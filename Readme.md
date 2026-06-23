# -> Create IAM Role 
### Create AIM role and Assign to user and Assume that role

### 1 Create User
#### [Steps]
- Login to Root Account
- IAM ->Users->Create New User->Complete steps 
- Select user -> Under Security and credentials Allow console login share Creds to user

### 2 Create Iam Role
#### [Steps]
- IAM ->[LSB] Roles -> Create Role ->[(*)Aws Account]   - - - -[[An AWS account]This Accoount ]->(Next)
- Search Policy example AmazonS3FullAccess (Next)
- Give Name (Create Role)

### 3 Attach IAM Role to user
### [steps]
- IAM ->[LSB]->Users->SELECT User
- Dropdown Add Permission Select - Create inline policy
- select JSON
-
```
{
	"Version": "2012-10-17",
	"Statement": [
		{
			"Sid": "Statement1",
			"Effect": "Allow",
			"Action": "sts:AssumeRole",
			"Resource": "arn:aws:iam::123456789123:role/S3FullACCESSROLE"
		}
	]
}
```
> [!NOTE] 
>"Action": "sts:AssumeRole" -> For Attaching Role [Assume Role]

> [!NOTE]
>"Resource": "arn:aws:iam::123456789123:role/S3FullACCESSROLE" -> This is ARN [Amazon resource number] (Go TO IAM [LSB]->Role->Newly created Role -> Copy ARN)
- (Next)
- Give Name 
- (Next) -- Attch complete

### 4 Assume Role
#### [Steps]
- Root User -> [LSB] Roles -> Newly created Role -> Copy Switch Role URL 
- Give that URL to IAM USER you created and attached the role

### 5 Assume Role BY IAM user
#### [Steps]
- Login With console Id password
- Now Simply Paste [IAM ROLE URL] in address bar ->next 
- Loggedin to Assumed Role
- Go to [TRC] profile ->switch back -[To return back to main IAM user Account]

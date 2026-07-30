---
title: "Prerequisites"
date: 2026-07-30
weight: 2
chapter: false
pre: " <b> 5.2. </b> "
---

To prepare for this workshop, you need to configure your local development environment, set up AWS CLI credentials, and provision infrastructure resources via CloudFormation.

---

### 1. Local Development Environment

Ensure your personal workstation is equipped with the following tools and command-line interfaces:

1. **AWS CLI (Command Line Interface):**
   - Command-line tool to interact with AWS services.
   - **Account Authentication:** Authenticate in your local environment using an AWS account with **AdministratorAccess** permissions via an **Access Key ID** and **Secret Access Key**.
   - Verify and configure using:
     ```bash
     aws configure
     # AWS Access Key ID: <YOUR_ACCESS_KEY>
     # AWS Secret Access Key: <YOUR_SECRET_KEY>
     # Default region name: us-east-1
     # Default output format: json
     ```

2. **Git CLI:**
   - Version control tool for cloning project repositories, storing automation scripts, and CloudFormation templates.
   - Verify with: `git --version`

3. **Python (v3.x):**
   - Runtime environment for automation scripts, API testing, and running the AWS SDK (`boto3`).
   - Verify with: `python --version` or `python3 --version`

4. **Node.js & npm + pnpm:**
   - JavaScript runtime and package managers for executing CLI tools, AWS CDK, or web applications.
   - Verify with: `node -v`, `npm -v`, `pnpm -v`

5. **Docker Desktop:**
   - Container virtualization engine on your local machine for packaging applications, testing containerized microservices, or local service emulation before cloud deployment.
   - Verify with: `docker --version`

---

### 2. IAM Permissions

If you choose not to use full AdministratorAccess and prefer to restrict permissions for your IAM User, attach the following IAM Policy:

```json
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "WorkshopPermissions",
            "Effect": "Allow",
            "Action": [
                "cloudformation:*",
                "cloudwatch:*",
                "ec2:AcceptTransitGatewayPeeringAttachment",
                "ec2:AcceptTransitGatewayVpcAttachment",
                "ec2:AllocateAddress",
                "ec2:AssociateAddress",
                "ec2:AssociateIamInstanceProfile",
                "ec2:AssociateRouteTable",
                "ec2:AssociateSubnetCidrBlock",
                "ec2:AssociateTransitGatewayRouteTable",
                "ec2:AssociateVpcCidrBlock",
                "ec2:AttachInternetGateway",
                "ec2:AttachNetworkInterface",
                "ec2:AttachVolume",
                "ec2:AttachVpnGateway",
                "ec2:AuthorizeSecurityGroupEgress",
                "ec2:AuthorizeSecurityGroupIngress",
                "ec2:CreateClientVpnEndpoint",
                "ec2:CreateClientVpnRoute",
                "ec2:CreateCustomerGateway",
                "ec2:CreateDhcpOptions",
                "ec2:CreateFlowLogs",
                "ec2:CreateInternetGateway",
                "ec2:CreateLaunchTemplate",
                "ec2:CreateNetworkAcl",
                "ec2:CreateNetworkInterface",
                "ec2:CreateNetworkInterfacePermission",
                "ec2:CreateRoute",
                "ec2:CreateRouteTable",
                "ec2:CreateSecurityGroup",
                "ec2:CreateSubnet",
                "ec2:CreateSubnetCidrReservation",
                "ec2:CreateTags",
                "ec2:CreateTransitGateway",
                "ec2:CreateTransitGatewayPeeringAttachment",
                "ec2:CreateTransitGatewayPrefixListReference",
                "ec2:CreateTransitGatewayRoute",
                "ec2:CreateTransitGatewayRouteTable",
                "ec2:CreateTransitGatewayVpcAttachment",
                "ec2:CreateVpc",
                "ec2:CreateVpcEndpoint",
                "ec2:CreateVpcEndpointConnectionNotification",
                "ec2:CreateVpcEndpointServiceConfiguration",
                "ec2:CreateVpnConnection",
                "ec2:CreateVpnConnectionRoute",
                "ec2:CreateVpnGateway",
                "ec2:DeleteCustomerGateway",
                "ec2:DeleteFlowLogs",
                "ec2:DeleteInternetGateway",
                "ec2:DeleteNetworkInterface",
                "ec2:DeleteNetworkInterfacePermission",
                "ec2:DeleteRoute",
                "ec2:DeleteRouteTable",
                "ec2:DeleteSecurityGroup",
                "ec2:DeleteSubnet",
                "ec2:DeleteSubnetCidrReservation",
                "ec2:DeleteTags",
                "ec2:DeleteTransitGateway",
                "ec2:DeleteTransitGatewayPeeringAttachment",
                "ec2:DeleteTransitGatewayPrefixListReference",
                "ec2:DeleteTransitGatewayRoute",
                "ec2:DeleteTransitGatewayRouteTable",
                "ec2:DeleteTransitGatewayVpcAttachment",
                "ec2:DeleteVpc",
                "ec2:DeleteVpcEndpoints",
                "ec2:DeleteVpcEndpointServiceConfigurations",
                "ec2:DeleteVpnConnection",
                "ec2:DeleteVpnConnectionRoute",
                "ec2:Describe*",
                "ec2:DetachInternetGateway",
                "ec2:DisassociateAddress",
                "ec2:DisassociateRouteTable",
                "ec2:GetLaunchTemplateData",
                "ec2:GetTransitGatewayAttachmentPropagations",
                "ec2:ModifyInstanceAttribute",
                "ec2:ModifySecurityGroupRules",
                "ec2:ModifyTransitGatewayVpcAttachment",
                "ec2:ModifyVpcAttribute",
                "ec2:ModifyVpcEndpoint",
                "ec2:ReleaseAddress",
                "ec2:ReplaceRoute",
                "ec2:RevokeSecurityGroupEgress",
                "ec2:RevokeSecurityGroupIngress",
                "ec2:RunInstances",
                "ec2:StartInstances",
                "ec2:StopInstances",
                "iam:AddRoleToInstanceProfile",
                "iam:AttachRolePolicy",
                "iam:CreateInstanceProfile",
                "iam:CreatePolicy",
                "iam:CreateRole",
                "iam:DeleteInstanceProfile",
                "iam:DeletePolicy",
                "iam:DeleteRole",
                "iam:DeleteRolePolicy",
                "iam:DetachRolePolicy",
                "iam:GetInstanceProfile",
                "iam:GetPolicy",
                "iam:GetRole",
                "iam:GetRolePolicy",
                "iam:ListPolicyVersions",
                "iam:ListRoles",
                "iam:PassRole",
                "iam:PutRolePolicy",
                "iam:RemoveRoleFromInstanceProfile",
                "lambda:CreateFunction",
                "lambda:DeleteFunction",
                "lambda:DeleteLayerVersion",
                "lambda:GetFunction",
                "lambda:GetLayerVersion",
                "lambda:InvokeFunction",
                "lambda:PublishLayerVersion",
                "logs:CreateLogGroup",
                "logs:DeleteLogGroup",
                "logs:DescribeLogGroups",
                "logs:PutRetentionPolicy",
                "route53:ChangeTagsForResource",
                "route53:CreateHealthCheck",
                "route53:CreateHostedZone",
                "route53:CreateTrafficPolicy",
                "route53:DeleteHostedZone",
                "route53:DisassociateVPCFromHostedZone",
                "route53:GetHostedZone",
                "route53:ListHostedZones",
                "route53resolver:AssociateResolverEndpointIpAddress",
                "route53resolver:AssociateResolverRule",
                "route53resolver:CreateResolverEndpoint",
                "route53resolver:CreateResolverRule",
                "route53resolver:DeleteResolverEndpoint",
                "route53resolver:DeleteResolverRule",
                "route53resolver:DisassociateResolverEndpointIpAddress",
                "route53resolver:DisassociateResolverRule",
                "route53resolver:GetResolverEndpoint",
                "route53resolver:GetResolverRule",
                "route53resolver:ListResolverEndpointIpAddresses",
                "route53resolver:ListResolverEndpoints",
                "route53resolver:ListResolverRuleAssociations",
                "route53resolver:ListResolverRules",
                "route53resolver:ListTagsForResource",
                "route53resolver:UpdateResolverEndpoint",
                "route53resolver:UpdateResolverRule",
                "s3:AbortMultipartUpload",
                "s3:CreateBucket",
                "s3:DeleteBucket",
                "s3:DeleteObject",
                "s3:GetAccountPublicAccessBlock",
                "s3:GetBucketAcl",
                "s3:GetBucketOwnershipControls",
                "s3:GetBucketPolicy",
                "s3:GetBucketPolicyStatus",
                "s3:GetBucketPublicAccessBlock",
                "s3:GetObject",
                "s3:GetObjectVersion",
                "s3:GetBucketVersioning",
                "s3:ListAllMyBuckets",
                "s3:ListBucket",
                "s3:PutAccountPublicAccessBlock",
                "s3:PutBucketAcl",
                "s3:PutBucketPolicy",
                "s3:PutBucketPublicAccessBlock",
                "s3:PutObject",
                "secretsmanager:*",
                "ssm:*"
            ],
            "Resource": "*"
        }
    ]
}
```

---

### 3. Repository Setup & Infrastructure Preparation for CodExecute

Before proceeding with the technical deployment steps of the workshop, prepare the Infrastructure as Code (AWS SAM / CloudFormation) codebase:

1. **Clone the CodExecute repository to your local workstation:**
   ```bash
   git clone https://github.com/phuvi301/CodExecute
   cd CodExecute
   ```
   For frontend: `cd fe && pnpm install` then use command `pnpm run dev` to run frontend at `http://localhost:3000`
   For backend: `cd be && python3 -m venv venv && source venv/bin/activate` for Linux and `cd be && python3 -m venv venv && venv\Scripts\activate` for Windows
   Then `pip install -r requirements.txt` inside the `be` folder and run `fastapi dev`.

2. **Overview of AWS Serverless Resources Provisioned in this Workshop:**
   - **3 Amazon S3 Buckets:** `codexecute-prod-frontend`, `codeexecute-testcases`, `codeexecuter-user-media`.
   - **8 Amazon DynamoDB Tables:** `Users`, `Problems`, `Submissions`, `TestCases`, `Posts`, `Notifications`, `UserFollows`, `Solutions`.
   - **Amazon SQS Queues:** `codeexecute-submission-queue`.
   - **AWS Lambda Functions:** `codeexecute-api` (FastAPI) and `codeexecute-worker` (Isolated sandbox execution engine).
   - **Amazon API Gateway & CloudFront Distribution:** REST API gateway entrypoint and global CDN web distribution.

3. **Infrastructure Readiness Check:**
   Once `aws configure` authentication is established and the project repository is downloaded, you are ready to proceed with the remaining hands-on steps of the **CodExecute** workshop.
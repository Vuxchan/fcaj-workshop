---
title: "Các bước chuẩn bị"
date: 2026-07-30
weight: 2
chapter: false
pre: " <b> 5.2. </b> "
---

Để sẵn sàng thực hành bài workshop này, bạn cần thiết lập môi trường phát triển tại máy local (Local Development Environment), cấu hình tài khoản AWS CLI và khởi tạo cụm hạ tầng bằng CloudFormation.

---

### 1. Môi Trường Phát Triển Local (Local Development Environment)

Đảm bảo máy tính cá nhân của bạn đã được cài đặt đầy đủ các công cụ phát triển và công cụ dòng lệnh sau:

1. **AWS CLI (Command Line Interface):**
   - Công cụ dòng lệnh giao tiếp với AWS API.
   - **Xác thực tài khoản:** Đăng nhập và cấu hình ở môi trường local bằng tài khoản AWS có quyền Admin (**AdministratorAccess**) thông qua cặp **Access Key ID** và **Secret Access Key**.
   - Kiểm tra và cấu hình bằng lệnh:
     ```bash
     aws configure
     # AWS Access Key ID: <YOUR_ACCESS_KEY>
     # AWS Secret Access Key: <YOUR_SECRET_KEY>
     # Default region name: us-east-1
     # Default output format: json
     ```

2. **Git CLI:**
   - Công cụ quản lý mã nguồn phiên bản dùng để clone các repository dự án, lưu trữ script và CloudFormation templates.
   - Kiểm tra bằng lệnh: `git --version`

3. **Python (v3.x):**
   - Môi trường thực thi script tự động hóa, kiểm thử API và chạy AWS SDK (`boto3`).
   - Kiểm tra bằng lệnh: `python --version` hoặc `python3 --version`

4. **Node.js & npm + pnpm:**
   - Môi trường JavaScript runtime và các trình quản lý gói (Package Managers) phục vụ việc chạy công cụ CLI, CDK hoặc các ứng dụng web.
   - Kiểm tra bằng lệnh: `node -v`, `npm -v`, `pnpm -v`

5. **Docker Desktop:**
   - Môi trường ảo hóa container tại máy local giúp đóng gói ứng dụng, chạy thử nghiệm các dịch vụ hoặc mô phỏng môi trường trước khi deploy lên Cloud.
   - Kiểm tra bằng lệnh: `docker --version`

---

### 2. Phân Quyền IAM (IAM Permissions)

Trong trường hợp bạn không sử dụng quyền AdministratorAccess tuyệt đối mà muốn thu hẹp chính sách phân quyền cho tài khoản IAM User, hãy gán IAM Policy sau:

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

### 3. Tải Mã Nguồn Dự Án & Chuẩn Bị Triển Khai Hạ Tầng CodExecute

Trước khi thực hiện các bước triển khai kỹ thuật của bài workshop, bạn cần chuẩn bị bộ kịch bản triển khai hạ tầng Infrastructure as Code (AWS SAM / CloudFormation):

1. **Clone repository mã nguồn CodExecute về máy local:**
   ```bash
   git clone https://github.com/phuvi301/CodExecute
   cd CodExecute
   ```
   Đối với frontend: `cd fe && pnpm install` và `pnpm run dev` để chạy môi trường dev tại link `http://localhost:3000`
   Đối với backend: `cd be && python3 -m venv venv && source venv/bin/activate` cho Linux và `cd be && python3 -m venv venv && venv\Scripts\activate` cho Windows
   Sau đó `pip install -r requirements.txt` bên trong thư mục `be` và chạy bằng lệnh `fastapi dev`.

2. **Cấu trúc tài nguyên dự án sẽ được khởi tạo trong bài workshop:**
   - **3 Amazon S3 Buckets:** `codeexecute-frontend`, `codeexecute-testcases`, `codeexecute-user-media`.
   - **7 Bảng Amazon DynamoDB:** `Users`, `Problems`, `Submissions`, `TestCases`, `Posts`, `Notifications`, `UserFollows`.
   - **Amazon SQS Queue:** `codexecute-submissions-queue`.
   - **AWS Lambda Functions:** `codeexecute-api` (FastAPI) và `codeexecute-worker` (Môi trường thực thi mã nguồn).
   - **Amazon API Gateway & CloudFront Distribution:** Cổng kết nối API và phân phối CDN cho ứng dụng web.

3. **Kiểm tra trạng thái sẵn sàng của hạ tầng:**
   Sau khi hoàn tất cấu hình `aws configure` và tải bộ mã nguồn, bạn đã sẵn sàng bước vào các nội dung thực hành tiếp theo của dự án **CodExecute**.
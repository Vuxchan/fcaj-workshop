---
title: "Deploy Frontend on Amazon S3"
date: 2026-07-30
weight: 3
chapter: false
pre: " <b> 5.3. </b> "
---

# DEPLOYING REACT FRONTEND APPLICATION ON AMAZON S3

In this section, we will create an **Amazon S3 Bucket**, build the **CodExecute React (Vite) Frontend** application targeting `VITE_API_URL`, upload the production assets (`dist` folder) to S3, enable Bucket Versioning for rollback protection, disable public Static Website Hosting to enhance security, and attach a restrictive **Bucket Policy** allowing access strictly to **Amazon CloudFront** via Origin Access Control (OAC).

---

### Step 1: Create S3 Bucket & Upload Build Assets in `dist` Folder to S3

1. Access the **Amazon S3 Console**.
2. Click **Create bucket**, enter your Bucket Name (e.g., `codeexecute-frontend`), and select your designated AWS Region.

<div align="center">

<img src="/images/5-Workshop/5.3-S3/bucket-fe1.jpg" alt="Create S3 Bucket" style="width: 80%; max-width: 900px; border-radius: 6px;">

<p style="font-size: 1rem; font-weight: 600; margin-top: 8px;">
<i>Figure 5.3.1: Entering S3 Bucket name and region selection</i>
</p>

</div>

3. Configure baseline bucket settings and confirm creation.

<div align="center">

<img src="/images/5-Workshop/5.3-S3/bucket-fe2.jpg" alt="Configure S3 Bucket creation" style="width: 80%; max-width: 900px; border-radius: 6px;">

<p style="font-size: 1rem; font-weight: 600; margin-top: 8px;">
<i>Figure 5.3.2: Confirming S3 Bucket configuration settings</i>
</p>

</div>

4. Verify creation of the `codeexecute-frontend` S3 Bucket.

<div align="center">

<img src="/images/5-Workshop/5.3-S3/bucket-fe3.jpg" alt="S3 Bucket created successfully" style="width: 80%; max-width: 900px; border-radius: 6px;">

<p style="font-size: 1rem; font-weight: 600; margin-top: 8px;">
<i>Figure 5.3.3: Successfully created codeexecute-frontend S3 Bucket</i>
</p>

</div>

5. Open your terminal in the `fe` directory of the CodExecute codebase. Build the application with `VITE_API_URL=https://d1hsp5bm4hkjmb.cloudfront.net` and upload the `dist` folder to S3:

#### Bash / Linux / macOS:
```bash
cd fe

# Set API URL environment variable
export VITE_API_URL=https://d1hsp5bm4hkjmb.cloudfront.net

# Build React Vite production bundle
pnpm build

# Sync compiled dist folder to S3 Bucket
aws s3 sync dist/ s3://codeexecute-frontend --delete
```

#### PowerShell (Windows):
```powershell
cd fe

# Set API URL environment variable in PowerShell
$env:VITE_API_URL="https://d1hsp5bm4hkjmb.cloudfront.net"

# Build React Vite production bundle
pnpm build

# Sync compiled dist folder to S3 Bucket
aws s3 sync dist/ s3://codeexecute-frontend --delete
```

<div align="center">

<img src="/images/5-Workshop/5.3-S3/bucket-fe4.jpg" alt="Build and upload assets to S3" style="width: 80%; max-width: 900px; border-radius: 6px;">

<p style="font-size: 1rem; font-weight: 600; margin-top: 8px;">
<i>Figure 5.3.4: Uploading compiled production assets to S3 Bucket</i>
</p>

</div>

6. Verify uploaded files inside the S3 Bucket.

<div align="center">

<img src="/images/5-Workshop/5.3-S3/bucket-fe5.jpg" alt="Uploaded files inside S3 Bucket" style="width: 80%; max-width: 900px; border-radius: 6px;">

<p style="font-size: 1rem; font-weight: 600; margin-top: 8px;">
<i>Figure 5.3.5: Uploaded dist files displayed in the S3 Console</i>
</p>

</div>

---

### Step 2: Enable Bucket Versioning & Disable Static Website Hosting for Security

1. In the **Properties** tab of your S3 Bucket, locate **Bucket Versioning** and click **Edit**. Select **Enable**. Enabling versioning preserves historical build artifacts, allowing seamless rollback to previous build versions whenever necessary.

<div align="center">

<img src="/images/5-Workshop/5.3-S3/bucket-fe7.jpg" alt="Enable Bucket Versioning" style="width: 80%; max-width: 900px; border-radius: 6px;">

<p style="font-size: 1rem; font-weight: 600; margin-top: 8px;">
<i>Figure 5.3.6: Enabling Bucket Versioning for build version rollback support</i>
</p>

</div>

2. Scroll down to **Static website hosting** and ensure it is set to **Disabled**. Disabling direct static website hosting enforces infrastructure security, mandating all incoming user web traffic to route securely through **Amazon CloudFront** with HTTPS encryption.

<div align="center">

<img src="/images/5-Workshop/5.3-S3/bucket-fe8.jpg" alt="Disable Static Website Hosting" style="width: 80%; max-width: 900px; border-radius: 6px;">

<p style="font-size: 1rem; font-weight: 600; margin-top: 8px;">
<i>Figure 5.3.7: Disabling Static Website Hosting to secure S3 Bucket content</i>
</p>

</div>

---

### Step 3: Configure CloudFront Origin Access Control (OAC) Bucket Policy

To allow Amazon CloudFront to fetch private static assets from S3 without exposing the bucket to the public Internet, attach the following **Bucket Policy**:

1. Under the **Permissions** tab, scroll to **Bucket policy** and click **Edit**.
2. Paste the JSON Bucket Policy granting explicit read permissions to your CloudFront Distribution (`E2O7SA7QXFHIBT`):

```json
{
    "Version": "2008-10-17",
    "Id": "PolicyForCloudFrontPrivateContent",
    "Statement": [
        {
            "Sid": "AllowCloudFrontServicePrincipal",
            "Effect": "Allow",
            "Principal": {
                "Service": "cloudfront.amazonaws.com"
            },
            "Action": "s3:GetObject",
            "Resource": "arn:aws:s3:::codeexecute-frontend/*",
            "Condition": {
                "StringEquals": {
                    "AWS:SourceArn": "arn:aws:cloudfront::014936669466:distribution/E2O7SA7QXFHIBT"
                }
            }
        }
    ]
}
```

3. Click **Save changes**.

---

### Verification

At this point, the `codeexecute-frontend` S3 Bucket is securely hardened with public access disabled, granting access exclusively to **Amazon CloudFront** to serve web traffic at: [https://d1hsp5bm4hkjmb.cloudfront.net](https://d1hsp5bm4hkjmb.cloudfront.net).
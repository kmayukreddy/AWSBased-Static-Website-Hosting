# 🌍 Static Website Hosting on AWS with Custom Domain (travelaws.xyz)

This project focuses on building and deploying a secure, cost-effective, and highly available static website using **AWS Cloud Services**, integrated with a custom domain purchased from GoDaddy.

---

## 🎯 Project Goals

- ✅ Deploy a static website using **AWS S3 + CloudFront**
- 🌐 Integrate a custom domain: **[travelaws.xyz](http://travelaws.xyz)**
- 🚀 Achieve global content delivery with **low latency**
- 🔐 Ensure secure access via HTTPS (SSL)
- 💸 Use a cost-effective serverless solution (no EC2)

---

## 🧰 Tools & Services Used

- **Amazon S3** – Static website hosting
- **Amazon CloudFront** – Global CDN (Content Delivery Network)
- **GoDaddy** – Custom domain registrar
- **AWS Certificate Manager (ACM)** – SSL certificate for HTTPS
- **Amazon Route 53** – DNS management (optional or manual DNS setup in GoDaddy)

---

## 📦 Project Workflow

### 1. **Purchased Custom Domain**
   - Bought `travelaws.xyz` from GoDaddy

### 2. **Created & Configured S3 Bucket**
   - Bucket name: `travelaws.xyz`
   - Enabled static website hosting
   - Uploaded `index.html` and `error.html`

### 3. **Set Bucket Policy for Public Read Access**
```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "PublicReadGetObject",
      "Effect": "Allow",
      "Principal": "*",
      "Action": "s3:GetObject",
      "Resource": "arn:aws:s3:::travelaws.xyz/*"
    }
  ]
}
4. Created CloudFront Distribution
Origin: travelaws.xyz.s3.amazonaws.com

Enabled HTTPS (via ACM)

Set default root object: index.html

5. Issued SSL Certificate (ACM)
Verified domain ownership via DNS (GoDaddy)

Attached certificate to CloudFront

6. Configured Domain in GoDaddy
Added a CNAME record pointing to CloudFront domain (e.g., d123abcxyz.cloudfront.net)

7. Tested Website
Visited: http://travelaws.xyz and https://travelaws.xyz


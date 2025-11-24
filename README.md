# Configure VPC Flow Logs and Store Logs in S3 Using IAM Role

## 📘 Project Overview

This project demonstrates how to capture all incoming and outgoing
network traffic from an AWS VPC using VPC Flow Logs and store those logs
securely in an Amazon S3 bucket. An IAM Role authorizes the VPC Flow
Logs service to deliver logs into S3. This setup is useful for security
monitoring, auditing, troubleshooting, and network visibility.

------------------------------------------------------------------------

## 🛠️ Services Used

-   Amazon VPC\
-   VPC Flow Logs\
-   Amazon S3\
-   IAM Role\
-   EC2 Instance

------------------------------------------------------------------------

## 🎯 Objective

Capture network traffic from a VPC and store logs in S3 using an IAM
role, ensuring secure logging and monitoring.

------------------------------------------------------------------------

## 🏗️ Architecture Diagram

(Add your diagram here if needed)

------------------------------------------------------------------------

# 🚀 Step-by-Step Implementation

## **Step 1: Create a VPC**

-   Open VPC Console\
-   Click *Create VPC* → Choose *VPC only*\
-   Provide a name\
-   Keep default CIDR\
-   Create VPC

------------------------------------------------------------------------

## **Step 2: Create an S3 Bucket with Versioning**

-   Open S3 Console\
-   Click *Create bucket*\
-   Enter a unique bucket name\
-   Select same region as VPC\
-   Enable *Versioning*\
-   Create bucket

------------------------------------------------------------------------

## **Step 3: Add Bucket Policy**

Add policy to allow VPC Flow Logs to write to S3.

------------------------------------------------------------------------

## **Step 4: Create IAM Role (Trust Policy)**

-   Go to IAM → Roles → *Create Role*\
-   Select *Custom Trust Policy*\
-   Paste trust policy JSON\
-   Skip permissions\
-   Name and create role

------------------------------------------------------------------------

## **Step 5: Attach Permission Policy**

-   Go to IAM → Role → *Permissions*\
-   Add inline policy with S3 write permissions

------------------------------------------------------------------------

## **Step 6: Enable VPC Flow Logs**

-   Open VPC → Your VPC → Flow Logs\
-   Click *Create Flow Log*\
-   Select **All traffic**\
-   Destination: **S3**\
-   Select IAM Role\
-   Provide S3 bucket ARN\
-   Create

------------------------------------------------------------------------

## **Step 7: Generate Traffic Using EC2**

SSH into EC2 and run:

    ping google.com

This generates network traffic for the flow logs.

------------------------------------------------------------------------

## **Step 8: Verify Logs in S3**

Navigate in S3:

    AWSLogs/<account-id>/vpcflowlogs/<region>/<date>/

Download the log file and verify captured entries.

------------------------------------------------------------------------

# 🏁 Conclusion

This project successfully built a secure and centralized network logging
system using AWS VPC, IAM, and S3. With VPC Flow Logs enabled and
verified through EC2-generated traffic, this setup provides reliable and
scalable monitoring of network activity, greatly improving security
visibility and operational insights.

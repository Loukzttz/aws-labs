# VPC Basics: Networking Exploration and IAM Describe Permissions

## Objective
Explore AWS networking fundamentals by examining the default VPC, subnets, route tables, and internet gateways using an IAM user with least-privilege permissions. Validate how IAM `Describe` permissions allow visibility into networking resources without modification rights.

---

## Services Used
- Amazon VPC
- Subnets
- Route Tables
- Internet Gateway
- AWS IAM

---

## IAM Configuration
This lab was performed using an IAM user (not the root account).

To ensure visibility into VPC networking components, JSON policies were added to allow read-only access to networking resources, including:
- `ec2:DescribeVpcs`
- `ec2:DescribeSubnets`
- `ec2:DescribeRouteTables`
- `ec2:DescribeInternetGateways`

These permissions enabled inspection of VPC resources without granting create, modify, or delete access.

---

## Steps Performed

### 1. Verified Region and IAM User Context
- Confirmed the correct AWS region was selected.
- Performed all actions using an IAM user following least-privilege best practices.

### 2. Identified the Default VPC
- Navigated to the VPC console and selected **Your VPCs**.
- Located the default VPC and reviewed:
  - VPC ID
  - CIDR block
  - Availability state

### 3. Explored Subnets
- Navigated to **Subnets**.
- Examined multiple subnets associated with the default VPC.
- Observed:
  - Subnet CIDR blocks
  - Availability Zones
  - Relationship between subnets and the VPC

### 4. Reviewed Internet Gateway
- Navigated to **Internet Gateways**.
- Verified that an Internet Gateway was attached to the default VPC.
- Confirmed its role in enabling outbound internet access.

### 5. Analyzed Route Tables
- Navigated to **Route Tables**.
- Selected the main route table associated with the default VPC.
- Reviewed routes including:
  - Local VPC routing
  - `0.0.0.0/0` route pointing to the Internet Gateway

### 6. Connected Networking Concepts to EC2
- Reviewed how EC2 instances rely on:
  - VPC placement
  - Subnet configuration
  - Route tables
  - Internet Gateway access
  - Security groups for traffic control
- Connected these concepts to prior EC2 SSH labs and instance connectivity.

---

## Issues Encountered
- Initial lack of visibility into some networking resources due to missing IAM `Describe` permissions.

---

## Resolution
- Added only required read-only EC2 `Describe` permissions via JSON policy.
- Revalidated access using the IAM user without switching to the root account.

---

## Key Takeaways
- A VPC is a logically isolated virtual network in AWS.
- Subnets divide a VPC and are scoped to individual availability zones.
- Internet Gateways enable communication between a VPC and the internet.
- Route tables control traffic flow within a VPC and externally.
- IAM `Describe` permissions allow safe visibility without risking configuration changes.
- Using an IAM user instead of root aligns with real-world cloud security best practices.
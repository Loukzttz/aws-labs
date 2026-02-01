# EC2 SSH Access, IAM, and Security Group Troubleshooting Lab

## Objective
Launch and manage an Amazon EC2 instance using least-privilege IAM permissions while configuring secure SSH access through a custom security group. Troubleshoot IAM AccessDenied errors related to security group management and EC2 instance lifecycle actions.

---

## Services Used
- Amazon EC2
- AWS IAM
- Amazon VPC (default)
- Security Groups

---

## Steps Performed

### 1. Security Group Creation
- Created a custom security group named `ec2-ssh-sg`.
- Configured an inbound rule allowing SSH (TCP port 22) from my public IP using a `/32` CIDR block.
- Left outbound rules as default (all traffic allowed).
- Used the default VPC.

### 2. IAM Permission Troubleshooting (Security Groups)
- Encountered IAM `AccessDenied` errors when attempting to modify and delete the security group.
- Identified missing EC2 API permissions required for security group management.
- Updated the custom EC2 IAM policy to include:
  - `ec2:RevokeSecurityGroupEgress`
  - `ec2:DeleteSecurityGroup`
- Logged out and back in as the IAM user to refresh permissions.
- Successfully deleted the security group to validate permissions.

### 3. EC2 Instance Launch
- Launched an EC2 instance using Amazon Linux and the `t2.micro` instance type.
- Attached the custom security group and key pair.
- Verified that the correct AWS region was selected to ensure instance visibility.

### 4. SSH Access Validation (Conceptual)
- Reviewed SSH connection requirements:
  - Port 22 allowed in the security group
  - Correct key pair
  - Correct username (`ec2-user`)
  - Public IPv4 address
- Confirmed understanding of SSH command structure and access flow.

### 5. IAM Permission Troubleshooting (Instance Termination)
- Encountered an `AccessDenied` error when attempting to terminate the EC2 instance.
- Identified the missing IAM permission required for instance termination.
- Updated the IAM policy to include:
  - `ec2:TerminateInstances`
- Logged out and back in to refresh the session.
- Successfully terminated the EC2 instance to complete the lab and prevent unnecessary costs.

---

## Issues Encountered
- Missing IAM permissions for security group modification and deletion.
- CIDR block requirement for SSH inbound rules.
- EC2 instance visibility depended on correct region selection.
- Missing permission to terminate EC2 instances.

---

## Resolutions
- Added only the required EC2 API permissions to maintain least privilege.
- Used a `/32` CIDR block to restrict SSH access to a single IP.
- Verified region alignment before managing resources.
- Updated IAM policy to allow EC2 instance termination.

---

## Key Takeaways
- IAM controls AWS resource actions, not OS-level SSH access.
- Security groups act as instance-level virtual firewalls.
- SSH access requires correct networking, key pairs, and region awareness.
- EC2 instance lifecycle actions require explicit IAM permissions.
- Applying least-privilege IAM policies improves security while enabling operational tasks.
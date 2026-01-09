📄 EC2 Lab 2 — Secure EC2 Launch Using Limited IAM User
Objective
Launch an EC2 instance successfully using an IAM user with least-privilege permissions, without using the root account or AdministratorAccess.

Lab Steps
Prepared the environment

Configured an AWS budget and alerts to prevent unexpected costs.

Verified that the IAM user did not have AdministratorAccess.

Created a custom IAM policy

Logged in as the root user to create an IAM policy using the JSON editor.

Defined a policy allowing only the required EC2 actions, including:

ec2:RunInstances

ec2:Describe*

ec2:CreateSecurityGroup

ec2:AuthorizeSecurityGroupIngress

ec2:CreateTags

Named the policy EC2LaunchLimited.

Attached the policy to an IAM user

Attached the custom policy directly to the IAM user.

Logged out and back in to ensure permissions applied correctly.

Launched an EC2 instance as the IAM user

Logged in using the IAM sign-in URL.

Navigated to the EC2 console and initiated the instance launch process.

Selected:

Amazon Linux AMI

t2.micro / t3.micro instance type

Default VPC and subnet

Created a new security group allowing SSH (port 22) from the local IP address.

Launched the instance successfully without permission errors.

Observed EC2 instance behavior

Verified the instance reached the Running state.

Reviewed instance details, security group rules, and monitoring metrics.

No key pair was attached during this lab due to IAM permission constraints.

Cleanup

Stopped or terminated the EC2 instance to avoid ongoing charges.

Results
The EC2 instance launched successfully using an IAM user with limited permissions.

Least-privilege access was enforced correctly.

No administrative or root-level permissions were used.

Cost controls were in place prior to deployment.

Key Takeaways
EC2 launches require multiple API permissions, not a single action.

IAM policies control who can launch resources, while IAM roles control what running resources can do.

Using custom IAM policies is safer and more realistic than granting broad administrative access.

Budget configuration should always precede resource creation.

Notes
A key pair was not attached during this lab due to permission restrictions.

A follow-up lab will cover EC2 key pairs and secure SSH access.
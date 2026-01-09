EC2 Lab 1 – Validating ReadOnlyAccess Permissions

Objective:
Confirm that an IAM user with the AWS-managed ReadOnlyAccess policy cannot create EC2 resources.

Checklist:

Logged in as IAM user ✅

Navigated to EC2 console ✅

Attempted to launch EC2 instance ✅

EC2 launch failed as expected ✅

Observations:

The EC2 launch workflow was accessible, but the operation failed during resource creation.

AWS returned an authorization error for the ec2:CreateSecurityGroup action.

Reflection:
This lab demonstrated how IAM enforces least-privilege access at the API level. Although the user could view and configure resources, AWS correctly blocked resource creation. In real-world cloud environments, this process is essential for preventing privilege escalation and ensuring users only have the permissions required for their role.
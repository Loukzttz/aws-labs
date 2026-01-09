First AWS Cloud Lab – IAM & Least Privilege

In my first AWS cloud lab, I created an IAM user and an IAM group using the root account. I attached the AWS-managed ReadOnlyAccess policy to the group and assigned the IAM user to it.

I then validated the configuration by signing in as the IAM user and attempting to launch an EC2 instance. Initially, I encountered an authorization error and realized the IAM user had not been properly added to the group. After correcting this from the root account, I signed back in as the IAM user and confirmed that read-only access was functioning as expected.

When attempting to launch an EC2 instance, the operation failed due to insufficient permissions, confirming that the ReadOnlyAccess policy was correctly enforcing least privilege. This lab reinforced the importance of validating IAM configurations and demonstrated how least-privilege access prevents unauthorized resource creation.

Steps:

1. Create IAM User
2. Create IAM Group
3. Attach "ReadOnlyAccess"
4. Log in as the IAM User
5. Try to launch an EC2 Instance.

Result: It should have successful workflow, but fail because the API actions failed, which is what AWS IAM is designed to do. It was denied due to insufficient IAM permissions.
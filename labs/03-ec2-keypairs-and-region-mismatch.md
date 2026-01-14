# EC2 Lab 3 — Key Pairs, Launch, and Region Awareness

## Objective
Create an EC2 key pair, launch an EC2 instance using the key pair, and practice secure cleanup. Reinforce that EC2 resources are region-scoped.

## Steps Performed
1. Updated IAM permissions to allow key pair creation (`ec2:CreateKeyPair`).
2. Logged in as IAM user and created a key pair (downloaded `.pem` file).
3. Launched an EC2 instance using:
   - Amazon Linux AMI
   - t2.micro/t3.micro
   - Default VPC
   - Security group allowing SSH (22) from My IP
   - Selected the created key pair during launch
4. Attempted to stop the instance using root and initially could not find it.
5. Identified the issue as a **region mismatch**, switched to the correct region, and located the instance.
6. Stopped the instance to prevent charges.

## Results
- Successfully created and used an EC2 key pair for instance launch.
- Confirmed IAM permissions and least-privilege workflow.
- Resolved a region mismatch while managing resources.
- Instance was stopped for cost control.

## Key Takeaways
- EC2 instances exist in exactly **one AWS region**.
- If you can’t find a resource, check **region first**, then confirm **account ID**.
- Private key files (`.pem`) must be stored securely and **never uploaded to GitHub**.

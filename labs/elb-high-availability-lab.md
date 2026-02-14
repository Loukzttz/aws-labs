# Application Load Balancer (ELB) – High Availability Lab

## Objective
Deploy an internet-facing Application Load Balancer across multiple Availability Zones and understand how ELB integrates with VPC networking and security groups.

## Services Used
- Elastic Load Balancing (Application Load Balancer)
- Amazon VPC
- Subnets (Multi-AZ)
- Security Groups
- Amazon EC2 (optional targets)

## Steps Performed
- Created an internet-facing Application Load Balancer.
- Selected the default VPC and mapped multiple subnets across Availability Zones.
- Created a dedicated security group allowing inbound HTTP traffic.
- Configured a listener and target group for HTTP routing.
- Encountered an IAM permission error for service-linked role creation.
- Updated IAM policy to allow `iam:CreateServiceLinkedRole` for ELB.
- Successfully deployed the load balancer and verified active status.

## Key Takeaways
- ALBs distribute traffic across multiple Availability Zones for high availability.
- Security groups enforce least-privilege access at both the ALB and EC2 layers.
- Service-linked roles are required for AWS services like ELB.
- IAM permission errors can be diagnosed and fixed using least-privilege policies.

# Commands — Custom VPC

Most of this project is done through the AWS Console. These are useful CLI commands for reference.

---

## AWS CLI — VPC operations

```bash
# List all VPCs
aws ec2 describe-vpcs

# List all subnets
aws ec2 describe-subnets

# List all internet gateways
aws ec2 describe-internet-gateways

# List all route tables
aws ec2 describe-route-tables

# Delete a VPC (must delete dependencies first)
aws ec2 delete-vpc --vpc-id vpc-0d5294e30060775d0
```

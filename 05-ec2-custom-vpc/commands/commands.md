# Commands — EC2 Inside Custom VPC

---

## Local machine (Windows PowerShell)

```powershell
# SSH into the EC2 instance
ssh -i "awswin.pem" ec2-user@13.126.59.120
```

## Local machine (Mac/Linux terminal)

```bash
# Fix key permissions
chmod 400 awswin.pem

# SSH into the instance
ssh -i "awswin.pem" ec2-user@13.126.59.120
```

---

## EC2 instance terminal

```bash
# Amazon Linux 2023 uses IMDSv2 — get a token first
TOKEN=$(curl -s -X PUT "http://169.254.169.254/latest/api/token" \
  -H "X-aws-ec2-metadata-token-ttl-seconds: 21600")

# Get the MAC address
MAC=$(curl -s -H "X-aws-ec2-metadata-token: $TOKEN" \
  http://169.254.169.254/latest/meta-data/network/interfaces/macs/)

# Get VPC ID
curl -s -H "X-aws-ec2-metadata-token: $TOKEN" \
  http://169.254.169.254/latest/meta-data/network/interfaces/macs/${MAC}vpc-id

# Get Subnet ID
curl -s -H "X-aws-ec2-metadata-token: $TOKEN" \
  http://169.254.169.254/latest/meta-data/network/interfaces/macs/${MAC}subnet-id

# Test internet connectivity
ping -c 4 google.com

# Check public IP from inside the instance
curl -s -H "X-aws-ec2-metadata-token: $TOKEN" http://checkip.amazonaws.com
```

---

## AWS CLI — verify resources

```bash
# List EC2 instances and their VPC/subnet
aws ec2 describe-instances --query "Reservations[*].Instances[*].[InstanceId,VpcId,SubnetId,PublicIpAddress]" --output table
```

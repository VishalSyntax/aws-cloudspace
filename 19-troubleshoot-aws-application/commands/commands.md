# Project 19 — Troubleshooting Commands

> Built through the AWS Console. The SSH/bash commands below were actually run on the EC2 instance while troubleshooting. The AWS CLI commands are just for reference.

---

## Check web server status

```bash
sudo systemctl status nginx
sudo systemctl status httpd
```

## Start web server

```bash
sudo systemctl start nginx
sudo systemctl enable nginx

sudo systemctl start httpd
sudo systemctl enable httpd
```

## View Nginx logs

```bash
sudo tail -f /var/log/nginx/error.log
sudo tail -f /var/log/nginx/access.log
```

## View Apache logs

```bash
sudo tail -f /var/log/httpd/error_log
sudo tail -f /var/log/httpd/access_log
```

## Check open ports on the instance

```bash
sudo ss -tlnp
```

## Test HTTP locally on the instance

```bash
curl -v http://localhost
```

---

> The commands below are CLI reference only — not used during the project.

## Describe security group rules

```bash
aws ec2 describe-security-groups \
  --group-ids YOUR_SECURITY_GROUP_ID \
  --region ap-south-1
```

## Describe route table

```bash
aws ec2 describe-route-tables \
  --route-table-ids YOUR_ROUTE_TABLE_ID \
  --region ap-south-1
```

## Describe target health

```bash
aws elbv2 describe-target-health \
  --target-group-arn YOUR_TARGET_GROUP_ARN \
  --region ap-south-1
```

# Commands — Load Balancer

## EC2 instances — install Apache with unique page

```bash
# On instance 1
sudo yum install httpd -y
sudo systemctl start httpd
sudo systemctl enable httpd
echo "<h1>Response from Server 1</h1>" | sudo tee /var/www/html/index.html

# On instance 2
sudo yum install httpd -y
sudo systemctl start httpd
sudo systemctl enable httpd
echo "<h1>Response from Server 2</h1>" | sudo tee /var/www/html/index.html
```

## AWS CLI

```bash
# List load balancers
aws elbv2 describe-load-balancers

# List target groups
aws elbv2 describe-target-groups

# Check target health
aws elbv2 describe-target-health \
  --target-group-arn My_TARGET_GROUP_ARN
```

# Commands — Two-Tier Web Application

---

## Local machine (Windows PowerShell)

```powershell
# SSH into EC2 app server
ssh -i "awswin.pem" ec2-user@13.203.207.68
```

## Local machine (Mac/Linux)

```bash
chmod 400 awswin.pem
ssh -i "awswin.pem" ec2-user@13.203.207.68
```

---

## EC2 instance terminal

```bash
# Update packages
sudo yum update -y

# Install Apache and PHP
sudo yum install httpd php php-mysqlnd -y

# Start and enable Apache
sudo systemctl start httpd
sudo systemctl enable httpd

# Check Apache status
sudo systemctl status httpd

# Install MySQL client to test DB connection
sudo yum install mysql -y

# Test connection from EC2 to RDS
mysql -h webapp-db.c9u0wwe0km51.ap-south-1.rds.amazonaws.com -u admin -p

# Create a simple PHP test page
sudo tee /var/www/html/db-test.php << 'EOF'
<?php
$host = 'webapp-db.c9u0wwe0km51.ap-south-1.rds.amazonaws.com';
$user = 'admin';
$pass = 'MY_DB_PASSWORD';
$db   = 'webapp-db';

$conn = new mysqli($host, $user, $pass, $db);

if ($conn->connect_error) {
    die("Connection failed: " . $conn->connect_error);
}
echo "<h1>Connected to RDS successfully!</h1>";
$conn->close();
?>
EOF

# Check the PHP file is there
cat /var/www/html/db-test.php
```



---

## AWS CLI — verify resources

```bash
# List EC2 instances
aws ec2 describe-instances --query "Reservations[*].Instances[*].[InstanceId,VpcId,SubnetId,PublicIpAddress,State.Name]" --output table

# List RDS instances
aws rds describe-db-instances --query "DBInstances[*].[DBInstanceIdentifier,DBInstanceStatus,Endpoint.Address]" --output table
```

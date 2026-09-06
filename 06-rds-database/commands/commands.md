# Commands — RDS Database

Most of this project is done through the AWS Console. These are the commands for connecting to and testing the database.

---

## Local machine (Windows PowerShell)

```powershell
# Step 1 — SSH into EC2 (jump box)
ssh -i "awswin.pem" ubuntu@13.233.17.142
```

## On the EC2 instance (Ubuntu) — install MySQL client and connect to RDS

```bash
# Install MySQL client
sudo apt update
sudo apt install mysql-client -y

# Test port connectivity before connecting via MySQL
nc -zv fct.c9u0wwe0km51.ap-south-1.rds.amazonaws.com 3306

# Connect to RDS from inside EC2
mysql -h fct.c9u0wwe0km51.ap-south-1.rds.amazonaws.com -u admin -p
```

## SSL error fix (if connection fails with SSL_CTX_set_default_verify_paths)

```bash
# Install missing CA certificates
sudo apt install ca-certificates -y

# Then retry the connection
mysql -h fct.c9u0wwe0km51.ap-south-1.rds.amazonaws.com -u admin -p
```

---

## Inside MySQL — basic test queries

```sql
-- Show all databases
SHOW DATABASES;

-- Create a test database
CREATE DATABASE testdb;

-- Use the database
USE testdb;

-- Create a test table
CREATE TABLE users (
  id INT AUTO_INCREMENT PRIMARY KEY,
  name VARCHAR(100),
  created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

-- Insert a test record
INSERT INTO users (name) VALUES ('test-user');

-- Query the table
SELECT * FROM users;

-- Drop the test table
DROP TABLE users;

-- Drop the test database
DROP DATABASE testdb;
```

---

## AWS CLI — RDS operations

```bash
# List all RDS instances
aws rds describe-db-instances

# List DB subnet groups
aws rds describe-db-subnet-groups

# Delete an RDS instance (skip final snapshot for test environments)
aws rds delete-db-instance \
  --db-instance-identifier DB_INSTANCE_ID \
  --skip-final-snapshot
```

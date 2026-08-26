# Commands — EC2 Web Server

Commands I ran during this project. Grouped by where they run.

---

## On my local machine (Windows Command Prompt)

```CMD
# SSH into the instance
ssh -i "masterkey.pem" ec2-user@3.110.120.197
```

## On my local machine (Linux terminal)

```bash
# Fix key permissions — required before SSH on Mac/Linux
chmod 400 masterkey.pem

# SSH into the instance
ssh -i "masterkey.pem" ec2-user@3.110.120.197
```

---

## On the EC2 instance

```bash
# Update packages first
sudo yum update -y

# Install Apache
sudo yum install httpd -y

# Start Apache
sudo systemctl start httpd

# Make Apache start on reboot
sudo systemctl enable httpd

# Check it's running
sudo systemctl status httpd

# Create a simple test page
echo "<h1>Hello from EC2\!</h1>" | sudo tee /var/www/html/index.html

# Verify the file is there
cat /var/www/html/index.html

# Check Apache is listening on port 80
sudo ss -tlnp | grep :80
```

# Commands — S3 Static Website

Commands I used during this project.

---

## Local machine (Windows Command Prompt)

```Command Prompt
# Check AWS CLI is installed
aws --version

# List all S3 buckets
aws s3 ls

# Sync local folder to S3 bucket
aws s3 sync ./website s3://my-static-website-vishal

# Make all objects in bucket publicly readable
aws s3api put-bucket-acl --bucket my-static-website-vishal --acl public-read
```

---

## AWS CLI — bucket operations

```bash
# Create a bucket
aws s3api create-bucket --bucket my-static-website-vishal --region ap-south-1 --create-bucket-configuration LocationConstraint=ap-south-1

# Enable static website hosting
aws s3 website s3://my-static-website-vishal/ --index-document index.html --error-document error.html

# Upload a single file
aws s3 cp index.html s3://my-static-website-vishal/

# Delete all objects in bucket (before deleting bucket)
aws s3 rm s3://my-static-website-vishal --recursive

# Delete the bucket
aws s3api delete-bucket --bucket my-static-website-vishal --region ap-south-1
```

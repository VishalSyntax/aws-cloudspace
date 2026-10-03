# Project 15 — S3 File Processing Workflow Commands

## Upload a test file to S3

```bash
aws s3 cp test.txt s3://my-file-processing-s3/s3-file.txt --region ap-south-1 
```

## Upload to a specific prefix (folder)

```bash
aws s3 cp test.txt s3://my-file-processing-s3/uploads/s3-file.txt --region ap-south-1 
```

## List objects in the bucket

```bash
aws s3 ls s3://my-file-processing-s3/ --region ap-south-1 
```

## AWS CLI — check Lambda resource-based policy

```bash
aws lambda get-policy \
  --function-name my-file-processing\
  --region ap-south-1
```

## AWS CLI — list S3 event notifications

```bash
aws s3api get-bucket-notification-configuration \
  --bucket my-file-processing-s3 \
  --region ap-south-1 
```

## AWS CLI — view latest CloudWatch log stream

```bash
aws logs describe-log-streams \
  --log-group-name /aws/lambda/ my-file-processing-s3\
  --order-by LastEventTime \
  --descending \
  --max-items 1 \
  --region ap-south-1 
```

## AWS CLI — empty and delete S3 bucket

```bash
aws s3 rm s3://my-file-processing-s3 --recursive --region ap-south-1 
aws s3api delete-bucket --bucket my-file-processing-s3 --region ap-south-1 
```


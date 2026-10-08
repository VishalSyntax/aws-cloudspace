# Project 16 — Private S3 CloudFront Commands

> This project was built through the AWS Console. The commands below are for reference only — useful if you want to do the same steps via CLI later.

---

## Upload files to S3

```bash
aws s3 cp index.html s3://vishal-private-site/ --region ap-south-1
aws s3 sync ./website/ s3://vishal-private-site/ --region ap-south-1
```

## Create a CloudFront cache invalidation

```bash
aws cloudfront create-invalidation \
  --distribution-id MY_DISTRIBUTION_ID \
  --paths "/*"
```

## Invalidate a specific file

```bash
aws cloudfront create-invalidation \
  --distribution-id MY_DISTRIBUTION_ID \
  --paths "/index.html"
```

## Get distribution status

```bash
aws cloudfront get-distribution \
  --id MY_DISTRIBUTION_ID \
  --query 'Distribution.Status'
```
## AWS CLI — disable distribution (required before delete)

```bash
aws cloudfront get-distribution-config \
  --id MY_DISTRIBUTION_ID \
  --query 'DistributionConfig' > dist-config.json
# Edit dist-config.json: set "Enabled": false
# Then update:
aws cloudfront update-distribution \
  --id MY_DISTRIBUTION_ID \
  --distribution-config file://dist-config.json \
  --if-match YOUR_ETAG
```

## Empty and delete S3 bucket

```bash
aws s3 rm s3://vishal-private-site --recursive --region ap-south-1
aws s3api delete-bucket --bucket vishal-private-site --region ap-south-1
```

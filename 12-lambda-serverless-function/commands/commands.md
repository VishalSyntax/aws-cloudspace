# Project 12 — Lambda Serverless Function Commands

## AWS CLI — list Lambda functions

```bash
aws lambda list-functions --region ap-south-1
```

## AWS CLI — invoke function manually

```bash
aws lambda invoke \
  --function-name hello-vishal \
  --payload '{}' \
  --region ap-south-1 \
  response.json

cat response.json
```

## AWS CLI — view function configuration

```bash
aws lambda get-function-configuration \
  --function-name hello-vishal \
  --region ap-south-1
```

## AWS CLI — update function timeout

```bash
aws lambda update-function-configuration \
  --function-name hello-vishal \
  --timeout 30 \
  --region ap-south-1
```

## AWS CLI — delete function

```bash
aws lambda delete-function \
  --function-name hello-vishal \
  --region ap-south-1
```

## AWS CLI — view CloudWatch log groups for Lambda

```bash
aws logs describe-log-groups \
  --log-group-name-prefix /aws/lambda/ \
  --region ap-south-1
```

## AWS CLI — get latest log stream

```bash
aws logs describe-log-streams \
  --log-group-name /aws/lambda/hello-vishal \
  --order-by LastEventTime \
  --descending \
  --max-items 1 \
  --region ap-south-1
```

# Project 13 — Serverless API Commands

## Test the API endpoint

```bash
curl https://pgualkjrnd.execute-api.ap-south-1.amazonaws.com/hello
```

## Test with verbose output (shows status code and headers)

```bash
curl -v https://pgualkjrnd.execute-api.ap-south-1.amazonaws.com/hello
```

## AWS CLI — list APIs

```bash
aws apigatewayv2 get-apis --region ap-south-1
```

## AWS CLI — get API details

```bash
aws apigatewayv2 get-api \
  --api-id pgualkjrnd \
  --region ap-south-1
```

## AWS CLI — list routes

```bash
aws apigatewayv2 get-routes \
  --api-id pgualkjrnd \
  --region ap-south-1
```

## AWS CLI — delete API

```bash
aws apigatewayv2 delete-api \
  --api-id pgualkjrnd \
  --region ap-south-1
```

## AWS CLI — delete Lambda function

```bash
aws lambda delete-function \
  --function-name vishal-api-handler \
  --region ap-south-1
```

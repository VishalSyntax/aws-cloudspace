# Serverless Database Application

Fourteenth project. Connected Lambda to DynamoDB to build a serverless database application — created a DynamoDB table, wrote a Lambda function using Boto3 to read and write items, attached the right IAM permissions, and wired it all together through API Gateway.

## What I built

A fully serverless stack where API Gateway receives HTTP requests, Lambda processes them using Boto3, and DynamoDB stores the data. POST to write an item, GET to read it back. No EC2, no RDS, no servers to manage.

![Architecture](./architecture/architecture.png)

## Why DynamoDB

Every project before this that needed a database used RDS — a relational database running on a managed server. DynamoDB is different. It's a NoSQL key-value store that's fully serverless, scales automatically, and charges per request. For a Lambda-based backend it's the natural fit — both scale to zero, both scale up automatically, and neither needs a server running 24/7.

## Services used

| Service | What I used it for |
|---------|-------------------|
| DynamoDB | NoSQL table that stores the application data |
| Lambda | Processes requests and reads/writes to DynamoDB using Boto3 |
| API Gateway | Receives HTTP requests and routes them to Lambda |
| IAM | Grants Lambda permission to access DynamoDB |
| CloudWatch Logs | Stores Lambda execution logs automatically |

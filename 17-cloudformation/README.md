# Deploy Infrastructure with CloudFormation

Seventeenth project. Infrastructure as Code â€” wrote a YAML template, deployed it as a CloudFormation stack, updated it, then deleted the whole stack in one action. No console clicking.

## What I built

A CloudFormation stack that creates an S3 bucket and an EC2 instance from a YAML template. Deployed it, updated it with a change, then deleted the whole thing in one action â€” all resources gone cleanly.

![Architecture](./architecture/architecture.png)

## Why CloudFormation

Every project before this involved clicking through the console. That works for learning but doesn't scale â€” it's slow, error-prone, and hard to repeat exactly. CloudFormation flips that. The infrastructure is in a file, stored in version control, deployed the same way every time. This is how real AWS environments are managed.

## Services used

| Service | What I used it for |
|---------|-------------------|
| CloudFormation | Reads the YAML template and creates/manages the AWS resources |
| S3 | Created as a resource by the template |
| EC2 | Created as a resource by the template |

## Resources I created

| Resource | Value |
|----------|-------|
| Region | ap-south-1 |
| Stack name | vishal-demo-stack |

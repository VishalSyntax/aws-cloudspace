# Troubleshoot a Broken AWS Application

Nineteenth project. Systematic troubleshooting instead of randomly changing settings and hoping something works. Intentionally broke an AWS application — misconfigured security groups, removed a route table entry, broke a health check — then diagnosed and fixed each issue layer by layer.

## What I built

A broken AWS application that I fixed. The point wasn't to build something new — it was to develop a mental model for diagnosing connectivity issues, security group problems, routing failures, and ALB health check errors. The kind of problems that come up constantly in real AWS environments.

![Architecture](./architecture/architecture.png)

## Why troubleshooting

Every project before this was about building things. This one is about fixing them. Knowing how to build an EC2 web server is useful. Knowing why it's not responding when it should be is more useful. Security groups and route tables are the most common causes of connectivity issues in AWS — this project was about getting comfortable diagnosing them systematically.

## Services used

| Service | What I used it for |
|---------|-------------------|
| EC2 | The application server being troubleshot |
| Security Groups | Firewall rules — a common source of connectivity issues |
| VPC / Route Tables | Network routing — missing IGW route breaks internet access |
| ALB | Load balancer — health check failures prevent traffic |
| CloudWatch | Logs and metrics for diagnosing issues |

## Resources used

| Resource | Value |
|----------|-------|
| Region | ap-south-1 |
| Starting point | EC2 instance with web server from Project 9 |

# Project 17 — CloudFormation Commands

> Built through the AWS Console. The commands below are for reference only — not used during the project.

---

## Validate the template before deploying

```bash
aws cloudformation validate-template \
  --template-body file://templates/example-template.yaml \
  --region ap-south-1
```

## Create the stack

```bash
aws cloudformation create-stack \
  --stack-name vishal-demo-stack \
  --template-body file://templates/example-template.yaml \
  --parameters ParameterKey=KeyPairName,ParameterValue=MY_KEY_PAIR \
  --capabilities CAPABILITY_IAM \
  --region ap-south-1
```

## Check stack status

```bash
aws cloudformation describe-stacks \
  --stack-name vishal-demo-stack \
  --query 'Stacks[0].StackStatus' \
  --region ap-south-1
```

## Delete the stack

```bash
aws cloudformation delete-stack \
  --stack-name vishal-demo-stack \
  --region ap-south-1
```

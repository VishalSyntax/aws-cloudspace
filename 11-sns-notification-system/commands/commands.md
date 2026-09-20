# Project 11 — SNS Notification System Commands

## AWS CLI — create SNS topic

```bash
aws sns create-topic \
  --name fct-alerts-alerts \
  --region ap-south-1
```

## AWS CLI — subscribe email to topic

```bash
aws sns subscribe \
  --topic-arn arn:aws:sns:ap-south-1:019540875443:fct-alerts \
  --protocol email \
  --notification-endpoint thatvishal007@gmail.com \
  --region ap-south-1
```

## AWS CLI — publish a test message

```bash
aws sns publish \
  --topic-arn arn:aws:sns:ap-south-1:019540875443:fct-alerts \
  --subject "Test Message" \
  --message "This is a test notification from SNS." \
  --region ap-south-1
```

## AWS CLI — list subscriptions for a topic

```bash
aws sns list-subscriptions-by-topic \
  --topic-arn arn:aws:sns:ap-south-1:019540875443:fct-alerts \
  --region ap-south-1
```

## AWS CLI — delete subscription

```bash
aws sns unsubscribe \
  --subscription-arn arn:aws:sns:ap-south-1:019540875443:fct-alerts \
  --region ap-south-1
```

## AWS CLI — delete topic

```bash
aws sns delete-topic \
  --topic-arn arn:aws:sns:ap-south-1:019540875443:fct-alerts \
  --region ap-south-1
```

# Project 14 — Serverless Database Application Commands

## Write an item (POST)

```bash
curl -X POST https://phdcuegk68.execute-api.ap-south-1.amazonaws.com/tasks \
  -H "Content-Type: application/json" \
  -d '{"TASKID": "task-001", "title": "Learn DynamoDB", "status": "in-progress"}'
```

## Read an item (GET)

```bash
curl "https://phdcuegk68.execute-api.ap-south-1.amazonaws.com/tasks?TASKID=task-001"
```

## AWS CLI — scan all items in the table

```bash
aws dynamodb scan \
  --table-name MY-TASKS \
  --region ap-south-1
```

## AWS CLI — get a specific item

```bash
aws dynamodb get-item \
  --table-name MY-TASKS \
  --key '{"TASKID": {"S": "task-001"}}' \
  --region ap-south-1
```

## AWS CLI — put an item directly

```bash
aws dynamodb put-item \
  --table-name MY-TASKS \
  --item '{"TASKID": {"S": "task-002"}, "title": {"S": "Test item"}}' \
  --region ap-south-1
```

## AWS CLI — delete an item

```bash
aws dynamodb delete-item \
  --table-name MY-TASKS \
  --key '{"TASKID": {"S": "task-001"}}' \
  --region ap-south-1
```

## AWS CLI — delete the table

```bash
aws dynamodb delete-table \
  --table-name MY-TASKS \
  --region ap-south-1
```

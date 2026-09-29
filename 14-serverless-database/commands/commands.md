
# Project 14 — Serverless Database Application Commands

## Write an item (POST)

```bash
curl -X POST MY_API_ENDPOINT/tasks \
  -H "Content-Type: application/json" \
  -d '{"TASKID": "task-001", "title": "Learn DynamoDB", "status": "in-progress"}'
```

## Read an item (GET)

```bash
curl "MY_API_ENDPOINT/tasks?TASKID=task-001"
```
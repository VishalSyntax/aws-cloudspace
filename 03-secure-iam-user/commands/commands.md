# Commands — Secure IAM User

Not many CLI commands for this one — most of it is done through the AWS Console. But here are a few useful ones.

---

## AWS CLI — IAM operations

```bash
# List all IAM users
aws iam list-users

# Get details about a specific user
aws iam get-user --user-name Steve

# List groups a user belongs to
aws iam list-groups-for-user --user-name Steve

# List policies attached to a user
aws iam list-attached-user-policies --user-name Steve

# List policies attached to a group
aws iam list-attached-group-policies --group-name admin

# Delete a user's login profile (removes console access)
aws iam delete-login-profile --user-name Steve

# Delete access keys for a user
aws iam delete-access-key --user-name Steve --access-key-id MY_ACCESS_KEY_ID

# Delete the IAM user
aws iam delete-user --user-name Steve
```

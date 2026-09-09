# Commands — Auto Scaling Group

## AWS CLI

```bash
# List Auto Scaling Groups
aws autoscaling describe-auto-scaling-groups

# Set desired capacity manually
aws autoscaling set-desired-capacity \
  --auto-scaling-group-name my-asg \
  --desired-capacity 2

# List Launch Templates
aws ec2 describe-launch-templates

# Delete Auto Scaling Group
aws autoscaling delete-auto-scaling-group \
  --auto-scaling-group-name my-asg \
  --force-delete
```

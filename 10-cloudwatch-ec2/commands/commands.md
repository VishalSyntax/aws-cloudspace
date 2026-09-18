# Project 10 — CloudWatch EC2 Monitoring Commands

## Install stress tool

```bash
# Amazon Linux 2023
sudo dnf install stress -y

# Amazon Linux 2
sudo amazon-linux-extras install epel -y
sudo yum install stress -y
```

# For Ubuntu, stress install is different:
sudo apt update && sudo apt install stress -y
stress --cpu 2 --timeout 300
```
Or the zero-install method:
    yes > /dev/null &
    yes > /dev/null &

Kill when done: killall yes
```


## Generate CPU load

```bash
stress --cpu 2 --timeout 300
```

## Check CPU from inside the instance

```bash
top
```

## View system log

```bash
sudo cat /var/log/messages | tail -50
```

## AWS CLI — describe alarm state

```bash
aws cloudwatch describe-alarms \
  --alarm-names "cpu-high-alarm" \
  --region ap-south-1
```

## AWS CLI — delete alarm

```bash
aws cloudwatch delete-alarms \
  --alarm-names "cpu-high-alarm" \
  --region ap-south-1
```

## AWS CLI — delete SNS topic

```bash
aws sns delete-topic \
  --topic-arn arn:aws:sns:ap-south-1:019540875443:cpu-alert-topic \
  --region ap-south-1
```

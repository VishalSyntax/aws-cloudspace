# Project 18 — AWS Backup Commands

> Built through the AWS Console. The SSH/bash commands below were actually run on the EC2 instance. The AWS CLI commands are just for reference.

---

## Check attached volumes and device names

```bash
lsblk
```

## Format the volume (only for new volumes — NOT for restored snapshots)

```bash
sudo mkfs -t ext4 /dev/xvdf
```

## Create mount point and mount

```bash
sudo mkdir /data
sudo mount /dev/xvdf /data
```

## Write test data

```bash
echo "VISHAL AWS BACKUP TEST DATA" | sudo tee /data/test.txt
```

## Verify data

```bash
cat /data/test.txt
ls -l /data/
df -h
```

## Unmount before detaching

```bash
sudo umount /data
```

---

> The commands below are CLI reference only — not used during the project.

## Create snapshot

```bash
aws ec2 create-snapshot \
  --volume-id MY_VOLUME_ID \
  --description "vishal-backup-test" \
  --tag-specifications 'ResourceType=snapshot,Tags=[{Key=Name,Value=vishal-backup-test}]' \
  --region ap-south-1
```

## Create volume from snapshot

```bash
aws ec2 create-volume \
  --snapshot-id MY_SNAPSHOT_ID \
  --availability-zone ap-south-1a \
  --volume-type gp3 \
  --region ap-south-1
```

## Delete snapshot

```bash
aws ec2 delete-snapshot \
  --snapshot-id MY_SNAPSHOT_ID \
  --region ap-south-1
```

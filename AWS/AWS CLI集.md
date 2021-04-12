## AWS CLI集

#### EC2(Name,ID,SG,State）
```
aws ec2 describe-instances --query 'Reservations[].Instances[].{InstanceID:InstanceId,Name:Tags[?Key==`Name`].Value|[0],SG:SecurityGroups,State:State.[Name]}'
```

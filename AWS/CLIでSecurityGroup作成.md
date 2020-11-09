### AWS CLIでSecurityGroupを作成する

- セキュリティグループ作成
```
aws ec2 create-security-group ¥
--group-name MySecurityGroup ¥
--description "My security group" ¥
--vpc-id vpc-xxxxxxx ¥
```


- ルール追加
```
aws ec2 authorize-security-group-ingress ¥
--group-id sg-xxxxxxx ¥
--ip-permissions IpProtocol=icmp,FromPort=3,ToPort=4,IpRanges='[{CidrIp=0.0.0.0/0}]' ¥
```


- CLIリファレンス：https://docs.aws.amazon.com/cli/latest/reference/ec2/index.html#cli-aws-ec2

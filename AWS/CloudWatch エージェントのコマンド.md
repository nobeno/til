## CloudWatch エージェントのコマンド

### 起動
- 設定ファイルをSSMパラメータストアに保存している場合
```sh
$ sudo /opt/aws/amazon-cloudwatch-agent/bin/amazon-cloudwatch-agent-ctl -a fetch-config -m ec2 -s -c ssm:configuration-parameter-store-name
```

<br/>

- 設定ファイルがローカルに保存している場合
```sh
$ sudo /opt/aws/amazon-cloudwatch-agent/bin/amazon-cloudwatch-agent-ctl -a fetch-config -m ec2 -s -c file:configuration-file-path
``` 

<br/>

### 停止
```sh
$ sudo /opt/aws/amazon-cloudwatch-agent/bin/amazon-cloudwatch-agent-ctl -m ec2 -a stop
```

<br/>

### 設定ファイル初期化
```sh
$ sudo /opt/aws/amazon-cloudwatch-agent/bin/amazon-cloudwatch-agent-config-wizard
```

<br/>

### 参考
- https://docs.aws.amazon.com/ja_jp/AmazonCloudWatch/latest/monitoring/install-CloudWatch-Agent-on-EC2-Instance-fleet.html#start-CloudWatch-Agent-EC2-fleet
- https://docs.aws.amazon.com/ja_jp/AmazonCloudWatch/latest/monitoring/troubleshooting-CloudWatch-Agent.html#CloudWatch-Agent-troubleshooting-stopping-restarting


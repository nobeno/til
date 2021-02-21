## AmazonLinuxでAWS CLIをUpdateする方法

- 手順
```
$ aws --version
aws-cli/1.16.300 Python/2.7.18 Linux/4.14.181-140.257.amzn2.x86_64 botocore/1.13.36
$ sudo rm -rf /usr/local/aws
$
$ sudo rm /usr/bin/aws
$ curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100 31.5M  100 31.5M    0     0  82.8M      0 --:--:-- --:--:-- --:--:-- 82.8M
$
$ unzip awscliv2.zip
Archive:  awscliv2.zip
   creating: aws/
   creating: aws/dist/
  inflating: aws/README.md
  inflating: aws/install
    ・
    ・
  (中略)
    ・
    ・
  inflating: aws/dist/include/python3.7m/pyconfig.h
   creating: aws/dist/lib/python3.7/
   creating: aws/dist/lib/python3.7/config-3.7m-x86_64-linux-gnu/
  inflating: aws/dist/lib/python3.7/config-3.7m-x86_64-linux-gnu/Makefile
$
```
- 参考
https://qiita.com/simis/items/46ffe04c346b9fdf7830

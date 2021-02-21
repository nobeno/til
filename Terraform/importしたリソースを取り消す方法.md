## importしたリソースを取り消す方法

### ドキュメント：https://www.terraform.io/docs/cli/commands/state/rm.html

```
# 既存のresourceをインポート
$ terraform import aws_vpc.vpc vpc-xxxxxxxxxx
# 取り消す
$ terraform state rm aws_vpc.vpc vpc-xxxxxxxxxx
```

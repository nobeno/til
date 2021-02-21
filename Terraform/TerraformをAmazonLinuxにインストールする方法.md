## TerraformをAmazonLinuxにインストールする方法

### 参考：https://learn.hashicorp.com/tutorials/terraform/install-cli

```
$ sudo yum install -y yum-utils
$ sudo yum-config-manager --add-repo https://rpm.releases.hashicorp.com/AmazonLinux/hashicorp.repo
$ sudo yum -y install terraform
$ terraform -help
```

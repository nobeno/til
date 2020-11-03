### CloudFrontのCNAMEAlreadyExistsエラー解決方法

- 原因：複数のCloudFrontディストリビューションに同じCNAMEエイリアスを使用している場合に出るエラー

- 解決方法：ディストリビューション間でCNAMESの切替を行う
  
  - Route53使用の場合、TXTレコードを追加する
    例：`example.com TXT d123.cloudfront.net`
  
  - SSL証明書をCloudFrontディストリビューションに追加する
  
  - AWSサポートへ連絡して、DNSドメイン名の所有者の検証を依頼する
  
 
- 参考URL
  - https://aws.amazon.com/jp/premiumsupport/knowledge-center/resolve-cnamealreadyexists-error/?nc1=h_ls
  - https://docs.aws.amazon.com/ja_jp/AmazonCloudFront/latest/DeveloperGuide/CNAMEs.html#alternate-domain-names-move-domain
  

## OpneVPNのTLS Error: cannot locate HMAC in incoming packet from x.x.x.xの対処方法

### tls-authとは
- tls-authはOpenVPNのTCP/UDPポートの「HMACファイアウォール」の一種
- 正しくないHMAC署名に基づくTLSコントロールチャネルのパケットが届いた場合は、応答することなく、すぐに破棄する

### 対処方法
- サーバー・クライアント側の設定ファイルを見直す
```
サーバー側   ： tls-auth ta.key 0
クライアント側 ： tls-auth ta.key 1
```

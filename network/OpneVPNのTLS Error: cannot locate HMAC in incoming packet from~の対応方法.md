## OpneVPNのTLS Error: cannot locate HMAC in incoming packet from x.x.x.xの対処方法

### tls-authとは
- tls-authはOpenVPNのTCP/UDPポートの「HMACファイアウォール」の一種
- 正しくないHMAC署名に基づくTLSコントロールチャネルのパケットが届いた場合は、応答することなく、すぐに破棄する

<br>

### 対処方法
- ta.keyが合っているか、正しく配置されてるか確認する
- サーバー・クライアント側の設定ファイルを見直す
```
サーバー側   ： tls-auth ta.key 0
クライアント側 ： tls-auth ta.key 1
```

<br>

### 参考
- https://www.openvpn.jp/document/how-to/
- https://qiita.com/megadreams14/items/0d5201245ec33ae463f4
- https://e-words.jp/w/HMAC.html

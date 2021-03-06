### HTTP

- HTTPとは
  - HTML文書や画像、動画、音声などのコンテンツの送受信に用いるプロトコル
  - TCPを使用
  
- HTTPにおける認証
  - Basic認証：base64でエンコード、IDとPASSは平文でネットワークに流れる
  - Digest認証:IDとPASSをMD5でハッシュ化して送信する
  
- バージョン
  - HTTP1.0:1つのコマンド・応答のやり取りのたびにTCPコネクションを確立して切断する
  - HTTP1.1:１つのTCPコネクションで複数のコマンド・応答できる
  - HTTP/2:1つの接続での並列処理や、バイナリデータの使用による送受信のデータ量の削減、ヘッダ圧縮、サーバープッシュなどにより、ネットワークリソースの効率化を実現している
  - HTTP/3:TCPのスリーハンドシェークのないUDPを使う
  
- 参考
  - [HTTP/2：サーバープッシュについて](https://blog.redbox.ne.jp/http2-server-push-cdn.html)

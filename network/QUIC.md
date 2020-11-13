### QUIC

- QUICとは
  - 新しいトランスポート層のプロトコル
  - TLS1.3を用いた暗号化
  - 従来のTLS1.2では暗号化チャネルの確立に3RTT(Round Trip Time)かかっていたのが、TLS1.3では0-1RTTで接続できるようになったため、オーバーヘッドが少ないかつより早い段階からの暗号化通信が可能
  - UDP上のQUICレイヤにて、輻輳・通信の多重化などの制御

- 参考：(HTTP/3が出るらしいという話を雑に書く)[https://qiita.com/inductor/items/61b824289ac9b2f11b3e]

![image](https://user-images.githubusercontent.com/50900163/99080494-bc8cc980-2604-11eb-8316-ae5dea664acf.png)

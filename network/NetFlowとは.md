## NetFlowとは

- シスコ社が開発したトラフィックの詳細情報を収集するための技術
- ネットワーク機器を通る通信のパケットから、いくつかの情報を取り出し「フローデータ」というものを生成
- フローデータにある情報：送信元IPアドレス、宛先IPアドレス、TCP/UDPポート送信元番号、TCP/UDPポート宛先番号、L3プロトコル、Tosバイト（DSCP）、入力インターフェースの情報
- ネットワークトラフィックの可視化とは、どこから・どこに・いつ・どのくらい・どのような　通信が流れていたかというトラフィックの分析
- https://blogs.manageengine.jp/itom_what_is_netflow/
- https://jtc-networkmanagementmaster.blogspot.com/2019/10/netflow.html

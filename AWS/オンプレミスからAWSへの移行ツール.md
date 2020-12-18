## オンプレミスからAWSへの移行ツール

### ①VM Import/Export
- オンプレミスの仮想イメージをEC2に移行できる
- 利用できる仮想化ソフトウェアやOSは限定される
<br/>

### ②AWS Server Migration Service
- VMware vSphere または Microsoft Hyper-V/SCVMM上で動いている仮想マシンをAWSに移行可能
- オンプレミスの仮想化環境にAWS Server Migration Service Connectorを導入
- AWS Server Migration Service Connector経由でAWS環境に仮想マシンのデータを転送
<br/>

### ③CloudEndure Migration
- OSごとにエージェントを導入すれば、物理・仮想マシン、どちらの移行も可能
- 移行先のサーバーにそのままデータを移行でき、切り替えを行うだけで移行が完了するため、最短のダウンタイムで移行できる
- データ転送ではAWS Direct Connectを利用可能
<br/>

### ④AWS Snowball
- 大容量の物理デバイスを利用した、データの配送サービス
<br/>

### ⑤AWS Database Migration Service
- データベース間のインポート・エクスポート、同期を実現する
- 異なるDBエンジン間のデータ移行にも対応

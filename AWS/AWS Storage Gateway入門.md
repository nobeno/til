# AWS Storage Gateway入門


## AWS Storage Gatewayとは
既存のオンプレミス環境と AWS クラウドを接続するハイブリッドクラウドストレージサービス

<br>

## データの格納先
- S3
- EBS
- Glacier

<br>

## 種類
1. ファイルゲートウェイ
    - NFSやSMBなどのファイルプロトコルを使用して、S3でオブジェクト保存および取得できる
    - ゲートウェイが必要
    - VMware ESXi、Microsoft Hyper-V、Linux Kernelベースの仮想マシン(KVM)ハイパーバイザーが使用可能
    - ゲートウェイは、S3 内のオブジェクトへのアクセスをファイルまたはファイル共有のマウントポイントとして提供される

<br>

2. ボリュームゲートウェイ
    - iSCSI (Internet Small Computer System Interface) デバイスとしてマウントできる、クラウドベースのストレージボリューム
    - キャッシュボリュームと保管型ボリュームがある

<br>

3. テープゲートウェイ
    - クラウドベースの仮想テープストレージを提供
    - バックアップデータをコスト効果や耐久性の高い方法で GLACIER または DEEP_ARCHIVE にアーカイブできる

<br>

## ドキュメント
https://docs.aws.amazon.com/ja_jp/storagegateway/latest/userguide/WhatIsStorageGateway.html

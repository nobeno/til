## VMware vSphere

#### 構成要素

参考URL：[新卒 SE 社員が贈る　vSphere のキソ！第1回〜 vSphere を俯瞰する〜 - VMware Japan Blog](https://blogs.vmware.com/vmware-japan/2014/08/vsphere_kiso01.html)

- ESXi
  - vSphere の中核となるハイパーバイザー型仮想化ソフトウェア

- VMware vCenter Server
  - 仮想基盤を管理する必須のコアサービス
  - vSphere 環境の管理一元化
  - 役割
    - 統合管理(複数の ESXi を束ねて管理) 
    - vSphereにある様々な機能を有効化

- vSphere Client / vSphere Web Client
  - 仮想環境にアクセスする、言わば vSphere への入り口となるインタフェースを提供
  - vSphere 基盤の運用・監視

- vSwith：仮想スイッチ
  - ポート
    - アップリンクポート：物理NICと対応づけられる
    - VMkernelポート：vSphereの機能を使用する
    - 仮想マシンポートグループ：仮想マシンのvNICを接続する
  
- vSphereの機能
  - vMotion：仮想マシンが動的に他の ESXi サーバに移行する
  - vSphere HA：ESXi サーバが停止した際に、他の ESXi サーバから仮想マシンを再起動させる
  - vSphere FT：２つの ESXi サーバで同一の仮想マシンを動作させてダウンタイムなしの可用性を実現する

---
title: ホスト通信
sidebar_position: 3
---


monoZ:Connectと通信するにはmonoZ:Connectサービス(MZCS)を使用します。\
MZCSをWindows/Linuxマシンにインストールして、ホストは簡単なコマンドをMZCSに送信するだけでmonoZ:Connectと通信することが出来ます。


<div className="card">
    <div className="card__body">
<img src={require('@site/static/img/monoZ-Connect-Host-Comm.jpg').default} className="img-center" />
</div>
</div>

### システム要件

#### Windows

<table>
    <tr>
        <td> <b>Item</b></td>
        <td> <b>Requirement</b></td>
    </tr>
    <tr>
        <td>OS Version</td>
        <td>
        <codeBlock>
        Windows 7 (64bit)/ Windows10 (64 bit)/ Windows11 (64bit)/ <br/>
Windows Server 2008 (64bit)/ Windows Server 2012 (64bit)/ <br/>
Windows Server 2016 (64bit)/ Windows Server 2019 (64 bit) 

       </codeBlock>
</td>
    </tr>
     <tr>
        <td>CPU</td>
        <td>
      <codeBlock>
       Intel Pentium 4415Y @ 1.60GHz and later
      </codeBlock>
</td>
    </tr>
</table>

#### Linux

<table>
    <tr>
        <td> <b>Item</b></td>
        <td> <b>Requirement</b></td>
    </tr>
    <tr>
        <td>Supported devices</td>
        <td>
        <codeBlock>
     Tinkerboard 2, 2S, 3S
       </codeBlock>
</td>
    </tr>
</table>


### COMポート設定
1. monoZ:ConnectをUSB経由でPCに接続します。

2. 「デバイスマネージャー」を起動して、デバイスが接続されているCOMポートのポート設定を下記の値に変更します。
        -	Bit rate:		115200

        -	Data bits:	8

        -	Parity:		None

        -	Stop bits:	1

        -	Flow control:	None
### monoZConnectを利用するための前提条件 
- monoZ:Connectは、LwM2M プロトコルを使用してクラウドと通信します。\
  ユーザーはLwM2Mプロトコルの基本的な仕様を理解していることが求められます。
- monoZ:Connectは、SoftBank IoT Platformに接続します。\
  ユーザーはSoftBank IoT Platformの基本的な振る舞いを理解していることが求められます。
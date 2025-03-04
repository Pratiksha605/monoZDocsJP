---
title: ホスト通信
sidebar_position: 3
---
ホストはmonoZ:JetとUSBもしくはUARTを介して通信することが出来ます。\
複雑なネットワーク接続手順やプラットフォーム通信プロトコルの設定を、\
monoZ:Jetは自動で行ってくれます。

### USB接続
ホストとmonoZ:JetをUSB-C ケーブルで接続するとUSB経由で通信が行えます。\
USBはmonoZ:Jet の主電源の役割も果たします。\
USBで通信する場合は、J1コネクタのUARTピンが接続されていないことを確認してください。


<div className="card">
    <div className="card__body">
       <div><b>UART Settings</b></div>
       <div className="row">
        <div className="col col--4">BAUD RATE</div>
        <div className="col col--8">115200</div>
       </div>
       <div className="row">
        <div className="col col--4">Data Bits</div>
        <div className="col col--8">8</div>
       </div>
       <div className="row">
        <div className="col col--4">Stop Bits</div>
        <div className="col col--8">1</div>
       </div>
       <div className="row">
        <div className="col col--4">Parity</div>
        <div className="col col--8">None</div>
       </div>
       <div className="row">
        <div className="col col--4">Flow Control</div>
        <div className="col col--8">None</div>
       </div>
    </div>
</div>
<div className="card">
    <div className="card__body">
       <div><b>Power Settings</b></div>
       <div className="row">
        <div className="col col--4">Voltage</div>
        <div className="col col--8">5V DC [4.5V DC ~ 6V DC]</div>
       </div>
       <div className="row">
        <div className="col col--4">Ampere</div>
        <div className="col col--8">max 1A</div>
       </div>
    </div>
</div>

### PCB端子接続
monoZ:JetはPCB端子接続をサポートしています。端子接続するには以下の2種類の方法が用意されています。

    方法 1: monoZ:Jetのオプション基板を切り離す方法です。この方法は簡単に行えますが、一度切り離したオプション基板は元に戻せないので注意してください。 
    <img className="img-center" src={require('@site/static/img/quickguide2.png').default} />
    方法 2: 以下に示す3つの抵抗を外す方法です。この方法で取り外した抵抗を元の位置につけ直すことでUSB接続を使用することが出来ます。抵抗器の不適切な取り外しや取り付けによる損傷や故障によって生じたハードウェアの問題については一切の責任を負いません。
    <img className="img-center" src={require('@site/static/img/quickguide3.png').default} />

J1コネクタのp7、p8をホストのRXとTXに接続することで、ホストとmonoZ:JetはUART 経由で通信が行えます。\
monoZ:Jetの主電源を確保するためにJ2コネクタのp1はDC5V電源に、p2はGNDに接続してください。

<div className="card">
    <div className="card__body">
        <img src={require('@site/static/img/uart.jpg').default} />
    </div>
</div>

<div className="card">
    <div className="card__body">
       <div><b>UART Settings</b></div>
       <div className="row">
        <div className="col col--4">BAUD RATE</div>
        <div className="col col--8">115200</div>
       </div>
       <div className="row">
        <div className="col col--4">Data Bits</div>
        <div className="col col--8">8</div>
       </div>
       <div className="row">
        <div className="col col--4">Stop Bits</div>
        <div className="col col--8">1</div>
       </div>
       <div className="row">
        <div className="col col--4">Parity</div>
        <div className="col col--8">None</div>
       </div>
       <div className="row">
        <div className="col col--4">Flow Control</div>
        <div className="col col--8">None</div>
       </div>
       <div className="row">
        <div className="col col--4">Pin Ratings</div>
        <div className="col col--8">3.3V, max 10mA</div>
       </div>
    </div>
</div>
<div className="card">
    <div className="card__body">
       <div><b>Power Settings</b></div>
       <div className="row">
        <div className="col col--4">Voltage</div>
        <div className="col col--8">5V DC [4.5V DC ~ 6V DC]</div>
       </div>
       <div className="row">
        <div className="col col--4">Ampere</div>
        <div className="col col--8">max 1A</div>
       </div>
    </div>
</div>

**注意:**
<br/>i)	monoZ:JetのUSBと5V/VBUSピン経由で同時に電源を入れないでください。monoZ:Jetが正常に動作しない可能性があります。また電源に過電流が発生し故障する可能性がございます。
<br/>ii) USB接続中はPCB端子接続を切断してください。USB接続中にPCB端子接続を介してデータを受信すると、正常にデータを受信できない可能性があります。またmonoZ:Jetが故障する可能性がございます。



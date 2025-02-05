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

### UART接続
J1コネクタのp7、p8をホストのRXとTXに接続することで、ホストとmonoZ:JetはUART 経由で通信が行えます。\
monoZ:Jetの主電源を確保するためにJ2コネクタのp1はDC5V電源に、p2はGNDに接続してください。\
UARTで通信する場合は、monoZ:Jetのオプション部分（USBコネクタがついている基板）を切り離して使用してください。

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

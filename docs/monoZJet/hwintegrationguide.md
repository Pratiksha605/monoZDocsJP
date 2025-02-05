---
title: ハードウェア仕様
sidebar_position: 2
---
### ピン配列
コネクタのピン割り当ては下記のとおりです。すべてのI/Oピンは最大10mAおよび3.3V定格で機能します。

#### J1コネクタ ピン配列
<div className="card">
    <div className="card__body">
        <div className="row">
            <div className="col col--4">
                <div>
                    <img src={require('@site/static/img/Connector-J1.jpg').default} className="img-center" />
                </div>
            </div>
            <div className="col col--8">
            <table>
                <thead>
                    <tr>
                        <th><b>PIN</b></th>
                        <th><b>PIN No.</b></th>
                        <th><b>DESCRIPTION</b></th>
                    </tr>
                </thead>
                <tbody>
                    <tr>
                        <td>RSTn</td>
                        <td>p6</td>
                        <td>monoZ:Jet Reset pin</td>
                    </tr>
                    <tr>
                        <td>TX (UART, transmit)</td>
                        <td>p7</td>
                        <td>Host {`<->`} monoZ:Jet comm. UART, baud rate:115200</td>
                    </tr>
                    <tr>
                        <td>RX (UART, receive)</td>
                        <td>p8</td>
                        <td>Host {`<->`} monoZ:Jet comm. UART, baud rate:115200</td>
                    </tr>
                    <tr>
                        <td>{`-`}</td>
                        <td>p9</td>
                        <td>Reserved GPIO</td>
                    </tr>
                    <tr>
                        <td>GND</td>
                        <td>p10</td>
                        <td>Ground connection</td>
                    </tr>
                </tbody>
            </table>
            </div>
        </div>
    </div>
</div>

#### J2コネクタ ピン配列
<div className="card">
    <div className="card__body">
        <div className="row">
            <div className="col col--4">
                <div>
                    <img src={require('@site/static/img/Connector-J2.jpg').default} className="img-center" />
                </div>
            </div>
            <div className="col col--8">
            <table>
                <thead>
                    <tr>
                        <td><b>PIN</b></td>
                        <td><b>PIN No.</b></td>
                        <td><b>DESCRIPTION</b></td>
                    </tr>
                </thead>
                <tbody>
                <tr>
                    <td>RSTn</td>
                    <td>p6</td>
                    <td>monoZ:Jet Reset pin</td>
                </tr>
                <tr>
                    <td>VBUS</td>
                    <td>p1</td>
                    <td>5V DC input power supply</td>
                </tr>
                <tr>
                    <td>GND</td>
                    <td>p2</td>
                    <td>Ground connection</td>
                </tr>
                <tr>
                    <td>INT (MOD2HOST_INT)</td>
                    <td>p3</td>
                    <td>monoZ:Jet to host inttrupt pin</td>
                </tr>
                <tr>
                    <td>WKP (HOST2MOD_WKP)</td>
                    <td>p4</td>
                    <td>monoZ:Jet wake up pin</td>
                </tr>
                <tr>
                    <td>GND</td>
                    <td>p5</td>
                    <td>Ground connection</td>
                </tr>
                </tbody>
            </table>
            </div>
        </div>
    </div>
</div>

### 基板寸法
基板寸法は下記の図に示しています。すべてのサイズにおける寸法公差は+-0.05mm です。

<div className="card">
<div className="card__body">
    <img src={require('@site/static/img/Mechanical-Dimensions.jpg').default} className="img-center" />
</div>
</div>
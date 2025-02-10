---
title: MZCSコマンド
sidebar_position: 4
---

MZCSコマンドはmomonZ:Connectサービスで使用される特別なATコマンドです。

import CodeBlock from '@theme/CodeBlock';  
import MDXComponents from '@theme-original/MDXComponents';

### MZCSを起動する

MZCSは、コンソールアプリケーションから実行することも、プロセスハンドラーから実行することもできます。\
MZCSを起動する際にはmonoZ:Connectが接続されているCOMポート番号を指定してください。
<CodeBlock language="javascript" title="Execution Command" className="execution">
{`monoZConnectService.exe-c<COM Port>`}
</CodeBlock>

<CodeBlock language="javascript" title="Response"  className="response">
{`<upon success>
MZOK 
<upon failure>
MZNG`}
</CodeBlock>

#### Defined Values
<div className="card">
    <div className="card__body">
        <div className='row'> 
            <div className='col col--4'> 
                COM Port
            </div>
            <div className='col col--8'> Valid COM Port</div>
        </div>
    </div>
</div>

#### Maximum Response Time
<table>
    <tr>
        <td>15s</td>
    </tr>
</table>

### mzcs_init &nbsp; monoZ:Connectの初期化
monoZ:Connectの初期化と、設定確認を実行します。\
設定が正しくない場合、エラーメッセージが表示されサービスが停止します。

<CodeBlock language="javascript" title="Execution Command" className="execution">
{`mzcs_init `}
</CodeBlock>

<CodeBlock language="javascript" title="Response"  className="response">
{`<upon success>
MZOK
<upon failure>
MZRUNDEVICECONFIG
MZNG`}
</CodeBlock>

#### Defined Values
<div className="card">
    <div className="card__body">
        <div className='row'> 
            <div className='col col--4'> 
                `None `
            </div>
            <div className='col col--8'> 
            </div>
        </div>
    </div>
</div>

#### Maximum Response Time
<table>
    <tr>
        <td>311 s + 900 ms</td>
    </tr>
</table>

### mzcs_devcfg  &nbsp; デバイス設定
このコマンドで通信モデムのAPN設定、LwM2M設定などの初期設定が実行されます。\
初めてmonoZ:Connectを使用する場合、SIMを入れ替えた場合は、monoZ:Connectを起動後このコマンドを実行してください。\
実行された設定はメモリに保存されるので、monoZConnectを起動するたびに実行する必要はありません。\
設定が正常に完了すると、SB IoT Platformとの通信に使用されるデバイスIDを返します。\
設定コマンド実行後サービスは一度停止します。続けてMZCSを利用したい場合はMZCSを起動してください。


<CodeBlock language="javascript" title="Execution Command" className="execution">
{`mzcs_devcfg `}
</CodeBlock>

<CodeBlock language="javascript" title="Response"  className="response">
{`<upon success>
MZOK 
<upon failure> 
MZNG`}
</CodeBlock>

#### Defined Values
<div className="card">
    <div className="card__body">
        <div className='row'> 
            <div className='col col--4'> 
                `None `
            </div>
            <div className='col col--8'> 
            </div>
        </div>
    </div>
</div>

#### Maximum Response Time
<table>
    <tr>
        <td>1407 s + 200 ms</td>
    </tr>
</table>

### mzcs_nwattach &nbsp; NW接続
NW接続、SB IoT Platformへの接続が実行されます。

以下の点に注意してご使用ください。

- コマンド実行前に
<font color="#ff943d;">mzcs_init</font>
コマンドでmonoZ:Connectの初期化が完了していること。
- このコマンド実行後は、ネットワークが切断されるまでこのコマンドを実行しないでください。
- Registration Intervalの時間が経過するまで呼び出さないでください。\
  詳細については「ネットワーク再接続」を参照してください。

<CodeBlock language="javascript" title="Execution Command" className="execution">
{`mzcs_nwattach `}
</CodeBlock>

<CodeBlock language="javascript" title="Response"  className="response">
{`<upon success>
MZOK 
<upon failure> 
MZNG`}
</CodeBlock>

#### Defined Values
<div className="card">
    <div className="card__body">
        <div className='row'> 
            <div className='col col--4'> 
                `None `
            </div>
            <div className='col col--8'> 
            </div>
        </div>
    </div>
</div>

#### Maximum Response Time
<table>
    <tr>
        <td>530 s + 200 ms</td>
    </tr>
</table>

### mzcs_setdata &nbsp; データ格納
特定の`<オブジェクト ID>/<インスタンス ID>/<リソース ID>`にデータを保存できます。

<font color="#ff943d;">mzcs_setdata</font>、<font color="#ff943d;">mzcs_senddata</font>で保存されたデータを上書きします。

データはHex形式で、最大1428 byteまで保存できます。\
FFで2byte、FFFFで4byte となります。 

保存されたデータはSB IoT PlatformからReadリクエストがあると送信されます。

<CodeBlock language="javascript" title="Execution Command" className="execution">
{`mzcs_setdata: -o <OID> -i <IID> -r <RID> -d <Data> `}
</CodeBlock>

<CodeBlock language="javascript" title="Response"  className="response">
{`<upon success> 
MZOK
<upon failure>
MZNG`}
</CodeBlock>

#### Defined Values
<div className="card">
    <div className="card__body">
        <div className='row'> 
            <div className='col col--4'> 
                `OID: `
            </div>
            <div className='col col--8'> 
                LwM2M Object (19) 
            </div>
        </div>
        <div className='row'> 
            <div className='col col--4'> 
                `IID: `
            </div>
            <div className='col col--8'> 
                LwM2M Instance (0~2)
            </div>
        </div>
        <div className='row'> 
            <div className='col col--4'> 
                `RID: `
            </div>
            <div className='col col--8'> 
                LwM2M Resource (0)
            </div>
        </div>
        <div className='row'> 
            <div className='col col--4'> 
                `Data: `
            </div>
            <div className='col col--8'> 
                Hex string (max. 1428 bytes)
            </div>
        </div>
    </div>
</div>

#### Maximum Response Time
<table>
    <tr>
        <td>15 s + 100 ms</td>
    </tr>
</table>

### mzcs_senddata &nbsp; データ送信
特定の`<オブジェクト ID>/<インスタンス ID>/<リソース ID>`にデータを保存しSB IoT Platformに送信できます。

<font color="#ff943d;">mzcs_setdata</font>、<font color="#ff943d;">mzcs_senddata</font>で保存されたデータを上書きします。

データはHex形式で、最大1428 byteまで保存できます。\
FFで2byte、FFFFで4byte となります。 

このコマンドには使用頻度の制限があり、900 秒間隔を空けて実行する必要があります。

詳細については、MZCS メッセージの説明のセクション 5.7 送信データ制限ロックを参照してください。

<CodeBlock language="javascript" title="Execution Command" className="execution">
{`1. mzcs_senddata: -o <OID> -i <IID> -r <RID> -d <Data> -a <ACK>
2. mzcs_senddata: -o <OID> -i <IID> -r <RID> -d <Data> -d <Data>`}
</CodeBlock>

<CodeBlock language="javascript" title="Response"  className="response">
{`
<upon success> 
MZOK
<upon failure>
MZNG
`}
</CodeBlock>

#### Defined Values
<div className="card">
    <div className="card__body">
        <div className='row'> 
            <div className='col col--4'> 
                `OID: `
            </div>
            <div className='col col--8'> 
                LwM2M Object (19) 
            </div>
        </div>
        <div className='row'> 
            <div className='col col--4'> 
                `IID: `
            </div>
            <div className='col col--8'> 
                LwM2M Instance (0~2)
            </div>
        </div>
        <div className='row'> 
            <div className='col col--4'> 
                `RID: `
            </div>
            <div className='col col--8'> 
                LwM2M Resource (0)
            </div>
        </div>
        <div className='row'> 
            <div className='col col--4'> 
                `Data: `
            </div>
            <div className='col col--8'> 
                Hex string (max. 1428 bytes)
            </div>
        </div>
        <div className='row'> 
            <div className='col col--4'> 
                `ACK: `
            </div>
            <div className='col col--8'> 
                0: Non conformable notify\
                1: Conformable notify (default)
            </div>
        </div>
    </div>
</div>

#### Maximum Response Time
<table>
    <tr>
        <td>245 s + 200 ms</td>
    </tr>
</table>

<font color="Red">こちらの仕様にいては現在実装されているか確認中のため、確認ができ次第、編集予定。</font>\
Please note that if the send data API returns with MZNG after displaying the message “Sending OK”, MZCS will clear the data stored on the device for the specified OID, IID and RID by replacing it with null data.

### mzcs_rf &nbsp; 無線ステータス取得
monoZ:ConnectのRF ステータスを取得します。\
<font color="#ff943d;">-r</font> オプションが指定された場合は、詳細情報が返されます。\
オプション指定がない場合は、RFステータスを5段階で表現して返します。

<CodeBlock language="javascript" title="Execution Command" className="execution">
{`mzcs_rf: -r`}
</CodeBlock>

<CodeBlock language="javascript" title="Response"  className="response">
{`<upon success - simplified>
RF status: [1] Good
           [2] Poor
           [3] Bad
           [4] Cell searching
           [5] No service: 
MZOK
<upon failure - simplified>
RF status: [6] No response
MZNG
<upon success - raw>
<earfcn>,<cellID>,<RSRP>,<RSRQ>,<SINR>
MZOK
<upon failure - raw>
MZNG`}
</CodeBlock>

#### Defined Values
<div className="card">
    <div className="card__body">
        <div className='row'> 
            <div className='col col--4'> 
                `None`
            </div>
            <div className='col col--8'> 
            </div>
        </div>
    </div>
</div>

#### Maximum Response Time
<table>
    <tr>
        <td>15 s + 100 ms</td>
    </tr>
</table>

### mzcs_devicereset &nbsp; デバイスリセット
monoZ:Connectをリセットします。設定は変更されません。\
ネットワークに接続し直すには、<font color="#ff943d;">mzcs_init</font> 実行後、Register Intervelの時間が経過したら、<font color="#ff943d;">mzcs_nwattach</font> を実行してください。

<CodeBlock language="javascript" title="Execution Command" className="execution">
{`mzcs_devicereset`}
</CodeBlock>

<CodeBlock language="javascript" title="Response"  className="response">
{`<upon success> 
MZOK
<upon failure>
MZNG`}
</CodeBlock>

#### Defined Values
<div className="card">
    <div className="card__body">
        <div className='row'> 
            <div className='col col--4'> 
                `None`
            </div>
            <div className='col col--8'> 
            </div>
        </div>
    </div>
</div>

#### Maximum Response Time
<table>
    <tr>
        <td> 120 s + 100ms</td>
    </tr>
</table>

### mzcs_heartbeat &nbsp; 死活監視 
monoZ:Connectの死活監視を行います。\
SIMの読み込みに異常がある場合は<font color="#ff943d;">MZNG</font>となります。

<CodeBlock language="javascript" title="Execution Command" className="execution">
{`mzcs_heartbeat`}
</CodeBlock>

<CodeBlock language="javascript" title="Response"  className="response">
{`<upon success> 
MZOK
<upon failure>
MZNG`}
</CodeBlock>

#### Defined Values
<div className="card">
    <div className="card__body">
        <div className='row'> 
            <div className='col col--4'> 
                `None`
            </div>
            <div className='col col--8'> 
            </div>
        </div>
    </div>
</div>

#### Maximum Response Time
<table>
    <tr>
        <td>30 s + 200ms</td>
    </tr>
</table>

### mzcs_led &nbsp; LED設定
はLEDの制御を行います。
赤色(LED1)と青色(LED2)のLEDを制御し、オン、オフ、点滅させることができます。

<CodeBlock language="javascript" title="Execution Command" className="execution">
{`1. mzcs_led: -l <LED> -m <Mode> -t <Time ms>
2. mzcs_led: -l <LED> -m <Mode>`}
</CodeBlock>

<CodeBlock language="javascript" title="Response"  className="response">
{`<upon success>
MZOK 
<upon failure>
MZNG`}
</CodeBlock>

#### Defined Values
<div className="card">
    <div className="card__body">
        <div className='row'> 
            <div className='col col--4'> 
                `LED`
            </div>
            <div className='col col--8'> 
                0: Both, 1: LED1, 2: LED2
            </div>
        </div>
        <div className='row'> 
            <div className='col col--4'> 
                `Mode: `
            </div>
            <div className='col col--8'> 
                0: OFF, 1: ON, 2: BLINK
            </div>
        </div>
        <div className='row'> 
            <div className='col col--4'> 
                `Time: `
            </div>
            <div className='col col--8'> 
                100 ms ~ 3000 ms (500 ms default)
            </div>
        </div>
    </div>
</div>

#### Maximum Response Time
<table>
    <tr>
        <td>66 s</td>
    </tr>
</table>

### mzcs_com &nbsp; COMポート番号確認
MZCSとmonoZ:Connect間の通信に使用されているCOMポート番号を確認することが出来ます。

<CodeBlock language="javascript" title="Execution Command" className="execution">
{` mzcs_com: ?`}
</CodeBlock>

<CodeBlock language="javascript" title="Response"  className="response">
{`<upon success>
Port:<COM Port>
MZOK 
<upon failure>
MZNG`}
</CodeBlock>

#### Defined Values
<div className="card">
    <div className="card__body">
        <div className='row'> 
            <div className='col col--4'> 
                `code?: `
            </div>
            <div className='col col--8'> 
                Query
            </div>
        </div>
    </div>
</div>

#### Maximum Response Time
<table>
    <tr>
        <td> 500 ms</td>
    </tr>
</table>

### mzcs_help &nbsp; ヘルプ
MZCSで利用可能なコマンドを確認することが出来ます。

<CodeBlock language="javascript" title="Execution Command" className="execution">
{`mzcs_help`}
</CodeBlock>

<CodeBlock language="javascript" title="Response"  className="response">
{`<upon success>
List of API
MZOK
<upon failure>
MZNG
`}
</CodeBlock>

#### Defined Values
<div className="card">
    <div className="card__body">
        <div className='row'> 
            <div className='col col--4'> 
                `None`
            </div>
            <div className='col col--8'> 
            </div>
        </div>
    </div>
</div>

#### Maximum Response Time
<table>
    <tr>
        <td> 500 ms</td>
    </tr>
</table>

### mzcs_stop &nbsp; MZCSを停止する
MZCSプロセスを終了し関連するサービスをシャットダウンします。

<CodeBlock language="javascript" title="Execution Command" className="execution">
{`mzcs_stop`}
</CodeBlock>

<CodeBlock language="javascript" title="Response"  className="response">
{`<upon success>
MZOK
<upon failure>
MZNG`}
</CodeBlock>

#### Defined Values
<div className="card">
    <div className="card__body">
        <div className='row'> 
            <div className='col col--4'> 
                `None`
            </div>
            <div className='col col--8'> 
            </div>
        </div>
    </div>
</div>

#### Maximum Response Time
<table>
    <tr>
        <td>391s + 100 ms</td>
    </tr>
</table>

<br/>
# MZCS メッセージ/ACK

### MZOK/MZNG

<font color="#ff943d;">MZOK</font>はプロセスが正常に完了し、サービス アプリケーションが次の要求を受信する準備ができていることを表します。\
<font color="#ff943d;">MZNG</font>はプロセスが正常に完了せず、サービスアプリケーションが次の要求を受信する準備ができていることを表します。

### Connection OK/Connection NG

<font color="#ff943d;">Connection OK</font>は、monoZ:ConnectとSB IoT Platformの接続が成功したことを表します。\
<font color="#ff943d;">Connection NG</font>は、monoZ:ConnectとSB IoT Platformの接続が失敗したことを表します。

### Registration OK/Registration NG

<font color="#ff943d;">Registration OK</font>は、monoZ:ConnectのSB IoT Platformへの登録プロセスが成功したことを表します。\
<font color="#ff943d;">Registration NG</font>は、monoZ:ConnectのSB IoT Platformへの登録プロセスが失敗したことを表します。

### Observe

SB IoT PlatformからOBSERVEコマンドを受信すると、MZCSは受信したOBSERVEの`<オブジェクト ID>/<インスタンス ID>/<リソース ID>`を表示します。\
`<CODE>`が [0] の場合、デバイスにデータを送信するためのトークンが提供されていることを意味します。\
`<CODE>`が [1] の場合、トークンがキャンセルされていることを意味します。トークンのキャンセルは有効期限が切れたことが原因の可能性があります。

<font color="#ff943d;">mzcs_senddata</font>コマンドを使用する前に、Observeのトークン受信している必要があります。\
トークンがキャンセルされていると、SB IoT Platformはデータを受け取れなくなります。したがって、次のObserveのトークンを受信する必要があります。


  #### Message: 
    ```jsx
    MZOBSERVE, <CODE>, <OID>, <IID>, <RID> 
    ```

  #### Parameters
<div className="card">
            <div className="card__body">
                <div className="row mb-2">
                    <div className="col col--4"><code>CODE: </code></div>
                    <div className="col col--8">[0] Observe start; [1] Observe cancel</div>
                </div>
                <div className="row mb-2">
                    <div className="col col--4"><code>OID: </code></div>
                    <div className="col col--8">19</div>
                </div>
                <div className="row mb-2">
                    <div className="col col--4"><code>IID: </code></div>
                    <div className="col col--8">0~2</div>
                </div>
                <div className="row mb-2">
                    <div className="col col--4"><code>RID: </code></div>
                    <div className="col col--8">0</div>
                </div>
            </div>
        </div>
        <br/>



### Notify Process ACK

### プロセス ACK を通知

<font color="#ff943d;">mzcs_senddata</font>コマンドを実行すると、ACK応答オプションに基づいて、以下に示すようにメッセージが送信されます。\
ACK応答オプション `0: Non conformable notify` を選択している場合はSending OKが返ります。\
ACK応答オプション `1: Conformable notify (default)` を選択している場合はSending OKが返った後、Send OKが返ります。
<div className="card">
    <div className="card_body">
        <img src={require('@site/static/img/monoZ-Connect-Non-Comforable.jpg').default} className="img-center" />
   </div>
</div>

<div className="card">
   <div className="card_body">
        <img src={require('@site/static/img/monoZ-Connect-Comforable-Notify.jpg').default} className="img-center" />
   </div>
</div>

### データ送信ロック

<font color="#ff943d;">mzcs_senddata</font>は、SB IoT Platformの負荷を軽減するために最後の送信から900秒経過するまでロックされます。

ロックが解除されると、次のメッセージが表示されます。\
<font color="#ff943d;">MZSEND</font>,1,00:00:00

ロック中に<font color="#ff943d;">mzcs_senddata</font>を実行すると、次のメッセージが表示されます。\
<font color="#ff943d;">MZSEND</font>,0,HH:MM:SS

HH:MM:SS はロックが解除される時刻を示します。

### Write（DLリクエスト）

SB IoT PlatformかWriteを受信すると、MZCSは以下の情報を表示します。

#### Message: 
    ```jsx
    MZDLREQ,<OID>,<IID>,<RID>,<DATA> 
    ```

  #### Parameters
 <div className="card">
            <div className="card__body">
                <div className="row mb-2">
                    <div className="col col--4"><code>OID: </code></div>
                    <div className="col col--8">19</div>
                </div>
                <div className="row mb-2">
                    <div className="col col--4"><code>IID: </code></div>
                    <div className="col col--8">0~2</div>
                </div>
                <div className="row mb-2">
                    <div className="col col--4"><code>RID: </code></div>
                    <div className="col col--8">0</div>
                </div>
                <div className="row mb-2">
                    <div className="col col--4"><code>Data: </code></div>
                    <div className="col col--8">Hex string (max. 1438 characters)</div>
                </div>
            </div>
        </div>
        <br/>

### ネットワーク接続ロック

<font color="#ff943d;">mzcs_nwattach</font>は、SB IoT Platformの負荷を軽減するために最後のネットワーク接続から242秒経過するまでロックされます。

ロックが解除されると、次のメッセージが表示されます。\
<font color="#ff943d;">MZNW</font>,1,00:00:00


ロック中に<font color="#ff943d;">mzcs_nwattach</font>を実行すると、次のメッセージが表示されます。\
<font color="#ff943d;">MZNW</font>,0,HH:MM:SS

HH:MM:SS はロックが解除される時刻を示します。

### COMポート切断

MZCSの起動後、COMポートの切断を検知すると、次のメッセージが表示されます 。\
COM10 disconnected.

COM10 は切断されたCOMポート番号を示します。
### プロセス進行中のコマンド実行

先に実行したコマンドによるプロセスが進行中に、新たにコマンドを実行すると、MZCS は次のメッセージを表示します。\
MZPROCESSRUNNING

### デバイス障害

実行したコマンドが失敗し、MZCS が次のメッセージを返した場合は以下の手順に従ってください。\
MZCSDEVICEFAILURE

1. MZCSが終了しているかどうかを確認し、終了していない場合はサービスが終了するまで待ちます。
2. monoZ:Connectを PC から切断します。
3. 数分後にmonoZ:Connectを PC に再接続します。
4. MZCSを開始します。

### 有効なリクエスト

コマンドを受信すると、MZCS はリクエスト引数を検証します。\
検証の結果、有効なリクエストであった場合、次のメッセージが表示されます。\
Valid Request.

### 無効なリクエスト

コマンドを受信すると、MZCS はリクエスト引数を検証します。\
検証の結果、無効なリクエストであった場合、次のメッセージが表示されます。\
Invalid Request.
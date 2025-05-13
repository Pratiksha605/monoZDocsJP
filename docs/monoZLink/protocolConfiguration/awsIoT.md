---
title: AWS IoT Core
sidebar_position: 3
---
このガイドでは、IoTデバイスからMQTTで送信されたデータを、monoZ:LinkからAWS IoT CoreにMQTTSで転送する設定を解説します。\
あわせてAWS IoT Coreの設定についても触れたいと思います。\
AWSアカウントの作成手順については割愛します。

<div className="card">
    <div className="card__body">
<img src={require('@site/static/img/monoZ-Link-AWS-Iot.png').default} />
</div>
</div>

#### AWS IoT Core "Things"
1. AWSアカウントでログインして、AWSコンソールを開きます。\
　[AWS IoT Core] → [Manage] → [All Devices] → [Things] をクリックします。
<div className="card">
    <div className="card__body">
    <img src={require('@site/static/img/monoZ-Link-AWS-Iot-step1.png').default} /></div></div>
 

2. [Create things]をクリックします。
<div className="card">
    <div className="card__body">
    <img src={require('@site/static/img/monoZ-Link-AWS-Iot-step2.png').default} /><br /><br />
 </div></div>

3. [Create single thing]を選択して、[Next]をクリックします。
<div className="card">
    <div className="card__body">
    <img src={require('@site/static/img/monoZ-Link-AWS-Iot-step3.png').default} />
    </div>
    </div>

4. [Thing name]にデバイス名を入力して、[Next]をクリックします。ここでは仮に "XXXXXXXXXXXXXXX5169"と入力します。
<div className="card">
    <div className="card__body">
    <img src={require('@site/static/img/monoZ-Link-AWS-Iot-step4.png').default} />
    </div>
    </div>
 


5. [Auto-generate a new certificate (recommended)]を選択して、[Next]をクリックします。
<div className="card">
    <div className="card__body">
    <img src={require('@site/static/img/monoZ-Link-AWS-Iot-step5.png').default} />
    </div>
    </div>
 

6. [Attach Policy to Certificate - optional]画面が表示されます。すでにポリシーを作成済みの場合はポリシーを選択してアタッチすることが出来ます。ここではポリシーがないので、ポリシーを添付せずに[Create thing]をクリックします。
<div className="card">
    <div className="card__body">
    <img src={require('@site/static/img/monoZ-Link-AWS-Iot-step6.png').default} />
    </div>
    </div>
 

7. 次の 4 つのファイルをダウンロードして、[Done]をクリックします。\
① Device certificate \
② Public key File \
③ Private key file \
④ Amazon Root CA 1 \
thingが作成されたので、thingにアサインするポリシーを作成できます。
<div className="card">
    <div className="card__body">
    <img src={require('@site/static/img/monoZ-Link-AWS-Iot-step7.png').default} />
    </div>
    </div>
 


8.  [Manage] → [Security] → [Policies] → [Create policy]をクリックします。\
今回は、任意の MQTT トピックにPublishできる新しいポリシーを作成します。
<div className="card">
    <div className="card__body">
    <img src={require('@site/static/img/monoZ-Link-AWS-Iot-step8.png').default} />
    </div>
    </div>
 

9. [Policy name]に"Test"と入力します。\
[Add new statement] をクリックしてポリシーを追加して、次の項目を設定します。
    <table>
        <thead>
            <tr>
                <th>[Policy Effects]</th>
                <th>[Policy Action]</th>
                <th>[Policy Resources]</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td>“permission”</td>
                <td>iot:Connect</td>
                <td>*</td>
            </tr>
            <tr>
                <td>“permission”</td>
                <td>iot:Publish</td>
                <td>*</td>
            </tr>
            <tr>
                <td>“permission”</td>
                <td>iot:Receive</td>
                <td>*</td>
            </tr>
            <tr>
                <td>“permission”</td>
                <td>iot:Subscribe</td>
                <td>*</td>
            </tr>
        </tbody>
    </table>
    	

10. [Create] をクリックするとポリシーが作成されます。
<div className="card">
    <div className="card__body">
    <img src={require('@site/static/img/monoZ-Link-AWS-Iot-step9.png').default} />
    </div>
    </div>
 

11. [Manage] → [Security] → [Certificates]をクリックします。\
Thing作成時に作られたCertificateにチェックを入れて、[Actions]のリストから[Attach policy]を選択します。
<div className="card">
    <div className="card__body">
    <img src={require('@site/static/img/monoZ-Link-AWS-Iot-step10.png').default} />
    </div>
    </div>
 

12. [Policies]の[Choose AWS IoT policy]ドロップダウンリストから作成した"Test" ポリシーにチェックを入れて、[Attach policies]をクリックします。\
これでAWS IoT Coreへのthingの登録が完了しました。
<div className="card">
    <div className="card__body">
    <img src={require('@site/static/img/monoZ-Link-AWS-Iot-step11.png').default} />
    </div>
    </div>
 


13. 最後に、AWS IoT Core にデータを送信するためのカスタムエンドポイントを取得します。\
このエンドポイントは、monoZ:Link で設定を作成するときに使用します。\
[Connect] → [Domain configurations]をクリックします。\
Domain configurationsの一覧からエンドポイントに使用したいDomain nameをコピーします。
<div className="card">
    <div className="card__body">
    <img src={require('@site/static/img/monoZ-Link-AWS-Iot-step12.png').default} />
    </div>
    </div>
 


#### monoZ:Linkのセットアップ 
1. AWS IoT Core にてthing作成時にダウンロードした下記のファイル
    <table>
        <tr><td>Endpoint</td><td>	(Unique device data endpoint of AWS IoT core)</td></tr>
        <tr><td>Private key file</td><td>	random string-private.pem.key</td></tr>
        <tr><td>Device certificate</td><td>	random string-certificate.pem.crt</td></tr>
        <tr><td>Amazon Root CA 1</td><td> 	AmazonRootCA1.pem</td></tr>
    </table>

2. monoZ:Link を開いて、[Configuration] → [Add Configuration]をクリックします。
<div className="card">
    <div className="card__body">
    <img src={require('@site/static/img/monoZ-Link-AWS-Iot-step13.png').default} />
    </div>
    </div>

3. ドロップダウンリストから[AWS IoT Core]を選択してください。
<div className="card">
    <div className="card__body">
    <img src={require('@site/static/img/monoZ-Link-AWS-Iot-step14.png').default} />
    </div>
    </div>
 

4. 下記の各種設定を選択、入力して[Save]をクリックします。
    <table>
    <tr><td>Source Protocol</td><td>	MQTT</td></tr>
    <tr><td>Configuration Name</td><td>	Test Config (Any suitable name)</td></tr>
    <tr><td>Host</td><td>	Paste the device endpoint from AWS</td></tr>
    <tr><td>CA File (Server Cert)</td><td>	Upload “Amazon Root CA 1” file</td></tr>
    <tr><td>Topic</td><td>	Topic to publish on AWS IoT Core. It could be “Same as incoming” or Custom topic.</td></tr>
    <tr><td>QOS</td><td>	MQTTS QOS for publish to AWS IoT Core. Zero or One </td></tr>
    </table>
    <div className="card">
    <div className="card__body">
    <img src={require('@site/static/img/monoZ-Link-AWS-Iot-step15.png').default} />
    </div>
    </div>

 

5. [Groups] → [Add Group]をクリックします。
<div className="card">
    <div className="card__body">
    <img src={require('@site/static/img/monoZ-Link-AWS-Iot-step16.png').default} />
    </div>
    </div>
 

6. 下記の各種設定を選択、入力して[Save]をクリックします。
    <table>
    <tr><td>Group Name</td><td>	Test Group (Any Name)</td></tr>
    <tr><td>Available Configuration</td><td>	Test Config (Select from the configuration)</td></tr>
    </table>
    <div className="card">
    <div className="card__body">
    <img src={require('@site/static/img/monoZ-Link-AWS-Iot-step17.png').default} />
    </div>
    </div>

 

7. [Devices]をクリックします。\
AWS IoT Coreにデータを転送させたいデバイスの[Edit]をクリックします。\
下記のグループ、Certificateファイルを選択して、[Update]をクリックします。\
これでAWS IoT Core接続用のmonoZ:Linkの設定が完了しました。

    <table>
        <tr><td>Group</td><td>	Select the created Test group </td></tr>
        <tr><td>Client Certificate</td><td>	random string-certificate.pem.crt</td></tr>
        <tr><td>Client Key file</td><td>	random string-private.pem.key</td></tr>
    </table>
    <div className="card">
    <div className="card__body">
    <img src={require('@site/static/img/monoZ-Link-AWS-Iot-step18.png').default} />
    </div>
    </div>

 

#### IoTデバイスからデータ送信

AWS IoT Coreの[Test] → [MQTT test client]をクリックします。\
[Topic fileter]に"#"を指定して[Subscribe]をクリックします。\
IoTデバイス "XXXXXXXXXXXXXXX5169"からmonoZ:Linkにペイロードを送信します。\
monoZ:LinkはペイロードをAWS IoT CoreにMQTTSプロトコルで転送します。\
AWS IoT Coreの[MQTT test client]で、転送されてきたペイロードを確認することが出来ます。   
<div className="card">
    <div className="card__body">
 <img src={require('@site/static/img/monoZ-Link-AWS-Iot-step19.png').default} />
 </div>
 </div>
 

#### AWS IoT Core データ形式
monoZ:Linkは、指定されたAWS IoT CoreのBrokerに次の形式でデータを転送します。\
デフォルトでは、monoZ:Linkは各受信メッセージを受信するたびに転送を行います。\
AWS IoT Coreに転送する際に使用するTopicから送信元のデバイスを識別するために各デバイスに固有のトピックを使用することをお勧めします。\
これを実現する簡単な方法は、monoZ:Link プロトコル構成で AWS IoT Core トピックに「受信と同じ」を設定することです。\bor
メッセージの転送に失敗した場合はデータは破棄されます。\
データベース機能が有効になっている場合は、転送に失敗したデータは保存されます。<br/>

    **Example 1:** Packet received at AWS IoT Core
    ```jsx
    ABC
    ```
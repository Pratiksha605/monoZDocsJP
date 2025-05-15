---
title: Webhook
sidebar_position: 1
---

このガイドでは、monoZ:Link からデータを受信できるHTTPサーバーがすでに用意されていることを前提としています。

1. monoZ:Link を開いて、[Configuration] → [Add Configuration]をクリックします。

2. ドロップダウンリストから[Webhook]を選択してください。

<div className="card">
    <div className="card__body">
<img src={require('@site/static/img/monoZ-Link-Wehbook.jpg').default} className="img-center" />
</div>
</div>

3. 下記の転送設定を行います。。
   1. [Source Protocol]に"MQTT"を指定します。

   2. [Configuration Name]を入力します。

   3. [Description]には必要なコメントを残しておくことが出来ます。

   4. [HOST]に転送先サーバーのURLを入力します。

   5. [Parameters]で認証方法を選択します。ここでは"No Authorization"を指定して進めます。

   6. [Custom Headers]にはカスタム ヘッダーを指定することが出来ます。ここでは何も指定せずに進みます。

   7. [Send]で転送するデータに含めるデバイス識別情報をデバイスのICCID、もしくはMQTTトピックのどちらかを選択します。ここではICCIDを選択します。

   8. [Save]をクリックすると転送設定が保存されます。
<div className="card">
    <div className="card__body">
  <img src={require('@site/static/img/monoZ-Link-Protocol-Configuration.png').default} className="img-center" />
</div>
</div>

#### Webhook データ転送仕様
monoz:Linkは以下の仕様でデータを転送します。
   - mooZ:Linkは同じグループ宛に受信したデータを1秒ごとにまとめて転送しています。1秒間に11個以上のパケットを受信した場合はデータを分割して転送します。分割された各データには最大10個の受信データが含まれます。
   - 転送先サーバーにデータを送信すると、monoZ:Linkは最大90 秒間応答を待ちます。
   - 転送先サーバーから応答がない場合、monoZ:Linkは再送を行います。再送は最大2回試行されます。最後の再送に応答がなかった場合は転送に失敗したデータを破棄します。
   - 転送先サーバーからエラー応答があった場合は、再送は行わずにデータを破棄します。
   - データベース機能が有効になっている場合、転送に失敗したデータは保存されます。

#### Webhook 転送データ形式
monoz:Linkは以下のデータ形式でデータを転送します。

##### データ形式:
<table>
   <tr>
      <td><b>フィールド</b></td>
      <td><b>項目</b></td>
      <td><b>備考 </b></td>
   </tr>
   <tr>
      <td rowspan="1">Method</td>
      <td>POST</td>
      <td></td>
   </tr>
   <tr>
      <td rowspan="1">API URL</td>
      <td>URL</td>
      <td>APIのURLが入ります。</td>
   </tr>
   <tr>
      <td rowspan="5">Header</td>
      <td>Authentication</td>
      <td>Basic、BearerToken、API Keyのいずれのセキュリティメソッドを指定したかによって内容が異なります。</td>
   </tr>
   <tr>
      <td>Content Type</td>
      <td>application/json</td>
   </tr>
   <tr>
      <td>content-length</td>
      <td>自動計算されます。</td>
   </tr>
   <tr>
      <td>HOST</td>
      <td>URLのドメインが入ります。</td>
   </tr>
   <tr>
      <td>Custom Header</td>
      <td>ユーザー指定のカスタムヘッダー</td>
   </tr>
   <tr>
      <td rowspan="4">Body</td>
      <td rowspan="2">ICCID</td>
      <td>Device ICCID registered in monoZ:Link</td>
   </tr>
   <tr>
      <td>monZ:Linkの設定にてTopicを指定するとフィールド名が「ICCID」から「Topic」に変更され、Topicの値が入ります。</td>
   </tr>
   <tr>
      <td>Timestamp</td>
      <td>The timestamp when the data was sent from monoZ:Link (ISO:8601 format with milliseconds)</td>
   </tr>
   <tr>
      <td>Payload</td>
      <td>デバイスから送信されたデータ。</td>
   </tr>
</table>

##### 例 1: 1秒間に1つのパケットを取得した場合

<table>
   <tr>
      <td><b>フィールド</b></td>
      <td><b>項目</b></td>
   </tr>
   <tr>
      <td rowspan="1">API URL</td>
      <td>URL</td>
   </tr>
   <tr>
      <td rowspan="5">Header</td>
      <td>Authentication: Basic dGVzdDoxMjM0NTY3ODk=</td>
   </tr>
   <tr>
      <td>Content-Type: application/json; charset=utf-8</td>
   </tr>
   <tr>
      <td>content-length: 102</td>
   </tr>
   <tr>
      <td>host: xxxxyyyxxxyyyxxx.net</td>
   </tr>
   <tr>
      <td>1_Area: Tokyo</td>
   </tr>
   <tr>
      <td rowspan="3">Body</td>
      <td>
         ```json
            { 
               "ICCID": 897612653856781234,
               "Timestamp": "2023-10-16T09:17:32.1233516Z", 
               "Payload": "ABC"
            }
         ```
      </td>
   </tr>
   
</table>

##### 例 2: 1秒間に複数のパケットを取得した場合
<table>
   <tr>
      <td><b>Field</b></td>
      <td><b>Item</b></td>
   </tr>
   <tr>
      <td rowspan="1">API URL</td>
      <td>URL</td>
   </tr>
   <tr>
      <td rowspan="5">Header</td>
      <td>Authentication: Basic dGVzdDoxMjM0NTY3ODk=</td>
   </tr>
   <tr>
      <td>Content-Type: application/json; charset=utf-8</td>
   </tr>
   <tr>
      <td>content-length: 102</td>
   </tr>
   <tr>
      <td>host: xxxxyyyxxxyyyxxx.net</td>
   </tr>
   <tr>
      <td>1_Area: Tokyo</td>
   </tr>
   <tr>
      <td rowspan="3">Body</td>
      <td>
      ```json
      [
        { 
          "ICCID": 897612653856781234,
          "Timestamp": "2023-10-16T09:17:32.1233516Z", 
          "Payload": "ABC"
        },
        { 
          "ICCID": 897612653856787890,
          "Timestamp": "2023-10-16T09:17:32.8383516Z", 
          "Payload": "123"
        }
      ]
      ```
    </td>
   </tr>
</table>
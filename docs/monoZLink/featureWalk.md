---
title: monoZ:Linkを使う
sidebar_position: 2
---

### monoZ&#58;Linkアカウントを作成する

mmonoZ:Linkのアカウントを作成してみましょう。

1. monoZ:Linkログインページに移動して、[Create Account] ボタンをクリックします。

2. monoZ:Linkアカウント作成画面で、必要な情報を入力したら、[アカウントを作成する]ボタンをクリックします。

    1.	名前: フルネームを入力してください。

    2.	Eメール: ログインIDに使用するEメールのアドレスを入力してください。

    3. パスワード: ログインに使用するパスワードを入力してください。最低1つの大文字、1つの数字、1つの特殊文字を含めてください。

    4.	組織名: あなたが所属している組織名を入力してください。

    5.	組織ID: あなたが所属している組織を特定できる最大8文字の英数字でIDを入力してください。monoZ:Linkで割り当たられます。

    6.	T番号: T番号もしくはVAT番号を入力してください。

    7.	担当者の名前とメールアドレスが同じです: チェックを入れるとEメールアドレスと同じになります。別の連絡先を登録したい場合はチェックを外して連絡先情報を入力してください。

    8.	連絡先電話番号: 連絡が出来る電話番号を入力してください。

    9.	請求先住所: 請求先の住所を入力してください。

    10.	請求先住所と配送先住所が同じです: チェックを入れると請求先住所と同じになります。別の住所で配送先を登録したい場合はチェックを外して配送先住所を入力してください。

3. 登録したEメール宛にAccount Verificationのメールが届いたら、メール本文にある[Active]ボタンをクリックしてアカウントを有効化してください。

<div className="card">
    <div className="card__body">
   <img src={require('@site/static/img/monoZ-Link-feature-walk-through.png').default} className="img-center" />
   </div>
   </div>
   <div className="card">
    <div className="card__body">
   <img src={require('@site/static/img/monoZ-Link-Account.png').default} className="img-center" />
   </div>
   </div>
     <div className="card">
    <div className="card__body">
   <img src={require('@site/static/img/emailActivate.png').default} className="img-center" />
   </div>
   </div>

### 注文を作成する

mmonoZ:Linkは、monoZ製品の注文と注文状況を確認できる注文管理システムも提供しています。注文の作成は組織の管理者ユーザーのみが行えます。注文を行うには、以下の手順に従ってください。
1. 「注文」画面に移動し、右上の「+注文の追加」をクリックします。    

2. ポップアップで、「注文タイプ」のドロップダウンリストから、注文したいmonoZ製品を選択します。「追加データ」もここで選択できます。

3. 次に「料金プラン」を選択します。例えば、「注文タイプ」で「monoZ:Link Bundle」を選択した場合は、「Essential」、「Essential +」、「Fleet」、「High Data」の4つの料金プランから選択できます。

4. 注文数量、請求先住所、配送先住所を入力し、ポップアップ右側の「注文の概要」ビューで注文内容を確認します。

5. 注文内容を確認出来たら「注文の作成」をクリックして注文を確定します。

6. 作成された注文は、注文番号と「保留中」ステータスとともに注文一覧に表示されます。作成された注文は注文ステータスが「保留中」の間は編集可能です。

7. 注文ステータスは以下の状態を表しています。

   1. 保留中: 注文が作成されました。monoZオーダー担当者の確認が完了していません。

   2. 処理中: 作成された注文がmonoZオーダー担当者に確認され、発送準備を行っています。

   3. 発送済み: 注文はmonoZオーダー担当者によって発送されました。 

   4. 配達済み: 注文された商品が配送先に配達されました。 

   5. キャンセル: 注文はmonoZオーダー担当者によってキャンセルされました。

8. 注文ステータスが更新されるたびに、組織に登録されている連絡先メールアドレスにメール通知が送信されます。
<div className="card">
    <div className="card__body">
<img src={require('@site/static/img/monoZ-Link-Order.jpg').default} className="img-center" />
</div>
</div>
<div className="card">
    <div className="card__body">
<img src={require('@site/static/img/monoZ-Link-Add-Order.jpg').default} className="img-center" />
</div>
</div>


### 転送設定を作成する

転送設定にて、ユーザーはデバイスの受信プロトコルと送信プロトコルを設定し、デバイスから受信したデータを指定した転送先にルーティングできます。monoZ:LinkはWebhookとAWS IoT Coreとの連携をサポートしています。詳しくは転送設定のチャプターをご確認ください。

### グループを作成する

グループはデバイスに共通の設定を提供し、ファームウェアを配布をグループ単位で管理することが出来ます。ユーザーは、製品ラインや展開地域などに基づいてデバイスをグループ化できます。グループの作成と設定は以下の手順に従ってください。

1.	「グループ」画面に移動し、右上の「+グループの追加」をクリックします。 

2.	以下の情報を入力し、「保存」をクリックします。

    1.	 グループ名: 記号「@$#._- 」を含む最大 20 文字の英数字 

    2.	 利用可能な転送設定: 作成済みの転送設定からグループに付与する転送設定を選択します。

    3. 説明: 自由なコメント。

    4.	 デフォルト設定：Enterpriseをご契約されていて、自動登録機能が有効になっている場合に使用できます。自動登録されたデバイスの所属先グループに指定する場合はチェックを入れてください。
    
    5.	 IMEI ロック: チェックを入れると、グループに所属するデバイスの IMEIロックが有効になります。
<div className="card">
    <div className="card__body">
 <img src={require('@site/static/img/monoZ-Link-Group.jpg').default} className="img-center" />
 </div>
 </div>

 ### デバイスをグループに追加する

デバイスはmonoZ:LinkにおいてSIMのICCIDによって一意に識別されます。新しいデバイスをグループに登録するには以下の手順に従ってください。

1.	「デバイス」メニューに移動し、「登録済みデバイス」をクリックします。

2.	登録済みデバイス一覧からグループに登録させたいデバイスにチェックを入れます。 

3.	左上の「移動」ボタンをクリックし、ドロップダウンリストから対象のグループを選択します。

4.	登録済みデバイスの移動が完了すると、選択したデバイスが「デバイス」ページに表示されます。これでセットアップは完了で、デバイスからデータを受信できるようになります。デバイスの移動後、データを送信を開始するまでに1分程度時間を空けてください。
<div className="card">
    <div className="card__body">
 <img src={require('@site/static/img/monoZ-Link-Registered-Devices.jpg').default} className="img-center" />
 </div></div>
 <div className="card">
    <div className="card__body">
 <img src={require('@site/static/img/monoZ-Link-Destination-Group.jpg').default} className="img-center" />
 </div>
 </div>
 <div className="card">
    <div className="card__body">
 <img src={require('@site/static/img/monoZ-Link-Devices.jpg').default} className="img-center" />
 </div>
</div>

 ### デバイスの閲覧/編集

 デバイスが登録されると、ユーザーはデバイスに関する様々な情報にアクセスできるようになります。デバイスページで既存のデバイス情報を編集することもできます。

   1.	リフレッシュ: ページを更新します。

   2.	フィルター: グループ、タグ、デバイス名、または ICCID でデバイスリストをフィルターします。

   3.	登録済みデバイス: 購入してグループに移動していないデバイスの一覧を確認できます。 

   4.	その他: ユーザーがすべてのデバイスまたは選択したデバイスをCSVに一括エクスポートしたり、選択したデバイスのグループを変更したりできるようにします。グループを変更する場合、選択したデバイスは同じグループに属している必要があります。 
   <div className="card">
    <div className="card__body">
<img src={require('@site/static/img/monoZ-Link-Actions.jpg').default} className="img-center" />
</div>
</div>

デバイス一覧で表示される情報と、2つのアクションボタンがあります。

1.	ICCID: デバイス SIMの19桁のID。

2.	デバイス名: ユーザーが設定したデバイス名。

3. タグ: ユーザーがデバイスに関連付けたタグ。

4.	グループ名: デバイスが登録されているグループの名前。 

5.	転送メソッド: デバイスのグループに添付された転送設定のメソッド。

6.	有効日: デバイスがアクティベーションされたタイムスタンプ（最初にデータ通信が発生したタイムスタンプ）

7. 編集ボタン: 名前、グループ、タグなどのデバイス情報を編集します。 

8.	送信ボタン: ダウンリンクのデータ送信を行います。 
<div className="card">
    <div className="card__body">
<img src={require('@site/static/img/monoZ-Link-Device-List.jpg').default} className="img-center" />
</div>
</div>

デバイスをクリックすると、デバイスに関する詳細情報を示すサイドメニューが表示されます。

1.	操作: IMEI ロックの有効化/無効化、SIM のリセット、SIM の有効化/無効化を行うボタン。

2.	 総使用量: 残りの容量に対する使用済みデータ容量。 

3.	接続ステータス: デバイスのオンライン/オフライン状態。 

4.	直近の接続先: 最後に接続したオペレータと国。

5.	最後に受信したメッセージのタイムスタンプ：最後にデータを受信したタイムスタンプです。

6.	IMEI: デバイスの IMEI 情報。

7.	IPアドレス: デバイスの IP 情報。

8.	SIMステータス：デバイスのデータステータス。無効になっている場合、デバイスはデータを転送できません。

9.	デバイスの有効期限: デフォルトでは、デバイスで使用される SIM カードの有効期限は、monoZ:Link エンドポイントの有効期限とは異なります。 

10.	使用状況グラフ: データ/UL および DL メッセージの使用状況統計を表示します。
<div className="card">
    <div className="card__body">
<img src={require('@site/static/img/monoZ-Link-Device-Info.jpg').default} className="img-center" />
</div>
</div>

### デバイスからmonoZ&#58;Linkにデータを送信する

ペイロード データは、QOS 0 または QOS 1 の MQTT プロトコルを使用して、生のテキストまたは JSON 経由で monoZ:Jet または任意の IoT デバイス上の monoZ:Link に登録されたエンドポイントに送信できます。

<table>
    <tr>
        <td>monoZ:Link broker </td>
        <td>data.monoz.io:1883</td>
    </tr>
    <tr>
        <td>Publish Topic</td>
        <td>< orgid>/< iccid></td>
    </tr>
</table>

monoZ エコシステムは、デバイス側でのデータ消費を最小限に抑えたソリューションの作成を目指しており、そのため monoZ:Jet の場合、ペイロードをクラウドに転送する際にメタデータを追加しません。

これはmonoZ:Jetを使ったデータ転送の簡単な例です。

<table>
    <tr>
        <td>HOST MCU to monoZ:Jet </td>
        <td>MZSEND = 35degC</td>
    </tr>
    <tr>
        <td>monoZ:Jet to monoZ:Link</td>
        <td>35degC</td>
    </tr>
      <tr>
        <td>monoZ:Link to user server (webhook)</td>
       <td> 
       ```jsx
{
  ICCID: < ICCID />,
  Timestamp: < Timestamp />,
  Payload: 35degC
}
```
</td>
    </tr>
</table>

### monoZ&#58;Linkからデバイスにデータを送信する

ペイロード データは、MQTT プロトコルを使用して、生のテキストまたは JSON 経由で monoZ:Link から登録済みの任意の IoT デバイス エンドポイントに送信できます。

<table>
    <tr>
        <td>monoZ:Link broker </td>
        <td>data.monoz.io:1883</td>
    </tr>
    <tr>
        <td>Subscribe Topic</td>
        <td>< orgid>/< iccid>/sub</td>
    </tr>
</table>

monoZ:Linkからデバイスにダウンリンクメッセージを送信するには、以下の手順に従ってください。

1.	ダウンリンクを開始するデバイスの送信ボタンをクリックします。

2.	ユーザーは、QOS 0 または QOS 1 で JSON/テキスト メッセージ形式を選択できます。

3.	DL メッセージ コンテンツにメッセージを入力し、送信を押してダウンリンク メッセージを開始します。

4. 登録されたデバイスがプラットフォームに接続されていない場合は、次回のサブスクライブが成功したときに受信されます。
<div className="card">
    <div className="card__body">
<img src={require('@site/static/img/monoZ-Link-DownLink-Message.jpg').default} className="img-center" />
</div>
</div>

### ユーザーを追加する

プロジェクトの管理を委任したり、他の開発者と共同作業したり、読み取り専用アクセスを提供したりするために、チームメンバーを追加できます。メンバーの追加は簡単で、以下に示すように、それぞれに異なるレベルのアクセス権限を割り当てることができます。

<table>
    <tr>
        <td><b>権限種別 </b> </td>
        <td> <b>ユーザー数制限 </b></td>
        <td><b>詳細 </b> </td>
    </tr>
    <tr>
        <td>オーナー</td>
        <td>1</td>
        <td>すべての画面への閲覧/編集権限があります。 </td>
    </tr>
     <tr>
        <td>Manager</td>
          <td> 4</td>
        <td>ダッシュボード、グループ、設定、デバイス管理への閲覧/編集権限があります。</td>
    </tr>
     <tr>
        <td>Read-only</td>
           <td>4</td>
        <td>ダッシュボード、グループ、設定、デバイス管理への閲覧権限があります。</td>
    </tr>
</table>

monoZ:Link プロジェクトに新しいメンバーを追加するには:

1. テナント管理者としてログインします。 
2. 「ユーザー」メニューに入り、「ユーザーの追加」をクリックします。

<div className="card">
    <div className="card__body">
<img src={require('@site/static/img/monoZ-Link-Users.jpg').default} className="img-center" />
</div>
</div>

3. それぞれの情報を入力し、「保存」をクリックします。

<div className="card">
    <div className="card__body">
<img src={require('@site/static/img/monoZ-Link-Save.jpg').default} className="img-center" />
</div>
</div>

    -   ユーザー名: 任意の名前を入力
    -   ログインID:ログインIDを入力します。メールアドレス形式で入力してください。
    -	役割：ユーザーの役割を指定します。[一般/読み取り専用]に設定します。
    -	パスワード：パスワードを入力します。
    -	アクティブ: アクティブかどうかに基づいてアカウントを作成します。アクティブな場合、ユーザーはすぐに利用可能になります。

### グループブロック機能

動作不良のサーバーへの不要なデータ送信を防ぐために、monoZ:Link にはグループブロック機能が組み込まれています。データ転送の失敗が10回連続して10分間続いた場合、monoZ:Link は転送先サーバーに問題があると判断し、そのグループ内のすべてのデバイスを対象にデータ転送を停止します。グループのブロックを解除するにはお客様に送信されるアラートメールよりブロックを解除してください。

<div className="card">
    <div className="card__body">
<img src={require('@site/static/img/monoZ-Link-Limitations-Group-Blocking.jpg').default} className="img-center" />
</div>
</div>

ブロック参考シナリオ:

<table>
    <tr>
        <td> <b>シナリオ </b></td>
        <td> <b>条件 </b></td>
        <td> <b>結果 </b></td>
    </tr>
    <tr>
        <td>データ送信開始から5分間は10回連続で送信失敗し、6分経過したときに送信が成功しました。</td>
        <td>
        <codeBlock>
         10分：× <br/>
       10回連続：〇
       </codeBlock>
</td>
        <td>ブロックしません。</td>
    </tr>
     <tr>
        <td>データ送信開始から10分間は20回連続で送信失敗し、10分経過した後は送信されません。 </td>
        <td>
      <codeBlock>
       10分：〇 <br/>
       10回連続：〇
      </codeBlock>
</td>
        <td>ブロックします。</td>
    </tr>
     <tr>
        <td>データ送信開始から18分間は9回連続で送信失敗し、20分経過したときに送信が成功しました。</td>
        <td>   
        <codeBlock>
         10分：〇 <br/>
       10回連続：×
       </codeBlock>
</td>
        <td>ブロックしません。</td>
    </tr>
</table>








    
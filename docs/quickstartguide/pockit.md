---
title: monoZ:Jet クイックスタートガイド
sidebar_position: 1
---

monoZ:Jetクイックスタートガイドへようこそ。このガイドではmonoZ:Jet PoCキットを使用して、ホストからmonoZ:Linkにメッセージを送信する方法と、monoZ:Linkからのメッセージをホストで受け取る方法を解説します。より詳しい内容を学びたい方は、monoZ:Jet、monoZ:Linkのドキュメントを参照してください。

### Prerequisites
クイックスタートガイドを始める前に、必要な情報がそろっているか確認しましょう。
1. monoZ:Linkを利用するにはmonoZ:Linkアカウントの登録が必要です。\
アカウントをお持ちでない場合は、組織の管理者に新規アカウントの作成を依頼するか、<a target="_blank" href="https://link.monoz.io/monoZLink/Login">ここをクリック</a>して新しい組織でアカウントを作成してください。
2. monoZ:JetのPoCキットを使用します。お持ちでない場合は、monoZ:Link の注文管理タブから注文してください。
3. PoCキットの1NCE SIMがmonoZ:Linkのデバイスメニューまたはデバイスメニューの登録済みデバイスにすでに登録されていることをご確認ください。登録されていない場合は、monoZサポート customer-care@meritech.odoo.com にお問い合わせください。
4. ホストとmonoZ:Jetを接続するために、はんだ付けキットもしくはUSBケーブルをご用意ください。

### 開封
1. POC キットのパッケージを開き、次のアイテムを見つけます。\
    i. monoZ:Jet \
    ii. 1NCE SIM \
    iii. 標準アンテナ \
    iv. Pi アドオン ボード (オプション ボード)
2. 1NCE SIMのICCIDがmonoZ:Linkの[デバイス]または[登録済みデバイス]に登録されていることを確認します。

    <img className="img-center" src={require('@site/static/img/quickguide1.png').default} />

### Setting Up monoZ:Jet
1. monoZ:Jetは、USBモードまたはUARTモードでホストと通信することが出来ます。デフォルトではUSB モードが有効になっています。
2. ホストがUARTモードでmonoZ:Jetと通信したい場合は、次のいずれかの方法でmonoZ:JetをUART モードに切り替えることができます。\
    i. 方法 1: PCBカッターを使用してmonoZ:JetボードのUSBコネクタ基板を切り取ります。一度切り離すとUSBモードで使用することは出来なくなりますのでご注意ください。
    <img className="img-center" src={require('@site/static/img/quickguide2.png').default} />
    ii. 以下の画像を参考に、3つの抵抗器を取り外します。この方法を使用した場合、抵抗器を元の位置にはんだ付けし直すことで、monoZ:JetをUSBモードに戻すことも出来ます。  
    <img className="img-center" src={require('@site/static/img/quickguide3.png').default} />
3. USBモードとUART モードの通信構成を確認する場合は、 <a target="_blank" href="https://docs.monoz.io/docs/monoZJet/hostcommunication">こちら</a>をご確認ください。
4. 本クイックスタートガイドでは、PCをホストデバイスとして使用し、コンソールアプリケーションを使用してUSB経由でmonoZ:Jetと通信します。
    <img className="img-center" src={require('@site/static/img/quickguide4.png').default} />

##### 注意:
    i. USBと5V VBUSピン経由で同時にmonoZ:Jetに給電しないでください。 過電流によりmonoZ:Jet が故障する可能性がございます。
    ii. USBモードの場合、UARTピンはどこにも接続しないでください。monoZ:JetがUSBモードのときに、UART経由でデータが送信されると、monoZ:Jetはデバイス障害が発生することがあります。



### monoZ:Linkの初回設定
組織で初めてmonoZ:Linkを使用する場合は登録済みデバイスをグループに所属させる必要があります。\
monoZ:Linkにログインして、転送設定の登録を行います。\
転送設定ではプロトコルの変換と、転送先の設定を行います。\
このガイドでは、転送先にHTTPSエンドポイントを指定します。
1.	[転送設定]>[転送設定の登録]>[Webhook]を選択して、新規の転送設定を登録します。
    <img className="img-center" src={require('@site/static/img/quickguide5.png').default} />
2. 登録が完了したら、[グループ]>[グループの登録]を選択して、新しいグループを作成します。\
グループの登録では手順1で登録した「転送設定」を選択してください。\
初めて作成したグループは自動的に「デフォルト」グループとして割り当てられます。
    <img className="img-center" src={require('@site/static/img/quickguide6.png').default} />
3. [デバイス]>[登録済みのデバイス]をクリックして、対象デバイスのICCIDにチェックを入れて[移動]をクリックします。
選択デバイスのグループ変更では、手順2で作成したグループを選択して[移動]をクリックします。\
デフォルトグループが割り当てられた後にSIMを購入した場合は、新しいデバイスがmonoZ:Linkに登録される際に自動的にデフォルトグループに割り当てられます。\
必要に応じてデバイスを別のグループに移動させてください。このステップで、monoZ:Link のセットアップは完了です。
    <img className="img-center" src={require('@site/static/img/quickguide7.png').default} />
 

### データを送信する
1. ホストからmonoZ:Jetへデータを送信します。\
前述のようにこのクイックスタートガイドではPCをホストデバイスとして使用します。\
まずはPoCパッケージの1NCE SIMをmonoZ:Jetに挿入し、U.FLポート(Main)に付属のアンテナを接続します。
    <img className="img-center" src={require('@site/static/img/quickguide8.png').default} />
 
2. USBケーブルを使用してmonoZ:JetをPCに接続します。接続すると、monoZ:Jetボードの電源LEDが赤く点灯します。
    <img className="img-center" src={require('@site/static/img/quickguide9.png').default} />
 
3. 次にターミナルエミュレーターを使ってmonoZ:Jetとの通信を確立します。\
オープンソースソフトウェアターミナルエミュレーターPuttyの設定に関するガイドについては、<a target="_blank" href="https://docs.monoz.io/v1/_d_e_b_u_g__c_o_n_s_o_l_e.html">こちらをクリックして参照してください</a>。
4. 電源がオンになると、monoZ:Jetはホストに+MZREADYを送信し、コマンドを受信する準備ができていることを示します。\
このメッセージはUSBをmonoZ:Jetに接続してから数ミリ秒以内に送信されるため、ターミナルエミュレータでは受信できない可能性があります。
5. デフォルトでは、monoZ:Jetはサポートされているすべてのbandを使用する設定になっています。
ネットワーク接続までの時間を短縮するには、ご利用の地域で使用されているbandのみを設定することを強くお勧めします。
推奨されるバンド設定の詳細については、MZコマンドのMZBANDを参照してください。\
このクイックスタートガイドでは日本から実行していいる想定で日本のバンドを設定します。\
Band設定は1度設定すれば、ご利用の地域が変わらない限りは繰り返し設定する必要はありません。\
+MZBAND: 0 応答は、バンド設定が成功したことを示します。
    <img className="img-center" src={require('@site/static/img/quickguide10.png').default} />
6. 次にmonoZ:JetのORG IDを設定します。\
ORG IDはデバイスが所属する組織を特定するために設定します。\
こちらも1度設定すればOKです。
    <img className="img-center" src={require('@site/static/img/quickguide11.png').default} /><br/>
    <img className="img-center" src={require('@site/static/img/quickguide12.png').default} />

7. 次にmonoZ:Jetを初期化し、MZSTARTを使用して接続します。\
MZSTART実行後、ホストは+MZSTART:0とメッセージが表示されるまで待ってください。\
+MZSTART:3または+MZSTART:4とメッセージが表示さえることがあります。\
これはmonoZ:Jetがネットワーク、monoZ:Linkプラットフォームへの接続を再試行していることを表しています。\
推奨のband設定をしていても、最初のネットワーク接続は2分～3分程度かかることがあります。\
推奨band設定をしていない場合、monoZ:Jetは全てのbandのスキャンを行うため、さらに接続に時間がかかります。
    <img className="img-center" src={require('@site/static/img/quickguide13.png').default} />
8. +MZSTART:0を受信すると、ホストはMZSENDコマンドを使用してmonoZ:Linkにデータを送信できます。
    <img className="img-center" src={require('@site/static/img/quickguide14.png').default} />

9. 送信されたデータは安全なチャネルを介してmonoZ:Linkに送信されます。\
その後、monoZ:Linkは転送設定に従って転送先サーバーに指定のプロトコルでデータを転送します。\
monoZ:Jetから送信されたデータは、monoZ:Linkを介して転送先サーバーで受信されます。
    <img className="img-center" src={require('@site/static/img/quickguide15.png').default} />
10. MZRECEIVEを使用して、monoZ:JetでmonoZ:Linkからのメッセージを受信状態にします。\
受信状態を有効にすると、monoZ:Jetは +MZRECEIVE URCを使用して、monoZ:Linkから受信したデータをホストに送信します。
    <img className="img-center" src={require('@site/static/img/quickguide16.png').default} />
11.	Let’s send downlink from monoZ:Link.
    <img className="img-center" src={require('@site/static/img/quickguide17.png').default} /><br/>
    <img className="img-center" src={require('@site/static/img/quickguide18.png').default} />
 
12. これでmonoZ:JetとmonoZ:Linkを使ったデータ送信のクイックスタートガイドは終了です。\
不明な点がある場合は、customer-care@meritech.odoo.com にメールでサポートリクエストを送信してください。
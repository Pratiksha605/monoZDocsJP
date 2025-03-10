---
title: API認証
sidebar_position: 2
---

公開されたAPIへのリクエストはすべて安全に認証されている必要があります。
<br/>monoZ:Linkプラットフォームで組織を登録する際に、monoZ:Link Rest APIへのアクセス用にAPIキーが生成されます。
<br/>リクエスト送信元を認証するために、APIキーはすべてのAPIリクエストのヘッダーで指定する必要があります。
<br/>APIキーは、アカウントの作成時にMeritechからアカウントマネージャーに提供されます。
<br/>APIキーがない場合は、Meritechサポートにお問い合わせください。
<br/>ヘッダー名には「X-API-Key」を指定してください。
<br/>組織に与えられたAPIキーが「exampleapikeyabcdefgh123456」である場合、ヘッダー情報は以下のようになります。



```jsx
--header 'X-API-Key: exampleapikeyabcdefgh123456'
```
<img src={require('@site/static/img/cc.jpg').default} />
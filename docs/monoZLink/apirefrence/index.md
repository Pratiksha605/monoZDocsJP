---
title: monoZ:Link API 
sidebar_position: 4
---

### はじめに

monoZ:Linkは、サポートされている様々なプロトコルでデータを受信し、プロトコル変換してデータを転送するサービスです。
<br/>このサービスは、受信プロトコル側ではセキュアネットワークを提供することで、オーバーヘッドの少ない軽量なデータを扱うことが出来ます。
<br/>送信プロトコル側ではセキュリティ保護されたプロトコルで安全なデータ転送を実現します。
<br/>このドキュメントでは、monoZ:Linkサービスによって公開されているREST APIについて説明します。

### 用語

以下の表は、このAPIドキュメント全体で使用される用語について説明しています。

<table>
<tr>
<td>API</td>
<td><strong>A</strong>pplication <strong>P</strong>rogramming <strong>I</strong>nterface</td>
</tr>
<tr>
<td>REST</td>
<td>Representational State Transfer, and HTTP base architecture for data transfer.</td>
</tr>
<tr>
<td>JSON</td>
<td>JavaScript Object Notation, a data structuring format.</td>
</tr>
<tr>
<td>IoT</td>
<td>Internet of Things.</td>
</tr>
<tr>
<td>MQTT</td>
<td>Message Queuing Telemetry Transport.</td>
</tr>
</table>

<!-- # URI Structure

The URIs for the API resources have the following structure:

For example:

This document details the version 1 of the APIs.
The OrgID is the Organization ID which is generate when the Organization is re.g.,istered on the monoZ:Link portal. This is provided by Meritech to the account manager when the account is created. Please contact Meritech Support if you do not have the OrgID.
The Resource-Name is detailed in the sections below.

### Authentication

Any call to the published APIs must be securely authenticated. During re.g.,istration of the Organization in the monoZ:Link Platform an API Key is generated for the programmatic access of monoZ:Link Rest APIs. The API Key needs to be passed in header for every API call so as to authenticate the caller.
The API Key is provided by Meritech to the account manager when the account is created. Please contact Meritech Support if you do not have the API Key.
This is standard API Key implementation and the header needs to be X-API-Key. Hence if the Key given to your organization is: abcdefg123456 then one needs to pass the following in the API header:

--header 'X-API-Key: abcdefgh123456' -->

### REST API Description

REST APIとその使用方法を解説します。
<br/>下記の表に示されているインスタンス、バージョン、組織ID、ICCIDを使用して説明します。

<table>
    <tr>
        <td>Instance: </td>
        <td>https://link.monoz.io/api</td>
    </tr>
    <tr>
        <td>Version: </td>
        <td>v1</td>
    </tr>
    <tr>
        <td>Organization ID: </td>
        <td>mti</td>
    </tr>
    <tr>
        <td>ICCID: </td>
        <td>1234567890</td>
    </tr>
</table>

APIリクエストには下記のHTTPヘッダーを組み合わせて使用します。

<table>
    <tr>
        <td><b>Header Name</b> </td>
        <td><b>Header Value</b></td>
    </tr>
    <tr>
        <td>Content-Type </td>
        <td>application/json </td>
    </tr>
    <tr>
        <td>X-API-Key </td>
        <td>exampleapikeyabcdefgh123456</td>
    </tr>
        <tr>
        <td>Authorization </td>
        <td>Bearer exampleauthabcdefgh123456</td>
    </tr>
</table>

cURLコマンドでAPIリクエストを実行する方法と、想定されるいくつかの戻り値について各APIのセクションで解説します。
<br/>各APIで返される応答結果については各APIのセクションで詳しく説明しますが、共通している応答規則について説明します。
<br/>すべてのAPIの応答結果には、JSON形式のResponse bodyが含まれていて、下記のkeyが含まれます。

<table>
<tr>
<td>Error:</td>
<td>HTTPステータスコードのエラーとは別に、リクエストされた処理の実行中にエラーがあったかどうかを示します。
    <br/>値はbooleanで表現され、Trueはエラーあり、Falseはエラーなしを示します</td>
</tr>
<tr>
<td>Message:</td>
<td>HTTPステータスエラー、プロセスエラーの原因説明が記載されます。エラーがない場合はFetchSuccessと記載されます。</td>
</tr>
<tr>
<td>StatusCode:</td>
<td>標準のHTTPステータスコードを示します。</td>
</tr>
<tr>
<td>Data:</td>
<td>APIリクエストで要求したデータ本体が含まれます。各APIごとに異なるデータ構造を持つため詳細は各APIセクションを確認してください。</td>
</tr>
</table>

すべてのレコードは組織に紐づけられているため、各API呼び出しには組織IDを指定する必要があります。基本的にURLパスに組織IDしてAPIリクエストを実行します。

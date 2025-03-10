---
title: POST Rawデータ取得
sidebar_position: 7
---
<!-- <div className="row">
    <div className="col col--7"> -->
        <p className="Get-link"><span className="get">POST</span> <em>https://link.monoz.io/api/v1/{Org-Id}/RawData</em></p>
        <p style={{ textAlign: 'justify' }}>このAPIはデータベース機能を契約されているユーザーのみが利用することが出来ます。
        データベースを契約されていると、monoZ:Linkはデバイスから受信した生データをデータベースに保存して、最大72時間データベースに保存します。このデータはRAW Data APIを使用して取得することができます。
        ユーザーは取得したい時刻範囲を指定してデータを取得する必要がありますが、指定した時刻範囲によってはデータベースの更新が完了していないために、指定した時刻範囲のデータを全て取得できないことがあります。
        データの取りこぼしを避けるためには、取得済みのデータのうち最新のタイムスタンプを、時刻範囲の開始時刻に指定してAPIを呼び出してください。
        受信データの頻度に応じて、このAPIを4時間に1回から、1日に1回の頻度で使用することを推奨しています。</p> 

        ##### Args
        <div className="card">
            <div className="card__body">
                <div className="row mb-2">
                    <div className="col col--4"><code>ORG-ID</code></div>
                    <div className="col col--8">The unique ID assigned to your organisation</div>
                </div>
                <div className="row mb-2">
                    <div className="col col--4"><code>StartTime</code></div>
                    <div className="col col--8">Starting time in ISO:8601 format</div>
                </div>
                <div className="row mb-2">
                    <div className="col col--4"><code>EndTime</code></div>
                    <div className="col col--8">End time in ISO:8601 format</div>
                </div>
            </div>
        </div>
        <br/>
        ##### Response
        <details>
            <summary>
                <div> <div class="error_200 HTTPStatus "><span class="HTTPStatus-chit"></span></div>200</div>
                <small>Success <small className="text-gray">FetchSuccess</small></small>
            </summary>
            ###### Response Body
            <div className="response_details">
                <strong>Error</strong>&nbsp;&nbsp;  <small className="text-gray">boolean</small> 
                <p>Indicates if there was an error.</p>
            </div>
            <div className="response_details">
                <strong>Message</strong>&nbsp;&nbsp;  <small className="text-gray">string</small> 
                <p>Message indicating the result of the operation.</p>
            </div>
            <div className="response_details">
                <strong>StatusCode</strong>&nbsp;&nbsp;  <small className="text-gray">integer</small> 
                <p>HTTP status code of the response.</p>
            </div>
            <div className="response_details">
                <strong>Data</strong>&nbsp;&nbsp;  <small className="text-gray">array</small> 
                <p>Array of JSON objects containing raw data details.</p>
            </div>
            <div className="response_details">
                <strong>Timestamp</strong>&nbsp;&nbsp;  <small className="text-gray">timestamp</small> 
                <p>The received timestamp in ISO:8601 format.</p>
            </div>
            <div className="response_details">
                <strong>Payload</strong>&nbsp;&nbsp;  <small className="text-gray">string</small> 
                <p>The actual packet received.</p>
            </div>
            <div className="response_details">
                <strong>ICCID</strong>&nbsp;&nbsp;  <small className="text-gray">string</small> 
                <p>The ICCID of the SIM.</p>
            </div>
            <div className="response_details">
                <strong>Topic</strong>&nbsp;&nbsp;  <small className="text-gray">string</small> 
                <p>The topic on which the payload was sent.</p>
            </div>
        </details> 
        <div className="Block-error">
            <div className="error_block_400">
                <summary className="border-bottom">
                    <div className="summery-error"> 
                        <div><code class="HTTPStatus  error_404"><span class="HTTPStatus-chit"></span></code>401</div>
                        <small>Unauthorized <small className="text-gray">If the API Key is wrong or there is no permission to access the requested data.</small></small>
                    </div>
                </summary>
            </div>
            <div className="error_block_400">
                <summary className="border-bottom">
                    <div className="summery-error"> 
                        <div><code class="HTTPStatus  error_404"><span class="HTTPStatus-chit"></span></code>400</div>
                        <small>Bad Request <small className="text-gray">If the input value is not in the correct format.</small></small>
                    </div>
                </summary>
            </div>
            <div className="error_block_400">
                <summary className="border-bottom">
                    <div className="summery-error"> 
                        <div><code class="HTTPStatus  error_404"><span class="HTTPStatus-chit"></span></code>500</div>
                        <small>Server Error <small className="text-gray">As described in the Message field.</small></small>
                    </div>
                </summary>
            </div>
        </div>
    <!-- </div>
    <div className="col col--5"> -->
        <div className="sticky">
            ##### cURL
            ```jsx
                curl --location 'https://link.monoz.io/api/v1/mti/RawData' \
                --header 'Content-Type: application/json' \
                --header 'X-API-Key: 3fa36b0e-c88b-45f4-95b9-d77c0e27c07a' \
                --data '{
                    "StartTime": "2024-02-11T07:26:54.441Z",
                    "EndTime": "2024-03-11T07:26:54.441Z"
                }'
            ```
            ##### Response
            ```jsx
            {
                "Error": false,
                "Message": "FetchSuccess",
                "StatusCode": 200,
                "Data": [
                    {
                        "Timestamp": "2024-03-11T04:19:55.5799558Z",
                        "Payload": "DFa0FC31EEC1569aA274f9ae5fffbB80AE2691BEe4EDBC89F6",
                        "ICCID": "123456789",
                        "Topic": "The topic on which the payload was received at monoZ:Link."
                    },
                    {
                        "Timestamp": "2024-03-11T04:19:55.5799458Z",
                        "Payload": "DEEDFa0FC3sfsdfsf1EEC1569aA274f9ae5fffbB80AE2691BEe4EDBC89F6",
                        "ICCID": null,
                        "Topic": "/mti/1234567777"
                    }
                ]
            }
            ```
        </div>
    <!-- </div>
</div> -->
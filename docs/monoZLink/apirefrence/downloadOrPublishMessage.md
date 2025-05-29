---
title: POST ダウンリンクメッセージ送信
sidebar_position: 9
---
<!-- <div className="row">
    <div className="col col--7"> -->
        <p className="Get-link"><span className="get">POST</span> <em>https://link.monoz.io/api/v1/{Org-Id}/Publish/Message</em></p>
        このAPIは接続されたデバイスにダウンリンクメッセージを送信するために使用されます。
        Topicに何も指定しないと、<b>\/\< ORGID\>\/\<ICCID\>\/sub</b> にデータがPublishされます。
        Topicに「\/ABC」を指定した場合は、<b>\/\<ORGID\>\/\<ICCID>\/sub\/ABC</b> にデータがPublishされます。


        ##### Args
        <div className="card">
            <div className="card__body">
                <div className="row mb-2">
                    <div className="col col--4"><code>ORG-ID</code></div>
                    <div className="col col--8">組織ごとにユニークなIDです。</div>
                </div>
                <div className="row mb-2">
                    <div className="col col--4"><code>ICCID</code></div>
                    <div className="col col--8">ICCIDは対象のデバイス（SIM）ごとにユニークに割り振られるIDです。</div>
                </div>
                <div className="row mb-2">
                    <div className="col col--4"><code>Topic</code></div>
                    <div className="col col--8">MQTTのTopicを指定します。「"/\<ORGID\>"/\<ICCID\>"/sub」に続くTopicを指定できます。空でも問題ありません。
                    <br/>最大長は「"/\<ORGID\>"/\<ICCID\>"/sub」を含めて512byteです。</div>
                </div>
                <div className="row mb-2">
                    <div className="col col--4"><code>QoS</code></div>
                    <div className="col col--8">MQTTのQoSを指定します。 monoZ:Linkでは0と1を指定できます。</div>
                </div>
                <div className="row mb-2">
                    <div className="col col--4"><code>Message</code></div>
                    <div className="col col--8">ダウンリンクメッセージ本文。最大長は4096byteです。
                    <br/>monoZ:Jetが受け取れるメッセージの最大長は1024byteです。</div>
                </div>
                <div className="row mb-2">
                    <div className="col col--4"><code>RetainLastMessage</code></div>
                    <div className="col col--8"> Trueに設定すると、最後に送信したメッセージはmonoZ:Linkブローカーによって保存され、デバイスがサブスクライブしたときに送信されます。
                    <br/>True: Retainを有効にしてメッセージを送信します。
                    <br/>False: Retainを無効にしてメッセージを送信します。</div>
                </div>
                <div className="row mb-2">
                    <div className="col col--4"><code>Format</code></div>
                    <div className="col col--8">ダウンリンクメッセージの形式を指定します。
                    <br/>0:JSON形式
                    <br/>&nbsp;入力したメッセージがJSON形式で改行を含む場合、改行を削除して送信します。（monoZ:Jetは改行を含むメッセージを強要しないため。）
                    <br/>1:TEXT形式
                    <br/>&nbsp;入力したメッセージをそのまま送信します。</div>
                </div>
            </div>
        </div>
        <br/>
        ##### Response
        <details>
            <summary>
                <div> <div class="error_200 HTTPStatus "><span class="HTTPStatus-chit"></span></div>200</div>
                <small>Success <small className="text-gray">MessagePublished</small></small>
            </summary>
            ###### Response Body
            <!-- <div className="response_details">
                <strong>Error</strong>&nbsp;&nbsp;  <small className="text-gray">boolean</small> 
                <p>Indicates if there was an error.</p>
            </div> -->
            <div className="response_details">
                <strong>StatusCode</strong>&nbsp;&nbsp;  <small className="text-gray">integer</small> 
                <p>HTTP status code of the response.</p>
            </div>
            <div className="response_details">
                <strong>Message</strong>&nbsp;&nbsp;  <small className="text-gray">string</small> 
                <p>Message indicating the result of the operation.</p>
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
                        <div><code class="HTTPStatus  error_404"><span class="HTTPStatus-chit"></span></code>404</div>
                        <small>Not Found <small className="text-gray">If the specified ICCID was not found in the system.</small></small>
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
                curl --location 'https://link.monoz.io/api/v1/mti/Publish/Message' \
                --header 'Content-Type: application/json' \
                --header 'X-API-Key: 3fa36b0e-c88b-45f4-95b9-d77c0e27c07a' \
                --data '{
                    "ICCID": "12345678",
                    "Topic": "/ABC",
                    "Message": "XYZ",
                    "RetainLastMessage": true,
                    "QoS": 0,
                    "Format": 1
                }'
            ```
            ##### Response
            ```jsx
            {
                "StatusCode": 200,
                "Message": "MessagePublished"
            }
            ```
        </div>
<!-- </div>
</div> -->
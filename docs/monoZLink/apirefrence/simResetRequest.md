---
title: PUT SIMリセット
sidebar_position: 6
---
<!-- <div className="row">
    <div className="col col--7"> -->
        <p className="Get-link"><span className="get">PUT</span> <em>https://link.monoz.io/api/v1/{OrganizationId}/Sim/Reset</em></p>
        SIM接続リセットのプロセスを開始し、プロセスが正常に開始された場合はOKを返します。

        ##### Args
        <div className="card">
            <div className="card__body">
                <div className="row mb-2">
                    <div className="col col--4"><code>ORG-ID</code></div>
                    <div className="col col--8">The unique ID assigned to your organisation</div>
                </div>
                <div className="row mb-2">
                    <div className="col col--4"><code>ICCID</code></div>
                    <div className="col col--8">Unique ICCID of target device</div>
                </div>
            </div>
        </div>
        <br/>
        ##### Response
        <details>
            <summary>
                <div> <div class="error_200 HTTPStatus "><span class="HTTPStatus-chit"></span></div>200</div>
                <small>Success <small className="text-gray">UpdateSuccess</small></small>
            </summary>
            ###### Response Body
            <div className="response_details">
                <strong>Error</strong>&nbsp;&nbsp;  <small className="text-gray">boolean</small> 
                <p>Indicates if there was an error.</p>
            </div>
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
                curl --location --request PUT 'https://link.monoz.io/api/v1/mti/Sim/Reset' \
                --header 'Content-Type: application/json' \
                --header 'X-API-Key: abcdefgh123456' \
                --data '{
                    "ICCID": "1234567890"
                }'
            ```
            ##### Response
            ```jsx
            {
                "Error": false,
                "StatusCode": 200,
                "Message": "UpdateSuccess"
            }
            ```
        </div>
    <!-- </div>
</div> -->
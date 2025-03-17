# Route and transform messages

In the previous tutorial, we learned how to develop, deploy, and test our first integration in WSO2 MI. In this tutorial, you'll learn how to dynamically build a payload and call an HTTP backend service.

## Prerequisites

1. You need Visual Studio Code (VS Code) with the <a target="_blank" href="https://marketplace.visualstudio.com/items?itemName=WSO2.micro-integrator">Micro Integrator for VS Code</a> extension installed.

    !!! Info
        See the [Install Micro Integrator for VS Code]({{base_path}}/develop/mi-for-vscode/install-wso2-mi-for-vscode/) documentation to learn how to install Micro Integrator for VS Code.

2. You must have completed the **Develop an API service** tutorial under **Build your first integration** before proceeding. Start the [Develop an API service]()  tutorial if you haven’t completed it yet.

Follow the instructions below to modify the API service to call an HTTP endpoint and dynamically build a payload.

## What you'll learn

- How to create an API resource.
- How to use the HTTP connector.
- How to use expressions.
- How to use the Mediator TryOut.

## What you'll build

Let's consider a scenario where a client sends a request to the `Bank` API deployed in WSO2 Micro Integrator. The API checks the currency type, and if it is not `USD`, it calls a currency converter service to convert the amount before responding with the updated value.

<a href="{{base_path}}/assets/img/integrate/quick-start-guide/mi-quick-start-guide.gif"><img src="{{base_path}}/assets/img/integrate/quick-start-guide/mi-quick-start-guide.gif"></a>

## Step 1 - Create a new API resource

To develop the above scenario, let's get started with creating a new API resource in the `Bank` API.

1. Click on the Service Designer `|||` icon of the `Bank` API in the **Micro Integrator Project Explorer** to open the Service Designer.

    <a href="{{base_path}}/assets/img/develop/mi-for-vscode/mi-vscode-extension.png"><img src="{{base_path}}/assets/img/develop/mi-for-vscode/mi-vscode-extension.png" alt="MI VS Code Extension" width="80%"></a>

2. In the Service Designer, click the **+ Resource** button to add a new API resource.

4. In the **Add API Resource** pane, set `/deposit` as the **Resource Path** and select the `POST` method. 

5. Finally, click **Create** to add the new API resource.

## Step 2 - Design the integration

Now, it's time to design the bank deposit flow. Follow the steps below to create the integration.

1. Open the **Resource View** of the newly created API resource by clicking the `POST /deposit` resource under **Available resources** in the **Service Designer**.

    <a href="{{base_path}}/assets/img/develop/mi-for-vscode/qsg/get-resource.png"><img src="{{base_path}}/assets/img/develop/mi-for-vscode/qsg/get-resource.png" alt="Add new connection" width="80%"></a>

2. After opening the **Resource View**, click on the **Start** node on the canvas to set an input payload for the integration flow.

    !!! Note
        Setting an input payload for the integration flow is not mandatory. However, it is recommended, as it will be used to enable expression suggestions and support the Mediator TryOut features, which you will explore in later steps of this tutorial.

3. Click **Add Request**, provide the following details, and then click **Add** to add each of the input payloads. Once both requests are added, click **Save**.

    | Name            | Request body                   |
    |-----------------|--------------------------------|
    | `sample1` | `{ "currency":"USD", "amount":100 }` |
    | `sample2` | `{ "currency":"EUR", "amount":50 }`  |

3. Click on the **+** icon on the canvas to open the **Mediator Palette**.

    <a href="{{base_path}}/assets/img/develop/mi-for-vscode/qsg/open-palette.png"><img src="{{base_path}}/assets/img/develop/mi-for-vscode/qsg/open-palette.png" alt="Add new connection" width="80%"></a>

4. Under **Mediators**, select the **If Else** mediator.

    <a href="{{base_path}}/assets/img/develop/mi-for-vscode/qsg/add-get-operation.png"><img src="{{base_path}}/assets/img/develop/mi-for-vscode/qsg/add-get-operation.png" alt="Add new connection" width="80%"></a>

    We will use an expression to define the condition for the **If Else** mediator. This condition checks whether the currency is USD or not and then determines which flow to execute. If the currency is not USD, the flow will call a currency converter service. The expression used for this check is: `#!python payload.currency != 'USD'`.

    !!! Tip "What is an expression?"
        Expressions in WSO2 Micro Integrator (MI) allow you to dynamically access, evaluate, and manipulate message content during processing. To explore expressions in detail, see the [Expressions documentation]({{base_path}}/reference/mediators/about-mediators/).

4. In the **Add If Else Mediator** pane that appears, click on the Expression editor `<>` icon to open the editor.

    ```json
    {
        "currency":"USD",
        "amount":100
    }
    ```

5. Select **Payload** → **currency** to extract the currency attribute from the payload.

6. Next, type a space to display the list of operators. Select the `!=` (not equal) operator and enter `'USD'` to complete the condition.

7. Finally, click **Add** to insert the **If Else** mediator into the integration flow.

8. Click on the **+** icon in the **Else** branch on the canvas to open the **Mediator Palette**. This branch executes when the currency is `USD`.

9. Under **Mediators**, select the **Log** mediator.

10. Enter `No currency conversion is required.` as the message, then click **Add** to insert the **Log** mediator into the integration flow.

11. Click on the **+** icon in the **Then** branch on the canvas to open the **Mediator Palette**. This branch executes when the currency is **not** `USD`.

    To convert the amount from the given currency to USD, we need to call a currency converter service. You can use the following `Currency Converter` service as the backend.

    <table>
        <tr>
            <td>URL</td>
            <td>
                <code>https://apis.wso2.com/zvdz/mi-qsg/v1.0/currency-converter</code>
            </td>
        </tr>
        <tr>
            <td>HTTP Method</td>
            <td>
                <code>POST</code> 
            </td>
        </tr>
        <tr>
            <td>Request payload format</td>
            <td>
                <code>
                {
                    "currency" : "EUR",
                    "amount" : 50
                }
                </code> 
            </td>
        </tr>
    </table>

12. Search for `post` in the **Mediator Palette** to add the HTTP POST operation for currency conversion.

    <a href="{{base_path}}/assets/img/get-started/how-to-guides/ai-data-mapping/ai-data-mapping-http-get.png"><img src="{{base_path}}/assets/img/get-started/how-to-guides/ai-data-mapping/ai-data-mapping-http-get.png" alt="search get in palette" width="80%"></a>

13. Click **+ Add new connection** to create a new connection.

    <a href="{{base_path}}/assets/img/get-started/how-to-guides/ai-data-mapping/ai-data-mapping-new-http-conn.png"><img src="{{base_path}}/assets/img/get-started/how-to-guides/ai-data-mapping/ai-data-mapping-new-http-conn.png" alt="add new connection" width="80%"></a>

14. Select `HTTPS` and fill in the following details to create a connection to `Currency Converter` service. Finally, click **Add** in the **Add New Connection** form to create the connection.

    | Property            | Value                   |
    |---------------------|-------------------------|
    | **Connection Name** | `CurrencyConverter`        |
    | **Base URL**        | `https://apis.wso2.com/zvdz/mi-qsg/v1.0` |

    <a href="{{base_path}}/assets/img/get-started/how-to-guides/ai-data-mapping/ai-data-mapping-connection.png"><img src="{{base_path}}/assets/img/get-started/how-to-guides/ai-data-mapping/ai-data-mapping-connection.png" alt="create connection" width="80%"></a>

15. Provide `/currency-converter` as the **Relative Path**, and click **Submit** to insert the operation to the integration flow.

    <a href="{{base_path}}/assets/img/get-started/how-to-guides/ai-data-mapping/ai-data-mapping-geo-request.png"><img src="{{base_path}}/assets/img/get-started/how-to-guides/ai-data-mapping/ai-data-mapping-geo-request.png" alt="geo http request" width="30%"></a>

    !!! Tip
        Since we have completed most of the flow, let's verify everything up to this point. You can use the **Mediator TryOut** feature to execute the flow up to a specific mediator and inspect its input and output.  
        To explore this feature in detail, see the [Mediator TryOut documentation]({{base_path}}/reference/mediators/about-mediators/).

        1. Click on the **If Else** mediator, then go to the **TryOut** tab in the **Edit If Else Mediator** pane.
        <img src="{{base_path}}/assets/img/develop/mi-for-vscode/qsg/download-java-and-mi.png" alt="Download Java and MI" width="80%">

        2. Once the data is loaded, click **Run** to execute the flow through this mediator and review the output.
        If you expand the **Payload** section, you will see the following JSON.
        ```json
        {
            "currency":"USD",
            "amount":100
        }
        ```

        3. Now, change the request to `sample2` under **Select a request to try out**, then click **Run** to execute the flow.
        If you expand the **Payload** section, you will see the following JSON, which represents the converted amount received from the `Currency Converter` service.
        ```json
        {
            "currency":"USD",
            "amount":78
        }
        ```

    Now that we have the currency amount in USD, let's send a response to the client, mentioning the amount deposited into the bank account.

16. Click on the **+** icon just after the **If Else** mediator to open the **Mediator Palette**.

17. Select **Payload** mediator under **Mediators**.

18. In the **Payload** box, enter the following sample JSON object. We will use an inline expression to extract the amount from the existing payload and insert it into this sample JSON object in the next step.

    ```json
    {
        "status": "successful",
        "amountDeposited": 
    }
    ```

19. In the JSON object, place your cursor in the corresponding location (next to `"amountDeposited": `), click on the inline expression editor (<img src="{{base_path}}/assets/img/get-started/build-first-integration/inline_expression_icon.png" alt="inline expression editor" class="inline-icon">) icon, then select **Payload** → **amount**, and click **Add** to insert the inline expression into the JSON object.

    <a href="{{base_path}}/assets/img/get-started/build-first-integration/add_inline_expression.gif">
        <img src="{{base_path}}/assets/img/get-started/build-first-integration/add_inline_expression.gif" width="50%" alt="Add inline expression">
    </a>

20. Click on the **+** icon placed just after the Payload mediator to open the **Mediator Palette** to add a [Respond Mediator]({{base_path}}/reference/mediators/respond-mediator) to respond the message to the client.

11. Select **Respond** mediator under **Mediators**, and click **Add** to insert it to the integration flow.

You may refer to the following API and HTTP connection for reference,

??? "Weather API"

    !!! info
        You can view the source view by clicking on the **Show Source** (`</>`) icon located in the top right corner of the VS Code.

    === "Design View"
        <a href="{{base_path}}/assets/img/get-started/how-to-guides/ai-data-mapping/ai-data-mapping-api.png"><img src="{{base_path}}/assets/img/get-started/how-to-guides/ai-data-mapping/ai-data-mapping-api.png" alt="ai datamapping api" width="70%"></a>

    === "Source View"
        ```yaml
        <?xml version="1.0" encoding="UTF-8"?>
        <api context="/weather" name="Weather"
            xmlns="http://ws.apache.org/ns/synapse">
            <resource methods="GET" uri-template="/?city={city}">
                <inSequence>
                    <variable name="API_KEY" type="STRING" value="REPLACE_API_KEY"/>
                    <http.get configKey="OpenWeather">
                        <relativePath>/geo/1.0/direct?q=${params.queryParams.city}&amp;limit=1&amp;appid=${vars.API_KEY}</relativePath>
                        <headers>[]</headers>
                        <forceScAccepted>false</forceScAccepted>
                        <disableChunking>false</disableChunking>
                        <forceHttp10>false</forceHttp10>
                        <noKeepAlive>false</noKeepAlive>
                        <responseVariable>http_get_1</responseVariable>
                        <overwriteBody>true</overwriteBody>
                    </http.get>
                    <http.get configKey="OpenWeather">
                        <relativePath>/data/2.5/weather?lat=${payload[0].lat}&amp;lon=${payload[0].lon}&amp;appid=${vars.API_KEY}</relativePath>
                        <headers>[]</headers>
                        <forceScAccepted>false</forceScAccepted>
                        <disableChunking>false</disableChunking>
                        <forceHttp10>false</forceHttp10>
                        <noKeepAlive>false</noKeepAlive>
                        <responseVariable>http_get_2</responseVariable>
                        <overwriteBody>true</overwriteBody>
                    </http.get>
                    <datamapper config="resources:datamapper/weatherDataMapper/weatherDataMapper.dmc" inputSchema="resources:datamapper/weatherDataMapper/weatherDataMapper_inputSchema.json" outputSchema="resources:datamapper/weatherDataMapper/weatherDataMapper_outputSchema.json"/>
                    <respond/>
                </inSequence>
                <faultSequence></faultSequence>
            </resource>
        </api>
        ```

??? "HTTP Connection"

    !!! info
        You can view the source view by clicking on the **Show Source** (`</>`) icon located in the top right corner of the VS Code.

    === "Design View"
        <a href="{{base_path}}/assets/img/get-started/how-to-guides/ai-data-mapping/ai-data-mapping-http-connection.png"><img src="{{base_path}}/assets/img/get-started/how-to-guides/ai-data-mapping/ai-data-mapping-http-connection.png" alt="http connection config" width="40%"></a>
        
    === "Source View"
        ```yaml
        <?xml version="1.0" encoding="UTF-8"?>
        <localEntry key="OpenWeather" xmlns="http://ws.apache.org/ns/synapse">
            <http.init>
                <connectionType>HTTPS</connectionType>
                <baseUrl>https://api.openweathermap.org/</baseUrl>
                <authType>None</authType>
                <timeoutAction>Never</timeoutAction>
                <retryCount>0</retryCount>
                <retryDelay>0</retryDelay>
                <suspendInitialDuration>-1</suspendInitialDuration>
                <suspendProgressionFactor>1</suspendProgressionFactor>
                <name>OpenWeather</name>
            </http.init>
        </localEntry>
        ```

## Step 4 - Run the integration

Now that you have updated the integration, it's time to deploy the integration to the Micro Integrator server runtime.

Click the **Build and Run** icon located in the top right corner of VS Code.

<a href="{{base_path}}/assets/img/develop/mi-for-vscode/qsg/build-and-run-project.png"><img src="{{base_path}}/assets/img/develop/mi-for-vscode/qsg/build-and-run-project.png" alt="Build and run" width="80%"></a>

## Step 5 - Test the integration service

1. Once the **Runtime Services** interface is open, select the `BankAPI`, and click the **Try It** button.

2. Select the `/deposit` resource and click **Try it Out** to test the API.

    <a href="{{base_path}}/assets/img/get-started/how-to-guides/ai-code-gen/ai-code-gen-op-try.png"><img src="{{base_path}}/assets/img/get-started/how-to-guides/ai-code-gen/ai-code-gen-op-try.png" alt="try out operation" width="80%"></a>

3. Provide a JSON payload and click the **Execute** button to invoke the API. You may use the following sample payloads to test the API.

    1. Amount in US dollar (USD)

    ```json
    {
        "currency":"USD",
        "amount":456
    }
    ```

    2. Amount in Japanese yen (JPY)

    ```json
    {
        "currency":"JPY",
        "amount":897
    }
    ```

    <a href="{{base_path}}/assets/img/get-started/how-to-guides/ai-code-gen/ai-code-gen-swagger-exec.png"><img src="{{base_path}}/assets/img/get-started/how-to-guides/ai-code-gen/ai-code-gen-swagger-exec.png" alt="execute request" width="80%"></a>

4. Check the response received from the server and verify that the currency conversion has been applied correctly.

<a href="{{base_path}}/assets/img/develop/mi-for-vscode/qsg/test-api.gif">
<img src="{{base_path}}/assets/img/develop/mi-for-vscode/qsg/test-api.gif" alt="Test API" style="display: block; max-width: 80%; margin: 0 auto;">
</a>

Congratulations!
You have now learned how to create an API resource, use the HTTP connector, work with expressions, and test mediators using Mediator TryOut.

## What's Next?  

So far, you have learned how to route and transform the payload efficiently. Next, you'll explore how to connect to a SaaS service to send an email.

Click on the **Next** button below to continue to the next tutorial.

<div style="display: flex; justify-content: center; align-items: center; gap: 100px; margin-top: 20px;">
  <a href="{{base_path}}/get-started/build-first-integration/first-integration-api-service/" class="md-button">← Previous</a>
  <a href="{{base_path}}/get-started/build-first-integration/first-integration-connect-saas/" class="md-button md-button--primary">Next →</a>
</div>

{% raw %}
<!-- <style>
.n {
    color:rgb(108, 108, 108) !important;
}
.o {
    color: #ff7043 !important;
}
.s1 {
    color: #569CD6 !important;
}
</style> -->
{% endraw %}

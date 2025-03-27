# Connect to SaaS or B2B Systems

In the previous tutorial, you learned how to route and transform messages, deploy, and test integrations in WSO2 Micro Integrator (MI). In this tutorial, you’ll learn how to create a loan review email notification flow that sends an email based on the client's loan status.

## Prerequisites

1. You need Visual Studio Code (VS Code) with the <a target="_blank" href="https://marketplace.visualstudio.com/items?itemName=WSO2.micro-integrator">Micro Integrator for VS Code</a> extension installed.

    !!! Info
        See the [Install Micro Integrator for VS Code]({{base_path}}/develop/mi-for-vscode/install-wso2-mi-for-vscode/) documentation to learn how to install Micro Integrator for VS Code.

2. You must have completed the **Route and Transform messages** tutorial under **Build your first integration** before proceeding. Start the [Route and Transform messages]({{base_path}}/get-started/build-first-integration/first-integration-route-and-transform/) tutorial if you haven’t completed it yet.

Follow the instructions below to modify the API service so it sends an email to the client with the loan status.

## What you'll learn

- How to integrate and send emails using the Email connector.

## What you'll build

Let's consider a scenario where a client sends a loan request to the `Bank` API deployed in WSO2 Micro Integrator. Upon receiving the request, the API sends an email notification to the client indicating that the loan request has been received and is under review. This is done using a SaaS-based email service.

In this example, we use <a target="_blank" href="https://developers.google.com/gmail/imap/imap-smtp">Gmail's SMTP service</a> as the email provider.

<a href="{{base_path}}/assets/img/get-started/build-first-integration/what_you_will_build_saas.png"><img src="{{base_path}}/assets/img/get-started/build-first-integration/what_you_will_build_saas.png" alt="Create New Project" width="60%"></a>

Now, it's time to design the email notification flow. Follow the steps below to create the email notification integration.

## Step 1 - Create a new API resource

To develop the above scenario, let's get started with creating a new API resource in the `Bank` API.

1. Click on the Service Designer (<img src="{{base_path}}/assets/img/get-started/build-first-integration/service_designer_icon.png" alt="inline expression editor" class="inline-icon">) icon of the `Bank` API in the **Micro Integrator Project Explorer** to open the Service Designer.

    <a href="{{base_path}}/assets/img/get-started/build-first-integration/service_designer_icon_bank_api_3.png"><img src="{{base_path}}/assets/img/get-started/build-first-integration/service_designer_icon_bank_api_3.png" alt="Create New Project" width="80%"></a>

2. In the Service Designer, click the **+ Resource** button to add a new API resource.

    <a href="{{base_path}}/assets/img/get-started/build-first-integration/add_resource_btn_3.png"><img src="{{base_path}}/assets/img/get-started/build-first-integration/add_resource_btn_3.png" alt="Create New Project" width="80%"></a>

3. In the **Add API Resource** pane, set `/loan-review` as the **Resource Path** and select the `POST` method.

    <a href="{{base_path}}/assets/img/get-started/build-first-integration/add_api_resource_pane_loan_review_post.png"><img src="{{base_path}}/assets/img/get-started/build-first-integration/add_api_resource_pane_loan_review_post.png" alt="Create New Project" width="80%"></a>

4. Finally, click **Create** to add the new API resource.

## Step 2 - Design the integration

1. Open the **Resource View** of the newly created API resource by clicking the `POST /loan-review` resource under **Available resources** in the **Service Designer**.

    <a href="{{base_path}}/assets/img/get-started/build-first-integration/select_loan_review_post_resource.png"><img src="{{base_path}}/assets/img/get-started/build-first-integration/select_loan_review_post_resource.png" alt="Create New Project" width="80%"></a>

2. After opening the **Resource View**, click on the **Start** node on the canvas to set an input payload for the integration flow.

    !!! Note
        Setting an input payload for the integration flow is not mandatory. However, it is recommended, as it will be used to enable expression suggestions, which you will explore in later steps of this tutorial.

    <a href="{{base_path}}/assets/img/get-started/build-first-integration/click_start_node_3.png"><img src="{{base_path}}/assets/img/get-started/build-first-integration/click_start_node_3.png" alt="Create New Project" width="80%"></a>

3. TODO: Click **Add Request**, provide the following details, and then click **Add** and Finally, click **Save**.

    | Name            | Request body                   |
    |-----------------|--------------------------------|
    | `sample1` | `{ "currency":"USD", "amount":100 }` |

    <a href="{{base_path}}/assets/img/get-started/build-first-integration/add_start_payload.gif"><img src="{{base_path}}/assets/img/get-started/build-first-integration/add_start_payload.gif" alt="Create New Project" width="80%"></a>

4. Click on the **+** icon on the canvas to open the **Mediator Palette**.

    <a href="{{base_path}}/assets/img/get-started/build-first-integration/add_new_mediator_loan_review_1.png"><img src="{{base_path}}/assets/img/get-started/build-first-integration/add_new_mediator_loan_review_1.png" alt="Create New Project" width="80%"></a>

5. Select **Variable** mediator under **Mediators**.

5. Click on the **+** icon just after the **Payload** mediator to open the **Mediator Palette**.

2. Search for `email` in the **Mediator Palette**, then click the download (<img src="{{base_path}}/assets/img/get-started/build-first-integration/connector_download_icon.png" alt="inline expression editor" class="inline-icon">) icon to add the [email connector]() to the project. In the confirmation pane, select **Yes** to add the required dependencies.

    !!! Tip "What is a connector?"
        Connectors in WSO2 Micro Integrator (MI) enable seamless integration with external systems, cloud platforms, and messaging services without the need for custom implementations. They provide a standardized way to send, receive, and process data from third-party applications like Salesforce, Kafka, and AWS services. To explore connectors in detail, see the [Connector documentation]({{base_path}}/reference/connectors/connectors-overview/).

    <a href="{{base_path}}/assets/img/develop/mi-for-vscode/qsg/get-resource.png"><img src="{{base_path}}/assets/img/develop/mi-for-vscode/qsg/get-resource.png" alt="Add new connection" width="80%"></a>

2. Once the connector is downloaded, select the `Send` operation from the **Mediator Palette**.

3. Click **+ Add new connection** to create a new connection.

    <a href="{{base_path}}/assets/img/develop/mi-for-vscode/qsg/open-palette.png"><img src="{{base_path}}/assets/img/develop/mi-for-vscode/qsg/open-palette.png" alt="Add new connection" width="80%"></a>

4. Select `SMTP` and fill in the following details to create a connection to Gmail's SMTP service. Finally, click **Add** in the **Add New Connection** form to create the connection.

    !!! Tip
        If two-factor authentication is enabled, you need to obtain an app password by following the instructions <a target="_blank" href="https://support.google.com/accounts/answer/185833?hl=en">here</a>.

    | Property            | Value                   |
    |---------------------|-------------------------|
    | **Connection Name** | `GmailConnection`        |
    | **Host**        | `smtp.gmail.com` |
    | **Port**        | `465` |
    | **Username**        | Your email address |
    | **Password**        | Your email password or app password|

    <a href="{{base_path}}/assets/img/get-started/how-to-guides/ai-data-mapping/ai-data-mapping-connection.png"><img src="{{base_path}}/assets/img/get-started/how-to-guides/ai-data-mapping/ai-data-mapping-connection.png" alt="create connection" width="80%"></a>

5. After creating the connection, enter the following details in the **Add Send** form to compose the email.

    | Property            | Value                   |
    |---------------------|-------------------------|
    | **To** | Some email address        |
    | **Subject**        | `Bank Deposit Status` |
    | **Content**        | `${payload}` |

6. Finally, click **Submit** to add the email operation to the integration flow.

You have successfully updated the integration flow to send an email with the deposit status. For reference, you can check the following API, HTTP connection, and Email connection.

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

??? "Email Connection"

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

## Step 2 - Run the integration

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

4. Check the response received from the server and confirm that the bank deposit status has been successfully sent to the email address.

Congratulations!
You have now learned how to integrate with an email SaaS provider using connectors to send emails as part of your integration flow.

## What's Next?  

So far, you have learned how to route and transform payloads efficiently and integrate with an email SaaS provider using connectors. Next, you'll explore how to monitor and manage your integrations using the Integration Control Plane (ICP).

Click on the **Next** button below to continue to the next tutorial.

<div style="display: flex; justify-content: center; align-items: center; gap: 100px; margin-top: 20px;">
  <a href="{{base_path}}/get-started/build-first-integration/first-integration-route-and-transform/" class="md-button">← Previous</a>
  <a href="{{base_path}}/get-started/build-first-integration/first-integration-monitor-icp/" class="md-button md-button--primary">Next →</a>
</div>

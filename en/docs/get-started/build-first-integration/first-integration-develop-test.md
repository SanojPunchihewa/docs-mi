# Implement Unit Tests

In the previous tutorial, you learned how to route and transform messages, connect to a SaaS provider, deploy, and manually test integrations in WSO2 MI. Now, let's implement unit tests to automate testing and ensure the reliability and correctness of your integration.

## Prerequisites

1. You need Visual Studio Code (VS Code) with the <a target="_blank" href="https://marketplace.visualstudio.com/items?itemName=WSO2.micro-integrator">Micro Integrator for VS Code</a> extension installed.

    !!! Info
        See the [Install Micro Integrator for VS Code]({{base_path}}/develop/mi-for-vscode/install-wso2-mi-for-vscode/) documentation to learn how to install Micro Integrator for VS Code.

2. You must have completed the **Connect to SaaS or B2B Systems** tutorial under **Build your first integration** before proceeding. Start the [Connect to SaaS or B2B Systems]() tutorial if you haven’t completed it yet.

Follow the instructions below to implement unit tests for the `Bank` API and validate its functionality.

## What you'll learn

- How to implement unit tests for your integration.
- How to create and use a mock service for testing.

## What you'll build

In this tutorial, you will create unit tests for the `Bank` API to ensure its functionality and reliability. You will also learn how to set up and use a mock service to simulate backend responses, enabling effective testing without external dependencies.

## Step 1 - Design the integration

Now, it's time to design the email notification flow. Follow the steps below to create the email notification integration. Since we will be updating the integration from the [Route and Transform Messages]() tutorial, make sure you have it open in VS Code.

1. Click on the **+** icon just after the **Payload** mediator to open the **Mediator Palette**.

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
    | **To** | `GmailConnection`        |
    | **Subject**        | `smtp.gmail.com` |
    | **Content**        | `465` |

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

## Step 3 - Test the integration service

Select `BankAPI` that you have developed and test the resource.

<a href="{{base_path}}/assets/img/develop/mi-for-vscode/qsg/test-api.gif">
<img src="{{base_path}}/assets/img/develop/mi-for-vscode/qsg/test-api.gif" alt="Test API" style="display: block; max-width: 80%; margin: 0 auto;">
</a>

Congratulations!
You have now learned how to integrate with an email SaaS provider using connectors to send emails as part of your integration flow.

## What's Next?  

So far, you have learned how to route and transform the payload efficiently and integrate with an email SaaS provider using connectors. Next, you'll explore how to write unit tests for your integration to ensure its reliability and correctness.  

Click on the **Next** button below to continue to the next tutorial.

<div style="display: flex; justify-content: center; align-items: center; gap: 100px; margin-top: 20px;">
  <a href="{{base_path}}/get-started/build-first-integration/first-integration-connect-saas/" class="md-button">← Previous</a>
  <a href="{{base_path}}/get-started/build-first-integration/first-integration-monitor-icp/" class="md-button md-button--primary">Next →</a>
</div>

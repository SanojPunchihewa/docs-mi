# Automations

## Introduction

In addition to traditional API-based and event-driven integrations, WSO2 Micro Integrator supports automation flows that can be triggered on a schedule or at server startup.

In this tutorial, you’ll learn how to create and configure automations using **Scheduled Triggers** (Task) to run integration logic without external requests or events.

!!! tip "New to WSO2 Micro Integrator?"
    If you're just getting started, we recommend completing the [Build your first Integration]({{base_path}}/get-started/build-first-integration/) tutorial first. It will help you understand key integration concepts and get familiar with the developer tool features before diving into automation flows.

## Prerequisites

You need Visual Studio Code (VS Code) with the <a target="_blank" href="https://marketplace.visualstudio.com/items?itemName=WSO2.micro-integrator">Micro Integrator for VS Code</a> extension installed. The MI for VS Code extension is the official developer tool for designing, developing, and testing integration solutions with WSO2 Micro Integrator.

!!! Info
    See the [Install Micro Integrator for VS Code]({{base_path}}/develop/mi-for-vscode/install-wso2-mi-for-vscode/) documentation to learn how to install Micro Integrator for VS Code.

## What you’ll learn

By following this tutorial, you will gain hands-on experience in:

- Creating a Scheduled Trigger (Task) in WSO2 Micro Integrator.
- Connecting to a MySQL database using the Database connector.
- Querying and aggregating data from a database.
- Generating a daily transaction summary as a JSON payload.

## What you'll build

Let’s try a simple scenario where WSO2 Micro Integrator uses a Scheduled Trigger to run a flow that connects to a MySQL database, aggregates the daily transaction data, and generates a summary report. This demonstrates how you can build time-based, automated integrations without requiring any external API calls or events.

<a href="{{base_path}}/assets/img/get-started/automation/what_you_will_build_automation.png"><img src="{{base_path}}/assets/img/get-started/automation/what_you_will_build_automation.png" alt="Create New Project" width="40%"></a>

## Step 1 - Setup MySQL

!!! Note "Already have MySQL running?"
    If MySQL is already installed and running in your environment (locally or remotely), you can skip the installation step and continue from [Create the tables](#create-the-tables).

To build the scheduled integration, you'll first need a **MySQL database** running. WSO2 Micro Integrator will connect to this database to query daily transaction data and generate a summary.

In this tutorial, we use the official <a target="_blank" href="https://hub.docker.com/layers/library/mysql/9.2.0/images/sha256-2b1e754b51504235d37ef7926031d6c0b93c53bff82e49fa1b19b9890541834b">MySQL v9.2.0 Docker image</a>.

### Prerequisites

- <a target="_blank" href="https://docs.docker.com/get-docker/">Docker</a> installed and running.

### Start MySQL using Docker

Open a command line prompt on your machine and run the following command. This will pull the official MySQL image (if not already cached) and start the MySQL server.

!!! Info
    The following command runs a temporary MySQL container named `mysql` with port `3306` exposed. It sets the root password to `root` and automatically creates a database named `bank`. The container will be removed once stopped (`--rm`).

    The `-e` flag is used to set environment variables inside the container:

    - `MYSQL_ROOT_PASSWORD=root`: Sets the root password for MySQL.

    - `MYSQL_DATABASE=bank`: Automatically creates a database named `bank` at startup.

```bash
docker run --rm --name mysql -e MYSQL_ROOT_PASSWORD=root -e MYSQL_DATABASE=bank -p 3306:3306 mysql:9.2.0
```

You should see a message like `MySQL Server - start` indicating that MySQL is up and running.

### Create the tables

In this tutorial, we’ll create a table named `transactions`, which will store daily deposit and withdrawal records.

!!! Note
    If you're using your own local or remote MySQL instance, use the appropriate commands that match your environment.

1. Open a new command line prompt on your machine and run the following command to access the MySQL server. Enter `root` as the password when prompted.

    ```bash
    docker exec -it mysql mysql -u root -p
    ```
 
2. Once inside the MySQL shell, switch to the `bank` database.

    ```sql
    USE bank;
    ```

3. Create the `transactions` table.

    ```sql
    CREATE TABLE transactions (
      id VARCHAR(10) PRIMARY KEY,
      accountId VARCHAR(20),
      type VARCHAR(20),
      amount DECIMAL(10,2),
      date DATE
    );
    ```

4. Insert some sample data.

    ```sql
    INSERT INTO transactions VALUES
    ('TXN001', 'ACC123', 'deposit', 500.00, CURDATE()),
    ('TXN002', 'ACC123', 'withdrawal', 200.00, CURDATE()),
    ('TXN003', 'ACC456', 'deposit', 1200.00, CURDATE());
    ```

    Once the data is inserted, you can type `exit;` to leave the MySQL shell. You're now ready to build the scheduled integration to summarize this data using WSO2 Micro Integrator.

## Step 2 - Create a new integration project

To develop the above scenario, let's get started with creating an integration project in the Micro Integrator extension installed VS Code.

1. Launch VS Code with the Micro Integrator extension installed.

2. Click on the Micro Integrator icon on the Activity Bar of the VS Code editor.

    <a href="{{base_path}}/assets/img/develop/mi-for-vscode/mi-vscode-extension.png"><img src="{{base_path}}/assets/img/develop/mi-for-vscode/mi-vscode-extension.png" alt="MI VS Code Extension" width="80%"></a>

3. Click **Create New Project** on **Design View**. For more options for creating a new integration project, see [Create an Integration Project]({{base_path}}/develop/create-integration-project).

    <a href="{{base_path}}/assets/img/get-started/build-first-integration/create_new_project_btn.png"><img src="{{base_path}}/assets/img/get-started/build-first-integration/create_new_project_btn.png" alt="Create New Project" width="80%"></a>

4. In the **Project Creation Form**, enter `ScheduledIntegration` as the **Project Name**.

5. Ensure `4.4.0` is selected as the **Micro Integrator runtime version**.

6. Provide a location for the integration project under **Project Directory**.

    <a href="{{base_path}}/assets/img/get-started/event-integration/create_new_event_integration_project.png"><img src="{{base_path}}/assets/img/get-started/event-integration/create_new_event_integration_project.png" alt="Create New Project" width="80%"></a>

7. Click **Create**.

   Once you click **Create**, the **Add Artifact** pane will be opened.

!!! note
    You need the following to work with the MI for VS Code extension.

    - Java Development Kit (JDK) version 21
    - WSO2 Micro Integrator (MI) 4.4.0 runtime

    If you don't have them installed on your local machine, these will be automatically prompted for downloading and configured by the Micro Integrator for VS Code extension during the project creation step:

    1. Click **Download Java & MI** to download and set up Java and MI runtime.

        <a href="{{base_path}}/assets/img/develop/mi-for-vscode/qsg/download-java-and-mi.png"><img src="{{base_path}}/assets/img/develop/mi-for-vscode/qsg/download-java-and-mi.png" alt="Download Java and MI" width="80%"></a>

        !!! info
            If a different JDK or WSO2 MI version is installed on your local machine, you'll be prompted to download the required versions. 

            1. Click **Download** to install the required JDK or/and MI version(s).
            2. Once the download is complete, configure the Java Home or/and MI Home paths by clicking **Select Java Home** or/and **Select MI Path**, respectively.

            If the required JDK and WSO2 MI versions are already installed, you can directly configure the Java Home and MI Home paths in this step by clicking **Select Java Home** and **Select MI Path**, respectively.

        Once the process is complete, a window reload will be required, and you will be prompted with the following message:

        <a href="{{base_path}}/assets/img/develop/mi-for-vscode/qsg/reload-window.png"><img src="{{base_path}}/assets/img/develop/mi-for-vscode/qsg/reload-window.png" alt="Reload Window" width="80%"></a>

    2. Click **Reload Window**.

## Step 3 - Create a scheduled trigger

Now that the integration project is ready, let's create a scheduled trigger (task).

1. In the **Add Artifact** interface, under **Create an Integration**, click **Automation**. This will open the **Automation Form**.

    <a href="{{base_path}}/assets/img/get-started/event-integration/select_event_integration.png"><img src="{{base_path}}/assets/img/get-started/event-integration/select_event_integration.png" alt="Create New Project" width="80%"></a>

2. Enter `DailyReportTrigger` as the **Task Name** and `30` as the **Interval**.

    !!! Note  
        In this tutorial, we use a 30 second interval to demonstrate the use case. To run the automation daily at a specific time, you can define a [Cron expression]().

    <a href="{{base_path}}/assets/img/get-started/event-integration/configure_kafka_listener.png"><img src="{{base_path}}/assets/img/get-started/event-integration/configure_kafka_listener.png" alt="Create New Project" width="80%"></a>

4. Finally, click **Create** to add the scheduled trigger to your integration project.

## Step 4 - Design the integration

Now it's time to design your integration. This defines the underlying logic that will be executed when a Kafka message is received. In this scenario, the message needs to be transformed and then published to another Kafka topic. Follow the steps below to complete the integration flow.

1. Click on the **Start** node on the canvas to set an input payload for the integration flow.

    !!! Note
        Setting an input payload for the integration flow is not mandatory. However, it is recommended, as it will be used to enable expression suggestions, which you will explore in later steps of this tutorial.

    <a href="{{base_path}}/assets/img/get-started/event-integration/click_start_node_event.png"><img src="{{base_path}}/assets/img/get-started/event-integration/click_start_node_event.png" alt="Create New Project" width="80%"></a>

2. Click **Add Request**, provide the following JSON payload, then click **Add**. Finally, click **Save** to complete the input payload setup.

    ```json
    {
        "id":"TXN001",
        "type":"deposit",
        "accountId":"ACC123",
        "amount":500
    }
    ```

    <a href="{{base_path}}/assets/img/get-started/event-integration/add_start_payload_kafka_event.gif"><img src="{{base_path}}/assets/img/get-started/event-integration/add_start_payload_kafka_event.gif" alt="Create New Project" width="80%"></a>

3. Click on the **+** icon on the canvas to open the **Mediator Palette**.

    <a href="{{base_path}}/assets/img/get-started/event-integration/add_first_mediator.png"><img src="{{base_path}}/assets/img/get-started/event-integration/add_first_mediator.png" alt="Create New Project" width="80%"></a>

    Since this is an event-driven integration, we’ll log the incoming message to ensure that events are being received by the Micro Integrator.

4. Under **Mediators**, select the **Log** mediator.

    !!! Tip  
        You can use the **Log** mediator to print the message content to the server logs. This is helpful for checking what data is being received and for debugging during development.

    <a href="{{base_path}}/assets/img/get-started/event-integration/select_log_mediator.png"><img src="{{base_path}}/assets/img/get-started/event-integration/select_log_mediator.png" alt="Create New Project" width="80%"></a>

5. We will use the following template to log the message. It will log the incoming message payload along with the text `Kafka event received`. You can either copy and paste the template or use the inline expression editor to construct it.

    ```text
    Kafka event received, data = ${payload}
    ```

    <a href="{{base_path}}/assets/img/get-started/event-integration/add_inline_log_message.gif"><img src="{{base_path}}/assets/img/get-started/event-integration/add_inline_log_message.gif" alt="Create New Project" width="50%"></a>

6. Click **Add** to insert the **Log** mediator into the integration flow.

7. Click on the **+** icon located just after the **Log** mediator to open the **Mediator Palette** to add a [Payload mediator]({{base_path}}/reference/mediators/payloadfactory-mediator/) to transform the Kafka message before publishing the result to the `bank-audit` topic.

8. Under **Mediators**, select the **Payload** mediator.

    <a href="{{base_path}}/assets/img/get-started/event-integration/select_payload_mediator.png"><img src="{{base_path}}/assets/img/get-started/event-integration/select_payload_mediator.png" alt="Create New Project" width="80%"></a>

9. In the **Payload** box, enter the following sample JSON object. In the next step, we will use an inline expression to extract the JSON payload from the Kafka message and insert it into this template.

    ```json
    {
        "eventType": "transaction",
        "source": "bank-transactions",
        "data": 
    }
    ```

10. In the JSON object, place your cursor next to `"data": `, then click on the inline expression editor (<img src="{{base_path}}/assets/img/get-started/build-first-integration/inline_expression_icon.png" alt="inline expression editor" class="inline-icon">) icon. From the editor, select **Payload** → **payload**, and click **Add** to insert the inline expression into the JSON object.

    <a href="{{base_path}}/assets/img/get-started/event-integration/add_inline_expression_payload.gif">
        <img src="{{base_path}}/assets/img/get-started/event-integration/add_inline_expression_payload.gif" width="50%" alt="Add inline expression">
    </a>

11. Finally, click **Add** to insert the **Payload** mediator into the integration flow.

12. Click on the **+** icon just after the **Payload** mediator to open the **Mediator Palette**.

    <a href="{{base_path}}/assets/img/get-started/event-integration/add_mediator_after_payload.png"><img src="{{base_path}}/assets/img/get-started/event-integration/add_mediator_after_payload.png" alt="Create New Project" width="80%"></a>

    We will use the Kafka connector to publish the transformed message to the `bank-audit` topic in the next steps.

5. Search for `kafka` in the **Mediator Palette**, then click the download (<img src="{{base_path}}/assets/img/get-started/build-first-integration/connector_download_icon.png" alt="inline expression editor" class="inline-icon">) icon to add the [Kafka connector]({{base_path}}/reference/connectors/kafka-connector/kafka-connector-overview/) to the project. In the confirmation pane, select **Yes** to add the required dependencies.

    <a href="{{base_path}}/assets/img/get-started/event-integration/select_kafka_connector.png"><img src="{{base_path}}/assets/img/get-started/event-integration/select_kafka_connector.png" alt="Create New Project" width="80%"></a>

6. Once the connector is downloaded, select the `PublishMessages` operation from the **Mediator Palette**.

    <a href="{{base_path}}/assets/img/get-started/event-integration/select_publish_message.png"><img src="{{base_path}}/assets/img/get-started/event-integration/select_publish_message.png" alt="Create New Project" width="80%"></a>

14. Click **+ Add new connection** to create a new connection.

    <a href="{{base_path}}/assets/img/get-started/event-integration/kafka_add_new_connection_btn.png"><img src="{{base_path}}/assets/img/get-started/event-integration/kafka_add_new_connection_btn.png" alt="Create New Project" width="80%"></a>

15. Select `KAFKA` and fill in the following details to create a connection to the Kafka broker. Finally, click **Add** in the **Add New Connection** form to complete the connection setup.

    | Property            | Value                   |
    |---------------------|-------------------------|
    | **Connection Name** | `KafkaConnection`        |
    | **Bootstrap Servers**        | `localhost:9092` |
    | **Key Serializer Class** | `org.apache.kafka.common.serialization.StringSerializer` |
    | **Value Serializer Class** | `org.apache.kafka.common.serialization.StringSerializer` |

    !!! Note  
        1. In this tutorial, we will use the local Kafka broker configured in [Step 1 - Setup Kafka](#step-1-setup-kafka). If you plan to use a different Kafka broker, update the **Bootstrap Servers** field accordingly.
        2. We will use the default values for the remaining fields. You may refer to the [Kafka connector]({{base_path}}/reference/connectors/kafka-connector/kafka-connector-config/) documentation and update them if needed.

    <a href="{{base_path}}/assets/img/get-started/event-integration/kafka_create_new_connection.png"><img src="{{base_path}}/assets/img/get-started/event-integration/kafka_create_new_connection.png" alt="Create New Project" width="80%"></a>

16. Fill in the following details in the **Add PublishMessages** pane, then click **Submit** to add the operation to the integration flow.

    | Property            | Value                   |
    |---------------------|-------------------------|
    | **Topic** | `bank-audit`        |
    | **Partition Number**        | `1` |
    | **Content-Type** | `application/json` |

    <a href="{{base_path}}/assets/img/get-started/event-integration/kafka_set_publish_params.png"><img src="{{base_path}}/assets/img/get-started/event-integration/kafka_set_publish_params.png" alt="Create New Project" width="30%"></a>

You have successfully completed the integration flow to listen to Kafka events and publish the transformed message to another Kafka topic. For reference, you can review the configured event listener, sequence and Kafka connection.

??? "BankTransactionListener"

    !!! info
        You can view the source view by clicking on the **Show Source** (`</>`) icon located in the top right corner of the VS Code.

    === "Design View"
        <a href="{{base_path}}/assets/img/get-started/event-integration/bank_transaction_listener_config.png"><img src="{{base_path}}/assets/img/get-started/event-integration/bank_transaction_listener_config.png" alt="Create New Project" width="40%"></a>

    === "Source View"
        ```yaml
        <?xml version="1.0" encoding="UTF-8"?>
        <inboundEndpoint name="BankTransactionListener" class="org.wso2.carbon.inbound.kafka.KafkaMessageConsumer" sequence="BankTransactionListener-inboundSequence" onError="BankTransactionListener-inboundErrorSequence" suspend="false">
            <parameters xmlns="http://ws.apache.org/ns/synapse">
                <parameter name="generateSequences">true</parameter>
                <parameter name="interval">100</parameter>
                <parameter name="sequential">true</parameter>
                <parameter name="coordination">true</parameter>
                <parameter name="bootstrap.servers">localhost:9092</parameter>
                <parameter name="topic.name">bank-transactions</parameter>
                <parameter name="group.id">group1</parameter>
                <parameter name="contentType">application/json</parameter>
                <parameter name="poll.timeout">1000</parameter>
                <parameter name="key.deserializer">org.apache.kafka.common.serialization.StringDeserializer</parameter>
                <parameter name="value.deserializer">org.apache.kafka.common.serialization.StringDeserializer</parameter>
                <parameter name="enable.auto.commit">true</parameter>
                <parameter name="auto.commit.interval.ms">5000</parameter>
                <parameter name="auto.offset.reset">latest</parameter>
                <parameter name="exclude.internal.topics">true</parameter>
                <parameter name="check.crcs">true</parameter>
                <parameter name="partition.assignment.strategy">org.apache.kafka.clients.consumer.RangeAssignor</parameter>
                <parameter name="max.poll.interval.ms">300000</parameter>
                <parameter name="max.poll.records">500</parameter>
                <parameter name="fetch.max.wait.ms">500</parameter>
                <parameter name="receive.buffer.bytes">65536</parameter>
                <parameter name="send.buffer.bytes">131072</parameter>
                <parameter name="request.timeout.ms">305000</parameter>
                <parameter name="reconnect.backoff.ms">50</parameter>
                <parameter name="retry.backoff.ms">100</parameter>
                <parameter name="connections.max.idle.ms">540000</parameter>
                <parameter name="security.protocol">PLAINTEXT</parameter>
                <parameter name="metrics.num.samples">2</parameter>
                <parameter name="metrics.recording.level">INFO</parameter>
                <parameter name="metrics.sample.window.ms">30000</parameter>
            </parameters>
        </inboundEndpoint>
        ```

??? "BankTransactionListener-inboundSequence"

    !!! info
        You can view the source view by clicking on the **Show Source** (`</>`) icon located in the top right corner of the VS Code.

    === "Design View"
        <a href="{{base_path}}/assets/img/get-started/event-integration/kafka_in_sequence_config.png"><img src="{{base_path}}/assets/img/get-started/event-integration/kafka_in_sequence_config.png" alt="ai datamapping api" width="70%"></a>

    === "Source View"
        ```yaml
        <?xml version="1.0" encoding="UTF-8"?>
        <sequence name="BankTransactionListener-inboundSequence" trace="disable" xmlns="http://ws.apache.org/ns/synapse">
            <log category="INFO" logMessageID="false" logFullPayload="false">
                <message>Kafka event received, data = ${payload}</message>
            </log>
            <payloadFactory media-type="json" template-type="default">
                <format>{
                    "eventType": "transaction",
                    "source": "bank-transactions",
                    "data": ${payload}
                    }
                </format>
            </payloadFactory>
            <kafkaTransport.publishMessages configKey="KafkaConnection">
                <topic>bank-audit</topic>
                <partitionNo>1</partitionNo>
                <contentType>application/json</contentType>
                <key></key>
                <keySchema></keySchema>
                <keySchemaId></keySchemaId>
                <valueSchema></valueSchema>
                <valueSchemaId></valueSchemaId>
                <keySchemaSubject></keySchemaSubject>
                <keySchemaVersion></keySchemaVersion>
                <keySchemaSoftDeleted>false</keySchemaSoftDeleted>
                <valueSchemaSubject></valueSchemaSubject>
                <valueSchemaVersion></valueSchemaVersion>
                <valueSchemaSoftDeleted>false</valueSchemaSoftDeleted>
                <value></value>
            </kafkaTransport.publishMessages>
        </sequence>
        ```

??? "Kafka Connection"

    !!! info
        You can view the source view by clicking on the **Show Source** (`</>`) icon located in the top right corner of the VS Code.

    === "Design View"
        <a href="{{base_path}}/assets/img/get-started/event-integration/kafka_connection_config.png"><img src="{{base_path}}/assets/img/get-started/event-integration/kafka_connection_config.png" alt="ai datamapping api" width="40%"></a>
        
    === "Source View"
        ```yaml
        <?xml version="1.0" encoding="UTF-8"?>
        <localEntry key="KafkaConnection" xmlns="http://ws.apache.org/ns/synapse">
            <kafkaTransport.init>
                <connectionType>KAFKA</connectionType>
                <bootstrapServers>localhost:9092</bootstrapServers>
                <keySerializerClass>org.apache.kafka.common.serialization.StringSerializer</keySerializerClass>
                <valueSerializerClass>org.apache.kafka.common.serialization.StringSerializer</valueSerializerClass>
                <poolingEnabled>false</poolingEnabled>
                <name>KafkaConnection</name>
            </kafkaTransport.init>
        </localEntry>
        ```

## Step 5 - Run the integration

Now that you have completed the integration, it's time to deploy it to the Micro Integrator server runtime.

Click the **Build and Run** icon located in the top right corner of VS Code.

<a href="{{base_path}}/assets/img/get-started/event-integration/build_and_run_btn.png"><img src="{{base_path}}/assets/img/get-started/event-integration/build_and_run_btn.png" alt="ai datamapping api" width="80%"></a>

## Step 6 - Test the integration

Once the Micro Integrator runtime is up and running, follow the steps below to publish a message and verify the integration.

1. Open a new command line prompt on your machine and run the following command to tail the logs for the `bank-audit` topic. The Micro Integrator will publish the transformed messages to this topic.

    ```bash
    docker exec -it kafka /opt/kafka/bin/kafka-console-consumer.sh --bootstrap-server localhost:9092 --topic bank-audit --from-beginning
    ```

2. Open another command line prompt and run the following command to launch the Kafka producer and publish a message to the `bank-transactions` topic.

    ```bash
    docker exec -it kafka /opt/kafka/bin/kafka-console-producer.sh --broker-list localhost:9092 --topic bank-transactions
    ```

    After the producer starts, you'll see a `>` prompt. Any line of text you type after that will be sent to the Kafka topic when you press `Enter`.

3. Copy and paste the following JSON payload and press `Enter` to publish the message to the topic.

    ```json
    { "id":"TXN011", "type":"withdraw", "accountId":"ACC456", "amount":1500 }
    ```

    You won’t see any confirmation, but the message is now sent to the `bank-transactions` topic.

4. Check the logs of the Micro Integrator runtime in **VS Code**. You should see a log entry similar to the following.

    ```bash
    [2025-04-03 09:49:23,029]  INFO {LogMediator} - Kafka event received, data = {"id":"TXN011","type":"withdraw","accountId":"ACC456","amount":1500}
    ```

5. Verify that the command line prompt monitoring the `bank-audit` topic now displays a new entry with the transformed message.

Congratulations! You’ve now learned how to create an event-driven integration using Kafka and apply message transformation using WSO2 Micro Integrator. This is a powerful pattern for building scalable, real-time systems.

## What's Next?

Now that you’ve built your first event-driven flow, you can explore how to improve the integration by,

- Connecting to [SaaS platforms]({{base_path}}/learn/integration-use-case/connectors/) (e.g., sending notifications via email).
- Integrating with external systems like [databases]({{base_path}}/learn/integration-use-case/data-integration-overview/) or [Backend services]({{base_path}}/learn/integration-tutorials/exposing-several-services-as-a-single-service/).
- [Routing]({{base_path}}/learn/integration-use-case/message-routing-overview/) events based on custom logic or content.
- [Enriching messages]({{base_path}}/learn/integration-tutorials/transforming-message-content/) with additional data before forwarding.

{% raw %}
<style>
.language-bash {
    color: var(--md-feedback-button-color) !important;
}
.language-bash .hljs-string, .language-bash .hljs-keyword {
    color: var(--md-feedback-button-color) !important;
}
.language-bash .hljs-variable {
    font-weight: 600;
    color: rgb(45, 116, 215) !important;
}
</style>
{% endraw %}

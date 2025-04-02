# Event-driven Integrations

## Introduction

In addition to traditional API-based integrations, modern systems often need to respond to **asynchronous events** from external systems such as message brokers and event buses. WSO2 Micro Integrator (MI) allows you to build **event-driven integrations** that react to incoming events, transform data, and publish messages in real time.

In this tutorial, you'll learn how to use [Kafka](https://kafka.apache.org/) with MI to build a message-driven integration that listens to a Kafka topic, transforms the received data, and optionally publishes the result to another topic.

## Prerequisites

You need Visual Studio Code (VS Code) with the <a target="_blank" href="https://marketplace.visualstudio.com/items?itemName=WSO2.micro-integrator">Micro Integrator for VS Code</a> extension installed. The MI for VS Code extension is the official developer tool for designing, developing, and testing integration solutions with WSO2 Micro Integrator.

!!! Info
    See the [Install Micro Integrator for VS Code]({{base_path}}/develop/mi-for-vscode/install-wso2-mi-for-vscode/) documentation to learn how to install Micro Integrator for VS Code.

## What you’ll learn

By following this tutorial, you will gain hands-on experience in:

- Setting up a Kafka Listener in WSO2 MI.
- Consuming and processing events from a Kafka topic.
- Transforming incoming messages using the Payload mediator.
- Publishing transformed messages to another Kafka topic using the Kafka connector.

## What you'll build

Let’s try a simple scenario where WSO2 Micro Integrator listens to a Kafka topic named `bank-transactions`, transforms each incoming bank transaction event, and publishes the normalized message to another topic called `bank-audit`. This demonstrates how you can build real-time, event-driven integrations without using any APIs.

<a href="{{base_path}}/assets/img/get-started/build-first-integration/what_you_will_build_greeting.png"><img src="{{base_path}}/assets/img/get-started/build-first-integration/what_you_will_build_greeting.png" alt="Create New Project" width="40%"></a>

## Step 1 - Create a new integration project

To develop the above scenario, let's get started with creating an integration project in the Micro Integrator extension installed VS Code.

1. Launch VS Code with the Micro Integrator extension installed.

2. Click on the Micro Integrator icon on the Activity Bar of the VS Code editor.

    <a href="{{base_path}}/assets/img/develop/mi-for-vscode/mi-vscode-extension.png"><img src="{{base_path}}/assets/img/develop/mi-for-vscode/mi-vscode-extension.png" alt="MI VS Code Extension" width="80%"></a>

3. Click **Create New Project** on **Design View**. For more options for creating a new integration project, see [Create an Integration Project]({{base_path}}/develop/create-integration-project).

    <a href="{{base_path}}/assets/img/get-started/build-first-integration/create_new_project_btn.png"><img src="{{base_path}}/assets/img/get-started/build-first-integration/create_new_project_btn.png" alt="Create New Project" width="80%"></a>

4. In the **Project Creation Form**, enter `EventIntegration` as the **Project Name**.

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

## Step 2 - Create an event listener

Now that the integration project is ready, let's create a Kafka event listener.

1. In the **Add Artifact** interface, under **Create an Integration**, click **Event Integration**. This will open the list of event integrations available in WSO2 Micro Integrator.

    <a href="{{base_path}}/assets/img/get-started/event-integration/select_event_integration.png"><img src="{{base_path}}/assets/img/get-started/event-integration/select_event_integration.png" alt="Create New Project" width="80%"></a>

2. Select **Kafka (Inbound)** from the list. In the confirmation pane, click **Yes** to add the required dependencies.

    <a href="{{base_path}}/assets/img/get-started/event-integration/select_kafka_listener.png"><img src="{{base_path}}/assets/img/get-started/event-integration/select_kafka_listener.png" alt="Create New Project" width="80%"></a>

3. In the **Create Event Integration** form, enter `BankTransactionListener` as the **Event Integration Name** and `bank-transactions` as the **Topic Name**.

    !!! Note  
        1. In this tutorial, we will use the local Kafka broker configured in [Step 1](). If you plan to use a different Kafka broker, update the **Kafka Servers** field accordingly.
        2. We will use the default values for the remaining fields. You may refer to the [Kafka Listener]() documentation and update them if needed.

    <a href="{{base_path}}/assets/img/get-started/event-integration/configure_kafka_listener.png"><img src="{{base_path}}/assets/img/get-started/event-integration/configure_kafka_listener.png" alt="Create New Project" width="80%"></a>

4. Finally, click **Create** to add the Kafka listener to your integration project.

## Step 3 - Design the integration

Now it's time to design your integration. This defines the underlying logic that will be executed when a Kafka message is received. In this scenario, the message needs to be transformed and then published to another Kafka topic. Follow the steps below to complete the integration flow.

1. Click on the **Start** node on the canvas to set an input payload for the integration flow.

    !!! Note
        Setting an input payload for the integration flow is not mandatory. However, it is recommended, as it will be used to enable expression suggestions, which you will explore in later steps of this tutorial.

    <a href="{{base_path}}/assets/img/get-started/build-first-integration/click_start_node_3.png"><img src="{{base_path}}/assets/img/get-started/build-first-integration/click_start_node_3.png" alt="Create New Project" width="80%"></a>

3. Click **Add Request**, provide the following JSON payload, then click **Add**. Finally, click **Save** to complete the input payload setup.

    ```json
    {
        "id":"TXN001",
        "type":"deposit",
        "accountId":"ACC123",
        "amount":500
    }
    ```

    <a href="{{base_path}}/assets/img/get-started/event-integration/add_start_payload_kafka_event.gif"><img src="{{base_path}}/assets/img/get-started/event-integration/add_start_payload_kafka_event.gif" alt="Create New Project" width="80%"></a>

4. Click on the **+** icon on the canvas to open the **Mediator Palette**.

    <a href="{{base_path}}/assets/img/get-started/build-first-integration/add_new_mediator_loan_review_1.png"><img src="{{base_path}}/assets/img/get-started/build-first-integration/add_new_mediator_loan_review_1.png" alt="Create New Project" width="80%"></a>
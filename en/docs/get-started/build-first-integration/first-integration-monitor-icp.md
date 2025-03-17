# Monitor and Manage Integrations

In the previous tutorial, you learned how to implement unit tests to automate testing and ensure the reliability and correctness of your integration in WSO2 MI. Now, let's explore how to monitor the integrations using the [Integration Control Plane]() (ICP).

!!! Tip "What is Integration Control Plane?"  
    The Integration Control Plane provides a centralized interface for monitoring and managing deployed integrations. It allows users to track integration statuses, view logs, and manage services efficiently. To learn more, see the [Integration Control Plane documentation]({{base_path}}/observe-and-manage/working-with-integration-control-plane/).

## Prerequisites

1. You need Visual Studio Code (VS Code) with the <a target="_blank" href="https://marketplace.visualstudio.com/items?itemName=WSO2.micro-integrator">Micro Integrator for VS Code</a> extension installed.

    !!! Info
        See the [Install Micro Integrator for VS Code]({{base_path}}/develop/mi-for-vscode/install-wso2-mi-for-vscode/) documentation to learn how to install Micro Integrator for VS Code.

2. You must have completed the **Connect to SaaS or B2B Systems** tutorial under **Build Your First Integration** before proceeding. Start the [Connect to SaaS or B2B Systems]() tutorial if you haven’t completed it yet. While the **Implement Unit Tests** tutorial is not required for this tutorial, completing it will help you better understand automated testing in WSO2 MI.

3. You need to have the **Integration Control Plane (ICP)** installed.

    !!! Info
        See the [Install the Integration Control Plane]({{base_path}}/install-and-setup/install/installing-integration-control-plane/) documentation for installation instructions.

Follow the instructions below to monitor and manage the `Bank` API in WSO2 MI using the Integration Control Plane.

## What you'll learn

- How to check the status of deployed integrations.
- How to use the Integration Control Plane to manage integrations.

## What you'll build

In this tutorial, you will learn how to monitor the status of the `Bank` API using the Integration Control Plane. You will explore how to view deployed integrations, check their status, and ensure they are running as expected.

## Step 1 - Configure MI

Now, it's time to configure the MI runtime to connect to the Integration Control Plane (ICP). Since we will be using an existing integration, ensure that you have completed the [Connect to SaaS or B2B Systems]() tutorial and have the integration project open in VS Code.

!!! Warning
        Before proceeding with the following steps, make sure the MI server linked to VS Code is not running.

1. Click the **Explorer** (`<>`) icon to switch to the default VS Code Explorer view.

2. Expand the **deployment** directory, then click on `deployment.toml` to open it.

    <a href="{{base_path}}/assets/img/develop/mi-for-vscode/qsg/get-resource.png"><img src="{{base_path}}/assets/img/develop/mi-for-vscode/qsg/get-resource.png" alt="Add new connection" width="80%"></a>

3. Uncomment or add the following configuration in the `deployment.toml` file, then save the changes.

    ```toml
    [dashboard_config]
    dashboard_url = "https://localhost:9743/dashboard/api/"
    group_id = "dev"
    node_id = "node_1"
    ```

## Step 2 - Start the Integration Control Plane (ICP)

!!! Warning
    The Integration Control Plane (ICP) **must be installed** before proceeding to the next step. If you haven't installed it yet, refer to the [Install the Integration Control Plane]({{base_path}}/install-and-setup/install/installing-integration-control-plane/) documentation for installation instructions.

1. Open a new terminal in VS Code and navigate to the `<ICP_HOME>/bin` folder.

    <a href="{{base_path}}/assets/img/develop/mi-for-vscode/qsg/open-palette.png"><img src="{{base_path}}/assets/img/develop/mi-for-vscode/qsg/open-palette.png" alt="Add new connection" width="80%"></a>

2. Execute one of the following commands to start the Integration Control Plane (ICP).

    === "On macOS/Linux"
        ```bash 
        sh dashboard.sh
        ```
    === "On Windows"
        ```bash 
        dashboard.bat
        ```

    Once the Integration Control Plane (ICP) has started successfully, you should see logs similar to the following in the terminal.

    ```log
    [2025-03-20 11:55:31,571]  INFO {DashboardServer} - WSO2 Integration Control Plane started.
    [2025-03-20 11:55:31,574]  INFO {DashboardServer} - Login to Integration Control Plane Dashboard : 'https://localhost:9743/login'
    ```

3. Click the **Build and Run** icon in the top-right corner of VS Code to start the MI server and deploy the integrations.

    <a href="{{base_path}}/assets/img/get-started/how-to-guides/ai-data-mapping/ai-data-mapping-connection.png"><img src="{{base_path}}/assets/img/get-started/how-to-guides/ai-data-mapping/ai-data-mapping-connection.png" alt="create connection" width="80%"></a>

4. Once the MI server has started successfully, you should see logs similar to the following in the terminal where the Integration Control Plane (ICP) was started.

    ```log
    [2025-03-20 11:55:31,571]  INFO {DashboardServer} - WSO2 Integration Control Plane started.
    [2025-03-20 11:55:31,574]  INFO {DashboardServer} - Login to Integration Control Plane Dashboard : 'https://localhost:9743/login'
    [2025-03-20 12:02:05,591]  INFO {HeartBeatDelegate} - New node f22efce1-8e1a-48b9-ac05-1100b6a3cb1c in group : default is registered. Inserting heartbeat information
    [2025-03-20 12:02:05,866]  INFO {InMemoryDataManager} - Inserting heartbeat details of node f22efce1-8e1a-48b9-ac05-1100b6a3cb1c in group default
    [2025-03-20 12:02:05,866]  INFO {MiArtifactsManager} - Fetching server details from node f22efce1-8e1a-48b9-ac05-1100b6a3cb1c in group default
    [2025-03-20 12:02:05,869]  INFO {InMemoryDataManager} - Adding serverInfo of node f22efce1-8e1a-48b9-ac05-1100b6a3cb1c in group default
    ```

## Step 3 - Monitor integrations

Now that the Integration Control Plane (ICP) is running, log in to the web portal to monitor your integrations.

1. Open your web browser and navigate to [https://localhost:9743/login](https://localhost:9743/login).

    <a href="{{base_path}}/assets/img/develop/mi-for-vscode/qsg/build-and-run-project.png"><img src="{{base_path}}/assets/img/develop/mi-for-vscode/qsg/build-and-run-project.png" alt="Build and run" width="80%"></a>

2. Use `admin` as both the username and password, then click **Sign In** to access the Integration Control Plane.

    !!! Tip  
        By default, `admin` is both the username and password. To enhance security, it is recommended to create new user accounts. See [Manage Users]({{base_path}}/install-and-setup/setup/user-stores/managing-users/) for instructions on adding new users and assigning roles in the Integration Control Plane.

    After signing in, you will land on the home page of the Integration Control Plane, which displays details about the connected MI nodes. This page lists all MI nodes, and you can view the **Group ID** and **Node ID** configured in Step 1.

3. Click the **Node ID** to view details about a specific MI node.

4. In the left navigation, click **APIs** to view the deployed APIs. You should see the `Bank` API listed. Click on a node to view the API details, including its source code.

5. 

Congratulations! You have now learned how to monitor and manage integrations using the Integration Control Plane (ICP). You explored how to check the status of deployed MI nodes and view integration artifact details, including their source code.

## What's Next?  

You have now completed this tutorial series, where you learned how to build a complete integration flow step by step. Throughout this journey, you have explored how to create API services, route and transform messages, connect to external SaaS and B2B systems, implement unit testing, and monitor integrations using the Integration Control Plane (ICP).  

Now, you can explore advanced integration scenarios, applying what you’ve learned to real-world use cases and expanding your expertise in WSO2 Micro Integrator.

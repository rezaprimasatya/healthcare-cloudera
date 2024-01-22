#  Demo: Navigating and Operating Cloudera Manager

This demo provides a detailed technical guide on navigating and using Cloudera Manager from a data engineer's perspective, focusing on key functionalities such as adding new services, monitoring cluster health, and viewing logs.

### 1. Accessing Cloudera Manager

- **URL Access:** Open a web browser and navigate to the Cloudera Manager interface using the URL `http://[Cloudera_Manager_Host]:7180`.
- **Login:** Enter your credentials (username and password) to log in.

### 2. Navigating the Cloudera Manager Interface

- **Dashboard Overview:**
  - Upon logging in, you'll land on the Dashboard. This provides a high-level view of your cluster's health, including any critical alerts or warnings.
- **Left Sidebar:**
  - The sidebar is your primary navigation tool, containing links to clusters, services, hosts, reports, and administration settings.

### 3. Monitoring Cluster Health

- **Viewing Cluster Health:**
  - Navigate to the ‘Home’ > ‘Status’ tab to view the overall health of your cluster.
  - Here, you’ll see a summary of all running services and any alerts or issues.
- **Service Status:**
  - Click on a specific service (like HDFS or YARN) to view detailed health status, including service-specific metrics.

### 4. Adding a New Service

- **Navigate to the Cluster:**
  - Go to the main dashboard, then click on your cluster name.
- **Add Service:**
  - Click on the ‘Add Service’ button.
  - Follow the wizard to select the service you want to add (e.g., Apache Spark, Kafka).
  - Configure the service settings as prompted by the wizard (like role assignments, configuration settings).
  - Complete the setup and start the service.

### 5. Viewing and Managing Logs

- **Accessing Logs:**
  - Navigate to a specific service from the main dashboard.
  - Go to the ‘Instances’ tab and select a specific role or instance.
  - Click on the ‘Logs’ tab to view the logs for that instance.
- **Searching and Filtering Logs:**
  - Use the search and filter features within the log viewer to pinpoint specific log entries or issues.

### 6. Managing Hosts

- **Hosts Overview:**
  - Go to ‘Hosts’ > ‘All Hosts’ to see a list of all nodes in your cluster.
  - This section provides details like IP addresses, health status, and roles assigned to each host.
- **Adding/Removing Hosts:**
  - To add a new host, use the ‘Add New Hosts to Cluster’ option.
  - To remove a host, select the host and use the ‘Actions’ menu.

### 7. Configuring and Tuning Services

- **Service Configuration:**
  - Select a service from the cluster dashboard.
  - Go to the ‘Configuration’ tab to view and edit settings.
  - Use the search feature to find specific configuration parameters.
- **Performance Tuning:**
  - Based on monitoring and performance metrics, tune the configurations (like memory settings, number of executors) for optimal performance.

### 8. Managing Users and Permissions

- **User Management:**
  - Access the ‘Administration’ tab.
  - Use ‘Users’ and ‘Groups’ to manage user accounts and their permissions.

### 9. Running Diagnostic Tools

- **Diagnostic Bundles:**
  - In case of issues, generate diagnostic bundles via ‘Support’ > ‘Diagnostics’.
  - These bundles can be used for troubleshooting or sent to Cloudera support.

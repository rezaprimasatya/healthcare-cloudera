# CDP Private Cloud Base Installation**

### Installation Overview

CDP Private Cloud Base is a modern platform for analytics and data management, optimized for on-premises deployments. It includes Cloudera Manager for managing the cluster and CDP Runtime, which comprises various data processing and analysis services.

### Cloudera Manager Installation

**Prerequisites:**
- Compatible Linux distribution (e.g., CentOS, Red Hat Enterprise Linux).
- Sufficient hardware resources (CPU, Memory, Disk Space) based on cluster size.
- Network access and proper DNS configuration.

**Installation Process:**
1. **Repository Setup:**
   - Configure the package repository. Download and install the Cloudera repository file.
   - Example: 
     ```bash
     wget [Cloudera Manager Repo URL]
     sudo rpm --install [Repo RPM]
     ```

2. **Install Cloudera Manager Server:**
   - Install the Cloudera Manager Server package using your package manager.
   - Example: 
     ```bash
     sudo yum install cloudera-manager-daemons cloudera-manager-server
     ```

### Hands-On Exercise: Installing Cloudera Manager Server

1. **Download and Install Cloudera Manager Server:**
   - Follow the steps outlined in the installation process above.

2. **Database Setup:**
   - Cloudera Manager requires a database. You can use embedded PostgreSQL or an external database.
   - Configure the database and connect it to Cloudera Manager.

3. **Start Cloudera Manager Server:**
   - Start the server using the command:
     ```bash
     sudo systemctl start cloudera-scm-server
     ```

### CDP Runtime Overview

CDP Runtime includes core Cloudera components like Hadoop, Spark, Hive, HBase, and more. It provides data processing, analytics, and machine learning capabilities.

### Cloudera Manager Introduction

Cloudera Manager is an administrative tool for CDP. It offers an intuitive UI to manage the entire lifecycle of the cluster, including deployment, configuration, monitoring, and troubleshooting.

### Instructor-Led Demo: Cloudera Manager

In a demo, an instructor can show:
- How to navigate Cloudera Manager’s interface.
- Key functionalities like adding a new service, monitoring cluster health, and viewing logs.

### Hands-On Exercise: Cluster Installation

1. **Access Cloudera Manager:**
   - Open a web browser and navigate to Cloudera Manager’s web interface.

2. **Cluster Setup Wizard:**
   - Use the Cloudera Manager installation wizard to set up your cluster.
   - Specify hosts, select services (like HDFS, YARN, Spark), and configure each service.

3. **Install CDP Runtime:**
   - The wizard will guide you through installing the CDP Runtime components on your nodes.

4. **Validation and Testing:**
   - Once installation is complete, validate the setup by running service-specific tests. For example, run a simple Spark job to test the Spark installation.

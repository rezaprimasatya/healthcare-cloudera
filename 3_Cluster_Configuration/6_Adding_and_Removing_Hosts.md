Adding and removing hosts in a Cloudera cluster is a significant task that involves careful planning and execution to ensure the cluster's stability and performance. Below is a detailed guide on how to approach these tasks:

### Adding Hosts

#### Steps to Add Hosts Using Cloudera Manager

1. **Preparation:**
   - Ensure the new hosts meet the hardware and network requirements.
   - Install the required OS and configure networking.
   - Make sure the new hosts can communicate with the existing cluster nodes.

2. **Access Cloudera Manager:**
   - Log in to Cloudera Manager's web interface.

3. **Launch Add Hosts Wizard:**
   - Navigate to the cluster you want to add hosts to.
   - Click on the "Hosts" tab at the top, then choose "Add New Hosts to Cluster".

4. **Enter Host Details:**
   - Enter the hostnames or IP addresses of the new hosts.
   - Provide SSH login credentials so that Cloudera Manager can automate the installation of necessary software on these hosts.

5. **Select Services:**
   - Choose the services to install on the new hosts. This step depends on the role you intend for these hosts (e.g., DataNode, NodeManager).

6. **Review and Install:**
   - Review the configuration and click "Continue" to start the installation process.
   - Cloudera Manager will install the Cloudera software and configure the hosts as part of the cluster.

7. **Post-Installation Checks:**
   - Verify that the new hosts are properly integrated into the cluster.
   - Check for any alerts or warnings in Cloudera Manager.

#### Scripting Example for Host Preparation

```bash
#!/bin/bash
# Script to prepare new hosts for cluster integration

new_hosts=("host1.example.com" "host2.example.com")

for host in "${new_hosts[@]}"; do
  ssh root@$host "
    yum install -y ntp;
    systemctl start ntpd;
    systemctl enable ntpd;
    setenforce 0;
    systemctl disable firewalld;
    systemctl stop firewalld;
  "
done
```

### Removing Hosts

#### Steps to Remove Hosts Using Cloudera Manager

1. **Decommission the Host:**
   - Before removing a host, decommission it to ensure data and tasks are properly migrated to other hosts.
   - For HDFS, decommission DataNodes through Cloudera Manager by selecting the host and choosing "Decommission".
   - For YARN, decommission NodeManagers in a similar fashion.

2. **Remove the Host:**
   - Once decommissioned, go to the "Hosts" tab.
   - Select the host you want to remove and choose "Delete" from the Actions menu.
   - Confirm the deletion. Cloudera Manager will remove the host from the cluster configuration.

3. **Post-Removal Checks:**
   - Verify that the cluster is functioning correctly without the removed host.
   - Check for any alerts or imbalance in the cluster.

#### Decommission Script Example

```bash
#!/bin/bash
# Script to decommission hosts in a Cloudera cluster

hosts_to_decommission=("host1.example.com" "host2.example.com")

decommission_host() {
  local host=$1
  # This is a pseudo-function. Replace with actual Cloudera Manager API calls or necessary commands.
  cloudera_manager_decommission_host $host
}

for host in "${hosts_to_decommission[@]}"; do
  decommission_host $host
done
```

Adding and removing hosts from a Cloudera cluster can significantly impact its performance and reliability. It's crucial to follow these steps meticulously and consider the overall architecture and load distribution of your cluster during the process.
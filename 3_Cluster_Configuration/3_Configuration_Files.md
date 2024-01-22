# Configuration Files

Configuration files in a Hadoop cluster are critical as they dictate the behavior of various components. Understanding and modifying these files requires a solid grasp of Hadoop's architecture and configuration parameters. Let's delve into each of these important files:

### 1. `hdfs-site.xml`: HDFS Configurations

This file contains settings specific to the Hadoop Distributed File System (HDFS). Key parameters include block size, replication factor, and path to the NameNode and DataNode directories.

- **Block Size:** `dfs.blocksize`
- **Replication Factor:** `dfs.replication`
- **NameNode Directory:** `dfs.namenode.name.dir`
- **DataNode Directory:** `dfs.datanode.data.dir`

#### Example:
```xml
<property>
  <name>dfs.blocksize</name>
  <value>268435456</value> <!-- 256 MB -->
</property>
<property>
  <name>dfs.replication</name>
  <value>3</value>
</property>
```

### 2. `core-site.xml`: Core Configurations for Hadoop

This file is used for settings that are common across all Hadoop daemons, like I/O settings and the default file system.

- **FS Default Name:** `fs.defaultFS`
- **I/O Settings:** Such as `io.file.buffer.size`

#### Example:
```xml
<property>
  <name>fs.defaultFS</name>
  <value>hdfs://namenode:8020</value>
</property>
```

### 3. `yarn-site.xml`: YARN-related Settings

This file configures parameters for YARN, the cluster resource management system.

- **Resource Manager Address:** `yarn.resourcemanager.address`
- **NodeManager Resources:** `yarn.nodemanager.resource.memory-mb`
- **Scheduler Class:** `yarn.resourcemanager.scheduler.class`

#### Example:
```xml
<property>
  <name>yarn.nodemanager.resource.memory-mb</name>
  <value>8192</value>
</property>
```

### 4. `mapred-site.xml`: Configurations for MapReduce

This file contains settings specific to MapReduce jobs, such as the framework name and memory settings for mappers and reducers.

- **MapReduce Framework Name:** `mapreduce.framework.name`
- **Mapper Memory:** `mapreduce.map.memory.mb`
- **Reducer Memory:** `mapreduce.reduce.memory.mb`

#### Example:
```xml
<property>
  <name>mapreduce.framework.name</name>
  <value>yarn</value>
</property>
```

### Complex Script for Configuration Management

Let's consider a scenario where we want to script the update of multiple configuration parameters across the cluster:

#### Example Script:
```bash
#!/bin/bash
# Script to update HDFS and YARN configuration across the cluster

# HDFS Block Size and Replication Factor
hdfs_block_size="268435456" # 256 MB
hdfs_replication="3"

# YARN NodeManager Memory
yarn_nm_memory="8192" # 8 GB

# Update hdfs-site.xml
update_config() {
  local file=$1
  local property=$2
  local value=$3
  local host=$4

  ssh $host "sed -i '/<name>$property<\/name>/{n;s/.*/<value>$value<\/value>/}' /etc/hadoop/conf/$file"
}

for host in $(cat hadoop_hosts.txt); do
  update_config "hdfs-site.xml" "dfs.blocksize" $hdfs_block_size $host
  update_config "hdfs-site.xml" "dfs.replication" $hdfs_replication $host
  update_config "yarn-site.xml" "yarn.nodemanager.resource.memory-mb" $yarn_nm_memory $host
done
```

### Considerations

- Always backup configuration files before making changes.
- Validate XML syntax after editing to avoid service startup issues.
- Restart the relevant Hadoop services to apply the changes.
- These configurations are sensitive; incorrect values can lead to cluster instability.
- Changes should be tested in a development environment before applying to production.
- Monitor the cluster after applying changes for any unexpected behavior.
## Monitoring Hosts....................................................................................................

```
Cloudera Manager's Host Monitoring features let you manage and monitor the status of the hosts in your clusters.
```
### Viewing All Hosts..............................................................................................................................................

```
You can view summary information about all the hosts managed by Cloudera Manager on the All Hosts page.
```


```
Procedure
```
- To display summary information about all the hosts managed by Cloudera Manager, click Hosts in the main
    navigation bar.
    The list of hosts shows the overall status of the Cloudera Manager-managed hosts in your cluster.
- Optionally, to change the columns, click the Columns: n Selected drop-down and select the checkboxes next to the
    columns to display.
    The information provided varies depending on which columns are selected.
- Optionally, click to the left of the number of roles to list all the role instances running on that host.
- Optionally, filter the hosts list by entering search terms (hostname, IP address, or role) in the search box separated
    by commas or spaces. Use quotes for exact matches (for example, strings that contain spaces, such as a role name)
    and brackets to search for ranges. Hosts that match any of the search terms are displayed. For example:

```
hostname[1-3], hostname8 hostname9, "hostname.example.com"
hostname.example.com “HDFS DataNode”
```
```
You can also search for hosts by selecting a value from the facets in the Filters section at the left of the page.
```
- If the Agent Heartbeat and Health Status options are configured as follows:
    - Send Agent heartbeat every x
    - Set health status to Concerning if the Agent heartbeats fail y
    - Set health status to Bad if the Agent heartbeats fail z
    The value v for a host's Last Heartbeat facet is computed as follows:
    - v < x * y = Good
    - v >= x * y and <= x * z = Concerning
    - v >= x * z = Bad

### Role Assignments

```
You can view the assignment of roles to hosts from the Roles tab.
```
```
Procedure
```
- Click the Roles tab.
- Click a cluster name or All Clusters.

### Viewing the Disks Overview

```
You can view an overview of the status of all disks in the deployment. The statistics displayed match or build on
those in iostat, and are shown in a series of histograms that by default cover every physical disk in the system.
```
```
Procedure
```
- Click HostsDisks Overview.
- Optionally, adjust the endpoints of the time line to see the statistics for different time periods.
- Optionally, specify a filter in the box to limit the displayed data. For example, to see the disks for a single rack
    rack1, set the filter to: logicalPartition = false and rackId = "rack1" and click Filter.
- Optionally, click a histogram to drill down and identify outliers. Mouse over the graph and click to display
    additional information about the chart.


### Viewing the Hosts in a Cluster

```
You can view the hosts in a cluster. The All Hosts page displays a list of the hosts filtered by the cluster name.
```
```
Procedure
Do one of the following:
```
- Select ClustersCluster nameHosts.
- In the Home screen, click in a full-form cluster table.

### Viewing Individual Hosts

```
You can view detailed information about an individual host—resources (CPU/memory/storage) used and available,
which processes it is running, details about the host agent, and much more—by clicking a host link on the All Hosts
page.
Related Information
```

### Host Details

```
You can view details about each host from the status page for each host.
The host details include:
```
- Name, IP address, rack ID
- Health status of the host and last time the Cloudera Manager Agent sent a heartbeat to the Cloudera Manager
    Server
- Number of cores
- System load averages for the past 1, 5, and 15 minutes
- Memory usage
- File system disks, their mount points, and usage
    Important: If you have multiple mount points under the same device, then the available free space on
    that device is counted multiple times and adds to the total available disk space.
- Health test results for the host
- Charts showing a variety of metrics and health test results over time.
- Role instances running on the host and their health
- CPU, memory, and disk resources used for each role instance

#### Viewing Host Details

```
You can view detailed information about each host, such as name, IP address, and rack ID, and more from the All
Hosts page.
```
```
Procedure
```
- To view detailed host information, click HostsAll Hosts.
- Click the name of one of the hosts. The Status page is displayed for the host you selected.
- Click tabs to access specific categories of information. Each tab provides various categories of information about
    the host, its services, components, and configuration.

#### Status

```
The Status page is displayed when a host is initially selected. It provides summary information about the status of the
selected host. Use the Status page to gain an understanding of work being done by the system, the configuration, and
health status.
```
```
If this host has been decommissioned or is in maintenance mode, you will see the following icon(s) ( , ) in the top
bar of the page next to the status message.
```
```
Details
This panel provides basic system configuration such as the host's IP address, rack, health status summary, and disk
and CPU resources. This information summarizes much of the detailed information provided in other panes on this
tab. To view details about the Host agent, click the Host Agent link in the Details section.
```
```
Health Tests
Cloudera Manager monitors a variety of metrics that are used to indicate whether a host is functioning as expected.
The Health Tests panel shows health test results in an expandable/collapsible list, typically with the specific metrics
that the test returned. (You can Expand All or Collapse All from the links at the upper right of the Health Tests
panel).
```
- The color of the text (and the background color of the field) for a health test result indicates the status of the
    results. The tests are sorted by their health status – Good, Concerning, Bad, or Disabled. The list of entries for
    good and disabled health tests are collapsed by default; however, Bad or Concerning results are shown expanded.
- The text of a health test also acts as a link to further information about the test. Clicking the text will pop up a
    window with further information, such as the meaning of the test and its possible results, suggestions for actions
    you can take or how to make configuration changes related to the test. The help text for a health test also provides
    a link to the relevant monitoring configuration section for the service.

```
Health History
The Health History provides a record of state transitions of the health tests for the host.
```
- Click the arrow symbol at the left to view the description of the health test state change.
- Click the View link to open a new page that shows the state of the host at the time of the transition. In this view
    some of the status settings are greyed out, as they reflect a time in the past, not the current status.

```
File Systems
The File systems panel provides information about disks, their mount points and usage. Use this information to
determine if additional disk space is required.
```
```
Roles
Use the Roles panel to see the role instances running on the selected host, as well as each instance's status and health.
Hosts are configured with one or more role instances, each of which corresponds to a service. The role indicates
which daemon runs on the host. Some examples of roles include the NameNode, Secondary NameNode, Balancer,
JobTrackers, DataNodes, RegionServers and so on. Typically a host will run multiple roles in support of the various
services running in the cluster.
Clicking the role name takes you to the role instance's status page.
You can delete a role from the host from the Instances tab of the Service page for the parent service of the role. You
can add a role to a host in the same way.
```
```
Charts
Charts are shown for each host instance in your cluster.
```


#### Processes

```
The Processes page provides information about each of the processes that are currently running on this host. Use this
page to access management web UIs, check process status, and access log information.
Note: The Processes page may display exited startup processes. Such processes are cleaned up within a day.
```
```
The Processes page includes a variety of categories of information.
```
- Service - The name of the service. Clicking the service name takes you to the service status page. Using the
    triangle to the right of the service name, you can directly access the tabs on the role page (such as the Instances,
    Commands, Configuration, Audits, or Charts Library tabs).
- Instance - The role instance on this host that is associated with the service. Clicking the role name takes you to the
    role instance's status page. Using the triangle to the right of the role name, you can directly access the tabs on the
    role page (such as the Processes, Commands, Configuration, Audits, or Charts Library tabs) as well as the status
    page for the parent service of the role.
- Name - The process name.
- Links - Links to management interfaces for this role instance on this system. These is not available in all cases.
- Status - The current status for the process. Statuses include stopped, starting, running, and paused.
- PID - The unique process identifier.
- Uptime - The length of time this process has been running.
- Full log file - A link to the full log (a file external to Cloudera Manager) for this host log entries for this host.
- Stderr - A link to the stderr log (a file external to Cloudera Manager) for this host.
- Stdout - A link to the stdout log (a file external to Cloudera Manager) for this host.

#### Resources

```
The Resources page provides information about the resources (Memory, disk, and ports) used by every service and
role instance running on the selected host.
Each entry on this page lists:
```
- The service name
- The name of the particular instance of this service
- A brief description of the resource
- The amount of the resource being consumed or the settings for the resource
The resource information provided depends on the type of resource:
- Memory - The number of bytes consumed
- Disk - The disk location where this service stores information
- Ports - The port number being used by the service to establish network connections

#### Commands

```
The Commands page shows you running or recent commands for the host you are viewing.
```

#### Configuration

```
The Configuration page for a host lets you set properties for the selected host.
You can set properties in the following categories:
```
- Advanced - Advanced configuration properties. These include the Java Home Directory, which explicitly sets the
    value of JAVA_HOME for all processes. This overrides the auto-detection logic that is normally used.
- Monitoring - Monitoring properties for this host. The monitoring settings you make on this page will override
    the global host monitoring settings you make on the Configuration tab of the Hosts page. You can configure
    monitoring properties for:
    - Health check thresholds
    - The amount of free space on the filesystem containing the Cloudera Manager Agent's log and process
       directories
    - A variety of conditions related to memory usage and other properties
    - Alerts for health check events
    For some monitoring properties, you can set thresholds as either a percentage or an absolute value (in bytes).
- Other - Other configuration properties
- Parcels - Configuration properties related to parcels. Includes the Parcel Director property, the directory that
    parcels will be installed into on this host. If the parcel_dir variable is set in the Agent's config.ini file, it will
    override this value.
- Resource Management - Enables resource management using control groups (cgroups)
Related Information
Modifying Configuration Properties Using Cloudera Manager

#### Components

```
The Components page lists every component installed on this host. This may include components that have been
installed but have not been added as a service (such as YARN, Flume, or Impala).
This includes the following information:
```
- Component - The name of the component.
- Version - The version of Cloudera Runtime from which each component came.
- Component Version - The detailed version number for each component.

#### Audits

```
The Audits page lets you filter for audit events related to this host.
```
#### Charts Library

```
The Charts Library page for a host instance provides charts for all metrics kept for that host instance, organized by
category. Each category is collapsible/expandable.
Related Information
Viewing Charts for Cluster, Service, Role, and Host Instances
```
### Host Inspector

```
You can use the host inspector to gather information about hosts that Cloudera Manager is currently managing.
You can review this information to better understand system status and troubleshoot any existing issues. For example,
you might use this information to investigate potential DNS misconfiguration.
The inspector runs tests to gather information for functional areas including:
```
- Networking
- System time


Cloudera Manager Monitoring Activities

- User and group configuration
- HDFS settings
- Component versions
Common cases in which this information is useful include:
- Installing components
- Upgrading components
- Adding hosts to a cluster
- Removing hosts from a cluster

#### Running the Host Inspector
```
You can run the host inspector to inspect all hosts and display a list of validations and their results.
```
```
Procedure
```
1. Click HostsAll Hosts.
2. Click the Inspect All Hosts button. Cloudera Manager begins several tasks to inspect the managed hosts.
3. After the inspection completes, click Download Result Data or Show Inspector Results to review the results.
    The results of the inspection displays a list of all the validations and their results, and a summary of all the
    components installed on your managed hosts.
    If the validation process finds problems, the Validations section will indicate the problem. In some cases the
    message may indicate actions you can take to resolve the problem. If an issue exists on multiple hosts, you may be
    able to view the list of occurrences by clicking a small triangle that appears at the end of the message.
    The Version Summary section shows all the components that are available from Cloudera, their versions (if
    known) and the Cloudera Runtime distribution to which they belong.

#### Viewing Past Host Inspector Results
```
You can view the results of a past host inspection by looking for the Host Inspector command using the Recent
Commands feature.
```
```
Procedure
-
```
```
Click the Running Commands indicator ( ) to the left of the Search box at the right side of the navigation
bar.
```
- Click the Recent Commands button.
- If the command is too far in the past, you can use the Time Range Selector to move the time range back to cover
    the time period you want.
- When you find the Host Inspector command, click its name to display its subcommands.
- Click the Show Inspector Results button to view the report.
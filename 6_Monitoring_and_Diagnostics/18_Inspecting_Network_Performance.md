
## Inspecting Network Performance

```
The Network Performance Inspector allows you to examine the network performance among hosts and clusters
managed by an instance of Cloudera Manager. You can use this tool to diagnose networking issues that can
significantly affect the performance of workloads such as MapReduce jobs, Spark jobs, Hive queries, and Impala
queries, particularly when using remote storage. You can run the inspector on-demand, and it also available when
adding a new cluster. You can also run the inspector using the Cloudera Manager API.
The Network Performance Inspector runs the following types of inspections:
```
- Latency test
    The inspector runs ping commands from each host to all other hosts, and reports the average ping time and packet
    loss percentage.
    You can run the latency test among the hosts in a single cluster and between hosts in different clusters.
- Bandwidth Test
    The bandwidth test measures the speed of data transfer between the hosts. You can use this information to identify
    problematic hosts or networking infrastructure issues so that you take corrective action.
    You can run the bandwidth test only between clusters managed by an instance of Cloudera Manager.


```
Important:
The Network Performance Inspector uses the ping command on each host in the cluster to check the latency
between the hosts. In some operating system configurations, only the root user can run the ping command.
Otherwise, it has insufficient privileges to open a raw socket in order to send the required ICMP messages.
If the ping command has insufficient privileges, then the Network Performance Inspector displays the
following error message:invocation of script- /opt/cloudera/cm-agent/service/perf/host_perf_diag.py could not
execute due to - "ping: socket: Operation not permitted"
To avoid this error, you must ensure that the ping command have the setuid permissions (not recommended)
or CAP_NET_RAW capability enabled to open a raw socket.
Include the specific capability for the ping command on each host in the cluster by running the following
command::
```
```
# setcap cap_net_admin,cap_net_raw=+p $(which ping)
```
```
Check the current capabilities by running the following command:
```
```
# getcap $(which ping)
```
### Running the Network Performance Inspector From the Cloudera Manager Admin Console

```
Minimum Required Role: Key Administrator or Cluster Administrator (also provided by Full Administrator) This
feature is not available when using Cloudera Manager to manage Data Hub clusters.
To run the Network Performance Inspector:
```
- Open the Network Performance Inspector from one of the following pages in the Cloudera Manager Admin
    Console:
    - From the All Hosts page:
       a. Select HostsAll Hosts.
       b. Click the Inspect Network Performance button to launch the inspector.
    - From the Cluster Status page:
       a. Select ClustersCluster Name
       b. In the Status section, click the Hosts link at the top of the list of Cluster Services to open the Hosts page.
       c. Click the Inspect Cluster Network Performance button to launch the inspector.
    The Inspect Network Performance dialog box opens.
- Enter the following information:
    - Source Cluster – Select a cluster to inspect from the drop-down list.
       Select Run against another cluster to select additional clusters. An additional drop-down list displays from
       which you can select an additional cluster to inspect. Select either the Latency Test or the Latency and
       Bandwidth Test option.
    - Ping Timeout – Amount of time, in seconds, after which the inspector reports a failure.
    - Ping Count – Number of times the inspector pings each host.
    - Ping Packet Size – Size, in bytes, of the test packet sent when pinging the hosts.
- Click Run.
    The Cluster Performance Inspector command window opens. When the Inspector finishes, click the Show
    Inspector Results button to open the Network Performance Inspector Results page.

```
Select Show Hosts with Issues to display any problems found by the inspector, or select Show All Hosts. The
Network Diagnostic Result page displays a table of results. Each row represents a single host. The Target Hosts
Summary column summarizes the performance of the host. Click the summary text to view detailed performance
statistics from this host to each of the other hosts.
```
```
The inspector summarizes the latency and bandwidth tests for the hosts using three icons:
```
```
Table 1:
```
```
Status Bandwidth Test Latency Test
Green
Good network performance.
```
```
More than 500 MBits/Second No packet loss.
```
```
Orange
Concerning network performance
```
```
250 - 500 MBits/Second Any host with a ping latency in the range of
1 to 4 milliseconds.
```


```
Status Bandwidth Test Latency Test
Red
Bad network performance.
```
```
Less than 250 MBits/Second Any target host that is unreachable by
hostname (has a 100% packet loss), any
host with a ping latency greater than 4
milliseconds, or any target host with a packet
loss of 1% or greater.
```
```
Poor performance can result from firewall settings, router configurations, network topology, and other factors.
You may need to work with your network administrator to mitigate these issues.
```
### Running the Network Performance Inspector From the Cloudera Manager API

```
You can invoke the Network Performance Inspector using the Cloudera Manager API and the following endpoints:
```
- /cm/commmands/hostsPerfInspector
    Invokes the inspector across an arbitrary set of hosts, (including hosts that are not part of the cluster).
- /cm/commands/clusterPerfInspector
    Invokes the inspector across the hosts in two clusters.
- /cm/clusters/cluster Name/commands/perfInspector
    Invokes the inspector across the hosts of a specified cluster.
For more information, see the Cloudera Manager API REST documentation.


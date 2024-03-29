### Filtering Metrics

```
Metric Filters limit the amount of metric data reported to the Cloudera Manager server to avoid gaps in the reported
data.
```
```
About this task
Metrics Filters allow you to limit the amount of metric data sent to the Cloudera Manager Service Monitor. In large
clusters, some services, such as Kudu, send a high volume of non-essential metrics data to the Service Monitor, which
can overload it, causing gaps in the data reported from these metrics in charts/dashboards and metrics queries, and
potentially limiting the ability for Cloudera Manager to effectively monitor cluster health. To mitigate this problem,
you can configure Metric Filters that limit the amount of data sent to the Service Monitor and Host Monitor. You can
configure Metric Filters for any service deployed in a cluster.
You can configure the filter in several ways:
```
- Limit the collected metrics to only include those required for Health Tests.
- Limit the collected metrics to only include metrics used in the charts on the main page (‘Dashboard’) of the
    service.
- Include specific metrics - only the specified metrics will be collected for this service
- Exclude specific metrics - the specified metrics will not be collected for this service

```
Procedure
To configure a Metric Filter:
```
- Log in to the Cloudera Manager Admin Console.
- Navigate to the cluster where you want to add the filter.
- Click ConfigurationMetric Filters.
    -  The Configuration page displays the Metric Filter parameter for all roles in the cluster.
    -  You can now choose whether to edit all the Metric Filters using the same values, or edit the filter for a specific role.
- Do one of the following:
    - To configure the filter for a specific role, click the Edit Individual Values link and locate the parameter for the service. Follow the steps below.
    - To configure the same filter for all roles, edit the Default Group.
- Select one of the following:
    - Include Only Health Test Metric Set
    - Include Only Default Dashboard Metric Set
- To filter specific metrics:
    - Select either Include or Exclude from the ‘Include/Exclude Custom Metrics’ drop-down list.
       If you selected either of the Metric sets, and select Include, the custom metrics will be added to the selected
       Metrics sets. If you select Exclude, they will be excluded from the selected sets.
    - Click the “Plus” icon to add a metric.
    - Enter the metric name.
    - Click the “Plus” icon to add additional metrics.
       Note: You can find the names of specific metrics you would like to include or exclude either from the
       Cloudera Manager Metrics Reference (see link below) or from a chart that is displaying the required
       metrics in the Cloudera Manager Admin Console, as follows:
       - Go to the Status page for a cluster or service.
       - In a chart, click the gear icon and select Open in Chart Builder.
          The query displays at the top of the page. Metric names are part of the query. For example, the
          following query:

```
select dfs_capacity, dfs_capacity_used, dfs_capacity_used_non_hdfs
where entityName=$SERVICENAME
```
```
contains the following metric names:
```
    - dfs_capacity
    - Dfs_capacity_used
    - dfs_capacity_used_non_hdfs
-  Click Save Changes.
-  Refresh the cluster:
-  Go the cluster's Status page.
-  Click ActionsRefresh Cluster. This action does not restart the cluster.
The cluster configuration is refreshed.
Note: You can configure Cloudera Manager to automatically refresh the cluster after you update Metric
configurations by enabling the Enable auto refresh for metric configurations parameter. This parameter is
set at the role level, and, when set to true, Cloudera Manager refreshes only the role affected by a change
to the metric filter or collection enable settings, not the entire cluster.

```
Results
Note: If you do not select any options, all metrics for the service will be sent to the Service Monitor and Host
Monitor.
```

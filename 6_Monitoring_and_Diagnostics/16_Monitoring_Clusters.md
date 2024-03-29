## Monitoring Clusters................................................................................................

```
There are several locations in Cloudera Manager where you can monitor clusters.
The Clusters tab in the top navigation bar displays each cluster's services in its own section, with the Cloudera
Management Service separately below. You can select the following cluster-specific pages: hosts, reports, activities,
and resource management.
The HomeStatus tab displays the clusters being displayed by Cloudera Manager.
To display a cluster Status page, click the cluster name on the HomeStatus tab Status tab. The cluster Status page
displays a table containing links to the Hosts page and the status pages of the services running in the cluster.
```
```
Each service row in the table has a menu of actions that you select by clicking and can contain one or more of the
following indicators:
```

```
Indicator Meaning Description
Health issue Indicates that the service has at least one health issue. The indicator shows the number of health
issues at the highest severity level. If there are Bad health test results, the indicator is red. If there are
no Bad health test results, but Concerning test results exist, then the indicator is yellow. No indicator
is shown if there are no Bad or Concerning health test results.
Important: If there is one Bad health test result and two Concerning health results, there
will be three health issues, but the number will be one.
```
```
Click the indicator to display the Health Issues pop-up dialog box.
By default only Bad health test results are shown in the dialog box. To display Concerning health
test results, click the Also show n concerning issue(s) link.Click the link to display the Status page
containing with details about the health test result.
```
```
Configuration issue Indicates that the service has at least one configuration issue. The indicator shows the number of
configuration issues at the highest severity level. If there are configuration errors, the indicator is red.
If there are no errors but configuration warnings exist, then the indicator is yellow. No indicator is
shown if there are no configuration notifications.
Important: If there is one configuration error and two configuration warnings, there will
be three configuration issues, but the number will be one.
```
```
Click the indicator to display the Configuration Issues pop-up dialog box.
By default only notifications at the Error severity level are listed, grouped by service name are shown
in the dialog box. To display Warning notifications, click the Also show n warning(s) link.Click the
message associated with an error or warning to be taken to the configuration property for which the
notification has been issued where you can address the issue. For more information see the topic
Managing Services.
```
```
Restart
Needed
Refresh
Needed
```
```
Configuration modified Indicates that at least one of a service's roles is running with a configuration that does not match the
current configuration settings in Cloudera Manager.
Click the indicator to display the Stale Configurations page.To bring the cluster up-to-date, click the
Refresh or Restart button on the Stale Configurations page to refresh the cluster, restart the cluster, or
restart the stale service.
```
```
Client configuration
redeployment required
```
```
Indicates that the client configuration for a service should be redeployed.
Click the indicator to display the Stale Configurations page. To bring the cluster up-to-date, click the
Deploy Client Configuration button on the Stale Configurations page or manually redeploy the Client
Configuration.
```
```
The right side of the status page displays charts that summarize resource utilization (IO, CPU usage) and processing
metrics.
Note: If you delete a cluster, the deleted cluster still displays in some charts. This is because the charts also
show historical data. Over time, data from the deleted cluster will drop off as older data is replaced by more
current data. You can work around this by:
```
- Waiting for the data from the deleted cluster to drop off.
- Editing the where clause of query for the chart to include only the cluster(s) you are interested in. (For
    example: clusterDisplayName=Cluster_1). You can revert to the original query at a later date, after the
    data for the deleted cluster has dropped off. See the topic Charting Time-Series Data.
- Deleting all data in the Host Monitor and Service Monitor storage directories and starting from scratch.
    You will, however, loose all historical data from both current and deleted clusters. See Configuring
    Service Monitor Data Storage and Configuring Host Monitor Data Storage to learn where the storage
    directories are located.

```
Client Configuration Files
Manually Redeploying Client Configuration Files
Stale Configurations
Viewing Role Instance Status
```
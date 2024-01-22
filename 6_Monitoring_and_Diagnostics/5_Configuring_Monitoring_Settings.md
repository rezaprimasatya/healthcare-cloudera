## Configuring Monitoring Settings

```
You can configure settings for various types of monitoring in Cloudera Manager, such as health tests, activities, and
more.
Minimum Required Role: Configurator (also provided by Cluster Administrator, Limited Cluster Administrator , and
Full Administrator)
There are several types of monitoring settings you can configure in Cloudera Manager:
```
- Health tests - For a service or role for which monitoring is provided, you can enable and disable selected health
    tests and events, configure how those health tests factor into the overall health of the service, and modify
    thresholds for the status of certain health tests. For hosts you can disable or enable selected health tests, modify
    thresholds, and enable or disable health alerts.
- Free space - For hosts, you can set threshold-based monitoring of free space in the various directories on the hosts
    Cloudera Manager monitors.
- Activities - For MapReduce, YARN, and Impala services, you can configure aspects of how Cloudera Manager
    monitors activities, applications, and queries.
- Alerts - For all roles you can configure health alerts and configuration change alerts. You can also configure some
    service specific alerts and how alerts are delivered.
- Log events - For all roles you can configure logging thresholds, log directories, log event capture, when log
    messages become events, and when to generate log alerts.
- Monitoring roles - For the Cloudera Management Service you can configure monitoring settings for the
    monitoring roles themselves—enable and disable health tests on the monitoring processes as well as configuring
    some general settings related to events and alerts (specifically with the Event Server and Alert Publisher). Each
    of the Cloudera Management Service roles has its own parameters that can be modified to specify how much data
    is retained by that service. For some monitoring functions, the amount of retained data can grow very large, so it
    may become necessary to adjust the limits.
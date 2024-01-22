## Monitoring Activities

```
Cloudera Manager's activity monitoring capability monitors the Hive, Oozie, and streaming jobs, Impala queries, and
YARN applications running or that have run on your cluster.
When the individual jobs are part of larger workflows (using Oozie, or Hive), these jobs are aggregated into
MapReduce jobs that can be monitored as a whole, as well as by the component jobs.
```

```
If you are running multiple clusters, there will be a separate link in the Clusters tab for each cluster's MapReduce
activities, Impala queries, and YARN applications.
The following sections describe how to view and monitor activities that run on your cluster.
```
### Selecting Columns to Show in the Activities List

```
In the Activities list, you can display or hide any of the statistics that Cloudera Manager collects. By default only a
subset of the possible statistics are displayed.
```
```
Procedure
```
1. Click the Select Columns to Display icon ( ). A pop-up panel lets you turn on or off a variety of metrics that
    may be of interest.
2. Check or uncheck the columns you want to include or remove from the display. As you check or uncheck an item,
    its column immediately appears or disappears from the display.
3. Click the in the upper right corner to close the panel.
    Note: You cannot hide the shortcut menu or chart icon columns. Also, column selections are retained
    only for the current session.

### Sorting the Activities List

```
You can sort the Activities list by the contents of any column.
```
```
Procedure
```
- Click the column header to initiate a sort. The small arrow that appears next to the column header indicates the
    sort direction.
- Click the column header to reverse the sort direction.

### Filtering the Activities List

```
You can filter the list of activities based on values of any of the metrics that are available. You can also easily filter
for certain common queries from the drop-down menu next to the Search button at the top of the Activities list. By
default, it is set to show All Activities.
```
```
Procedure
```
- To use one of the predefined filters, click the to the right of the Search button and select the filter you want to
    run.
    There are predefined filters to search by job type (for example Pig activities, MapReduce jobs, and so on) or for
    running, failed, or long-running activities.
- To create a filter, click the to the right of the Search button and select Custom.
- Select a metric from the drop-down list in the first field; you can create a filter based on any of the available
    metrics.
- Once you select a metric, fill in the rest of the fields; your choices depend on the type of metric you have selected.
    Use the percent character % as a wildcard in a string; for example, Id matches job%0001 will look for any
    MapReduce job ID with suffix 0001.
- To create a compound filter, click the plus icon at the end of the filter row to add another row. If you combine
    filter criteria, all criteria must be true for an activity to match.
- To remove a filter criteria from a compound filter, click the minus icon at the end of the filter row. Removing the
    last row removes the filter.
- To include any children of a Pig, Hive, or Oozie activity in your search results, check the Include Child Activities
    checkbox. Otherwise, only the top-level activity will be included, even if one or more child activities matched the
    filter criteria.
- Click the Search button (which appears when you start creating the filter) to run the filter.
    Note: Filters are remembered across user sessions — that is, if you log out the filter will be preserved and
    will still be active when you log back in. Newly-submitted activities will appear in the Activity List only
    if they match the filter criteria.

### Activity Charts

```
By default the charts show aggregated statistics about the performance of the cluster: Tasks Running, CPU Usage,
and Memory Usage. There are additional charts you can enable from a pop-up panel. You can also superimpose
individual job statistics on any of the displayed charts.
Most charts display multiple metrics within the same chart. For example, the Tasks Running chart shows two metrics:
Cluster, Running Maps and Cluster, Running Reduces in the same chart. Each metric appears in a different color.
```
- To see the exact values at a given point in time, move the cursor over the chart – a movable vertical line pinpoints
    a specific time, and a tooltip shows you the values at that point.
- You can use the time range selector at the top of the page to zoom in – the chart display will follow. In order to
    zoom out, you can use the Time Range Selector at the top of the page or click the link below the chart.
To select additional charts:
-
    Click at the top right of the chart panel to open the Customize dialog box.
- Check or uncheck the boxes next to the charts you want to show or hide.
To show or hide cluster-wide statistics:
- Check or uncheck the Cluster checkbox at the top of the Charts panel.
To chart statistics for an individual job:
-
    Click the chart icon ( ) in the row next to the job you want to show on the charts. The job ID will appear in
    the top bar next to the Cluster checkbox, and the statistics will appear on the appropriate chart.
- To remove a job's statistics from the chart, click the next to the job ID in the top bar of the chart.
    Note: Chart selections are retained only for the current session.

```
To expand, contract, or hide the charts:
```
- Move the cursor over the divider between the Activities list and the charts, grab it and drag to expand or contract
    the chart area compared to the Activities list.
- Drag the divider all the way to the right to hide the charts, or all the way to the left to hide the Activities list.

### Viewing the Jobs in a Pig, Oozie, or Hive Activity

```
The Activity Children tab shows the same information as does the Activities tab, except that it shows only jobs that
are children of a selected Pig, Hive or Oozie activity. In addition, from this tab you can view the details of the Pig,
Hive or Oozie activity as a whole, and compare it to similar activities.
```

```
Procedure
```
- Click the Activities tab.
- Click the Pig, Hive or Oozie activity you want to inspect. This presents a list of the jobs that make up the Pig,
    Hive or Oozie activity.
    The functions under the Children tab are the same as those seen under the Activities tab. You can filter the job list,
    show and hide columns in the job list, show and hide charts and plot job statistics on those charts.
    Click an individual job to view Task information and other information for that child. See the topic Viewing and
    Filtering MapReduce Activities for details of how the functions on this page work.
    In addition, viewing a Pig, Hive or Oozie activity provides the following tabs:
    - The Details tab shows Activity details in a report form.
    - The Compare tab compares this activity to other similar activity. The main difference between this and a
       comparison for a single MapReduce activity is that the comparison is done looking at other activities of the
       same type (Pig, Hive or Oozie) but does include the child jobs of the activity. See the topic Comparing Similar
       Activities for an explanation of that tab.

### Task Attempts.

```
The Tasks tab contains a list of the Map and Reduce task attempts that make up a job.
```
#### Viewing a Job's Task Attempts

```
You can view a job's task attempts to inspect statistics about the performance of and resources used by the task
attempts spawned by a selected job.
```
```
Procedure
```
- From the Clusters tab, in the section marked Other, select the activity you want to inspect.
    - If the activity is a MapReduce job, the Tasks tab opens.
    - If the activity is a Pig, Hive, or Oozie activity, select the job you want to inspect from the activity's Children
       tab to open the Tasks tab.
    The columns shown under the Tasks tab display statistics about the performance of and resources used by the task
    attempts spawned by the selected job. By default only a subset of the possible metrics are displayed — you can
    modify the columns that are displayed to add or remove the columns in the display.
    The status of an attempt is shown in the Attempt Status column:

```
The attempt is running.
```
```
The attempt has succeeded.
```
```
The attempt has failed.
```
```
The attempt has been unassigned.
```
```
The attempt has been killed.
```
```
The attempt's final state is unknown.
```
- Click the task ID to view details of the individual task.
- Optionally, use the Zoom to Duration button to zoom the Time Range Selector to the exact time range spanned by
    the activity whose tasks you are viewing.

#### Selecting Columns to Show in the Tasks List

```
In the Tasks list, you can display or hide any of the metrics the Cloudera Manager collects for task attempts. By
default a subset of the possible metrics are displayed.
```
```
Procedure
```
- Click the Select Columns to Display icon ( ). A pop-up panel lets you turn on or off a variety of metrics that
    may be of interest.
- Check or uncheck the columns you want to include or remove from the display. As you check or uncheck an item,
    its column immediately appears or disappears from the display.
- Click the in the upper right corner to close the panel.

#### Sorting the Tasks List

```
You can sort the tasks list by any of the information displayed in the list.
```
```
Procedure
```
- Click the column header to initiate a sort. The small arrow that appears next to the column header indicates the
    sort direction.
- Click the column header to reverse the sort direction.

#### Filtering the Tasks List

```
You can filter the list of tasks based on values of any of the metrics that are available.
```
```
Procedure
```
- To use one of the predefined filters, click the to the right of the Search button and select the filter you want to
    run. There are predefined filters to search by job type (for example Pig activities, MapReduce jobs, and so on) or
    for running, failed, or long-running activities.
- To create a filter, click the to the right of the Search button and select Custom.
- Select a metric from the drop-down list in the first field; you can create a filter based on any of the available
    metrics.
- Once you select a metric, fill in the rest of the fields; your choices depend on the type of metric you have selected.
    Use the percent character % as a wildcard in a string; for example, Id matches job%0001 will look for any
    MapReduce job ID with suffix 0001.
- To create a compound filter, click the plus icon at the end of the filter row to add another row. If you combine
    filter criteria, all criteria must be true for an activity to match.
- To remove a filter criteria from a compound filter, click the minus icon at the end of the filter row. Removing the
    last row removes the filter.
- To include any children of a Pig, Hive, or Oozie activity in your search results, check the Include Child Activities
    checkbox. Otherwise, only the top-level activity will be included, even if one or more child activities matched the
    filter criteria.
- Click the Search button (which appears when you start creating the filter) to run the filter.
    Note: The filter persists only for this user session — when you log out, tasks list filter is removed.

### Viewing Activity Details in a Report Format

```
The Details tab for an activity shows the job or activity statistics in a report format.
To view activity details for an individual MapReduce job:
```
- Select a MapReduce job from the Clusters tab or Select a Pig, Hive or Oozie activity, then select a MapReduce
    job from the Children tab.
- Select the Details tab after the job page is displayed.
This displays information about the individual MapReduce job in a report format.
From this page you can also access the Job Details and Job Configuration pages on the JobTracker web UI.
- Click the Job Details link at the top of the report to be taken to the job details web page on the JobTracker host.
- Click the Job Configuration link to be taken to the job configuration web page on the JobTracker host.
To view activity details for a Pig, Hive, or Oozie activity:
- Select a Pig, Hive or Oozie activity.
- Select the Details tab after the list of child jobs is displayed.
This displays information about the Pig, Oozie, or Hive job as a whole.
Note that this the same data you would see for the activity if you displayed all possible columns in the Activities list.

### Comparing Similar Activities.

```
It can be useful to compare the performance of similar activities if, for example, you suspect that a job is performing
differently than other similar jobs that have run in the past. The Compare tab shows you the performance of the
selected job compared with the performance of other similar jobs.
Cloudera Manager identifies jobs that are similar to each other (jobs that are basically running the same code – the
same Map and Reduce classes, for example).
To compare an activity to other similar activities:
```
1. Select the job or activity from the Activities list.
2. Click the Compare tab.
The activity comparison feature compares performance and resource statistics of the selected job to the mean value of
those statistics across a set of the most recent similar jobs. The table provides visual indicators of how the selected job
deviates from the mean calculated for the sample set of jobs, as well as providing the actual statistics for the selected
job and the set of the similar jobs used to calculate the mean.
- The first row in the comparison table displays a set of visual indicators of how the selected job deviates from
    the mean of all the similar jobs (the combined Average values). This is displayed for each statistic for which a
    comparison makes sense. The diagram in the ID column shows the elements of the indicator, as follows:
    - The line at the midpoint of the bar represents the mean value of all similar jobs. The colored portion of the bar
       indicates the degree of deviation of your selected job from the mean. The top and bottom of the bar represent
       two standard deviations (plus or minus) from the mean.
    - For a given metric, if the value for your selected job is within two standard deviations of the mean, the colored
       portion of the bar is blue.
    - If a metric for your selected job is more than two standard deviations from the mean, the colored portion of the
       bar is red.
- The following rows show the actual values for other similar jobs. These are the sets of values that were used to
    calculate the mean values shown in the Combined Averages row. The most recent ten similar jobs are used to
    calculate the average job statistics, and these are the jobs that are shown in the table.

### Viewing the Distribution of Task Attempts

```
The Task Distribution tab provides a graphical view of the performance of the Map and Reduce tasks that make up a
job.
```
```
Procedure
```
- To display the task distribution metrics for a job, do one of the following:
    - Select a MapReduce job from the Activities list.
    - Select a job from the Children tab of a Pig, Hive, or Oozie activity.
- Click the Task Distribution tab.
    The chart that appears initially shows the distribution of Map Input Records by Duration; you can change the Y-
    axis to chart a number of different metrics.
- Optionally, you can use the Zoom to Duration button to zoom the Time Range Selector to the exact time range
    spanned by the activity whose tasks you are viewing.

#### The Task Distribution Chart.

```
The Task Distribution chart shows the distribution of attempts according to their duration on the X-axis and a number
of different metrics on the Y-axis.
Each cell of the chart represents the number of tasks whose performance statistics fall within the parameters of the
cell. The Task Distribution chart is useful for detecting tasks that are outliers in your job, either because of skew, or
because of faulty TaskTrackers. The chart can clearly show if some tasks deviate significantly from the majority of
task attempts.
Normally, the distribution of tasks will be fairly concentrated. If, for example, some Reducers receive much more
data than others, that will be represented by having two discrete sections of density on the graph. That suggests that
there may be a problem with the user code, or that there's skew in the underlying data. Alternately, if the input sizes
of various Map or Reduce tasks are the same, but the time it takes to process them varies widely, it might mean that
certain TaskTrackers are performing more poorly than others.
You can click in a cell and see a list of the TaskTrackers that correspond to the tasks whose performance falls within
the cell.
The X-axis show the task duration is seconds. From the drop-down you can chose different metrics for the Y-axis:
Input or Output records or bytes for Map tasks, or the number of CPU seconds for the user who ran the job:
```
- Map Input Records vs. Duration
- Map Output Records vs. Duration
- Map Input Bytes vs. Duration
- Map Output Bytes vs. Duration
- Map Total User CPU seconds vs. Duration
- Reduce Input Records vs. Duration
- Reduce Output Records vs. Duration
- Reduce Total User CPU seconds vs. Duration

#### TaskTracker Hosts..

```
To the right of the chart is a table that shows the TaskTracker hosts that processed the tasks in the selected cell, along
with the number of task attempts each host executed.
You can select a cell in the table to view the TaskTracker hosts that correspond to the tasks in the cell.
```
- The area above the TaskTracker table shows the type of task and range of data volume (or User CPUs) and
    duration times for the task attempts that fall within the cell.
- The table itself shows the TaskTracker hosts that executed the tasks that are represented within the cell, and the
    number of task attempts run on that host.


```
Clicking a TaskTracker hostname takes you to the Role Status page for that TaskTracker instance.
```
### Monitoring Impala Queries

```
The Impala Queries page displays information about Impala queries that are running and have run in your cluster.
You can filter the queries by time period and by specifying simple filtering expressions.
Note: The Impala query monitoring feature requires Impala 1.0.1 and higher.
```

#### Viewing Queries.

```
You can view queries, filter queries, and more from the Impala service Queries tab.
Do one of the following:
```
- Select Clusters Cluster name Impala service name Queries.
- On the Home Status tab, select Impala service name and click the Queries tab.
The Impala queries run during the selected time range display in the Results tab.
You can also perform the following actions on this page:

```
Table 4: Viewing Queries Actions
```
```
Action Description
Filter the displayed queries Create filter expressions manually, select preconfigured filters, or use
the Workload Summary section to build a query interactively.
Select additional attributes for display. Click Select Attributes. Selected attributes also display as available
filters in the Workload Summary section. To display information about
attributes, hover over a field label..
Only attributes that support filtering appear in the Workload Summary
section.
View a histogram of the attribute values. Click the icon to the right of each attribute displayed in the
Workload Summary section.
Display charts based on the filter expression and selected attributes. Cick the Charts tab.
View charts that help identify whether Impala best practices are being
followed.
```
```
Click the Best Practices link.
```
```
Export a JSON file with the query results that you can use for further
analysis.
```
```
Click Export.
```

#### Configuring Impala Query Monitoring.

```
You can configure the visibility of the Impala query results and the size of the storage allocated to Impala query
results.
```
```
About this task
To configure whether admin or non-admin users can view all queries, only that user's queries, or no queries:
```

```
Minimum Required Role: Configurator (also provided by Cluster Administrator, Limited Cluster Administrator , and
Full Administrator)
```
```
Procedure
```
- Go to the Impala service.
- Click the Configuration tab.
- Select ScopeImpala service_name (Service-Wide).
- Click the Monitoring category.
- Set the Visibility Settings properties for admin and non-admin users.
- Enter a Reason for change, and then click Save Changes to commit the changes.
- Click the Cloudera Manager logo to return to the Home page.
- Click the icon that is next to any stale services to invoke the cluster restart wizard.

#### Impala Best Practices.

```
The Impala Best Practices page contains charts that include description of each best practice and how to determine
if it is being followed.
To open the Impala Best Practices page, click the Best Practices tab on the Impala service page. See the Impala
documentation for more detail on each best practice and for additional best practices.
Adjust the time range to see data on queries run at different times. Click the charts to get more detail on individual
queries. Use the filter box at the top right of the Best Practices page to adjust which data is shown on the page. For
example, to see just the queries that took more than ten seconds, make the filter query_duration > 10s.
Create a trigger based on any best practice by choosing Create Trigger from the individual chart drop-down menu.
```
#### Results Tab

```
Queries appear on the Results tab, with the most recent at the top. Each query has summary and detail information.
A query summary includes the following default attributes: start and end timestamps, statement, duration, rows
produced, user, coordinator, database, and query type. For example:
```
```
You can add additional attributes to the summary by clicking the Attribute Selector. In each query summary, the
query statement is truncated if it is too long to display. To display the entire statement, click. The query entry
expands to display the entire query string. To collapse the query display, click. To display information about query
attributes and possible values, hover over a field in a query. For example:
```
```
A running job displays a progress bar under the starting timestamp:
```

```
If an error occurred while processing the query, displays under the complete timestamp.
```
```
Use the Actions drop-down menu to the right of each query listing to do the following. (Not all options
display, depending on the type of job.)
```
- Query Details – Opens a details page for the job.
- User's Impala Queries – Displays a list of queries run by the user for the current job.
- Cancel (running queries only) – Cancel a running query (administrators only). Canceling a running query creates

```
an audit event. When you cancel a query, replaces the progress bar.
```
- Queries in the same YARN pool – Displays queries that use the same resource pool.

#### Filtering Queries.

```
You filter queries by selecting a time range and specifying a filter expression in the search box.
You filter queries by selecting a time range and specifying a filter expression in the search box.
You can use the Time Range Selector or a duration link (
```
```
) to set the time range.
Related Information
Time Line
```
#### Filter Expressions

```
Filter expressions specify which entries should display when you run the filter.
The simplest expression consists of three components:
```
- Attribute - Query language name of the attribute.
- Operator - Type of comparison between the attribute and the attribute value. Cloudera Manager supports the
    standard comparator operators =, !=, >, <, >=, <=, and RLIKE. (RLIKE performs regular expression matching
    as specified in the Java Pattern class documentation.) Numeric values can be compared with all operators. String
    values can be compared with =, !=, and RLIKE. Boolean values can be compared with = and !=.
- Value - The value of the attribute. The value depends on the type of the attribute. For a Boolean value, specify
    either true or false. When specifying a string value, enclose the value in double quotes.
You create compound filter expressions using the AND and OR operators. When more than one operator is used
in an expression, AND is evaluated first, then OR. To change the order of evaluation, enclose subexpressions in
parentheses.
Compound Expressions
To find all the queries issued by the root user that produced over 100 rows, use the expression:

```
user = "root" AND rowsProduced > 100
```

Cloudera Manager Monitoring Activities

```
To find all the executing queries issued by users Jack or Jill, use the expression:
```
```
executing = true AND (user = "Jack" OR user = "Jill")
```

#### Filter Attributes

```
The following table includes available filter attributes and their names in Cloudera Manager, types, and descriptions.
Note: Only attributes for which the Supports Filtering? column value is TRUE appear in the Workload
Summary section.
```
```
Table 5: Attributes
```
```
Display Name
(Attribute Name)
```
```
Type Supports
Filtering?
```
```
Description
```
```
Admission Result
(admission_result)
```
```
STRING TRUE The result of admission, whether immediately, queued, rejected,
or timed out. Called 'admission_result' in searches.
```
```
Admission Wait Time
(admission_wait)
```
```
MILLISECONDSTRUE The time from submission for admission to completion of
admission. Called 'admission_wait' in searches.
```
```
Aggregate Peak Memory Usage
(memory_aggregate_peak)
```
```
BYTES TRUE The highest amount of memory allocated by this
query at a particular time across all nodes. Called
'memory_aggregate_peak' in searches.
Bytes Streamed
(bytes_streamed)
```
```
BYTES TRUE The total number of bytes sent between Impala Daemons while
processing this query. Called 'bytes_streamed' in searches.
```
```
Client Fetch Wait Time
(client_fetch_wait_time)
```
```
MILLISECONDSTRUE The total amount of time the query spent waiting for the client to
fetch row data. Called 'client_fetch_wait_time' in searches.
```
```
Client Fetch Wait Time Percentage
(client_fetch_wait_time_percentage)
```
```
NUMBER TRUE The total amount of time the query spent waiting for the
client to fetch row data divided by the query duration. Called
'client_fetch_wait_time_percentage' in searches.
Connected User
(connected_user)
```
```
STRING TRUE The user who created the Impala session that issued this query.
This is distinct from 'user' only if delegation is in use. Called
'connected_user' in searches.
Coordinator
(coordinator_host_id)
```
```
STRING TRUE The host coordinating this query. Called 'coordinator_host_id' in
searches.
```
```
Database
(database)
```
```
STRING TRUE The database on which the query was run. Called 'database' in
searches.
```
```
DDL Type
(ddl_type)
```
```
STRING TRUE The type of DDL query. Called 'ddl_type' in searches.
```
```
Delegated User
(delegated_user)
```
```
STRING TRUE The effective user for the query. This is set only if delegation is
in use. Called 'delegated_user' in searches.
```
```
Duration
(query_duration)
```
```
MILLISECONDSTRUE The duration of the query in milliseconds. Called
'query_duration' in searches.
```
```
Estimated per Node Peak Memory
(estimated_per_node_peak_memory)
```
```
BYTES TRUE The planning process's estimate of per-node peak memory usage
for the query. Called 'estimated_per_node_peak_memory' in
searches.
```

Cloudera Manager Monitoring Activities

```
Display Name
(Attribute Name)
```
```
Type Supports
Filtering?
```
```
Description
```
```
Executing
(executing)
```
```
BOOLEAN FALSE Whether the query is currently executing. Called 'executing' in
searches.
```
```
File Formats
(file_formats)
```
```
STRING FALSE An alphabetically sorted list of all the file formats used in the
query. Called 'file_formats' in searches.
```
```
HBase Bytes Read
(hbase_bytes_read)
```
```
BYTES TRUE The total number of bytes read from HBase by this query. Called
'hbase_bytes_read' in searches.
```
```
HBase Scanner Average Read Throughput
(hbase_scanner_average_bytes_read_per_sec
ond)
```
```
BYTES_PER_SECONDTRUE The average HBase scanner read throughput for this query.
This is computed by dividing the total bytes read from HBase
by the total time spent reading by all HBase scanners. Called
'hbase_scanner_average_bytes_read_per_second' in searches.
HDFS Average Scan Range
(hdfs_average_scan_range)
```
```
BYTES TRUE The average HDFS scan range size for this query. HDFS scan
nodes that contained only a single scan range are not included
in this computation. Low numbers for a query might indicate
reading many small files which negatively impacts performance.
Called 'hdfs_average_scan_range' in searches.
HDFS Bytes Read
(hdfs_bytes_read)
```
```
BYTES TRUE The total number of bytes read from HDFS by this query. Called
'hdfs_bytes_read' in searches.
```
```
HDFS Bytes Read From Cache
(hdfs_bytes_read_from_cache)
```
```
BYTES TRUE The total number of bytes read from HDFS that were read from
the HDFS cache. This is only for completed queries. Called
'hdfs_bytes_read_from_cache' in searches.
HDFS Bytes Read From Cache Percentage
(hdfs_bytes_read_from_cache_percentage)
```
```
NUMBER TRUE The percentage of all bytes read by this query that were read
from the HDFS cache. This is only for completed queries.
Called 'hdfs_bytes_read_from_cache_percentage' in searches.
HDFS Bytes Skipped
(hdfs_bytes_skipped)
```
```
BYTES TRUE The total number of bytes that had to be skipped by this query
while reading from HDFS. Any number above zero may indicate
a problem. Called 'hdfs_bytes_skipped' in searches.
HDFS Bytes Written
(hdfs_bytes_written)
```
```
BYTES TRUE The total number of bytes written to HDFS by this query. Called
'hdfs_bytes_written' in searches.
```
```
HDFS Local Bytes Read
(hdfs_bytes_read_local)
```
```
BYTES TRUE The total number of local bytes read from HDFS by
this query. This is only for completed queries. Called
'hdfs_bytes_read_local' in searches.
HDFS Local Bytes Read Percentage
(hdfs_bytes_read_local_percentage)
```
```
NUMBER TRUE The percentage of all bytes read from HDFS by this query
that were local. This is only for completed queries. Called
'hdfs_bytes_read_local_percentage' in searches.
HDFS Remote Bytes Read
(hdfs_bytes_read_remote)
```
```
BYTES TRUE The total number of remote bytes read from HDFS by
this query. This is only for completed queries. Called
'hdfs_bytes_read_remote' in searches.
HDFS Remote Bytes Read Percentage
(hdfs_bytes_read_remote_percentage)
```
```
NUMBER TRUE The percentage of all bytes read from HDFS by this query
that were remote. This is only for completed queries. Called
'hdfs_bytes_read_remote_percentage' in searches.
HDFS Scanner Average Read Throughput
(hdfs_scanner_average_bytes_read_per_second)
```
```
BYTES_PER_SECONDTRUE The average HDFS scanner read throughput for this query.
This is computed by dividing the total bytes read from HDFS
by the total time spent reading by all HDFS scanners. Called
'hdfs_scanner_average_bytes_read_per_second' in searches.
HDFS Short Circuit Bytes Read
(hdfs_bytes_read_short_circuit)
```
```
BYTES TRUE The total number of bytes read from HDFS by this query that
used short-circuit reads. This is only for completed queries.
Called 'hdfs_bytes_read_short_circuit' in searches.
HDFS Short Circuit Bytes Read Percentage
(hdfs_bytes_read_short_circuit_percentage)
```
```
NUMBER TRUE The percentage of all bytes read from HDFS by this query that
used short-circuit reads. This is only for completed queries.
Called 'hdfs_bytes_read_short_circuit_percentage' in searches.
```

```
Display Name
(Attribute Name)
```
```
Type Supports
Filtering?
```
```
Description
```
```
Impala Version
(impala_version)
```
```
STRING TRUE The version of the Impala Daemon coordinating this query.
Called 'impala_version' in searches.
```
```
Memory Accrual
(memory_accrual)
```
```
BYTE_SECONDSTRUE The total accrued memory usage by the query. This is computed
by multiplying the average aggregate memory usage of the
query by the query's duration. Called 'memory_accrual' in
searches.
Memory Spilled
(memory_spilled)
```
```
BYTES TRUE Amount of memory spilled to disk. Called 'memory_spilled' in
searches.
```
```
Network Address
(network_address)
```
```
STRING TRUE The network address that issued this query. Called
'network_address' in searches.
```
```
Node with Peak Memory Usage
(memory_per_node_peak_node)
```
```
STRING TRUE The node with the highest peak memory usage for this query.
See Per Node Peak Memory Usage for the actual peak value.
Called 'memory_per_node_peak_node' in searches.
Out of Memory
(oom)
```
```
BOOLEAN TRUE Whether the query ran out of memory. Called 'oom' in searches.
```
```
Per Node Peak Memory Usage
(memory_per_node_peak)
```
```
BYTES TRUE The highest amount of memory allocated by any single node that
participated in this query. See Node with Peak Memory Usage
for the name of the peak node. Called 'memory_per_node_peak'
in searches.
Planning Wait Time
(planning_wait_time)
```
```
MILLISECONDSTRUE The total amount of time the query spent waiting for planning to
complete. Called 'planning_wait_time' in searches.
```
```
Planning Wait Time Percentage
(planning_wait_time_percentage)
```
```
NUMBER TRUE The total amount of time the query spent waiting for
planning to complete divided by the query duration. Called
'planning_wait_time_percentage' in searches.
Pool
(pool)
```
```
STRING TRUE The name of the resource pool in which this query executed.
Called 'pool' in searches. If YARN is in use, this corresponds to
a YARN pool. Within YARN, a pool is referred to as a queue.
Query ID
(query_id)
```
```
STRING FALSE The id of this query. Called 'query_id' in searches.
```
```
Query State
(query_state)
```
```
STRING TRUE The current state of the query (running, finished, and so on).
Called 'query_state' in searches.
```
```
Query Status
(query_status)
```
```
STRING TRUE The status of the query. If the query hasn't failed the status will
be 'OK', otherwise it will provide more information on the cause
of the failure. Called 'query_status' in searches.
Query Type
(query_type)
```
```
STRING TRUE The type of the query's SQL statement (DML, DDL, Query).
Called 'query_type' in searches.
```
```
Resource Reservation Wait Time
(resources_reserved_wait_time)
```
```
MILLISECONDSTRUE The total amount of time the query spent waiting
for pool resources to become available. Called
'resources_reserved_wait_time' in searches.
Resource Reservation Wait Time Percentage
(resources_reserved_wait_time_percentage)
```
```
NUMBER TRUE The total amount of time the query spent waiting for pool
resources to become available divided by the query duration.
Called 'resources_reserved_wait_time_percentage' in searches.
Rows Inserted
(rows_inserted)
```
```
NUMBER TRUE The number of rows inserted by the query. Called
'rows_inserted' in searches.
```
```
Rows Produced
(rows_produced)
```
```
NUMBER TRUE The number of rows produced by the query. Called
'rows_produced' in searches.
```

Cloudera Manager Monitoring Activities

```
Display Name
(Attribute Name)
```
```
Type Supports
Filtering?
```
```
Description
```
```
Service Name
(service_name)
```
```
STRING FALSE The name of the Impala service. Called 'service_name' in
searches.
```
```
Session ID
(session_id)
```
```
STRING TRUE The ID of the session that issued this query. Called 'session_id'
in searches.
```
```
Session Type
(session_type)
```
```
STRING TRUE The type of the session that issued this query. Called
'session_type' in searches.
```
```
Statement
(statement)
```
```
STRING FALSE The query's SQL statement. Called 'statement' in searches.
```
```
Statistics Missing
(stats_missing)
```
```
BOOLEAN TRUE Whether the query was flagged with missing table or column
statistics warning during the planning process. Called
'stats_missing' in searches.
Threads: CPU Time
(thread_cpu_time)
```
```
MILLISECONDSTRUE The sum of the CPU time used by all threads of the query.
Called 'thread_cpu_time' in searches.
```
```
Threads: CPU Time Percentage
(thread_cpu_time_percentage)
```
```
NUMBER TRUE The sum of the CPU time used by all threads of
the query divided by the total thread time. Called
'thread_cpu_time_percentage' in searches.
Threads: Network Receive Wait Time
(thread_network_receive_wait_time)
```
```
MILLISECONDSTRUE The sum of the time spent waiting to receive data over the
network by all threads of the query. A query will almost
always have some threads waiting to receive data from
other nodes in the query's execution tree. Unlike other wait
times, network receive wait time does not usually indicate
an opportunity for improving a query's performance. Called
'thread_network_receive_wait_time' in searches.
Threads: Network Receive Wait Time
Percentage
(thread_network_receive_wait_time_percent
age)
```
```
NUMBER TRUE The sum of the time spent waiting to receive data over
the network by all threads of the query divided by the
total thread time. A query will almost always have
some threads waiting to receive data from other nodes
in the query's execution tree. Unlike other wait times,
network receive wait time does not usually indicate an
opportunity for improving a query's performance. Called
'thread_network_receive_wait_time_percentage' in searches.
Threads: Network Send Wait Time
(thread_network_send_wait_time)
```
```
MILLISECONDSTRUE The sum of the time spent waiting to send data
over the network by all threads of the query. Called
'thread_network_send_wait_time' in searches.
Threads: Network Send Wait Time Percentage
(thread_network_send_wait_time_percentage)
```
```
NUMBER TRUE The sum of the time spent waiting to send data over the
network by all threads of the query divided by the total thread
time. Called 'thread_network_send_wait_time_percentage' in
searches.
Threads: Storage Wait Time
(thread_storage_wait_time)
```
```
MILLISECONDSTRUE The sum of the time spent waiting for storage by all threads of
the query. Called 'thread_storage_wait_time' in searches.
```
```
Threads: Storage Wait Time Percentage
(thread_storage_wait_time_percentage)
```
```
NUMBER TRUE The sum of the time spent waiting for storage by all
threads of the query divided by the total thread time. Called
'thread_storage_wait_time_percentage' in searches.
Threads: Total Time
(thread_total_time)
```
```
MILLISECONDSTRUE The sum of thread CPU, storage wait and network wait times
used by all threads of the query. Called 'thread_total_time' in
searches.
User
(user)
```
```
STRING TRUE The effective user for the query. This is the delegated user if
delegation is in use. Otherwise, this is the connected user. Called
'user' in searches.
```

```
Display Name
(Attribute Name)
```
```
Type Supports
Filtering?
```
```
Description
```
```
Work CPU Time
(cm_cpu_milliseconds)
```
```
MILLISECONDSTRUE Attribute measuring the sum of CPU time used by all threads of
the query, in milliseconds. Called 'work_cpu_time' in searches.
For Impala queries, CPU time is calculated based on the
'TotalCpuTime' metric. For YARN MapReduce applications,
this is calculated from the 'cpu_milliseconds' metric.
```
```
Examples
Consider the following filter expressions: user = "root", rowsProduced > 0, fileFormats RLIKE ".TEXT.*", and exec
uting = true. In the examples:
```
- The filter attributes are user, rowsProduced, fileFormats, and executing.
- The operators are =, >, and RLIKE.
- The filter values are root, 0, .TEXT.*, and true.

#### Choosing and Running a Filter

```
You can construct a filter, type a filter, or select a suggested or recently run filter.
```

```
Procedure
```
- Do one of the following:
    - Select a Suggested or Recently Run Filter: Click the to the right of the Search button to display a list of
       sample and recently run filters, and select a filter. The filter text displays in the text box.
    - Construct a Filter from the Workload Summary Attributes: Optionally, click Select Attributes to display a
       dialog box where you can chose which attributes to display in the Workload Summary section. Select the
       checkbox next to one or more attributes, and click Close.
       The attributes display in the Workload Summary section along with values or ranges of values that you can
       filter on. The values and ranges display as links with checkboxes. Select one or more checkboxes to add the
       range or value to the query. Click a link to run a query on that value or range. For example:
    - Type a Filter: Start typing or press Spacebar in the text box.
       As you type, filter attributes matching the typed letter display. If you press Spacebar, standard filter attributes
       display. These suggestions are part of typeahead, which helps build valid queries. For information about the
       attribute name and supported values for each field, hover over the field in an existing query.


Cloudera Manager Monitoring Activities

```
- Select an attribute and press Enter.
- Press Spacebar to display a drop-down list of operators.
- Select an operator and press Enter.
- Specify an attribute value. For attribute values that support typeahead, press the spacebar to display a drop-
down list of values and press Enter. Alternatively, you can type a value.
```
- Click in the text box and press Enter or click Search. The list displays the results that match the specified filter.
    The Workload Summary section refreshes to show only the values for the selected filter. The filter is added to the
    Recently Run list.

### Query Details..

```
The Query Details page contains the low-level details of how a SQL query is processed through Impala.
The initial information on the page can help you tune the performance of some kinds of queries, primarily those
involving joins. The more detailed information on the page is primarily for troubleshooting with the assistance of
Cloudera Support; you might be asked to attach the contents of the page to a trouble ticket. The Query Details page
displays the following information that is also available in the Query Profile.
To download the contents of the query profile details, select one of the following:
```
- Download Profile or Download ProfileDownload Text Profile - to download a text version of the query
    detail.
- Download ProfileDownload Thrift Encoded Profile - to download a binary version of the query detail.

```
Query Plan
The Query Plan section can help you diagnose and tune performance issues with queries. This information is
especially useful to understand performance issues with join queries, such as inefficient order of tables in the SQL
statement, lack of table and column statistics, and the need for query hints to specify a more efficient join mechanism.
You can also learn valuable information about how queries are processed for partitioned tables.
The information in this section corresponds to the output of the EXPLAIN statement for the Impala query. Each
fragment shown in the query plan corresponds to a processing step that is performed by the central coordinator host or
distributed across the hosts in the cluster.
```
```
Query Timeline
The Query Timeline section reports statistics about the execution time for phases of the query.
```
```
Planner Timeline
The Planner Timeline reports statistics about the execution time for phases of the query planner.
```
```
Query Info
The Query Info section reports the attributes of the query, start and end time, duration, and statistics about HDFS
access. You can hover over an attribute for information about the attribute name and supported values (for
enumerated values). For example:
```

Cloudera Manager Monitoring Activities

```
Query Fragments
The Query Fragments section reports detailed low-level statistics for each query plan fragment, involving physical
aspects such as CPU utilization, disk I/O, and network traffic. This is the primary information that Cloudera Support
might use to help troubleshoot performance issues and diagnose bugs. The details for each fragment display on
separate tabs.
```
### Monitoring YARN Applications

```
The YARN Applications page displays information about the YARN jobs that are running and have run in your
cluster. You can filter the jobs by time period and by specifying simple filtering expressions.
```
#### Viewing Jobs.

```
You can view YARN jobs, filter YARN jobs, and more from the YARN service Applications tab.
Do one of the following:
```
- Select Clusters Cluster name YARN service name Applications.
- On the Home Status tab, select YARN service name and click the Applications tab.
The YARN jobs run during the selected time range display in the Results tab. The results displayed can be filtered by
creating filter expressions.
You can also perform the following actions on this page:

```
Table 6: Viewing Jobs Actions
```
```
Action Description
Filter jobs that display. Create filter expressions manually, select preconfigured filters, or use
the Workload Summary section to build a query interactively.
Select additional attributes for display. Click Select Attributes. Selected attributes also display as available
filters in the Workload Summary section. To display information about
attributes, hover over a field label.
Only attributes that support filtering appear in the Workload Summary
section.
View a histogram of the attribute values. Click the icon to the right of each attribute displayed in the
Workload Summary section.
Display charts based on the filter expression and selected attributes. Click the Charts tab.
Send a YARN application diagnostic bundle to Cloudera support. Click Collect Diagnostics Data.
Export a JSON file with the query results that you can use for further
analysis.
```
```
Click Export.
```

#### Configuring YARN Application Monitoring..

```
You can configure the visibility of the YARN application monitoring results.
```

```
About this task
To configure whether admin and non-admin users can view all applications, only that user's applications, or no
applications:
Minimum Required Role: Configurator (also provided by Cluster Administrator, Limited Cluster Administrator , and
Full Administrator)
```
```
Procedure
```
- Go to the YARN service.
- Click the Configuration tab.
- Select Scope YARN service_name (Service-Wide).
- Click the Monitoring category.
- Set the Applications List Visibility Settings properties for admin and non-admin users.
- Enter a Reason for change, and then click Save Changes to commit the changes.
- Click the Cloudera Manager logo to return to the Home page.
- Click the icon that is next to any stale services to invoke the cluster restart wizard.

#### Results Tab

```
Jobs appear on the Results tab, with the most recent at the top. Each job has summary and detail information.
Jobs are ordered with the most recent at the top. Each job has summary and detail information. A job summary
includes start and end timestamps, query (if the job is part of a Hive query) name, pool, job type, job ID, and user. For
example:
```
```
A running job displays a progress bar under the start timestamp:
```
```
Use the Actions drop-down menu to the right of each job listing to do the following. (Not all options
display, depending on the type of job.)
```
- Application Details – Open a details page for the job.
- Collect Diagnostic Data – Send a YARN application diagnostic bundle to Cloudera support.
- Similar MR2 Jobs – Display a list of similar MapReduce 2 jobs.
- User's YARN Applications – Display a list of all jobs run by the user of the current job.
- View on JobHistory Server – View the application in the YARN JobHistory Server.
- Kill (running jobs only) – Stop a job (administrators only). Stopping a job creates an audit event. When you stop a

```
job, replaces the progress bar.
```

- Applications in Hive Query (Hive jobs only)
- Applications in Oozie Workflow (Oozie jobs only)
- Applications in Pig Script (Pig jobs only)

#### Filtering Jobs.

```
You filter jobs by selecting a time range and specifying a filter expression in the search box.
You can use the Time Range Selector or a duration link (
```
```
) to set the time range.
Related Information
Time Line
```
#### Filter Expressions

```
Filter expressions specify which entries should display when you run the filter.
```
```
Filter Expressions
The simplest expression consists of three components:
```
- Attribute - Query language name of the attribute.
- Operator - Type of comparison between the attribute and the attribute value. Cloudera Manager supports the
    standard comparator operators =, !=, >, <, >=, <=, and RLIKE. (RLIKE performs regular expression matching
    as specified in the Java Pattern class documentation.) Numeric values can be compared with all operators. String
    values can be compared with =, !=, and RLIKE. Boolean values can be compared with = and !=.
- Value - The value of the attribute. The value depends on the type of the attribute. For a Boolean value, specify
    either true or false. When specifying a string value, enclose the value in double quotes.
You create compound filter expressions using the AND and OR operators. When more than one operator is used
in an expression, AND is evaluated first, then OR. To change the order of evaluation, enclose subexpressions in
parentheses.
Compound Expressions
To find all the jobs issued by the root user that ran for longer than ten seconds, use the expression:

```
user = "root" AND application_duration >= 100000.0
```
```
To find all the jobs that had more than 200 maps issued by users Jack or Jill, use the expression:
```
```
maps_completed >= 200.0 AND (user = "Jack" OR user = "Jill")
```
```
Related Information
Java Pattern
```
#### Choosing and Running a Filter

```
You can construct a filter, type a filter, or select a suggested or recently run filter.
```
```
Procedure
```
- Do one of the following:
    - Select a Suggested or Recently Run Filter: Click the to the right of the Search button to display a list of
       sample and recently run filters, and select a filter. The filter text displays in the text box.
    - Construct a Filter from the Workload Summary Attributes: Optionally, click Select Attributes to display a
       dialog box where you can chose attributes to display in the Workload Summary section. Select the checkbox


```
next to one or more attributes and click Close. Only attributes that support filtering appear in the Workload
Summary section. See the Attributes table.
The attributes display in the Workload Summary section along with values or ranges of values that you can
filter on. The values and ranges display as links with checkboxes. Select one or more checkboxes to add the
range or value to the query. Click a link to run a query on that value or range. For example:
```
- Type a Filter: Start typing or press Spacebarin the text box.
    As you type, filter attributes matching the typed letter display. If you press Spacebar, standard filter attributes
    display. These suggestions are part of typeahead, which helps build valid queries. For information about the
    attribute name and supported values for each field, hover over the field in an existing query.
    a. Select an attribute and press Enter.
    b. Press Spacebar to display a drop-down list of operators.
    c. Select an operator and press Enter.
    d. Specify an attribute value. For attribute values that support typeahead, press the spacebar to display a drop-
       down list of values and press Enter. Alternatively, you can type a value.


- Click in the text box and press Enter or click Search. The list displays the results that match the specified filter. If
    the histograms are showing, they are redrawn to show only the values for the selected filter. The filter is added to
    the Recently Run list.

#### Filter Attributes

```
The table below describes filter attributes, their names as they are displayed in Cloudera Manager, their types, and
descriptions.
Note: Only attributes where the Supports Filtering? column value is TRUE appear in the Workload
Summary section.
```
```
Table 7: Attributes
```
```
Display Name
(Attribute Name)
```
```
Type Supports
Filtering?
```
```
Description
```
```
Allocated Memory
(allocated_mb)
```
```
NUMBER FALSE The sum of memory in MB allocated to the application's running
containers. Called 'allocated_mb' in searches.
```
```
Allocated Memory Seconds
(allocated_memory_seconds)
```
```
NUMBER TRUE The amount of memory the application has allocated (megabyte-
seconds). Called 'allocated_memory_seconds' in searches.
```
```
Allocated VCores
(allocated_vcores)
```
```
NUMBER FALSE The sum of virtual cores allocated to the application's running
containers. Called 'allocated_vcores' in searches.
```
```
Allocated VCore Seconds
(allocated_vcore_seconds)
```
```
NUMBER TRUE The amount of CPU resources the application has allocated
(virtual core-seconds). Called 'allocated_vcore_seconds' in
searches.
Application ID
(application_id)
```
```
STRING FALSE The ID of the YARN application. Called 'application_id' in
searches.
```
```
Application State
(state)
```
```
STRING TRUE The state of this YARN application. This reflects the
ResourceManager state while the application is running and
the JobHistory Server state after the application has completed.
Called 'state' in searches.
Application Tags
(application_tags)
```
```
STRING FALSE A list of tags for the application. Called 'application_tags' in
searches.
```
```
Application Type
(application_type)
```
```
STRING TRUE The type of the YARN application. Called 'application_type' in
searches.
```
```
Bytes Read
(bytes_read)
```
```
BYTES TRUE Bytes read. Called 'bytes_read' in searches.
```
```
Bytes Written
(bytes_written)
```
```
BYTES TRUE Bytes written. Called 'bytes_written' in searches.
```
```
Combine Input Records
(combine_input_records)
```
```
NUMBER TRUE Combine input records. Called 'combine_input_records' in
searches.
```
```
Combine Output Records
(combine_output_records)
```
```
NUMBER TRUE Combine output records. Called 'combine_output_records' in
searches.
```
```
Committed Heap
(committed_heap_bytes)
```
```
BYTES TRUE Total committed heap usage. Called 'committed_heap_bytes' in
searches.
```

Cloudera Manager Monitoring Activities

```
Display Name
(Attribute Name)
```
```
Type Supports
Filtering?
```
```
Description
```
```
Completed Maps and Reduces
(tasks_completed)
```
```
NUMBER TRUE The number of completed map and reduce tasks in this
MapReduce job. Called 'tasks_completed' in searches. Available
only for running jobs.
CPU Allocation
(vcores_millis)
```
```
NUMBER TRUE CPU allocation. This is the sum of 'vcores_millis_maps' and
'vcores_millis_reduces'. Called 'vcores_millis' in searches.
```
```
CPU Time
(cpu_milliseconds)
```
```
MILLISECONDSTRUE CPU time. Called 'cpu_milliseconds' in searches.
```
```
Data Local Maps
(data_local_maps)
```
```
NUMBER TRUE Data local maps. Called 'data_local_maps' in searches.
```
```
Data Local Maps Percentage
(data_local_maps_percentage)
```
```
NUMBER TRUE The number of data local maps as a percentage of the total
number of maps. Called 'data_local_maps_percentage' in
searches.
Diagnostics
(diagnostics)
```
```
STRING FALSE Diagnostic information on the YARN application. If the
diagnostic information is long, this may only contain the
beginning of the information. Called 'diagnostics' in searches.
Duration
(application_duration)
```
```
MILLISECONDSTRUE How long YARN took to run this application. Called
'application_duration' in searches.
```
```
Executing
(executing)
```
```
BOOLEAN FALSE Whether the YARN application is currently running. Called
'executing' in searches.
```
```
Failed Map and Reduce Attempts
(failed_tasks_attempts)
```
```
NUMBER TRUE The number of failed map and reduce attempts for this
MapReduce job. Called 'failed_tasks_attempts' in searches.
Available only for failed jobs.
Failed Map Attempts
(failed_map_attempts)
```
```
NUMBER TRUE The number of failed map attempts for this MapReduce job.
Called 'failed_map_attempts' in searches. Available only for
running jobs.
Failed Maps
(num_failed_maps)
```
```
NUMBER TRUE Failed maps. Called 'num_failed_maps' in searches.
```
```
Failed Reduce Attempts
(failed_reduce_attempts)
```
```
NUMBER TRUE The number of failed reduce attempts for this MapReduce job.
Called 'failed_reduce_attempts' in searches. Available only for
running jobs.
Failed Reduces
(num_failed_reduces)
```
```
NUMBER TRUE Failed reduces. Called 'num_failed_reduces' in searches.
```
```
Failed Shuffles
(failed_shuffle)
```
```
NUMBER TRUE Failed shuffles. Called 'failed_shuffle' in searches.
```
```
Failed Tasks
(num_failed_tasks)
```
```
NUMBER TRUE The total number of failed tasks. This is the sum of
'num_failed_maps' and 'num_failed_reduces'. Called
'num_failed_tasks' in searches.
Fallow Map Slots Time
(fallow_slots_millis_maps)
```
```
MILLISECONDSTRUE Fallow map slots time. Called 'fallow_slots_millis_maps' in
searches.
```
```
Fallow Reduce Slots Time
(fallow_slots_millis_reduces)
```
```
MILLISECONDSTRUE Fallow reduce slots time. Called 'fallow_slots_millis_reduces' in
searches.
```
```
Fallow Slots Time
(fallow_slots_millis)
```
```
MILLISECONDSTRUE Total fallow slots time. This is the sum of
'fallow_slots_millis_maps' and 'fallow_slots_millis_reduces'.
Called 'fallow_slots_millis' in searches.
```

Cloudera Manager Monitoring Activities

```
Display Name
(Attribute Name)
```
```
Type Supports
Filtering?
```
```
Description
```
```
File Bytes Read
(file_bytes_read)
```
```
BYTES TRUE File bytes read. Called 'file_bytes_read' in searches.
```
```
File Bytes Written
(file_bytes_written)
```
```
BYTES TRUE File bytes written. Called 'file_bytes_written' in searches.
```
```
File Large Read Operations
(file_large_read_ops)
```
```
NUMBER TRUE File large read operations. Called 'file_large_read_ops' in
searches.
```
```
File Read Operations
(file_read_ops)
```
```
NUMBER TRUE File read operations. Called 'file_read_ops' in searches.
```
```
File Write Operations
(file_write_ops)
```
```
NUMBER TRUE File write operations. Called 'file_large_write_ops' in searches.
```
```
Garbage Collection Time
(gc_time_millis)
```
```
MILLISECONDSTRUE Garbage collection time. Called 'gc_time_millis' in searches.
```
```
HDFS Bytes Read
(hdfs_bytes_read)
```
```
BYTES TRUE HDFS bytes read. Called 'hdfs_bytes_read' in searches.
```
```
HDFS Bytes Written
(hdfs_bytes_written)
```
```
BYTES TRUE HDFS bytes written. Called 'hdfs_bytes_written' in searches.
```
```
HDFS Large Read Operations
(hdfs_large_read_ops)
```
```
NUMBER TRUE HDFS large read operations. Called 'hdfs_large_read_ops' in
searches.
```
```
HDFS Read Operations
(hdfs_read_ops)
```
```
NUMBER TRUE HDFS read operations. Called 'hdfs_read_ops' in searches.
```
```
HDFS Write Operations
(hdfs_write_ops)
```
```
NUMBER TRUE HDFS write operations. Called 'hdfs_write_ops' in searches.
```
```
Hive Query ID
(hive_query_id)
```
```
STRING FALSE If this MapReduce job ran as a part of a Hive query, this field
contains the ID of the Hive query. Called 'hive_query_id' in
searches.
Hive Query String
(hive_query_string)
```
```
STRING TRUE If this MapReduce job ran as a part of a Hive query, this field
contains the string of the query. Called 'hive_query_string' in
searches.
Hive Sentry Subject Name
(hive_sentry_subject_name)
```
```
STRING TRUE If this MapReduce job ran as a part of a Hive query on a secured
cluster using impersonation, this field contains the name of the
user that initiated the query. Called 'hive_sentry_subject_name'
in searches.
Input Directory
(input_dir)
```
```
STRING TRUE The input directory for this MapReduce job. Called 'input_dir' in
searches.
```
```
Input Split Bytes
(split_raw_bytes)
```
```
BYTES TRUE Input split bytes. Called 'split_raw_bytes' in searches.
```
```
Killed Map and Reduce Attempts
(killed_tasks_attempts)
```
```
NUMBER TRUE The number of map and reduce attempts that were killed by
user(s) for this MapReduce job. Called 'killed_tasks_attempts' in
searches. Available only for killed jobs.
Killed Map Attempts
(killed_map_attempts)
```
```
NUMBER TRUE The number of map attempts killed by user(s) for this
MapReduce job. Called 'killed_map_attempts' in searches.
Available only for running jobs.
```

Cloudera Manager Monitoring Activities

```
Display Name
(Attribute Name)
```
```
Type Supports
Filtering?
```
```
Description
```
```
Killed Reduce Attempts
(killed_reduce_attempts)
```
```
NUMBER TRUE The number of reduce attempts killed by user(s) for this
MapReduce job. Called 'killed_reduce_attempts' in searches.
Available only for running jobs.
Launched Map Tasks
(total_launched_maps)
```
```
NUMBER TRUE Launched map tasks. Called 'total_launched_maps' in searches.
```
```
Launched Reduce Tasks
(total_launched_reduces)
```
```
NUMBER TRUE Launched reduce tasks. Called 'total_launched_reduces' in
searches.
```
```
Map and Reduce Attempts in NEW State
(new_tasks_attempts)
```
```
NUMBER TRUE The number of map and reduce attempts in NEW state for
this MapReduce job. Called 'new_tasks_attempts' in searches.
Available only for running jobs.
Map Attempts in NEW State
(new_map_attempts)
```
```
NUMBER TRUE The number of map attempts in NEW state for this MapReduce
job. Called 'new_map_attempts' in searches. Available only for
running jobs.
Map Class
(mapper_class)
```
```
STRING TRUE The class used by the map tasks in this MapReduce job. Called
'mapper_class' in searches. You can search for the mapper class
using the class name alone, for example 'QuasiMonteCarlo
$QmcMapper', or the fully qualified classname, for example,
'org.apache.hadoop.examples.QuasiMonteCarlo$QmcMapper'.
Map CPU Allocation
(vcores_millis_maps)
```
```
NUMBER TRUE Map CPU allocation. Called 'vcores_millis_maps' in searches.
```
```
Map Input Records
(map_input_records)
```
```
NUMBER TRUE Map input records. Called 'map_input_records' in searches.
```
```
Map Memory Allocation
(mb_millis_maps)
```
```
NUMBER TRUE Map memory allocation. Called 'mb_millis_maps' in searches.
```
```
Map Output Bytes
(map_output_bytes)
```
```
BYTES TRUE Map output bytes. Called 'map_output_bytes' in searches.
```
```
Map Output Materialized Bytes
(map_output_materialized_bytes)
```
```
BYTES TRUE Map output materialized bytes. Called
'map_output_materialized_bytes' in searches.
```
```
Map Output Records
(map_output_records)
```
```
NUMBER TRUE Map output records. Called 'map_output_records' in searches.
```
```
Map Progress
(map_progress)
```
```
NUMBER TRUE The percentage of maps completed for this MapReduce job.
Called 'map_progress' in searches. Available only for running
jobs.
Maps Completed
(maps_completed)
```
```
NUMBER TRUE The number of map tasks completed as a part of this
MapReduce job. Called 'maps_completed' in searches.
```
```
Map Slots Time
(slots_millis_maps)
```
```
MILLISECONDSTRUE Total time spent by all maps in occupied slots. Called
'slots_millis_maps' in searches.
```
```
Maps Pending
(maps_pending)
```
```
NUMBER TRUE The number of maps waiting to be run for this MapReduce job.
Called 'maps_pending' in searches. Available only for running
jobs.
Maps Running
(maps_running)
```
```
NUMBER TRUE The number of maps currently running for this MapReduce job.
Called 'maps_running' in searches. Available only for running
jobs.
Maps Total
(maps_total)
```
```
NUMBER TRUE The number of Map tasks in this MapReduce job. Called
'maps_total' in searches.
```

Cloudera Manager Monitoring Activities

```
Display Name
(Attribute Name)
```
```
Type Supports
Filtering?
```
```
Description
```
```
Memory Allocation
(mb_millis)
```
```
NUMBER TRUE Total memory allocation. This is the sum of 'mb_millis_maps'
and 'mb_millis_reduces'. Called 'mb_millis' in searches.
```
```
Merged Map Outputs
(merged_map_outputs)
```
```
NUMBER TRUE Merged map outputs. Called 'merged_map_outputs' in searches.
```
```
Name
(name)
```
```
STRING TRUE Name of the YARN application. Called 'name' in searches.
```
```
Oozie Workflow ID
(oozie_id)
```
```
STRING FALSE If this MapReduce job ran as a part of an Oozie workflow, this
field contains the ID of the Oozie workflow. Called 'oozie_id' in
searches.
Other Local Maps
(other_local_maps)
```
```
NUMBER TRUE Other local maps. Called 'other_local_maps' in searches.
```
```
Other Local Maps Percentage
(other_local_maps_percentage)
```
```
NUMBER TRUE The number of other local maps as a percentage of the total
number of maps. Called 'other_local_maps_percentage' in
searches.
Output Directory
(output_dir)
```
```
STRING TRUE The output directory for this MapReduce job. Called 'output_dir'
in searches.
```
```
Pending Maps and Reduces
(tasks_pending)
```
```
NUMBER TRUE The number of maps and reduces waiting to be run for this
MapReduce job. Called 'tasks_pending' in searches. Available
only for running jobs.
Physical Memory
(physical_memory_bytes)
```
```
BYTES TRUE Physical memory. Called 'physical_memory_bytes' in searches.
```
```
Pig Script ID
(pig_id)
```
```
STRING FALSE If this MapReduce job ran as a part of a Pig script, this field
contains the ID of the Pig script. Called 'pig_id' in searches.
```
```
Pool
(pool)
```
```
STRING TRUE The name of the resource pool in which this application ran.
Called 'pool' in searches. Within YARN, a pool is referred to as
a queue.
Progress
(progress)
```
```
NUMBER TRUE The progress reported by the application. Called 'progress' in
searches.
```
```
Rack Local Maps
(rack_local_maps)
```
```
NUMBER TRUE Rack local maps. Called 'rack_local_maps' in searches.
```
```
Rack Local Maps Percentage
(rack_local_maps_percentage)
```
```
NUMBER TRUE The number of rack local maps as a percentage of the total
number of maps. Called 'rack_local_maps_percentage' in
searches.
Reduce Attempts in NEW State
(new_reduce_attempts)
```
```
NUMBER TRUE The number of reduce attempts in NEW state for this
MapReduce job. Called 'new_reduce_attempts' in searches.
Available only for running jobs.
Reduce Class
(reducer_class)
```
```
STRING TRUE The class used by the reduce tasks in this MapReduce
job. Called 'reducer_class' in searches. You can search for
the reducer class using the class name alone, for example
'QuasiMonteCarlo$QmcReducer', or fully qualified classname,
for example, 'org.apache.hadoop.examples.QuasiMonteCarlo
$QmcReducer'.
Reduce CPU Allocation
(vcores_millis_reduces)
```
```
NUMBER TRUE Reduce CPU allocation. Called 'vcores_millis_reduces' in
searches.
```
```
Reduce Input Groups
(reduce_input_groups)
```
```
NUMBER TRUE Reduce input groups. Called 'reduce_input_groups' in searches.
```

Cloudera Manager Monitoring Activities

```
Display Name
(Attribute Name)
```
```
Type Supports
Filtering?
```
```
Description
```
```
Reduce Input Records
(reduce_input_records)
```
```
NUMBER TRUE Reduce input records. Called 'reduce_input_records' in searches.
```
```
Reduce Memory Allocation
(mb_millis_reduces)
```
```
NUMBER TRUE Reduce memory allocation. Called 'mb_millis_reduces' in
searches.
```
```
Reduce Output Records
(reduce_output_records)
```
```
NUMBER TRUE Reduce output records. Called 'reduce_output_records' in
searches.
```
```
Reduce Progress
(reduce_progress)
```
```
NUMBER TRUE The percentage of reduces completed for this MapReduce job.
Called 'reduce_progress' in searches. Available only for running
jobs.
Reduces Completed
(reduces_completed)
```
```
NUMBER TRUE The number of reduce tasks completed as a part of this
MapReduce job. Called 'reduces_completed' in searches.
```
```
Reduce Shuffle Bytes
(reduce_shuffle_bytes)
```
```
BYTES TRUE Reduce shuffle bytes. Called 'reduce_shuffle_bytes' in searches.
```
```
Reduce Slots Time
(slots_millis_reduces)
```
```
MILLISECONDSTRUE Total time spent by all reduces in occupied slots. Called
'slots_millis_reduces' in searches.
```
```
Reduces Pending
(reduces_pending)
```
```
NUMBER TRUE The number of reduces waiting to be run for this MapReduce
job. Called 'reduces_pending' in searches. Available only for
running jobs.
Reduces Running
(reduces_running)
```
```
NUMBER TRUE The number of reduces currently running for this MapReduce
job. Called 'reduces_running' in searches. Available only for
running jobs.
Reduces Total
(reduces_total)
```
```
NUMBER TRUE The number of reduce tasks in this MapReduce job. Called
'reduces_total' in searches.
```
```
Running Containers
(running_containers)
```
```
NUMBER FALSE The number of containers currently running for the application.
Called 'running_containers' in searches.
```
```
Running Map and Reduce Attempts
(running_tasks_attempts)
```
```
NUMBER TRUE The number of map and reduce attempts currently running
for this MapReduce job. Called 'running_tasks_attempts' in
searches. Available only for running jobs.
Running Map Attempts
(running_map_attempts)
```
```
NUMBER TRUE The number of running map attempts for this MapReduce job.
Called 'running_map_attempts' in searches. Available only for
running jobs.
Running MapReduce Application Information
Retrieval Duration.
(running_application_info_retrieval_time)
```
```
NUMBER TRUE How long it took, in seconds, to retrieve information about the
MapReduce application.
```
```
Running Maps and Reduces
(tasks_running)
```
```
NUMBER TRUE The number of maps and reduces currently running for this
MapReduce job. Called 'tasks_running' in searches. Available
only for running jobs.
Running Reduce Attempts
(running_reduce_attempts)
```
```
NUMBER TRUE The number of running reduce attempts for this MapReduce job.
Called 'running_reduce_attempts' in searches. Available only for
running jobs.
Service Name
(service_name)
```
```
STRING FALSE The name of the YARN service. Called 'service_name' in
searches.
```
```
Shuffle Bad ID Errors
(shuffle_errors_bad_id)
```
```
NUMBER TRUE Shuffle bad ID errors. Called 'shuffle_errors_bad_id' in searches.
```

Cloudera Manager Monitoring Activities

```
Display Name
(Attribute Name)
```
```
Type Supports
Filtering?
```
```
Description
```
```
Shuffle Connection Errors
(shuffle_errors_connection)
```
```
NUMBER TRUE Shuffle connection errors. Called 'shuffle_errors_connection' in
searches.
```
```
Shuffled Maps
(shuffled_maps)
```
```
NUMBER TRUE Shuffled maps. Called 'shuffled_maps' in searches.
```
```
Shuffle IO Errors
(shuffle_errors_io)
```
```
NUMBER TRUE Shuffle IO errors. Called 'shuffle_errors_io' in searches.
```
```
Shuffle Wrong Length Errors
(shuffle_errors_wrong_length)
```
```
NUMBER TRUE Shuffle wrong length errors. Called
'shuffle_errors_wrong_length' in searches.
```
```
Shuffle Wrong Map Errors
(shuffle_errors_wrong_map)
```
```
NUMBER TRUE Shuffle wrong map errors. Called 'shuffle_errors_wrong_map' in
searches.
```
```
Shuffle Wrong Reduce Errors
(shuffle_errors_wrong_reduce)
```
```
NUMBER TRUE Shuffle wrong reduce errors. Called
'shuffle_errors_wrong_reduce' in searches.
```
```
Slots Time
(slots_millis)
```
```
MILLISECONDSTRUE Total slots time. This is the sum of 'slots_millis_maps' and
'slots_millis_reduces'. Called 'slots_millis' in searches.
```
```
Spilled Records
(spilled_records)
```
```
NUMBER TRUE Spilled Records. Called 'spilled_records' in searches.
```
```
Successful Map and Reduce Attempts
(successful_tasks_attempts)
```
```
NUMBER TRUE The number of successful map and reduce attempts for this
MapReduce job. Called 'successful_tasks_attempts' in searches.
Available only for successful jobs.
Successful Map Attempts
(successful_map_attempts)
```
```
NUMBER TRUE The number of successful map attempts for this MapReduce job.
Called 'successful_map_attempts' in searches. Available only for
running jobs.
Successful Reduce Attempts
(successful_reduce_attempts)
```
```
NUMBER TRUE The number of successful reduce attempts for this MapReduce
job. Called 'successful_reduce_attempts' in searches. Available
only for running jobs.
Total Maps and Reduces Number
(total_task_num)
```
```
NUMBER TRUE The number of map and reduce tasks in this MapReduce job.
Called 'tasks_total' in searches. Available only for running jobs.
```
```
Total Tasks
(total_launched_tasks)
```
```
NUMBER TRUE The total number of tasks. This is the sum of
'total_launched_maps' and 'total_launched_reduces'. Called
'total_launched_tasks' in searches.
Tracking Url
(tracking_url)
```
```
STRING FALSE The MapReduce application tracking URL.
```
```
Uberized Job
(uberized)
```
```
BOOLEAN FALSE Whether this MapReduce job is uberized - running completely
in the ApplicationMaster. Called 'uberized' in searches.
Available only for running jobs.
Unused Memory Seconds
(unused_memory_seconds)
```
```
NUMBER TRUE The amount of memory the application has allocated but not
used (megabyte-seconds). This metric is calculated hourly
if container usage metric aggregation is enabled. Called
'unused_memory_seconds' in searches.
Unused VCore Seconds
(unused_vcore_seconds)
```
```
NUMBER TRUE The amount of CPU resources the application has allocated
but not used (virtual core-seconds). This metric is calculated
hourly if container usage metric aggregation is enabled. Called
'unused_vcore_seconds' in searches.
Used Memory Max
(used_memory_max)
```
```
NUMBER TRUE The maximum container memory usage for a YARN
application. This metric is calculated hourly if container
usage metric aggregation is enabled and a Cloudera Manager
Container Usage Metrics Directory is specified.
```

```
Display Name
(Attribute Name)
```
```
Type Supports
Filtering?
```
```
Description
```
```
User
(user)
```
```
STRING TRUE The user who ran the YARN application. Called 'user' in
searches.
```
```
Virtual Memory
(virtual_memory_bytes)
```
```
BYTES TRUE Virtual memory. Called 'virtual_memory_bytes' in searches.
```
```
Work CPU Time
(cm_cpu_milliseconds)
```
```
MILLISECONDSTRUE Attribute measuring the sum of CPU time used by all threads of
the query, in milliseconds. Called 'work_cpu_time' in searches.
For Impala queries, CPU time is calculated based on the
'TotalCpuTime' metric. For YARN MapReduce applications,
this is calculated from the 'cpu_milliseconds' metric.
```
```
Examples
Consider the following filter expressions: user = "root", rowsProduced > 0, fileFormats RLIKE ".TEXT.*", and exec
uting = true. In the examples:
```
- The filter attributes are user, rowsProduced, fileFormats, and executing.
- The operators are =, >, and RLIKE.
- The filter values are root, 0, .TEXT.*, and true.

#### Sending Diagnostic Data to Cloudera for YARN Applications

```
You can send diagnostic data collected from YARN applications, including metadata, configurations, and log data, to
Cloudera Support for analysis. Include a support ticket number if one exists to enable Cloudera Support to address the
issue more quickly and efficiently.
```
```
About this task
Minimum Required Role: Cluster Administrator (also provided by Full Administrator)
```
```
Procedure
```
- From the YARN page in Cloudera Manager, click the Applications menu.
- Collect diagnostics data. There are two ways to do this:
    - To collect data from all applications that are visible in the list, click the top Collect Diagnostics Data button on
       the upper right, above the list of YARN applications.
    - To collect data from only one specific application, click the down arrow on the right-hand end of the row of
       the application and select Collect Diagnostics Data.
- In the Send YARN Applications Diagnostic Data dialog box, provide the following information:
    - If applicable, the Cloudera Support ticket number of the issue being experienced on the cluster.
    - Optionally, add a comment to help the support team understand the issue.
- Click the checkbox Send Diagnostic Data to Cloudera.
- Click the button Collect and Send Diagnostic Data.
    Note: Passwords from configuration will not be retrieved.

### Monitoring Spark Applications..

```
To obtain information about Spark application behavior you can consult cluster manager logs and the Spark web
application UI. These two methods provide complementary information.
Logs enable you to see fine grained events in the lifecycle of an application. The web UI provides both a broad
overview of the various aspects of Spark application behavior and fine grained metrics. This section provides an
overview of both methods.
For further information on Spark monitoring, see the Spark documentation on monitoring and instrumentation.
Related Information
Monitoring and Instrumentation
```
#### Viewing and Debugging Spark Applications Using Logs..

```
You can view overview information about all running Spark applications.
```
```
Procedure
```
1. Go to the YARN Applications page in the Cloudera Manager Admin Console.
2. To debug Spark applications running on YARN, view the logs for the NodeManager role. Open the log event
    viewer.
3. Filter the event stream.
4. For any event, click View Log File to view the entire log file.

#### Managing Spark Driver Logs

```
You can change the default directory for Spark driver logs, or disable the log collection.
```
```
About this task
The Spark service collects Spark driver logs when Spark applications are run in YARN-client mode or with the Spark
Shell. This feature is enabled by default, and the logs are persisted to an HDFS directory and included in YARN
Diagnostic Bundles. The default directory for the logs is /user/spark/driverLogs.
```
```
Procedure
```
1. In the Cloudera Manager Admin Console, go to the Spark service.
2. Select the Configuration page.
3. Configure the default log directory, or disable the log collection:
    - To configure the default log directory, search for the Spark Driver Log Location configuration and change the
       directory specified in the field.
    - To disable the log collection, search for the Persist Driver Logs to Dfs configuration.
4. Save the changes.
5. Deploy the updated client configuration.

#### Visualizing Spark Applications Using the Web Application UI..

```
Every Spark application launches a web application UI that displays useful information about the application.
The web application UI includes the following information:
```
- An event timeline that displays the relative ordering and interleaving of application events. The timeline view is
    available on three levels: across all jobs, within one job, and within one stage. The timeline also shows executor
    allocation and deallocation.
- A list of stages and tasks.
- The execution directed acyclic graph (DAG) for each job.
- A summary of RDD sizes and memory usage.
- Environment - runtime information, property settings, library paths.
- Information about Spark SQL jobs.
The web UI is available in different ways depending on whether the application is running or has completed.

#### Accessing the Web UI of a Running Spark Application.

```
You can access the web UI of a running Spark application from a web browser.
To access the web application UI of a running Spark application, open http://spark_driver_host:4040 in a web
browser. If multiple applications are running on the same host, the web application binds to successive ports
beginning with 4040 (4041, 4042, and so on). The web application is available only for the duration of the
application.
```
#### Accessing the Web UI of a Completed Spark Application

```
You can access the web application UI of a completed Spark application through the Spark history server.
```
```
Procedure
```
1. Open the Spark History Server UI in one of the following ways:
    - Open the URL [http://spark_history_server_host:18088.](http://spark_history_server_host:18088.)
    - Open the UI in the Cloudera Manager Admin Console:
       a. Go to the Spark service.
       b. Click the History Server Web UI link.
    The History Server displays a list of completed applications.
2. In the list of applications, click an App ID link. The application UI displays.
    Note: In CDH 5.10 and higher, and in CDK 2.x Powered By Apache Spark, the Storage tab of the Spark
    History Server is always blank. To see storage information while an application is running, use the
    web UI of the application as described in the previous section. After the application is finished, storage
    information is not available.
Example Spark Application Web Application
Consider a job consisting of a set of transformation to join data from an accounts dataset with a weblogs dataset in
order to determine the total number of web results for every account and then an action write the result to HDFS. In
this example, the write is performed twice, resulting in two jobs. To view the application UI, in the History Server
click the link in the App ID column:

```
The following screenshot shows the timeline of the events in the application including the jobs that were run and the
allocation and deallocation of executors. Each job shows the last action, saveAsTextFile, run for the job. The timeline
shows that the application acquires executors over the course of running the first job. After the second job finishes,
the executors become idle and are returned to the cluster.
```
```
You can manipulate the timeline as follows:
```
- Pan - Press and hold the left mouse button and swipe left and right.
- Zoom - Select the Enable zooming checkbox and scroll the mouse up and down.
To view the details for Job 0, click the link in the Description column. The following screenshot shows details of each
stage in Job 0 and the DAG visualization. Zooming in shows finer detail for the segment from 28 to 42 seconds:

```
Clicking a stage shows further details and metrics:
```

Cloudera Manager Monitoring Activities

```
The web page for Job 1 shows how preceding stages are skipped because Spark retains the results from those stages:
```
```
Example Spark SQL Web Application
In addition to the screens described above, the web application UI of an application that uses the Spark SQL API
also has an SQL tab. Consider an application that loads the contents of two tables into a pair of DataFrames, joins
```

Cloudera Manager Monitoring Activities

```
the tables, and then shows the result. After you click the application ID, the SQL tab displays the final action in the
query:
```
```
If you click the show link you see the DAG of the job. Clicking the Details link on this page displays the logical
query plan:
```

```
Example Spark Streaming Web Application
Note: The following example demonstrates the Spark driver web UI. Streaming information is not captured
in the Spark History Server.
```
```
The Spark driver web application UI also supports displaying the behavior of streaming applications in the Streaming
tab. If you run the example described in the Spark streaming example, and provide three bursts of data, the top of the
tab displays a series of visualizations of the statistics summarizing the overall behavior of the streaming application:
```
```
The application has one receiver that processed 3 bursts of event batches, which can be observed in the events,
processing time, and delay graphs. Further down the page you can view details of individual batches:
```

```
To view the details of a specific batch, click a link in the Batch Time column. Clicking the 2016/06/16 14:23:20 link
with 8 events in the batch, provides the following details:
```


## Viewing Charts for Cluster, Service, Role, and Host Instances

```
For cluster, service, role, and host instances, you can see dashboards of charts of various metrics relevant to the entity
you are viewing. While the metrics displayed are different for each entity, the basic functionality works in the same
way.
The HomeStatus tab for clusters and the Status tab for a service, role, or host display dashboards containing a limited
set of charts.
The Status page Charts Library tab displays a dashboard containing a much larger set of charts, organized by
categories such as process charts, host charts, CPU charts, and so on, depending on the entity (service, role, or host)
that you are viewing.
A custom dashboard is displayed by default when you view the Status tab for an entity. You can switch between
```
```
custom and default dashboards by using the edit button to the upper right of the chart.
```
```
Displaying Information from Charts
There are various ways to display information from charts.
```
- Click the icon at the top right to see a menu for opening the chart in the Chart Builder or exporting its data.
- Change the size of a chart on a dashboard by dragging the lower-right corner of the chart.
- Hovering with the mouse over a stream on a chart (for example, a line on a line chart) opens a small pop-up
    window that displays information about that stream. Move the mouse horizontally to see the data values change in
    the small pop-up window, based on the time represented at the mouse's position along the chart's horizontal axis.
    Click any stream within the chart to display a larger pop-up window that includes additional information for the
    stream at the point in time where the mouse was clicked. At the bottom of the large pop-up window is a button for
    viewing the Cloudera Manager page for the entity (service, host, role, query, or application) associated with the
    chart, if applicable (View Service, View Host, and so on). Click the button View Entity Chart to display a chart


Cloudera Manager Viewing Charts for Cluster, Service, Role, and Host Instances

```
for the stream on its own page. If the chart displays more than one stream, the new chart displays only the stream
that was selected when the button was clicked.
```
- The chart page includes an editable text field containing a default title based on the select statement that was used
    to create the chart. This title will be used if you save the chart as a dashboard. Type a new title for the chart into
    this field, if desired.

### Exporting Data from Charts

```
You can export data from charts in either JSON or CSV format.
```
```
Procedure
```
- On the HomeStatus tab, hover over the chart that you want to export data from.
- Click the icon in the upper right corner of the chart.
    - Click Export JSON to display the chart data in JSON format in a new browser window.
    - Click Export CSV to open a Save dialog box enabling you to save the data as a CSV file. Choose a program to
       open the CSV, or open the file with your system's default program for editing and displaying CSV files.
          Note: Time values that appear in Cloudera Manager charts reflect the time zone setting on the Cloudera
          Manager client machine, but time values returned by the Cloudera Manager API (including those that
          appear in JSON and CSV files exported from charts) reflect Coordinated Universal Time (UTC). For more
          information on the timestamp format, see the Cloudera Manager API documentation, for example, ApiT
          imeSeriesData.java.

### Adding and Removing Charts from a Dashboard.............................................................................................

```
You can add a chart to a dashboard or remove a chart from a custom dashboard. When you add a chart to a dashboard,
you can add it to an existing dashboard or a new custom dashboard, which creates a new dashboard at the same time.
```
```
About this task
Minimum Required Role: Configurator (also provided by Cluster Administrator, Limited Cluster Administrator , and
Full Administrator)
```
```
Procedure
```
- On the HomeStatus tab, hover over the chart that you want to export data from.
- To add a chart to a custom dashboard, click the icon in the upper right corner of the chart and then click Add to
    Dashboard.
    - To add the chart to an existing dashboard, select Add chart to an existing custom or system dashboard and then
       the dashboard name.
    - To add the chart to a new dashboard, select Add chart to a new custom dashboard and enter a name for the
       dashboard in the Dashboard Name field.

```
To remove a chart from a custom dashboard, click the icon in the upper right corner of the chart and then click
Remove. The Remove button does not appear in the menu when the default dashboard is used because the default
```
```
dashboard does not allow removing the original charts. Use the edit button to the upper right of the chart
```


```
to switch between custom and default dashboards. The Remove button is only available to users with the required
roles.
```
### Creating Triggers from Charts

```
You can create a trigger for most charts. Triggers allow you to define actions to be taken when a specified condition
is met.
```
```
About this task
Minimum Required Role: Full Administrator. This feature is not available when using Cloudera Manager to manage
Data Hub clusters.
```
```
Procedure
```
- On the HomeStatus tab, hover over the chart that you want to create a trigger for.
- Click the icon in the upper right corner of the chart and select Create Trigger.
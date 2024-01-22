## Time Line...................................................................................................................

```
The Time Line allows you to view status and health information for a specific point in time or across a range of time.
The Time Line appears on many pages in Cloudera Manager.
When you view the top level service and Hosts tabs, the Time Line shows status and health only for a specific point
in time. When you are viewing the Logs and Events tabs, and when you are viewing the Status, Commands, Audits,
Jobs, Applications, and Queries pages of individual services, roles, and hosts, the Time Line appears as a Time Range
Selector, which lets you highlight a range of time over which to view historical data.
```
```
Click the ( ) icon at the far right to turn on and turn off the display of the Time Line.
Cloudera Manager displays timestamped data using the time zone of the host where Cloudera Manager server is
running. The time zone information can be found under the Support About menu.
The background chart in the Time Line shows the percentage of CPU utilization on all hosts in the cluster, updated
at approximately one-minute intervals, depending on the total visible time range. You can use this graph to identify
periods of activity that may be of interest.
In the pages that support a time range selection, the area between the handles shows the selected time range.
```
```
There are a variety of ways to change the time range in this mode.
```

Cloudera Manager Time Line

```
The Reports screen ( Clusters Reports ) does not support the Time Range Selector: the historical reports accessed
from the Reports screen have their own time range selection mechanism.
```
```
Use the Zoom In and Zoom Out buttons ( and ) to zoom the time line graph in or out.
```
- Zoom In shows a shorter time period with more detailed interval segments. Zooming does not change your
    selected time range. However, the ability to zoom the Time Line can make it easier to use the selector to highlight
    a time range.
- Zoom Out lets you show a longer time period on the time range graph (with correspondingly less granular
    segmentation).


### Selecting a Point In Time or a Time Range......................................................................................................

```
Depending on what page the Time Line appears, you can select a point in time or a time range.
There are two ways to look at information about your cluster—its current status and health, or its status and health
at some point (or during some interval) in the past. When you are looking at a point in the past, some functions may
not be available. For example, on a Service Status page, the Actions menu (where you can take actions like stopping,
starting, or restarting services or roles) is accessible only when you are looking at Current status.
```
```
Selecting a Point in Time
Status information on pages such as the service Status pages, reflects the state at a single point in time (a snapshot of
the health and status). When displayed data is from a single point in time (a snapshot), the panel or column displays
a small version of the Time Marker icon ( ) in the panel. This indicates that the data corresponds to the time at the
location of the Time Marker on the Time Line.
By default, the status is shown at the current time. If you specify an earlier point on the time range graph, you see the
status as it was at the selected point in the past.
```
- When the Time Marker is set to the current time, it is blue ( ).
- When the Time Marker is set to a time in the past, it is orange ( ).

```
You can select the point in time in one of the following ways:
```
- By moving the Time Marker ( )
- When the Time Marker is set to a past time, you can quickly switch back to view the current time using the Now
    button ( ).
- By clicking the date, choosing the date and time, and clicking Apply.

```
Selecting a Time Range
Pages such as the Logs, Events, and Activities show data over a time range rather than at a single point. These default
to showing the past 30 minutes of data (ending at the current time). The charts that appear on the individual Service
Status and Host Status pages also show data over a time range. For this type of display, there are several ways to
select a time range of interest:
```
- Drag one (or both) edges of the time range handles to expand or contract the range.

```
Choose a duration by clicking a duration link and
then do one of the following:
```
- Click the next or previous buttons to select the next or previous duration.
- Click somewhere in the dark portion of the time range to choose the selected duration.
- Click the date range

```
to open the time selection widget. Enter a start and end time and click Apply to put your choice into effect.
```
- When you are under the Clusters tab with an individual activity selected, a Zoom to Duration button is available.
    This lets you zoom the time selection to include just the time range that corresponds to the duration of your
    selected activity.
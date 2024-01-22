## Triggers

```
A trigger is a statement that specifies an action to be taken when one or more specified conditions are met for a
service, role, role configuration group, or host. The conditions are expressed as a tsquery statement, and the action to
be taken is to change the health for the service, role, role configuration group, or host to either Concerning (yellow) or
Bad (red).
```

Cloudera Manager Triggers

```
Triggers can be created for services, roles, role configuration groups, or hosts. Create a trigger by doing one of the
following:
```
- Directly editing the configuration for the service, role (or role configuration group), or host configuration.
- Clicking Create Trigger on the drop-down menu for most charts. Note that the Create Trigger command is not
    available on the drop-down menu for charts where no context (role, service, and so on) is defined, such as on the
    HomeStatus tab.
       Important: Because triggers are a new and evolving feature, backward compatibility between releases is
       not guaranteed at this time.
- Use the Create Trigger expression builder.

```
The Structure of Triggers
A trigger is defined by a JSON formatted string that includes four parts:
```
- Name
- Expression
- Stream threshold
- Whether or not the trigger should be enabled
Each of the four parts of a trigger is described in the following sections.

```
Name (required)
A trigger's name must be unique in the context for which the trigger is defined. That is, there cannot be two triggers
for the same service or role with the same name. Different services or different roles can have triggers with the same
name.
```
```
Expression (required)
A trigger expression takes the form:
IF (CONDITIONS) DO HEALTH_ACTION
When the conditions of the trigger are met, the trigger is considered to be firing. A condition is any valid tsquery
statement. In most cases conditions employ stream filters to filter out streams below or above a certain threshold.
For example, the following tsquery can be used to retrieve the streams for DataNodes with more than 500 open file
descriptors:
```
```
SELECT fd_open WHERE roleType=DataNode AND last(fd_open) > 500
```
```
The stream filter used here, last(fd_open) > 50, is composed of four parts:
```
- A scalar producing function "last" that takes a stream and returns its last data point
- A metric to operate on
    Note: For more information about metric expression functions, see Metric Expression Functions.
- A comparator
- A scalar value
Other scalar producing functions are available, like min or max, and they can be combined to create arbitrarily
complex expressions:

```
last(moving_avg(fd_open)) >= 500
```
```
See the tsquery documentation for more details.
```

Cloudera Manager Triggers

```
Conditions can be combined using the logical operators AND and OR. For example, here is a trigger expression with
two conditions:
```
```
IF ((SELECT fd_open WHERE roleType=DataNode AND last(fd_open) > 500) OR (SEL
ECT fd_open WHERE roleType=NameNode AND last(fd_open) > 500)) DO health:bad
```
```
A condition is met if it returns more than the number of streams specified by the streamThreshold (see below). A
trigger fires if the logical evaluation of all of its conditions results in a met condition. When a trigger fires, two
actions can be taken: health:concerning or health:bad. These actions change the health of the entity on which the
trigger is defined.
```
```
Stream Threshold (optional)
The stream threshold determines the number of streams that need to be returned by the tsquery before the condition
is met. The default is 0; that is, if the tsquery returns any results the condition will be met. For example if the stream
threshold is set to 10 and the condition is SELECT fd_open WHERE roleType=DataNode AND last(fd_open) >
500 the condition will be considered met only if there are at least 10 DataNodes that have more than 500 file
descriptor opened, so at least 10 streams were returned by the tsquery.
```
```
Enabled (optional)
Whether the trigger is enabled. The default is true, (enabled).
Trigger Example
The following is a JSON formatted trigger that fires if there are more than 10 DataNodes with more than 500 file
descriptors opened:
```
```
[{"triggerName": "sample-trigger", "triggerExpression": "IF (SELECT fd_open
WHERE roleType = DataNode and last(fd_open) > 500) DO health:bad", "streamTh
reshold": 10, "enabled": "true"}]
```
```
Related Information
tsquery Language
```
### Creating a Trigger Using the Expression Editor

```
About this task
The Create New Trigger screen allows you to use a graphical editor to build the JSON string that defines a trigger.
You can use the expression editor section to build the tsquery statement, or you can edit the tsquery statement
manually. Triggers use the tsquery language to create trigger expressions.
```
```
Procedure
To create a trigger using the expression editor:
```

Cloudera Manager Triggers

1. Go to a service, role, role configuration group, or host configuration page and click the Create Trigger button next
    to the Health Test section.

```
The Create New Trigger screen displays.
As you build the trigger, the actual query text displays to the right, along with a preview of a chart returned by the
query.
```
2. Enter a name for the trigger in the Name field.
3. Build the metric expressions:
    a. Select the function to use in your expression, either Last, Min, or Max.
    b. Select the metric by typing its name in the Metric field. A list of available metrics displays as you type.
    c. Select the operator, either >, >=, =, <, or <=.
    d. Enter the value to use for the comparison in the Value field.
    e. (Optional) Click the + icon to add additional expressions. Additional expressions are added to the query using
       the logical operator AND.
4. (Optional) Create a predicate for the query. Under Attribute Conditions, click the + icon to add an attribute
    condition.
    A set of fields displays that you use to build an expression for the predicate.
    a. Type the attribute name in the Attribute field. A list of attributes displays as you type.
    b. Select the operator, either = or RLIKE.
    c. Enter the value for the comparison in the Value field.
    d. (Optional) Click the + icon to add additional expressions. Additional expressions are added to the predicate
       using the logical operator AND.
5. Select an Action from the drop-down menu to define the action taken when the trigger fires:
    - Mark as bad (red)
    - Mark as concerning (yellow)
6. Enter a value for the Stream Threshold. Leave the value set to 0 to include all streams; enter an integer to set the
    number of streams required to meet the condition.
7. Select Enabled to enable the trigger. If you disable the trigger, it does not run.
8. (Optional) Select Suppressed. A suppressed trigger still runs but does not impact the health display of the owning
    entity.


Cloudera Manager Triggers

9. Verify your expression:
    In the area to the right of the expression builder, in the Preview section, the expression you have built displays.
    A chart also displays the result of the query. Click Show Filtered Streams to see all streams. Click Hide Filtered
    Streams to hide streams that do not meet the stream threshold.
    You can edit your trigger using the fields in the expression builder, or you can click the Edit Manually link to
    display a text box in which you can manually edit the trigger. Click Use Editor to return to the expression builder.
       Important: If you select Edit Manually, changes you make manually do not appear in the expression
       builder when you click Use Editor.

```
10.Click Create Trigger to save your trigger.
Related Information
tsquery Language
Metric Expressions
Predicates
```
### Editing, Deleting, Suppressing, or Deleting a Trigger

```
Procedure
```
1. Go to the service, role, role configuration group, or host configuration page where the trigger was created. (For
    example: select ClustersHDFS.)
2. In the Health Tests section, click the trigger name. (You may need to click a Show ... link to expand the list of
    triggers.)
    A page displays showing the query and chart for the trigger. Click Show Filtered Streams to see all streams. Click
    Hide Filtered Streams to hide streams that do not meet the stream threshold.
3. Click the Actions drop-down menu and select one of the following actions:
    - Edit Trigger
       A page opens where you can edit the query. Click Save Trigger to save your changes.
    - Disable Trigger or Enable Trigger
    - Suppress Trigger or Unsuppress Trigger
    - Delete Trigger

### Cloudera Manager Trigger Use Cases

```
Cloudera Manager allows you to monitor cluster performance. Some indicators require timely attention to keep your
data safe. Triggers let you track occurrence and severity of issues so that you can fix problems before they result in
system failures.
The conditions you create for your trigger can be quite complex, but they do not need to be in order to be useful. This
topic describes two triggers that alert you when you are approaching capacity limits for your cluster.
```
#### Creating a Trigger for Memory Capacity

```
About this task
A common use case is to monitor memory usage, and trigger a warning if your system is approaching its upper limit.
```
```
Procedure
To create a memory usage trigger:
```

Cloudera Manager Triggers

1. In Cloudera Manager, go to the Hosts page.
2. Click a link in the Name column to open a host status page.
3. In the Health Tests section, click Create Trigger.
4. On the New Trigger page, enter the name Resident Memory In Use.
5. In Expression, set these metric conditions:
    a. Scalar Function: Min.
    b. Metric: mem_rss.
    c. Comparator: > (greater than).
    d. Scalar Value: 1.75GB. (This is a low value for demonstration purposes, so that it will trigger the action. In
       practice, use a value that more accurately reflects the memory limits of your cluster.)
6. Set Action to Mark as bad.
    As you work, the Preview shows the resulting chart and current status of your host.
7. Scroll down and choose whether to apply this trigger to All hosts.
8. Click Create Trigger.

#### Creating a Trigger for CPU Capacity

```
Procedure
```
1. In Cloudera Manager, go to the Hosts page.
2. Click a link in the Name column to open a host status page.
3. In the Health Tests section, click Create Trigger.
4. On the New Trigger page, enter the name CPU Capacity.
5. In Expression, set these metric conditions.
    - Scalar Function: Min.
    - Metric: cpu_percent.
    - Comparator: > (greater than).
    - Scalar Value: 90.
6. Set Action to Mark as concerning.
7. Click Create Trigger.
```
Results
This trigger fires whenever the CPU percentage exceeds 90%. However, just exceeding 90% of available CPU
resources is not necessarily a bad thing. What would be of more concern is if CPU resources were to consistently
exceed 90% over an extended period. You can modify the trigger to evaluate the average CPU usage over time.
To modify the trigger to capture high CPU usage in a five minute window, do the following.
```
1. In Cloudera Manager, go to the Hosts page.
2. Click a link in the Name column to open the host status page.
3. In the Health Tests section, click the Show n Good link.
4. Click the link for CPU Capacity.
5. Choose Actions Edit Trigger.

```
The metric expression function for average over time, moving_avg, is not available from the pop-up menu in the
editor. You can edit the expression directly using tsquery language.
```
6. Above the Expression editor, click Edit manually.
7. Revise the expression as follows.

```
IF (select cpu_percent where entityName=$HOSTID and min(moving_avg(cpu_p
ercent, 300) ) > 90)
DO health:concerning
```
8. Click Save Trigger.
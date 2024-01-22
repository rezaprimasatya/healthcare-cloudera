## Health Tests

```
Cloudera Manager monitors the health of the services, roles, and hosts that are running in your clusters using health
tests.
The Cloudera Management Service also provides health tests for its roles. Role-based health tests are enabled by
default. For example, a simple health test is whether there's enough disk space in every NameNode data directory.
A more complicated health test may evaluate when the last checkpoint for HDFS was compared to a threshold or
whether a DataNode is connected to a NameNode. Some of these health tests also aggregate other health tests: in a
distributed system like HDFS, it's normal to have a few DataNodes down (assuming you've got dozens of hosts), so
we allow for setting thresholds on what percentage of hosts should color the entire service down.
Health tests can return one of three values: Good, Concerning, and Bad. A test returns Concerning health if the test
falls below a warning threshold. A test returns Bad if the test falls below a critical threshold. The overall health of a
service or role instance is a roll-up of its health tests. If any health test is Concerning (but none are Bad) the role's or
service's health is Concerning; if any health test is Bad, the service's or role's health is Bad.
```
```
In the Cloudera Manager Admin Console, health tests results are indicated with colors: Good , Concerning , and Bad.
```
```
There are two types of health tests:
```
- Pass-fail tests - there are two types:
    - Compare a property to a yes-no value. For example, whether a service or role started as expected, a DataNode
       is connected to its NameNode, or a TaskTracker is (or is not) blocked.
    - Exercise a service lightly to confirm it is working and responsive. HDFS (NameNode role), HBase, and
       ZooKeeper services perform these tests, which are referred to as "canary" tests.
    Both types of pass-fail tests result in the health reported as being either Good or Bad.
- Metric tests - compare a property to a numeric value. For example, the number of file descriptors in use, the
    amount of disk space used or free, how much time spent in garbage collection, or how many pages were swapped
    to disk in the previous 15 minutes. In these tests the property is compared to a threshold that determine whether
    everything is Good, (for example, plenty of disk space available), whether it is Concerning (disk space getting
    low), or is Bad (a critically low amount of disk space).
By default most health tests are enabled and (if appropriate) configured with reasonable thresholds. You can modify
threshold values by editing the monitoring properties under the entity's Configuration tab. You can also enable or
disable individual or summary health tests, and in some cases specify what should be included in the calculation of
overall health for the service, role instance, or host.

### Viewing Health Test Results

```
You can view health test results in multiple locations.
Health test results are available in the following locations:
```
- Home Status tab where various health results determine an overall health assessment of the service or role.
    The overall health of a role or service is a roll-up of its health tests; if any health test is Bad, the service's or
    role's health will be Bad. If any health test is Concerning (but none are Bad) the role's or service's health will be
    Concerning.
- Hosts tab, which shows summary result for the hosts.
- Status tab - which shows metrics for services, role instances, and hosts. These are reflected in the results shown in
    the Health Tests panel when you have selected a service, role instance, or host.
- The All Health Issues tab of the Home page displays all health issues. You can sort the display by entity or by
    Health Test.
For some health test results, you can chart the associated metrics over a time range. See the related information for
details.

### Suppressing Health Test Results

```
Cloudera Manager displays warnings when health tests indicate a problem in the cluster. Sometimes these warnings
are expected or do not indicate a real problem in your deployment. You can suppress display of these warnings in
Cloudera Manager.
Minimum Required Role: Configurator (also provided by Cluster Administrator, Limited Cluster Administrator , and
Full Administrator)
You can suppress health test warnings as they appear or before any tests run. Suppressed health tests are hidden in
Cloudera Manager and their status does not affect the roll-up of health tests that display for a service, host, or role
instance. Suppressed health test warnings remain available in Cloudera Manager, and the tests continue to run but the
results are hidden. You can unsuppress a suppressed health test at any time.
On pages where you have suppressed validations, you will see a link that says Show # Suppressed Test. On this
screen, you can:
```
- Click the Show # Suppressed Test link to view all suppressed health tests for the page.
- Click the Unsuppress... link to unsuppress the health test.
- Click Hide Suppressed Tests to re-hide the suppressed tests.
    Note: Suppressing a health test is different than disabling a health test. A disabled health test never runs,
    whereas a suppressed health test runs but its results are hidden.

### Suppressing a Health Test

```
You can suppress a health test to hide its results.
```


```
About this task
Minimum Required Role: Configurator (also provided by Cluster Administrator, Limited Cluster Administrator , and
Full Administrator)
```
```
Procedure
```
1. Go to the health test you want to suppress.
2. Click the Suppress... link to the right of the health test description.
    A dialog box opens where you can enter a comment about the suppression action.
3. Click Confirm.
    The display changes to Suppressing... while the change is propagated.


### Configuring Suppression of Health Tests Before Tests Run

```
You can configure a health test to suppress its results before the health test runs.
```
```
About this task
Minimum Required Role: Configurator (also provided by Cluster Administrator, Limited Cluster Administrator , and
Full Administrator)
```
```
Procedure
```
1. Go to the service or host with the health test that you want to suppress.
2. Click the Configuration tab.
3. In the filters on the left, select Category Suppressions.
    A list of suppression properties displays. The names of the properties begin with Suppress Health Test.
4. Select a health test suppression property to suppress the test.
5. Enter a Reason for change, and then click Save Changes to commit the changes.

### Viewing a List of Suppressed Health Tests

```
You can view a list of suppressed health tests from the Configuration menu.
```
```
About this task
Minimum Required Role: Configurator (also provided by Cluster Administrator, Limited Cluster Administrator , and
Full Administrator)
```
```
Procedure
```
1. From the Home page or the Status page of a cluster, select Configuration Suppressed Health and Configuration
    Issues.
2. Select Status Non-default.
    A list of suppressed health tests and configuration issues displays.
3. To limit the list to health tests, enter “health test” in the Search box.


### Unsuppressing Health Tests

```
You can unsuppress a health test from where it displays, or unsuppress one or more health tests from the
configuration page of the service or host.
```
```
About this task
Minimum Required Role: Configurator (also provided by Cluster Administrator, Limited Cluster Administrator , and
Full Administrator)
```
```
Procedure
```
1. To unsuppress a single health test where it displays, click the Unsuppress... link next to a suppressed test. (You
    may need to click the Show # Suppressed Test link first.)
2. To unsuppress one or more health tests from the configuration screen:
    - Go to the service or host with the health test you want to unsuppress.
    - Select Status Non-default.
       - A list of suppressed health tests and configuration issues displays.
    - Optionally, type the name of the health test in the Search box to locate it.
    - Clear the suppression property for the health test.
    - Enter a Reason for change, and then click Save Changes to commit the changes.
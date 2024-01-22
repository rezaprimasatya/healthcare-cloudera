## Alerts

```
An alert is an event that is considered especially noteworthy and is triggered by a selected event. Alerts are shown
with an badge when they appear in a list of events. You can configure the Alert Publisher to send alert
notifications by email or by SNMP trap to a trap receiver.
Service instances of type HDFS, MapReduce, and HBase (and their associated roles) can generate alerts if so
configured. Alerts can also be configured for the monitoring roles that are a part of the Cloudera Management
Service.
The settings to enable or disable specific alerts are found under the Configuration tab for the services to which they
pertain.
```
### Managing Alerts

```
Minimum Required Role: Limited Cluster Administrator (also provided by Full Administrator and Cluster
Administrator)
The AdministrationAlerts page provides a summary of the settings for alerts in your clusters.
Alert Type The left column lets you select by alert type (Health, Log, or Activity) and within that by service instance.
In the case of Health alerts, you can look at alerts for Hosts as well. You can select an individual service to see just
the alert settings for that service.
Health/Log/Activity Alert Settings Depending on your selection in the left column, the right hand column show you
the list of alerts that are enabled or disabled for the selected service type.
```


```
To change the alert settings for a service, click Edit next to the service name. This will take you to the Monitoring
section of the Configuration tab for the service. From here you can enable or disable alerts and configure thresholds
as needed.
Recipients You can also view the list of recipients configured for the enabled alerts.
```
```
Configuring Alert Delivery
When you install Cloudera Manager you can configure the mail server you will use with the Alert Publisher.
However, if you need to change these settings, you can do so under the Alert Publisher section of the Management
Services configuration tab. Under the Alert Publisher role of the Cloudera Manager Management Service, you can
configure email or SNMP delivery of alert notifications and you can also configure a custom script that runs in
response to an alert.
```
```
Viewing Which Alerts are Enabled and Disabled
Minimum Required Role: Cluster Administrator (also provided by Full Administrator)
Select AdministrationAlerts.
```
### Configuring Alert Email Delivery

```
Minimum Required Role: Limited Cluster Administrator (also provided by Full Administrator and Cluster
Administrator)
```
```
Sending A Test Alert E-mail
Select the AdministrationAlerts tab and click the Send Test Alert link.
```
```
Configuring the List Of Alert Recipient Email Addresses
```
- Click ClustersCloudera Management Service.
- Select the Configuration tab.
- Select ScopeAlert Publisher.
- Select CategoryMain.
- Locate the Alerts: Mail Message Recipients property or search for it by typing its name in the Search box.
- Configure the Alerts: Mail Message Recipients property. Use the + icon to add new recipients.
- Click the Save Changes button at the top of the page to save your settings.
    To apply this configuration property to other role groups as needed, edit the value for the appropriate role group.
    See the topic Modifying Configuration Properties Using Cloudera Manager.
- Restart the Alert Publisher role.

```
Configuring Alert Email Properties
```
- Display the Cloudera Management Service status page.
- Click the Configuration tab.
- Select ScopeAlert Publisher.

- Select CategoryMain to see the list of properties. To receive email alerts, you must set (or verify) the following
    settings:
    - Enable email alerts
    - Email protocol to use.
    - Your mail server hostname and port.
    - The username and password of the email user that will be logged into the mail server as the "sender" of the
       alert emails.
          Important: If a password contains special characters such as @, #, $, %, ^, &, and *, then enclose the
          password inside the RAW() method. For example, "RAW(pass@*word)".
    - A comma-separated list of email addresses that will be the recipients of alert emails.
    - The format of the email alert message. Select json if you need the message to be parsed by a script or program.
    To apply this configuration property to other role groups as needed, edit the value for the appropriate role group.
    See the topic Modifying Configuration Properties Using Cloudera Manager.
- Click the Save Changes button at the top of the page to save your settings.
- Restart the Alert Publisher role.

### Configuring Alert SNMP Delivery

```
Minimum Required Role: Limited Cluster Administrator (also provided by Full Administrator and Cluster
Administrator)
```
```
Enabling, Configuring, and Disabling SNMP Traps
```
- Before you enable SNMP traps, configure the trap receiver (Network Management System or SNMP server) with
    the Cloudera MIB.
- Do one of the following:
    - Select Clusters Cloudera Management Service.
    - On the HomeStatus tab, in Cloudera Management Service table, click the Cloudera Management Service link.
- Click the Configuration tab.
- Select ScopeAlert Publisher SNMP.
- Select CategorySNMP
    - Enter the DNS name or IP address of the Network Management System (SNMP server) acting as the trap
       receiver in the SNMP NMS Hostname property.
    - In the SNMP Security Level property, select the version of SNMP you are using: SNMPv2, SNMPv3 without
       authentication and without privacy (noAuthNoPriv), or SNMPv3 with authentication and without privacy (auth
       NoPriv) and specify the required properties:
       - SNMPv2 - SNMPv2 Community String.
       - SNMPv3 without authentication (noAuthNoPriv) - SNMP Server Engine Id and SNMP Security
          UserName.
       - SNMPv3 with authentication (authNoPriv) - SNMP Server Engine Id, SNMP Security UserName, SNMP
          Authentication Protocol, and SNMP Authentication Protocol Pass Phrase.
    - You can also change other settings such as the port, retry, or timeout values.
    To apply this configuration property to other role groups as needed, edit the value for the appropriate role group.
    See the topic Modifying Configuration Properties Using Cloudera Manager.
- Click Save Changes when you are done.
- Restart the Alert Publisher role.


```
To disable SNMP traps, remove the hostname from the SNMP NMS Hostname property
(alert.snmp.server.hostname).
```
```
Viewing the Cloudera MIB
```
1. Do one of the following:
    - Select Clusters Cloudera Management Service.
    - On the HomeStatus tab, in Cloudera Management Service table, click the Cloudera Management Service link.
2. Click the Configuration tab.
3. Select ScopeAlert Publisher SNMP.
4. Select CategorySNMP.
5. Locate the SNMP NMS Hostname property and click the? icon to display the property description.
6. Click the SMNP Mib link.
Related Information
Modifying Configuration Properties Using Cloudera Manager

### Configuring Custom Alert Scripts

```
You can configure the Alert Publisher to call a user-provided script in response to an alert.
Minimum Required Role: Limited Cluster Administrator (also provided by Full Administrator and Cluster
Administrator)
You can configure the Alert Publisher to run a user-written script in response to an alert. The Alert Publisher passes
a single argument to the script that is a UTF-8 JSON file containing a list of alerts. The script runs on the host where
the Alert Publisher service is running and must have read and execute permissions for the cloudera-scm user. Only
one instance of a script runs at a time. The standard out and standard error messages from the script are logged to the
Alert Publisher log file.
You use the Alert Publisher: Maximum Batch Size and Alert Publisher: Maximum Batch interval to configure when
the Alert Publisher delivers alerts.
To configure the Alert Publisher to deliver alerts using a script:
```
- Save the script on the host where the Alert Publisher role is running.
- Change the owner of the file to cloudera-scm and set its permissions to read and execute:

```
sudo chown cloudera-scm:cloudera-scm path_to_script
sudo chmod u+rx path_to_script
```
- Open the Cloudera Manager Admin console and select ClustersCloudera Management Service.
- Click the Configuration tab.
- Select ScopeAlert Publisher.
- Enter the path to the script in the Custom Alert Script property.
- Enter a Reason for change, and then click Save Changes to commit the changes.
A sample Python script is available that parses the alert file and sends alerts to different email addresses based on the
content of the alert. See Sample Custom Alert Script on page 113.

```
Sample JSON Alert File
When a custom script runs, it passes a JSON file that contains the alerts. For example:
```
```
[ {
"body" : {
"alert" : {
```

```
"content" : "The health test result for MAPREDUCE_HA_JOB_TRACKER_HEAL
TH has become bad: JobTracker summary: myCluster.com (Availability: Active,
Health: Bad). This health test reflects the health of the active JobTracker.
",
"timestamp" : {
"iso8601" : "2015-06-11T03:52:56Z",
"epochMs" : 1433994776083
},
"source" : "http://myCluster.com:7180/cmf/eventRedirect/89521139-0859-
4bef-bf65-eb141e63dbba",
"attributes" : {
"__persist_timestamp" : [ "1433994776172" ],
"ALERT_SUPPRESSED" : [ "false" ],
"HEALTH_TEST_NAME" : [ "MAPREDUCE_HA_JOB_TRACKER_HEALTH" ],
"SEVERITY" : [ "CRITICAL" ],
"HEALTH_TEST_RESULTS" : [ {
"content" : "The health test result for MAPREDUCE_HA_JOB_TRACKER_H
EALTH has become bad: JobTracker summary: myCluster.com (Availability: Activ
e, Health: Bad). This health test reflects the health of the active JobTrack
er.",
"testName" : "MAPREDUCE_HA_JOB_TRACKER_HEALTH",
"eventCode" : "EV_SERVICE_HEALTH_CHECK_BAD",
"severity" : "CRITICAL"
} ],
"CLUSTER_DISPLAY_NAME" : [ "Cluster 1" ],
"ALERT" : [ "true" ],
"CATEGORY" : [ "HEALTH_CHECK" ],
"BAD_TEST_RESULTS" : [ "1" ],
"SERVICE_TYPE" : [ "MAPREDUCE" ],
"EVENTCODE" : [ "EV_SERVICE_HEALTH_CHECK_BAD", "EV_SERVICE_HEALTH
_CHECK_GOOD" ],
"ALERT_SUMMARY" : [ "The health of service MAPREDUCE-1 has become ba
d." ],
"CLUSTER_ID" : [ "1" ],
"SERVICE" : [ "MAPREDUCE-1" ],
"__uuid" : [ "89521139-0859-4bef-bf65-eb141e63dbba" ],
"CLUSTER" : [ "Cluster 1" ],
"CURRENT_COMPLETE_HEALTH_TEST_RESULTS" : [ "{\"content\":\"The hea
lth test result for MAPREDUCE_HA_JOB_TRACKER_HEALTH has become bad: JobTrack
er summary: myCluster.com (Availability: Active, Health: Bad). This health t
est reflects the health of the active JobTracker.\",\"testName\":\"MAPREDUCE
_HA_JOB_TRACKER_HEALTH\",\"eventCode\":\"EV_SERVICE_HEALTH_CHECK_BAD\",\"sev
erity\":\"CRITICAL\"}", "{\"content\":\"The health test result for MAPREDUCE
_TASK_TRACKERS_HEALTHY has become good: Healthy TaskTracker: 3. Concerning T
askTracker: 0. Total TaskTracker: 3. Percent healthy: 100.00%. Percent healt
hy or concerning: 100.00%.\",\"testName\":\"MAPREDUCE_TASK_TRACKERS_HEALTHY\
",\"eventCode\":\"EV_SERVICE_HEALTH_CHECK_GOOD\",\"severity\":\"INFORMATIONA
L\"}" ],
"PREVIOUS_HEALTH_SUMMARY" : [ "GREEN" ],
"CURRENT_HEALTH_SUMMARY" : [ "RED" ],
"MONITOR_STARTUP" : [ "false" ],
"PREVIOUS_COMPLETE_HEALTH_TEST_RESULTS" : [ "{\"content\":\"The hea
lth test result for MAPREDUCE_HA_JOB_TRACKER_HEALTH has become good: JobTrac
ker summary: myCluster.com (Availability: Active, Health: Good)\",\"testName
\":\"MAPREDUCE_HA_JOB_TRACKER_HEALTH\",\"eventCode\":\"EV_SERVICE_HEALTH_CHE
CK_GOOD\",\"severity\":\"INFORMATIONAL\"}", "{\"content\":\"The health test
result for MAPREDUCE_TASK_TRACKERS_HEALTHY has become good: Healthy TaskTrac
ker: 3. Concerning TaskTracker: 0. Total TaskTracker: 3. Percent healthy: 10
0.00%. Percent healthy or concerning: 100.00%.\",\"testName\":\"MAPREDUCE_TA
SK_TRACKERS_HEALTHY\",\"eventCode\":\"EV_SERVICE_HEALTH_CHECK_GOOD\",\"sever
ity\":\"INFORMATIONAL\"}" ],
"SERVICE_DISPLAY_NAME" : [ "MAPREDUCE-1" ]
}
}
```

##### },

```
"header" : {
"type" : "alert",
"version" : 2
}
}, {
"body" : {
"alert" : {
"content" : "The health test result for JOB_TRACKER_SCM_HEALTH has bec
ome bad: This role's process exited. This role is supposed to be started.",
"timestamp" : {
"iso8601" : "2015-06-11T03:52:56Z",
"epochMs" : 1433994776083
},
"source" : "http://myCluster.com:7180/cmf/eventRedirect/67b4d1c4-791b
-428e-a9ea-8a09d4885f5d",
"attributes" : {
"__persist_timestamp" : [ "1433994776173" ],
"ALERT_SUPPRESSED" : [ "false" ],
"HEALTH_TEST_NAME" : [ "JOB_TRACKER_SCM_HEALTH" ],
"SEVERITY" : [ "CRITICAL" ],
"ROLE" : [ "MAPREDUCE-1-JOBTRACKER-10624c438dee9f17211d3f33fa899957"
],
"HEALTH_TEST_RESULTS" : [ {
"content" : "The health test result for JOB_TRACKER_SCM_HEALTH has
become bad: This role's process exited. This role is supposed to be started
.",
"testName" : "JOB_TRACKER_SCM_HEALTH",
"eventCode" : "EV_ROLE_HEALTH_CHECK_BAD",
"severity" : "CRITICAL"
} ],
"CLUSTER_DISPLAY_NAME" : [ "Cluster 1" ],
"HOST_IDS" : [ "75e763c2-8d22-47a1-8c80-501751ae0db7" ],
"ALERT" : [ "true" ],
"ROLE_TYPE" : [ "JOBTRACKER" ],
"CATEGORY" : [ "HEALTH_CHECK" ],
"BAD_TEST_RESULTS" : [ "1" ],
"SERVICE_TYPE" : [ "MAPREDUCE" ],
"EVENTCODE" : [ "EV_ROLE_HEALTH_CHECK_BAD", "EV_ROLE_HEALTH_CHECK_
GOOD", "EV_ROLE_HEALTH_CHECK_DISABLED" ],
"ALERT_SUMMARY" : [ "The health of role jobtracker (nightly-1) has
become bad." ],
"CLUSTER_ID" : [ "1" ],
"SERVICE" : [ "MAPREDUCE-1" ],
"__uuid" : [ "67b4d1c4-791b-428e-a9ea-8a09d4885f5d" ],
"CLUSTER" : [ "Cluster 1" ],
"CURRENT_COMPLETE_HEALTH_TEST_RESULTS" : [ "{\"content\":\"The healt
h test result for JOB_TRACKER_SCM_HEALTH has become bad: This role's process
exited. This role is supposed to be started.\",\"testName\":\"JOB_TRACKER_S
CM_HEALTH\",\"eventCode\":\"EV_ROLE_HEALTH_CHECK_BAD\",\"severity\":\"CRITIC
AL\"}", "{\"content\":\"The health test result for JOB_TRACKER_UNEXPECTED_EX
ITS has become good: This role encountered 0 unexpected exit(s) in the previ
ous 5 minute(s).\",\"testName\":\"JOB_TRACKER_UNEXPECTED_EXITS\",\"eventCode
\":\"EV_ROLE_HEALTH_CHECK_GOOD\",\"severity\":\"INFORMATIONAL\"}", "{\"conte
nt\":\"The health test result for JOB_TRACKER_FILE_DESCRIPTOR has become goo
d: Open file descriptors: 244. File descriptor limit: 32,768. Percentage in
use: 0.74%.\",\"testName\":\"JOB_TRACKER_FILE_DESCRIPTOR\",\"eventCode\":\"E
V_ROLE_HEALTH_CHECK_GOOD\",\"severity\":\"INFORMATIONAL\"}", "{\"content\":\
"The health test result for JOB_TRACKER_SWAP_MEMORY_USAGE has become good: 0
B of swap memory is being used by this role's process.\",\"testName\":\"JOB
_TRACKER_SWAP_MEMORY_USAGE\",\"eventCode\":\"EV_ROLE_HEALTH_CHECK_GOOD\",\"s
everity\":\"INFORMATIONAL\"}", "{\"content\":\"The health test result for JO
B_TRACKER_LOG_DIRECTORY_FREE_SPACE has become good: This role's Log Director
y (/var/log/hadoop-0.20-mapreduce) is on a filesystem with more than 20.00%
```

```
of its space free.\",\"testName\":\"JOB_TRACKER_LOG_DIRECTORY_FREE_SPACE\",\
"eventCode\":\"EV_ROLE_HEALTH_CHECK_GOOD\",\"severity\":\"INFORMATIONAL\"}",
"{\"content\":\"The health test result for JOB_TRACKER_HOST_HEALTH has beco
me good: The health of this role's host is good.\",\"testName\":\"JOB_TRACKE
R_HOST_HEALTH\",\"eventCode\":\"EV_ROLE_HEALTH_CHECK_GOOD\",\"severity\":\"I
NFORMATIONAL\"}", "{\"content\":\"The health test result for JOB_TRACKER_WEB
_METRIC_COLLECTION has become good: The web server of this role is respondin
g with metrics. The most recent collection took 49 millisecond(s).\",\"testN
ame\":\"JOB_TRACKER_WEB_METRIC_COLLECTION\",\"eventCode\":\"EV_ROLE_HEALTH_C
HECK_GOOD\",\"severity\":\"INFORMATIONAL\"}", "{\"content\":\"The health tes
t result for JOB_TRACKER_GC_DURATION has become good: Average time spent in
garbage collection was 0 second(s) (0.00%) per minute over the previous 5 mi
nute(s).\",\"testName\":\"JOB_TRACKER_GC_DURATION\",\"eventCode\":\"EV_ROLE_
HEALTH_CHECK_GOOD\",\"severity\":\"INFORMATIONAL\"}", "{\"content\":\"The he
alth test result for JOB_TRACKER_HEAP_DUMP_DIRECTORY_FREE_SPACE has become d
isabled: Test disabled because role is not configured to dump heap when out
of memory. Test of whether this role's heap dump directory has enough free s
pace.\",\"testName\":\"JOB_TRACKER_HEAP_DUMP_DIRECTORY_FREE_SPACE\",\"eventC
ode\":\"EV_ROLE_HEALTH_CHECK_DISABLED\",\"severity\":\"INFORMATIONAL\"}" ],
"CURRENT_HEALTH_SUMMARY" : [ "RED" ],
"PREVIOUS_HEALTH_SUMMARY" : [ "GREEN" ],
"MONITOR_STARTUP" : [ "false" ],
"ROLE_DISPLAY_NAME" : [ "jobtracker (nightly-1)" ],
"PREVIOUS_COMPLETE_HEALTH_TEST_RESULTS" : [ "{\"content\":\"The heal
th test result for JOB_TRACKER_SCM_HEALTH has become good: This role's statu
s is as expected. The role is started.\",\"testName\":\"JOB_TRACKER_SCM_HEAL
TH\",\"eventCode\":\"EV_ROLE_HEALTH_CHECK_GOOD\",\"severity\":\"INFORMATIONA
L\"}", "{\"content\":\"The health test result for JOB_TRACKER_UNEXPECTED_EXI
TS has become good: This role encountered 0 unexpected exit(s) in the previo
us 5 minute(s).\",\"testName\":\"JOB_TRACKER_UNEXPECTED_EXITS\",\"eventCode\
":\"EV_ROLE_HEALTH_CHECK_GOOD\",\"severity\":\"INFORMATIONAL\"}", "{\"conten
t\":\"The health test result for JOB_TRACKER_FILE_DESCRIPTOR has become good
: Open file descriptors: 244. File descriptor limit: 32,768. Percentage in u
se: 0.74%.\",\"testName\":\"JOB_TRACKER_FILE_DESCRIPTOR\",\"eventCode\":\"EV
_ROLE_HEALTH_CHECK_GOOD\",\"severity\":\"INFORMATIONAL\"}", "{\"content\":\"
The health test result for JOB_TRACKER_SWAP_MEMORY_USAGE has become good: 0
B of swap memory is being used by this role's process.\",\"testName\":\"JOB_
TRACKER_SWAP_MEMORY_USAGE\",\"eventCode\":\"EV_ROLE_HEALTH_CHECK_GOOD\",\"se
verity\":\"INFORMATIONAL\"}", "{\"content\":\"The health test result for JOB
_TRACKER_LOG_DIRECTORY_FREE_SPACE has become good: This role's Log Directory
(/var/log/hadoop-0.20-mapreduce) is on a filesystem with more than 20.00% o
f its space free.\",\"testName\":\"JOB_TRACKER_LOG_DIRECTORY_FREE_SPACE\",\"
eventCode\":\"EV_ROLE_HEALTH_CHECK_GOOD\",\"severity\":\"INFORMATIONAL\"}",
"{\"content\":\"The health test result for JOB_TRACKER_HOST_HEALTH has becom
e good: The health of this role's host is good.\",\"testName\":\"JOB_TRACKER
_HOST_HEALTH\",\"eventCode\":\"EV_ROLE_HEALTH_CHECK_GOOD\",\"severity\":\"IN
FORMATIONAL\"}", "{\"content\":\"The health test result for JOB_TRACKER_WEB_
METRIC_COLLECTION has become good: The web server of this role is responding
with metrics. The most recent collection took 49 millisecond(s).\",\"testNa
me\":\"JOB_TRACKER_WEB_METRIC_COLLECTION\",\"eventCode\":\"EV_ROLE_HEALTH_CH
ECK_GOOD\",\"severity\":\"INFORMATIONAL\"}", "{\"content\":\"The health test
result for JOB_TRACKER_GC_DURATION has become good: Average time spent in g
arbage collection was 0 second(s) (0.00%) per minute over the previous 5 min
ute(s).\",\"testName\":\"JOB_TRACKER_GC_DURATION\",\"eventCode\":\"EV_ROLE_H
EALTH_CHECK_GOOD\",\"severity\":\"INFORMATIONAL\"}", "{\"content\":\"The hea
lth test result for JOB_TRACKER_HEAP_DUMP_DIRECTORY_FREE_SPACE has become di
sabled: Test disabled because role is not configured to dump heap when out o
f memory. Test of whether this role's heap dump directory has enough free sp
ace.\",\"testName\":\"JOB_TRACKER_HEAP_DUMP_DIRECTORY_FREE_SPACE\",\"eventCo
de\":\"EV_ROLE_HEALTH_CHECK_DISABLED\",\"severity\":\"INFORMATIONAL\"}" ],
"SERVICE_DISPLAY_NAME" : [ "MAPREDUCE-1" ],
"HOSTS" : [ "myCluster.com" ]
}
}
```


##### },

```
"header" : {
"type" : "alert",
"version" : 2
}
}, {
"body" : {
"alert" : {
"content" : "The health test result for JOB_TRACKER_UNEXPECTED_EXITS
has become bad: This role encountered 1 unexpected exit(s) in the previous 5
minute(s).This included 1 exit(s) due to OutOfMemory errors. Critical thres
hold: any.",
"timestamp" : {
"iso8601" : "2015-06-11T03:53:41Z",
"epochMs" : 1433994821940
},
"source" : "http://myCluster.com:7180/cmf/eventRedirect/b8c4468d-08c
2-4b5b-9bda-2bef892ba3f5",
"attributes" : {
"__persist_timestamp" : [ "1433994822027" ],
"ALERT_SUPPRESSED" : [ "false" ],
"HEALTH_TEST_NAME" : [ "JOB_TRACKER_UNEXPECTED_EXITS" ],
"SEVERITY" : [ "CRITICAL" ],
"ROLE" : [ "MAPREDUCE-1-JOBTRACKER-10624c438dee9f17211d3f33fa8999
57" ],
"HEALTH_TEST_RESULTS" : [ {
"content" : "The health test result for JOB_TRACKER_UNEXPECTED_
EXITS has become bad: This role encountered 1 unexpected exit(s) in the prev
ious 5 minute(s).This included 1 exit(s) due to OutOfMemory errors. Critical
threshold: any.",
"testName" : "JOB_TRACKER_UNEXPECTED_EXITS",
"eventCode" : "EV_ROLE_HEALTH_CHECK_BAD",
"severity" : "CRITICAL"
} ],
"CLUSTER_DISPLAY_NAME" : [ "Cluster 1" ],
"HOST_IDS" : [ "75e763c2-8d22-47a1-8c80-501751ae0db7" ],
"ALERT" : [ "true" ],
"ROLE_TYPE" : [ "JOBTRACKER" ],
"CATEGORY" : [ "HEALTH_CHECK" ],
"BAD_TEST_RESULTS" : [ "1" ],
"SERVICE_TYPE" : [ "MAPREDUCE" ],
"EVENTCODE" : [ "EV_ROLE_HEALTH_CHECK_BAD", "EV_ROLE_HEALTH_CHECK
_GOOD", "EV_ROLE_HEALTH_CHECK_DISABLED" ],
"ALERT_SUMMARY" : [ "The health of role jobtracker (nightly-1) has
become bad." ],
"CLUSTER_ID" : [ "1" ],
"SERVICE" : [ "MAPREDUCE-1" ],
"__uuid" : [ "b8c4468d-08c2-4b5b-9bda-2bef892ba3f5" ],
"CLUSTER" : [ "Cluster 1" ],
"CURRENT_COMPLETE_HEALTH_TEST_RESULTS" : [ "{\"content\":\"The heal
th test result for JOB_TRACKER_SCM_HEALTH has become bad: This role's proces
s exited. This role is supposed to be started.\",\"testName\":\"JOB_TRACKER_
SCM_HEALTH\",\"eventCode\":\"EV_ROLE_HEALTH_CHECK_BAD\",\"severity\":\"CRITI
CAL\"}", "{\"content\":\"The health test result for JOB_TRACKER_UNEXPECTED_E
XITS has become bad: This role encountered 1 unexpected exit(s) in the previ
ous 5 minute(s).This included 1 exit(s) due to OutOfMemory errors. Critical
threshold: any.\",\"testName\":\"JOB_TRACKER_UNEXPECTED_EXITS\",\"eventCode\
":\"EV_ROLE_HEALTH_CHECK_BAD\",\"severity\":\"CRITICAL\"}", "{\"content\":\"
The health test result for JOB_TRACKER_FILE_DESCRIPTOR has become good: Open
file descriptors: 244. File descriptor limit: 32,768. Percentage in use: 0.
74%.\",\"testName\":\"JOB_TRACKER_FILE_DESCRIPTOR\",\"eventCode\":\"EV_ROLE_
HEALTH_CHECK_GOOD\",\"severity\":\"INFORMATIONAL\"}", "{\"content\":\"The he
alth test result for JOB_TRACKER_SWAP_MEMORY_USAGE has become good: 0 B of s
wap memory is being used by this role's process.\",\"testName\":\"JOB_TRACKE
```

```
R_SWAP_MEMORY_USAGE\",\"eventCode\":\"EV_ROLE_HEALTH_CHECK_GOOD\",\"severity
\":\"INFORMATIONAL\"}", "{\"content\":\"The health test result for JOB_TRACK
ER_LOG_DIRECTORY_FREE_SPACE has become good: This role's Log Directory (/var
/log/hadoop-0.20-mapreduce) is on a filesystem with more than 20.00% of its
space free.\",\"testName\":\"JOB_TRACKER_LOG_DIRECTORY_FREE_SPACE\",\"eventC
ode\":\"EV_ROLE_HEALTH_CHECK_GOOD\",\"severity\":\"INFORMATIONAL\"}", "{\"co
ntent\":\"The health test result for JOB_TRACKER_HOST_HEALTH has become good
: The health of this role's host is good.\",\"testName\":\"JOB_TRACKER_HOST_
HEALTH\",\"eventCode\":\"EV_ROLE_HEALTH_CHECK_GOOD\",\"severity\":\"INFORMAT
IONAL\"}", "{\"content\":\"The health test result for JOB_TRACKER_WEB_METRIC
_COLLECTION has become good: The web server of this role is responding with
metrics. The most recent collection took 49 millisecond(s).\",\"testName\":\
"JOB_TRACKER_WEB_METRIC_COLLECTION\",\"eventCode\":\"EV_ROLE_HEALTH_CHECK_GO
OD\",\"severity\":\"INFORMATIONAL\"}", "{\"content\":\"The health test resul
t for JOB_TRACKER_GC_DURATION has become good: Average time spent in garbage
collection was 0 second(s) (0.00%) per minute over the previous 5 minute(s)
.\",\"testName\":\"JOB_TRACKER_GC_DURATION\",\"eventCode\":\"EV_ROLE_HEALTH_
CHECK_GOOD\",\"severity\":\"INFORMATIONAL\"}", "{\"content\":\"The health te
st result for JOB_TRACKER_HEAP_DUMP_DIRECTORY_FREE_SPACE has become disabled
: Test disabled because role is not configured to dump heap when out of memo
ry. Test of whether this role's heap dump directory has enough free space.\"
,\"testName\":\"JOB_TRACKER_HEAP_DUMP_DIRECTORY_FREE_SPACE\",\"eventCode\":\
"EV_ROLE_HEALTH_CHECK_DISABLED\",\"severity\":\"INFORMATIONAL\"}" ],
"CURRENT_HEALTH_SUMMARY" : [ "RED" ],
"PREVIOUS_HEALTH_SUMMARY" : [ "RED" ],
"MONITOR_STARTUP" : [ "false" ],
"ROLE_DISPLAY_NAME" : [ "jobtracker (nightly-1)" ],
"PREVIOUS_COMPLETE_HEALTH_TEST_RESULTS" : [ "{\"content\":\"The h
ealth test result for JOB_TRACKER_SCM_HEALTH has become bad: This role's pro
cess exited. This role is supposed to be started.\",\"testName\":\"JOB_TRACK
ER_SCM_HEALTH\",\"eventCode\":\"EV_ROLE_HEALTH_CHECK_BAD\",\"severity\":\"CR
ITICAL\"}", "{\"content\":\"The health test result for JOB_TRACKER_UNEXPECTE
D_EXITS has become good: This role encountered 0 unexpected exit(s) in the p
revious 5 minute(s).\",\"testName\":\"JOB_TRACKER_UNEXPECTED_EXITS\",\"event
Code\":\"EV_ROLE_HEALTH_CHECK_GOOD\",\"severity\":\"INFORMATIONAL\"}", "{\"c
ontent\":\"The health test result for JOB_TRACKER_FILE_DESCRIPTOR has become
good: Open file descriptors: 244. File descriptor limit: 32,768. Percentage
in use: 0.74%.\",\"testName\":\"JOB_TRACKER_FILE_DESCRIPTOR\",\"eventCode\"
:\"EV_ROLE_HEALTH_CHECK_GOOD\",\"severity\":\"INFORMATIONAL\"}", "{\"content
\":\"The health test result for JOB_TRACKER_SWAP_MEMORY_USAGE has become goo
d: 0 B of swap memory is being used by this role's process.\",\"testName\":\
"JOB_TRACKER_SWAP_MEMORY_USAGE\",\"eventCode\":\"EV_ROLE_HEALTH_CHECK_GOOD\"
,\"severity\":\"INFORMATIONAL\"}", "{\"content\":\"The health test result fo
r JOB_TRACKER_LOG_DIRECTORY_FREE_SPACE has become good: This role's Log Dire
ctory (/var/log/hadoop-0.20-mapreduce) is on a filesystem with more than 20.
00% of its space free.\",\"testName\":\"JOB_TRACKER_LOG_DIRECTORY_FREE_SPACE
\",\"eventCode\":\"EV_ROLE_HEALTH_CHECK_GOOD\",\"severity\":\"INFORMATIONAL\
"}", "{\"content\":\"The health test result for JOB_TRACKER_HOST_HEALTH has
become good: The health of this role's host is good.\",\"testName\":\"JOB_TR
ACKER_HOST_HEALTH\",\"eventCode\":\"EV_ROLE_HEALTH_CHECK_GOOD\",\"severity\"
:\"INFORMATIONAL\"}", "{\"content\":\"The health test result for JOB_TRACKER
_WEB_METRIC_COLLECTION has become good: The web server of this role is respo
nding with metrics. The most recent collection took 49 millisecond(s).\",\"t
estName\":\"JOB_TRACKER_WEB_METRIC_COLLECTION\",\"eventCode\":\"EV_ROLE_HEAL
TH_CHECK_GOOD\",\"severity\":\"INFORMATIONAL\"}", "{\"content\":\"The health
test result for JOB_TRACKER_GC_DURATION has become good: Average time spent
in garbage collection was 0 second(s) (0.00%) per minute over the previous
5 minute(s).\",\"testName\":\"JOB_TRACKER_GC_DURATION\",\"eventCode\":\"EV_R
OLE_HEALTH_CHECK_GOOD\",\"severity\":\"INFORMATIONAL\"}", "{\"content\":\"Th
e health test result for JOB_TRACKER_HEAP_DUMP_DIRECTORY_FREE_SPACE has beco
me disabled: Test disabled because role is not configured to dump heap when
out of memory. Test of whether this role's heap dump directory has enough fr
ee space.\",\"testName\":\"JOB_TRACKER_HEAP_DUMP_DIRECTORY_FREE_SPACE\",\"ev
```

```
entCode\":\"EV_ROLE_HEALTH_CHECK_DISABLED\",\"severity\":\"INFORMATIONAL\"}"
],
"SERVICE_DISPLAY_NAME" : [ "MAPREDUCE-1" ],
"HOSTS" : [ "myCluster.com" ]
}
}
},
"header" : {
"type" : "alert",
"version" : 2
}
} ]
```

#### Sample Custom Alert Script

```
You can use this sample script to respond to an alert by sending emails based on the content of the alert.
The Sample Custom Alert Script provided below provides an example of how custom alert scripts can be
implemented. This example uses a Python script, which includes multiple routing rules called Alert Templates. Once
the script is called, it parses the alert JSON file using a path provided by the Alert Publisher. Based on the Alert
Templates, it sends out alerts to different email addresses based on the content of the alert.
The script requires an SMTP server (defined by its host and port) and an email address to send out the emails. You
need to set these parameters in the script.
There are multiple Alert Templates in the sample script as examples. Pick the ones you need and delete the rest, or
create new templates.
Python should be always available on your hosts because hosts managed by Cloudera Manager require Python for the
Cloudera Manager Agent to run. Because the Alert Publisher is not able to execute python scripts, a small Bash script
is needed to execute the main Python script.
```
```
Bash Script
This Bash script is required to execute the Python script.
```
```
# © 2022 by Cloudera, Inc. All rights reserved.
# Scripts and sample code are licensed under the Apache License,
# Version 2.0
#!/bin/bash
```
```
python /bin/script_test/main.py $1
```
```
Python script
Setting up the Python script
To use the Python script, you will need to provide the values described below.
```
- SMTP hostname:

```
host = "mailserver.mycompany.com"
```
- SMTP port:

```
port = 25
```

- Sender email address:

```
sender_address = "noreply@mycompany.com"
```
- Values for the AlertTemplate(email, attribute_key, attribute_value, remove_after) method:
    - Email addresses:

```
AlertTemplate("admin@mycompany.com", "SEVERITY", "CRITICAL", False)
```
```
Specify two or more recipients using this format:
```
```
AlertTemplate("admin@mycompany.com, admin2@mycompany.com", "SEVERITY",
"CRITICAL", False)
```
- An attribute_key and attribute_value containing the rules that your alert should match for the email to be sent:

```
AlertTemplate("admin@mycompany.com", "SEVERITY", "CRITICAL", False),
```
```
To use Regular Expression matching for your alerts, use “REGEX” as the attribute_key:
```
```
AlertTemplate("admin@mycompany.com", "REGEX", '.*content": "This is a
test alert that was generated.*', False)
```
```
A None attribute_key and attribute_value pair indicates a default template, which should be applied to all
alerts. You can use this when there's no matching AlertTemplate, but you still do not want to lose the Alert.
```
- remove_after:
    Set this argument to True if you want the alert to not be sent, even if further Alert Templates match the alert:

```
AlertTemplate("admin@mycompany.com", "SEVERITY", "CRITICAL", True),
```
```
Sample Python script
You can copy this script and modify it for your deployment.
```
```
# -*- coding: utf-8 -*-
# © 2022 by Cloudera, Inc. All rights reserved.
# Scripts and sample code are licensed under the Apache License,
# Version 2.0
```
```
#!/usr/bin/env python2
from __future__ import print_function
```
```
import sys
import smtplib
import json
import re
```
```
from email.mime.text import MIMEText
from email.mime.multipart import MIMEMultipart
```
```
class AlertReader(object):
def __init__(self, file_path):
self.alerts = []
self.file_path = file_path
```
```
def read_alert(self):
alert_file = open(self.file_path, "r")
data = json.load(alert_file)
for alert in data:
self.alerts.append(alert["body"]["alert"])
print("Done reading " + self.file_path)
```

```
def print_alerts(self):
print(self.alerts)
```
```
def alert_as_string(alert):
return json.dumps(alert)
```
```
class AlertTemplate(object):
def __init__(self, email, attribute_key, attribute_value, remove_after):
self.email = email
self.attribute_key = attribute_key
self.attribute_value = attribute_value
self.remove_after = remove_after
"""
A None attribute_key and attribute_value pair
indicates a default template, which should be
applied to all alerts. You can use this when
there's no matching AlertTemplate, but you still
don't want to lose the Alert.
```
```
Put these AlertTemplates to the end of your
AlertTemplate list to catch all remaining alerts.
But if only one of the attribute_key or attribute_value is None,
that is an invalid state.
"""
if (self.attribute_key is None) != (self.attribute_value is None):
raise ValueError("AlertTemplate is in invalid state, "
"one of attribute_key or attribute_value is N
one.")
```
```
def does_apply(self, alert):
if self.attribute_key == "REGEX":
alert_string = alert_as_string(alert)
search_result = re.search(self.attribute_value, alert_string)
return search_result is not None
if self.attribute_key == "CONTENT":
if self.attribute_value in alert["content"]:
return True
return False
if self.attribute_key is None and self.attribute_value is None:
return True
try:
if self.attribute_value in alert["attributes"][self.attribute
_key]:
return True
except KeyError:
print("There's no match for attribute_key: " + self.attribute_ke
y)
return False
def to_string(self):
return "AlertTemplate[" + \
str(self.attribute_key) + ": " + \
str(self.attribute_value) + ", " + \
str(self.email) + "]"
```
```
class EmailSender(object):
def __init__(self, smtp_host, smtp_port, sender):
self.server = smtplib.SMTP(smtp_host, smtp_port)
self.sender = sender
```
```
def send_email_to_recipients(self, alerts, alert_templates):
print("Processing alerts to send emails.")
for alert in alerts:
for alert_template in alert_templates:
```

```
if alert_template.does_apply(alert):
"""
With a template with no email address, you usually want
to exclude
a type of alert from the processed alert list. Use None
to email address
with remove_after = True if you want an alert to be remo
ved from the
list of alerts sent.
These templates should be in the beginning of the temp
late list.
"""
if alert_template.email is not None:
self.send_email(alert_template, alert)
print(create_message_text(alert_template, alert))
print("Sending alert based on " + alert_template.to_str
ing())
if alert_template.remove_after:
break
print("All alerts are processed.")
def send_email(self, alert_template, alert):
message = MIMEMultipart("alternative")
message["Subject"] = "Cloudera Alert"
message["From"] = self.sender
message["To"] = alert_template.email
message.attach(MIMEText(create_message_text(alert_template, alert),
"plain"))
self.server.sendmail(self.sender, alert_template.email.split(","), m
essage.as_string())
```
```
def create_message_text(alert_template, alert):
out = alert_template.to_string()
out += " firing for: \n"
out += alert_as_string(alert)
return out
```
```
if __name__ == '__main__':
"""
SMTP server parameters:
```
- email where the emails sent from
- file name, where the alerts are coming from. This is provided by
the script interface.
Alert templates:
- email address to send email to when the alert contains the specif
ied key with the specified value.
- Set remove_after to True if you don't want the alert sent to other
recipients,
even if the template is matching. Because of this, it is required t
hat the recipients
list is in a specific order.
"""
host = "mailserver.mycompany.com" # SMTP server host name
port = 25 # SMTP Server port
sender_address = "noreply@"MyCompanyMailServer" # Email address to send
emails from
# The file's name which contains the alerts is provided by the script
framework
if len(sys.argv) < 2:
print("Please provide a file path for alerts. Usually this comes fro
m the script framework.")
exit(2)
file_name = sys.argv[1]
alert_reader = AlertReader(file_name)


```
recipients = []
try:
recipients = [AlertTemplate(None, None, None, True), # This templ
ate matches every alert
# This template matches to all alerts which matches to
the given regex pattern
AlertTemplate("admin@mycompany.com", "REGEX", '.*cont
ent": "This is a test alert that was generated.*', False),
# This template matches only for issues with critical
severity
AlertTemplate("admin@mycompany.com", "SEVERITY", "CRIT
ICAL", False),
# This template matches only for Kafka related issues
AlertTemplate("kafka_admin@mycompany.com", "SERVICE
_TYPE", "KAFKA", True),
# This template matches only for Kafka Broker related
issues
AlertTemplate("user1@gmail.com", "ROLE_TYPE", "KAFK
A_BROKER", True),
# This template matches only for a specific host's a
lerts
AlertTemplate("admin2@mycompany.com", "HOSTS", "myho
st", True),
# This template matches for a specific cluster's alert
s
AlertTemplate("admin3@mycompany.com", "CLUSTER", "Cl
uster 1", True),
# This template matches for a specific health test me
ssage
AlertTemplate("admin@mycompany.com", "CONTENT", "This
is a test alert that was generated by user request from "
"Cloudera Manager", Tru
e)]
except ValueError as error:
print(error)
exit(2)
```
```
alert_reader.read_alert()
alert_reader.print_alerts()
email_sender = EmailSender(host, port, sender_address)
email_sender.send_email_to_recipients(alert_reader.alerts, recipients)
```
### Alert email routing

```
In multi-tenant or large-cluster environments, routing specific alerts to the right person can ensure a healthy
deployment. With Alert email routing, you can define the alert rules in Cloudera Manager to send email alerts to
selected email addresses and avoid sending all alert notifications to one or more email addresses.
Alert rules are defined based on user profiles, clusters, hosts, services, roles, host groups, service groups, service
types, role groups, role types, the severity of the alert, priority, and specific health tests. A host or service or role
group is a collection of hosts or services or roles respectively to which the same alert rule applies.
Some of the use cases for Alert email routing are as follows:
```
- You can create a role group that includes all the secondary roles such as Data Nodes. When configuring an alert
    rule for this role group, you can include the email addresses of the experts of these roles so that they receive email
    notifications only about the critical alerts of the secondary roles. You can even silence the alerts of the non-critical
    roles of this group and react more quickly to the critical alerts.
- You can create a service group that includes all the storage services such as HDFS and HBase. When configuring
    an alert rule for this service group, you can include the email addresses of your storage experts who should receive
    email notifications only about the alerts of the storage services.


- You can create a host group that includes the hosts that are in the same rack such as Rack1. When configuring an
    alert rule for this host group, you can include the email addresses of the cluster administrator of these hosts who
    should receive email notifications only about the alerts of Rack1.
- If the cluster operator does not need email notifications about a health test that is often in a bad state and is not
    critical for the operation, then the operator can define an alert rule to silence the alerts of that health test.
You can configure the following parameters for Alert email routing:
- User profiles - A user profile defines a user or a user group who should receive email alerts.
- Host groups - A host group defines a subset of hosts. You can use this group as one logical unit for email alerting.
- Service grouos - A service group defines a subset of services. You can use this group as one logical unit for email
    alerting.
- Role groups - A role group defines a subset of roles. You can use this group as one logical unit for email alerting.
- Alert rules - An alert rule ensures certain hosts or services or roles or health test alerts are sent to only selected
    email addresses.

#### Configuring user profiles for email alerts

```
You can configure a user profile using Cloudera Manager. A user profile defines a user or a user group who should
receive email alerts. You can create any number of user profiles.
```
```
Before you begin
Minimum Required Role: Limited Cluster Administrator (also provided by Full Administrator and Cluster
Administrator)
```
```
Procedure
```
1. Log into Cloudera Manager as an Administrator.
2. Go to Clusters Cloudera Management Service Configuration.
3. Select Alert Publisher from the SCOPE drop-down menu and select Main from the CATEGORY drop-down
    menu.
4. Locate the User profiles for email alerting property or search for it by typing its name in the Search box.
5.
    Configure the User profiles for email alerting property. Click Add Another to add a new user profile.
6. Enter a unique name for the user profile in the Key field.
7. Enter the comma-separated list of email addresses in the Value field.
8. Click Save Changes at the bottom of the page to save your settings.
9. Restart the Alert Publisher role. For more information, see Starting, Stopping, and Restarting Role Instances.


#### Configuring host groups for email alerts

```
You can configure a host group using Cloudera Manager. A host group defines a subset of hosts and alerts generated
by hosts are sent to the cluster administrator who manages these hosts. You can create any number of host groups.
```
```
Before you begin
Minimum Required Role: Limited Cluster Administrator (also provided by Full Administrator and Cluster
Administrator)
```
```
Procedure
```
- Log into Cloudera Manager as an Administrator.
- Go to Clusters Cloudera Management Service Configuration.


Cloudera Manager Alerts

- Select Alert Publisher from the SCOPE drop-down menu and select Main from the CATEGORY drop-down
    menu.
- Locate the Host groups for email alerting property or search for it by typing its name in the Search box.
-
    Configure the Host groups for email alerting property. Click Add Another to add a new host group.
- Enter a unique name for the host group in the Key field.
- Enter the comma-separated list of host names in the Value field.
    Important: If you do not enter a valid host name, then you might encounter a validation error. In case of
    an empty list, all managed hosts are considered as a host group.
- Click Save Changes at the bottom of the page to save your settings.
- Restart the Alert Publisher role. For more information, see Starting, Stopping, and Restarting Role Instances.

#### Configuring service groups for email alerts

```
You can configure a service group using Cloudera Manager. A service group defines a subset of services for which
you need email alerts. You can create any number of service groups.
```
```
Before you begin
Minimum Required Role: Limited Cluster Administrator (also provided by Full Administrator and Cluster
Administrator)
```
```
Procedure
```
1. Log into Cloudera Manager as an Administrator.
2. Go to Clusters Cloudera Management Service Configuration.
3. Select Alert Publisher from the SCOPE drop-down menu and select Main from the CATEGORY drop-down
    menu.
4. Locate the Service groups for email alerting property or search for it by typing its name in the Search box.
5.
    Configure the Service groups for email alerting property. Click Add Another to add a new service group.
6. Enter a unique name for the service group in the Key field.
7. Enter the comma-separated list of service names in the Value field.
    Important: If you do not enter a valid service name, then you might encounter a validation error. In case
    of an empty list, all managed services are considered as a service group.
8. Click Save Changes at the bottom of the page to save your settings.
9. Restart the Alert Publisher role. For more information, see Starting, Stopping, and Restarting Role Instances.

#### Configuring role groups for email alerts

```
You can configure a role group using Cloudera Manager. A role group defines a subset of roles and their alerts are
sent to the experts who manage these roles. You can create any number of role groups.
```
```
Before you begin
Minimum Required Role: Limited Cluster Administrator (also provided by Full Administrator and Cluster
Administrator)
```

```
Procedure
```
- Log into Cloudera Manager as an Administrator.
- Go to Clusters Cloudera Management Service Configuration.
- Select Alert Publisher from the SCOPE drop-down menu and select Main from the CATEGORY drop-down
    menu.
- Locate the Role groups for email alerting property or search for it by typing its name in the Search box.
-
    Configure the Role groups for email alerting property. Click Add Another to add a new role group.
- Enter a unique name for the role group in the Key field.
- Enter the comma-separated list of role names in the Value field.
    Important: If you do not enter a valid role name, then you might encounter a validation error. In case of
    an empty list, all managed roles are considered as a role group.
- Click Save Changes at the bottom of the page to save your settings.
- Restart the Alert Publisher role. For more information, see Starting, Stopping, and Restarting Role Instances.

```
Related Information
Starting, Stopping, and Restarting Role Instances
```
#### Configuring alert rules for email alerts................................................................................................

```
You can configure an alert rule using Cloudera Manager. An alert rule ensures certain hosts or services or roles or
health test alerts are sent to only selected email addresses. You can create any number of alert rules.
```
```
Before you begin
Minimum Required Role: Limited Cluster Administrator (also provided by Full Administrator and Cluster
Administrator)
```
```
Procedure
```
1. Log into Cloudera Manager as an Administrator.
2. Go to Clusters Cloudera Management Service Configuration.
3. Select Alert Publisher from the SCOPE drop-down menu and select Main from the CATEGORY drop-down
    menu.
4. Locate the Alert rules for email alerting property or search for it by typing its name in the Search box.
5.
    Configure the Alert rules for email alerting property. Click Add Another to add a new alert rule.
6. Select the severity level of the alert from the list of severity levels (Warning, Critical, or Both).
    Important:
    For Health Alert Threshold, you must select the Concerning parameter to ensure the email alerts are sent
    with the warning severity.
    To select this parameter, from the Cloudera Manager home page, navigate to Clusters Cloudera
    Management Console Configuration and in the search bar, type Health Alert Threshold.
7. Enter the priority value for the alert rule in the Priority field.
    Important: The alert rule with the lowest priority value is processed first. The priority value must be a
    non-negative integer.

8. Specify the values in the User Profiles, Clusters, Hosts, Services, Roles, Host Groups, Service Groups, Service
    Types, Role Groups, Role Types, and Health Tests fields as needed. You must enter the values atleast in one of
    these fields to create a matching alert rule.
       Important: If the User Profiles field remains empty, then no users receive email notifications about the
       alerts. You can enter any number of predefined user profiles in the User Profiles field. If there is more
       than one user profile, then email alerts are sent to more addresses.
       You must set the Alert: Mail From Address parameter according to the mail server hostname. Otherwise,
       the emails may not sent to an external email service.
9. Click Save Changes at the bottom of the page to save your settings.
10.Restart the Alert Publisher role. For more information, see Starting, Stopping, and Restarting Role Instances.

### Enabling Configuration Change Alerts

```
You can set configuration change alerts to be service-wide, or on specific roles for the service.
```
```
About this task
Minimum Required Role: Limited Cluster Administrator (also provided by Full Administrator and Cluster
Administrator)
```
```
Procedure
```
1. Click a service, role, or host.
2. Click the Configuration tab.
3. Click the Monitoring category.
4. Check the Enable Configuration Change Alerts checkbox.
5. Enter a Reason for change, and then click Save Changes to commit the changes.
6. Click the Cloudera Manager logo to return to the Home page.
7. Click the icon that is next to any stale services to invoke the cluster restart wizard.

### Enabling HBase Alerts

```
You can enable region or Hbck alerts for the HBase service.
```
```
About this task
Minimum Required Role: Limited Cluster Administrator (also provided by Full Administrator and Cluster
Administrator)
```
```
Procedure
```
1. Go to the HBase service.
2. Click the Configuration tab.
3. Select Scope HBase service_name (Service-Wide).
4. Click the Monitoring category.
5. Set one of the region or Hbck alerts:
    - Hbck Region Error Count
    - Hbck Error Count
    - Hbck Alert Error Codes
    - Hbck Slow Run
    - Region Health Canary Slow Run
    - Canary Unhealthy Region Count
    - Canary Unhealthy Region Percentage
6. Enter a Reason for change, and then click Save Changes to commit the changes.
7. Click the Cloudera Manager logo to return to the Home page.
8. Click the icon that is next to any stale services to invoke the cluster restart wizard.

### Enabling Health Alerts

```
You can enable alerts when the health of a role or service crosses a threshold.
```
```
About this task
Minimum Required Role: Limited Cluster Administrator (also provided by Full Administrator and Cluster
Administrator)
```
```
Procedure
```
1. Select Clusterscluster_nameservice_name or open the page for a role.
2. Click the Configuration tab.
3. Select Scoperole_name or service_name (Service-Wide).
4. Click the Monitoring category.
5. Check the Enable Health Alerts for this Role or Enable Service Level Health Alerts checkbox, depending on
    whether you are configuring a role or a service.
6. Enter a Reason for change, and then click Save Changes to commit the changes.
7. Click the Cloudera Manager logo to return to the Home page.
8. Click the icon that is next to any stale services to invoke the cluster restart wizard.

### Modifying the Health Threshold

```
You can configure the threshold for when a health alert is raised.
```
```
About this task
Minimum Required Role: Limited Cluster Administrator (also provided by Full Administrator and Cluster
Administrator)
```
```
Procedure
```
1. Select AdministrationAlerts.
2. Click to the right of Health Alert Threshold.
3. Select ScopeEvent Server.
4. Click the Main category.
5. Select the Bad or Concerning option.
6. Enter a Reason for change, and then click Save Changes to commit the changes.
7. Click the Cloudera Manager logo to return to the Home page.
8. Click the icon that is next to any stale services to invoke the cluster restart wizard.

### Configuring Alerts Transitioning Out of Alerting Health Threshold

```
You can configure an alert when a service or role instance transitions from an alerting to a non-alerting health
threshold.
```
```
About this task
Minimum Required Role: Limited Cluster Administrator (also provided by Full Administrator and Cluster
Administrator)
```
```
Procedure
```
1. Select AdministrationAlerts.
2. Click to the right of Alert on Transitions out of Alerting Health.
3. Select Scoperole_name or service_name (Service-Wide).
4. In the category Event Server Default Group, check the Alert on Transitions out of Alerting Health checkbox.
5. Enter a Reason for change, and then click Save Changes to commit the changes.
6. Click the Cloudera Manager logo to return to the Home page.
7. Click the icon that is next to any stale services to invoke the cluster restart wizard.

### Configuring Log Alerts

```
You can configure an alert when a daemon emits a log message that matches a specified regular expression. For more
information, see Configuring Log Alerts.
Related Information
Configuring Log Alerts
```
### Configuring Alert Delivery

```
You can configure alerts to be delivered by email or sent as SNMP traps.
If you choose email delivery, you can add to or modify the list of alert recipient email addresses. You can also send a
test alert email.
Note: If alerting is enabled for events, you can search for and view alerts in the Events tab, even if you do
not have email notification configured.
```
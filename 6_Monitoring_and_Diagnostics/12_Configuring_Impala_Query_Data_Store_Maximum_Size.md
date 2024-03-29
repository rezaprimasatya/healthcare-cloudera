### Configuring Impala Query Data Store Maximum Size

```
You can configure the Impala query data store size. The query store stores enough information to make the query
searchable through the filter language.
```
```
About this task
Minimum Required Role: Configurator (also provided by Cluster Administrator, Limited Cluster Administrator , and
Full Administrator)
```
```
Procedure
```
-  Do one of the following:
   - Select ClustersCloudera Management Service.
   - On the HomeStatustab, in the Cloudera Management Service table, click the Cloudera Management Service
-      link.
-  Click the Configuration tab.
-  Select ScopeService Monitor.
-  Click the Main category.
-  In the Impala Storage section, set the firehose_impala_storage_bytes property. The default is 1 GiB.
    -   The firehose_impala_storage_bytes property determines the approximate amount of disk space dedicated to
    -   storing Impala query data. Once the store reaches its maximum size, older data is deleted to make room for newer
    -   queries. The disk usage is approximate because data deletion begins only when the limit has been reached.
-  Enter a Reason for change, and then click Save Changes to commit the changes.
-  Click the Cloudera Manager logo to return to the Home page.
-  Click the icon that is next to any stale services to invoke the cluster restart wizard.
### Configuring Impala Query Monitoring

```
You can configure the visibility of the Impala query results and the size of the storage allocated to Impala query
results.
```
```
About this task
To configure whether admin or non-admin users can view all queries, only that user's queries, or no queries:
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

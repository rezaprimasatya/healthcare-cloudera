### Configuring Health Monitoring

```
Depending on the service or role you select, and the configuration category, you can enable or disable health tests,
determine when health tests cause alerts, or determine whether specific health tests are used in computing the overall
health of a role or service. In most cases you can disable these "roll-up" health tests separately from the individual
health tests.
The initial health monitoring configuration is handled during the installation and configuration of your cluster, and
most monitoring parameters have default settings. However, you can set or modify these at any time.
As a rule, a health test whose result is considered "Concerning" or "Bad" is forwarded as an event to the Event Server.
That includes health tests whose results are based on configured Warning or Critical thresholds, as well pass-fail type
health tests. An event is also published when the health test result returns to normal.
You can control when an individual health test is forwarded as an event or as an alert by modifying the threshold
values for the relevant health test.
```
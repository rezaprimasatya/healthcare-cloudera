### Configuring Directory Monitoring

```
Cloudera Manager can perform threshold-based monitoring of free space in the various directories on the hosts it
monitor, such as log directories or checkpoint directories (for the Secondary NameNode).
These thresholds can be set in one of two ways—as absolute thresholds (in terms of MiB and GiB, and so on) or as
percentages of space. As with other threshold properties, you can set values that trigger events at both the Warning
and Critical levels.
If you set both thresholds, the Absolute Threshold setting is used.
```
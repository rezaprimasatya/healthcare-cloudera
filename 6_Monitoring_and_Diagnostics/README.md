# Monitoring and Diagnostics

- Accessing the Cloudera Manager Admin Console
- Monitoring and Diagnostics
- Time Line.
   - Selecting a Point In Time or a Time Range
- Health Tests.
   - Viewing Health Test Results
   - Suppressing Health Test Results
   - Suppressing a Health Test
   - Configuring Suppression of Health Tests Before Tests Run
   - Viewing a List of Suppressed Health Tests.
   - Unsuppressing Health Tests.
- Viewing Charts for Cluster, Service, Role, and Host Instances.
   - Exporting Data from Charts.
   - Adding and Removing Charts from a Dashboard
   - Creating Triggers from Charts
- Configuring Monitoring Settings
   - Configuring Health Monitoring
   - Configuring Service Monitoring
   - Configuring Host Monitoring
   - Configuring Directory Monitoring
   - Configuring YARN Application Monitoring
   - Configuring Impala Query Monitoring
   - Configuring Impala Query Data Store Maximum Size
   - Enabling Configuration Change Alerts
   - Filtering Metrics
   - Configuring Log Events
      - Configuring Logs
      - Configuring Logging Thresholds
      - Configuring Log Directories
      - Enabling and Disabling Log Event Capture
      - Configuring Which Log Messages Become Events
      - Configuring Log Alerts
- Monitoring Clusters
- Cluster Utilization Report overview
   - Enable the Cluster Utilization Report
   - Configure the Cluster Utilization Report Cloudera Manager
   - Use the Cluster Utilization Report to manage resources
      - Overview Tab
      - Impala Tab
      - Download the Cluster Utilization Report
   - Creating a Custom Cluster Utilization Report
      - Metrics and queries
      - Impala query counter metrics
      - Calculations for reports
      - Retrieving metric data
      - Querying metric data
- Inspecting Network Performance.
   - Running the Network Performance Inspector From the Cloudera Manager Admin Console
   - Running the Network Performance Inspector From the Cloudera Manager API
- Monitoring Services
   - Monitoring Service Status
      - Viewing the URLs of the Client Configuration Files
      - Viewing the Status of a Service Instance
      - Viewing the Health and Status of a Role Instance
      - Viewing the Maintenance Mode Status of a Cluster
   - Viewing Service Status
      - Viewing Past Status
      - Status Summary.
      - Service Summary
      - Health Tests and Health History
   - Viewing Service Instance Details
      - Role Instance Reference.
   - Viewing Role Instance Status
      - The Actions Menu
      - Viewing Past Status
      - Summary.
      - Health Tests and Health History
      - Status Summary.
      - Charts.
      - The Processes Tab
   - Running Diagnostic Commands for Roles
   - Periodic Stacks Collection
      - Configuring Periodic Stacks Collection.
      - Viewing and Downloading Stacks Logs
   - Viewing Running and Recent Commands
      - Viewing Running and Recent Commands For a Cluster
      - Viewing Running and Recent Commands for a Service or Role
      - Command Details
- Monitoring Hosts
   - Viewing All Hosts
   - Role Assignments
   - Viewing the Disks Overview
   - Viewing the Hosts in a Cluster
   - Viewing Individual Hosts
   - Host Details
      - Viewing Host Details Cloudera Manager
      - Status.
      - Processes.
      - Resources.
      - Commands
      - Configuration
      - Components
      - Audits
      - Charts Library
   - Host Inspector
      - Running the Host Inspector
      - Viewing Past Host Inspector Results
- Monitoring Activities
   - Selecting Columns to Show in the Activities List
   - Sorting the Activities List
   - Filtering the Activities List
   - Activity Charts
   - Viewing the Jobs in a Pig, Oozie, or Hive Activity
   - Task Attempts
      - Viewing a Job's Task Attempts
      - Selecting Columns to Show in the Tasks List
      - Sorting the Tasks List
      - Filtering the Tasks List
   - Viewing Activity Details in a Report Format
   - Comparing Similar Activities
   - Viewing the Distribution of Task Attempts.
      - The Task Distribution Chart.
      - TaskTracker Hosts
   - Monitoring Impala Queries
      - Viewing Queries
      - Configuring Impala Query Monitoring
      - Impala Best Practices
      - Results Tab
      - Filtering Queries
      - Filter Expressions
      - Filter Attributes
      - Choosing and Running a Filter
   - Query Details
   - Monitoring YARN Applications
      - Viewing Jobs
      - Configuring YARN Application Monitoring
      - Results Tab
      - Filtering Jobs
      - Filter Expressions
      - Choosing and Running a Filter
      - Filter Attributes
      - Sending Diagnostic Data to Cloudera for YARN Applications
   - Monitoring Spark Applications
      - Viewing and Debugging Spark Applications Using Logs
      - Managing Spark Driver Logs
      - Visualizing Spark Applications Using the Web Application UI
      - Accessing the Web UI of a Running Spark Application
      - Accessing the Web UI of a Completed Spark Application.
- Events Cloudera Manager
   - Viewing Events.
   - Filtering Events.
      - Adding an Event Filter.
      - Removing an Event Filter
- Alerts
   - Managing Alerts
   - Configuring Alert Email Delivery
   - Configuring Alert SNMP Delivery
   - Configuring Custom Alert Scripts
      - Sample Custom Alert Script
   - Alert email routing
      - Configuring user profiles for email alerts.
      - Configuring host groups for email alerts
      - Configuring service groups for email alerts
      - Configuring role groups for email alerts
      - Configuring alert rules for email alerts
   - Enabling Configuration Change Alerts
   - Enabling HBase Alerts
   - Enabling Health Alerts
   - Modifying the Health Threshold
   - Configuring Alerts Transitioning Out of Alerting Health Threshold
   - Configuring Log Alerts
   - Configuring Alert Delivery
- Triggers
   - Creating a Trigger Using the Expression Editor
   - Editing, Deleting, Suppressing, or Deleting a Trigger
   - Cloudera Manager Trigger Use Cases.
      - Creating a Trigger for Memory Capacity.
      - Creating a Trigger for CPU Capacity
- Lifecycle and Security Auditing
   - Viewing Audit Events.
   - Filtering Audit Events.
      - Adding a Filter.
      - Removing a Filter
   - Downloading Audit Events
- Charting Time-Series Data
   - Terminology
   - Building a Chart with Time-Series Data
   - Configuring Time-Series Query Results
   - Using Context-Sensitive Variables in Charts
   - Chart Properties
      - Changing the Chart Type
      - Grouping (Faceting) Time Series
   - Displaying Chart Details
   - Editing a Chart
   - Saving a Chart Cloudera Manager
   - Obtaining Time-Series Data Using the API
   - Dashboards
      - Dashboard Types
      - Creating a Dashboard
      - Managing Dashboards
      - Configuring Dashboards
      - Saving Charts to Dashboards
      - Saving Charts to a New Dashboard
      - Saving Charts to an Existing Dashboard
      - Adding a New Chart to the Custom Dashboard
      - Removing a Chart from a Custom Dashboard
      - Moving and Resizing Charts
   - tsquery Language
      - tsquery Syntax
      - Metric Expressions
      - Metric Expression Functions
      - Predicates
      - Discovering possible predicates
      - Filtering by Day of Week or Hour of Day
      - Time Series Attributes
      - Time Series Entities and their Attributes
      - FAQ.
   - Metric Aggregation
      - Presentation of Aggregate Data
      - Accessing Aggregate Statistics Through tsquery
   - Filtering Metrics
- Logs.
   - Viewing Logs
   - Logs List
   - Filtering Logs
   - Log Details
   - Viewing the Cloudera Manager Server Log
      - Viewing Cloudera Manager Server Logs in the Logs Page
      - Viewing the Cloudera Manager Server Log
   - Viewing the Cloudera Manager Agent Logs
      - Viewing Cloudera Manager Agent Logs in the Logs Page
      - Viewing the Cloudera Manager Agent Log
   - Managing Disk Space for Log Files
      - Disk Space Requirements
      - Managing Log Files
- Reports.
   - Directory Usage Report
      - Accessing the Directory Usage Report
      - Using the Directory Usage Report.
   - Disk Usage Reports
      - Viewing Current Disk Usage by User, Group, or Directory
      - Viewing Historical Disk Usage by User, Group, or Directory
      - Downloading Reports as CSV and XLS Files
   - Activity, Application, and Query Reports.
   - The File Browser
      - Searching Within the File System
      - Enabling Snapshots.
      - Setting Quotas
      - Designating Directories to Include in Disk Usage Reports
      - Downloading HDFS Directory Access Permission Reports
- Cluster Support Tokens using Cloudera Manager
- Sending Usage and Diagnostic Data to Cloudera
   - Configuring a Proxy Server
   - Managing Anonymous Usage Data Collection
   - Diagnostic Data Collection.
   - Log support in Cloudera Manager for ECS cluster
   - Configuring the Frequency of Diagnostic Data Collection
   - Configuring collection of Cloudera Manager table data
   - Specifying the Diagnostic Data Directory.
   - Redaction of Sensitive Information from Diagnostic Bundles
   - Disabling the Automatic Sending of Diagnostic Data from a Manually Triggered Collection
   - Manually Triggering Collection and Transfer of Diagnostic Data to Cloudera
- Troubleshooting Cluster Configuration and Operation
   - Solutions to Common Problems
   - Logs and Events
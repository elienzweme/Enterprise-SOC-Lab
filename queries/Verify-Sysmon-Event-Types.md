# Verify Sysmon Event Types

## Query

```spl id="8z2g4r"
sourcetype="XmlWinEventLog:Microsoft-Windows-Sysmon/Operational"
| rex "<EventID>(?<EventID>\d+)</EventID>"
| stats count by EventID
```

## Purpose

This query was used to identify and validate the different Sysmon event types being collected and indexed by Splunk Enterprise.

By extracting the Event ID field from raw Sysmon XML telemetry and grouping results by Event ID, the query provides visibility into the categories of endpoint activity being monitored across the Enterprise SOC Lab environment.

## Results

| Event ID | Description        |
| -------- | ------------------ |
| 1        | Process Creation   |
| 3        | Network Connection |
| 11       | File Create        |
| 13       | Registry Value Set |
| 22       | DNS Query          |

The query confirmed that multiple categories of Sysmon telemetry were successfully collected and searchable within Splunk Enterprise.

## Security Value of Each Event Type

### Event ID 1 – Process Creation

Provides visibility into executable activity, command-line arguments, parent-child process relationships, and user activity.

### Event ID 3 – Network Connection

Tracks outbound network connections initiated by processes and helps identify suspicious communications.

### Event ID 11 – File Create

Records file creation activity and assists in detecting malware drops, ransomware behavior, and unauthorized file changes.

### Event ID 13 – Registry Value Set

Monitors registry modifications that may indicate persistence mechanisms or system configuration changes.

### Event ID 22 – DNS Query

Captures DNS requests made by processes and helps identify suspicious domains, command-and-control activity, and malware communications.

## Validation Outcome

The results confirmed that:

* Sysmon was functioning correctly on all monitored endpoints.
* The SwiftOnSecurity Sysmon configuration was generating useful security telemetry.
* Splunk Universal Forwarders were successfully forwarding events.
* Splunk Enterprise was receiving and indexing Sysmon data.
* Multiple threat-hunting data sources were available for analysis.

## Why It Matters

Threat hunting relies on high-quality endpoint telemetry.

This validation query demonstrated that the Enterprise SOC Lab was collecting a diverse set of security-relevant events capable of supporting:

* Threat Detection
* Incident Investigation
* Endpoint Monitoring
* Security Analytics
* Threat Hunting
* SOC Operations

The successful collection of these event types provided the foundation for subsequent investigations and custom Splunk SPL searches.

## Skills Demonstrated

* Sysmon Deployment
* Splunk Enterprise
* XML Field Extraction
* Security Telemetry Validation
* Endpoint Monitoring
* Threat Hunting
* SIEM Administration
* Security Operations

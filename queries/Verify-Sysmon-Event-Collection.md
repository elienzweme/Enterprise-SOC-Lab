# Verify Sysmon Event Collection

## Query

```spl id="prq4n2"
index=* sourcetype="XmlWinEventLog:Microsoft-Windows-Sysmon/Operational"
| stats count by host
```

## Purpose

This query was used to confirm that Sysmon telemetry was successfully being collected, forwarded, indexed, and stored within Splunk Enterprise.

By counting Sysmon events by host, the search provides visibility into which systems are actively generating endpoint security telemetry.

## Results

The query successfully verified Sysmon event collection from:

* DC01 (Windows Server 2025 Domain Controller)
* Client01 (Windows 11 Pro)
* Client02 (Windows 11 Pro)

Each host generated searchable Sysmon events within Splunk Enterprise.

## Validation Outcome

The results confirmed that:

* Sysmon was installed and operational.
* Windows Event Logs were recording Sysmon telemetry.
* Splunk Universal Forwarders were collecting events.
* Splunk Enterprise was receiving and indexing data.
* Endpoint telemetry was available for threat hunting and investigation.

## Security Monitoring Pipeline Validated

```text id="qakj8u"
Sysmon
   ↓
Windows Event Log
   ↓
Splunk Universal Forwarder
   ↓
TCP Port 9997
   ↓
Splunk Enterprise
   ↓
Indexing
   ↓
Search & Reporting
```

## Why It Matters

Successful security monitoring depends on reliable telemetry collection.

This query provided evidence that all monitored endpoints were successfully integrated into the SIEM environment and that endpoint telemetry was available for:

* Threat Hunting
* Security Monitoring
* Incident Investigation
* Detection Engineering
* SOC Operations

Without successful event collection, security analysts would have limited visibility into endpoint activity and potential threats.

## Skills Demonstrated

* Splunk Enterprise Administration
* Sysmon Deployment
* Endpoint Telemetry Collection
* Log Validation
* SIEM Operations
* Security Monitoring
* Threat Hunting Preparation
* Troubleshooting and Verification

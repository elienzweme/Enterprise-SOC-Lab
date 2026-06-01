# Final Validation Search

## Query

```spl id="2u3n4t"
sourcetype="XmlWinEventLog:Microsoft-Windows-Sysmon/Operational"
| table host sourcetype
```

## Purpose

This query was used as the final validation step to confirm that Sysmon telemetry was successfully reaching Splunk Enterprise from all monitored endpoints.

The query provides a simple view of the host names generating Sysmon events and verifies that Splunk is receiving and indexing endpoint telemetry.

## Results

The query successfully displayed events from:

* DC01 (Windows Server 2025 Domain Controller)
* Client01 (Windows 11 Pro)
* Client02 (Windows 11 Pro)

All systems were actively generating Sysmon events that were searchable within Splunk Enterprise.

## Validation Outcome

The results confirmed that:

* Sysmon was successfully installed on all endpoints.
* Windows Event Logs were being generated correctly.
* Splunk Universal Forwarders were forwarding telemetry.
* Splunk Enterprise was receiving and indexing events.
* Host information was properly associated with incoming data.

## Why It Matters

This search provided definitive proof that all endpoints were successfully integrated into the SIEM environment.

Without successful validation, threat hunting and security investigations would not be possible because the required telemetry would not be available for analysis.

This query served as the final confirmation that the Security Monitoring Pipeline was functioning end-to-end.

## Security Monitoring Pipeline Validated

```text id="1b99oh"
Windows Endpoint
      ↓
Sysmon
      ↓
Windows Event Logs
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

## Skills Demonstrated

* Splunk Enterprise Administration
* Sysmon Deployment
* Endpoint Telemetry Validation
* Log Management
* SIEM Operations
* Security Monitoring
* Troubleshooting and Validation

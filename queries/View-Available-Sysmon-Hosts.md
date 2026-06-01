# View Available Sysmon Hosts

## Query

```spl id="5uvbkt"
sourcetype="XmlWinEventLog:Microsoft-Windows-Sysmon/Operational"
| head 20
```

## Purpose

This query was used to inspect raw Sysmon events and verify that endpoint telemetry was being received and indexed by Splunk Enterprise.

By viewing a sample of recent Sysmon events, the search provides quick confirmation that monitored hosts are actively generating telemetry.

## Results

The query returned Sysmon events from:

* DC01 (Windows Server 2025 Domain Controller)
* Client01 (Windows 11 Pro)
* Client02 (Windows 11 Pro)

The results confirmed that Sysmon events from multiple endpoints were successfully available within Splunk Enterprise.

## Validation Outcome

The search verified that:

* Sysmon was operational on all monitored endpoints.
* Splunk Universal Forwarders were forwarding telemetry correctly.
* Splunk Enterprise was receiving and indexing Sysmon events.
* Host information was being preserved within the event data.
* Multiple systems were contributing telemetry to the centralized SIEM platform.

## Why It Matters

Before performing threat hunting or security investigations, analysts must verify that telemetry is actually being collected.

This query served as a quick validation step to confirm that endpoint telemetry was being indexed correctly and that all monitored systems were visible within Splunk Enterprise.

Without this validation, threat-hunting results could be incomplete due to missing or improperly collected data.

## Skills Demonstrated

* Splunk Enterprise
* Sysmon Validation
* Endpoint Monitoring
* Log Collection Verification
* SIEM Administration
* Security Monitoring
* Threat Hunting Preparation

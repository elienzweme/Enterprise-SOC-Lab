# Verify Endpoint Connectivity

## Query

```spl id="q5m4k8"
index=* | stats count by host sourcetype
```

## Purpose

This query was used to verify that all monitored systems were successfully forwarding log data to Splunk Enterprise.

By grouping events by host and sourcetype, the query provides visibility into which systems are actively sending logs and what types of events are being collected.

## Results

The query confirmed successful log ingestion from:

* DC01 (Windows Server 2025 Domain Controller)
* Client01 (Windows 11 Pro)
* Client02 (Windows 11 Pro)

Each host appeared within Splunk search results, demonstrating successful communication with the SIEM platform.

## Validation Outcome

The results verified that:

* Splunk Universal Forwarders were installed and operational.
* Forwarders could communicate with Splunk Enterprise.
* TCP Port 9997 was functioning correctly.
* Log data was being received and indexed.
* Multiple hosts were contributing telemetry to the centralized monitoring platform.

## Security Monitoring Pipeline Validated

```text id="4tuz8n"
Windows Endpoint
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

This query served as the initial validation step for the Enterprise SOC Lab.

Before investigating Sysmon telemetry or conducting threat hunting activities, it was necessary to confirm that endpoints were successfully connected to Splunk Enterprise and actively forwarding log data.

This validation provided evidence that the centralized logging infrastructure was functioning correctly and established the foundation for subsequent security monitoring and threat-hunting activities.

## Skills Demonstrated

* Splunk Enterprise Administration
* Log Collection Validation
* Endpoint Connectivity Verification
* Splunk Universal Forwarder Configuration
* SIEM Operations
* Security Monitoring
* Troubleshooting and Validation

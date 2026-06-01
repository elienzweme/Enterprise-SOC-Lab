# Process Name Extraction from Sysmon XML

## Query

```spl id="c8b2rq"
sourcetype="XmlWinEventLog:Microsoft-Windows-Sysmon/Operational"
| rex "<Data Name='Image'>(?<Image>[^<]+)</Data>"
| stats count by host Image
```

## Purpose

This query extracts executable names from raw Sysmon XML events using the Splunk `rex` command.

The extracted process names are then grouped by host and counted to provide visibility into process execution activity across the Enterprise SOC Lab environment.

## Data Extracted

The query extracts:

* Host Name
* Executable Image Name
* Process Execution Count

## Example Results

The query successfully identified process activity such as:

* notepad.exe
* powershell.exe
* splunkd.exe
* splunk-regmon.exe
* splunk-netmon.exe
* splunk-admon.exe
* splunk-powershell.exe

These results confirmed that Sysmon process creation events were being collected and indexed correctly.

## Investigation Benefits

The query provides analysts with the ability to:

* Identify processes running on monitored systems.
* Detect unusual or unauthorized executables.
* Establish a baseline of normal process activity.
* Support threat hunting investigations.
* Monitor endpoint behavior across multiple hosts.

## Why It Matters

Process execution visibility is a fundamental component of security monitoring and threat detection.

By extracting executable names from Sysmon telemetry, analysts can quickly identify suspicious applications, investigate endpoint activity, and detect potential malicious behavior.

This query demonstrates how raw XML security events can be transformed into actionable security intelligence within Splunk Enterprise.

## Skills Demonstrated

* Splunk Enterprise
* SPL Query Development
* XML Field Extraction
* Sysmon Analysis
* Endpoint Monitoring
* Security Monitoring
* Threat Hunting
* SIEM Operations

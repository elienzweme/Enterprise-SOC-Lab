# Notepad Threat Hunt

## Query

```spl
sourcetype="XmlWinEventLog:Microsoft-Windows-Sysmon/Operational"
| rex "<EventID>(?<EventID>\d+)</EventID>"
| rex "<Data Name='Image'>(?<Image>[^<]+)</Data>"
| search EventID=1 Image="*notepad.exe*"
| table _time host Image
| sort -_time
```

## Purpose

This query was used to identify instances of **Notepad.exe** execution across all monitored endpoints within the Enterprise SOC Lab environment.

By filtering Sysmon Event ID 1 (Process Creation) events, the query provides visibility into when and where Notepad was launched.

## Results

The query successfully detected Notepad execution on:

* DC01 (Windows Server 2025 Domain Controller)
* Client01 (Windows 11 Pro)
* Client02 (Windows 11 Pro)

The results confirmed that Sysmon process creation telemetry was being successfully collected, forwarded, indexed, and searched through Splunk Enterprise.

## Why It Matters

This threat hunt demonstrates the ability to:

* Perform endpoint activity monitoring
* Search and analyze Sysmon process creation events
* Validate end-to-end SIEM data ingestion
* Conduct basic threat hunting across multiple systems
* Investigate process execution activity within an enterprise environment

Although Notepad.exe is a legitimate application, the same methodology can be used to identify suspicious tools, malware, unauthorized executables, and attacker activity.

## Skills Demonstrated

* Splunk Enterprise
* Splunk SPL
* Sysmon Analysis
* Threat Hunting
* Process Investigation
* Security Monitoring
* Endpoint Detection and Response Concepts
* SIEM Operations

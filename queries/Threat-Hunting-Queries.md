# Advanced Threat Hunting Query (Process Investigation)

## Query

```spl
sourcetype="XmlWinEventLog:Microsoft-Windows-Sysmon/Operational"
| rex "<EventID>(?<EventID>\d+)</EventID>"
| rex "<Data Name='Image'>(?<Image>[^<]+)</Data>"
| rex "<Data Name='CommandLine'>(?<CommandLine>[^<]+)</Data>"
| rex "<Data Name='ParentImage'>(?<ParentImage>[^<]+)</Data>"
| search EventID=1
| table _time host Image CommandLine ParentImage
| sort -_time
```

## Purpose

This query extracts Sysmon Event ID 1 (Process Creation) events and displays:

* Executable name (Image)
* Command line arguments
* Parent process
* Host name
* Event timestamp

The query is useful for process creation investigations and endpoint threat hunting.

## Why It Matters

Process creation events provide visibility into activity occurring on monitored endpoints. Security analysts frequently review:

* Executable image names
* Parent-child process relationships
* Command-line arguments
* Execution timestamps
* Host activity

These artifacts help identify suspicious behavior, malware execution, persistence mechanisms, and unauthorized processes.

## Validation Results

The query successfully detected:

* Notepad.exe execution
* Splunk Universal Forwarder processes
* Sysmon-monitored endpoint activity
* Process creation events from Client01, Client02, and DC01

## Skills Demonstrated

* Splunk SPL
* Threat Hunting
* Sysmon Analysis
* Process Investigation
* SIEM Operations
* Security Monitoring

## Validation Results

The query successfully detected:

- Notepad.exe execution
- Splunk Universal Forwarder processes
- Sysmon-monitored endpoint activity
- Process creation events from Client01
- Process creation events from Client02
- Process creation events from DC01

The results confirmed that Sysmon Event ID 1 telemetry was successfully collected, forwarded, indexed, and searchable within Splunk Enterprise.

## Skills Demonstrated

- Splunk Enterprise
- Splunk SPL
- Sysmon Analysis
- Threat Hunting
- Process Investigation
- Security Monitoring
- Endpoint Detection
- SIEM Administration

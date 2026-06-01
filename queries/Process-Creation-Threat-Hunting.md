# Process Creation Threat Hunting

## Query

```spl id="8xw5uq"
sourcetype="XmlWinEventLog:Microsoft-Windows-Sysmon/Operational"
| rex "<EventID>(?<EventID>\d+)</EventID>"
| search EventID=1
```

## Purpose

This query was used to identify and investigate Sysmon Process Creation events across all monitored endpoints in the Enterprise SOC Lab.

By filtering for Sysmon Event ID 1, the search provides visibility into every process launched on monitored systems.

## Sysmon Event Monitored

### Event ID 1 – Process Creation

Event ID 1 records information whenever a new process is created, including:

* Executable Image
* Process ID
* Parent Process
* Command Line Arguments
* User Context
* Timestamp
* Host Information

## Investigation Use Cases

This query can be used to investigate:

* PowerShell execution
* Command Prompt activity
* Script execution
* Administrative tool usage
* Unauthorized applications
* Malware execution attempts
* Living-off-the-Land (LOLBins) techniques

## Example Processes Observed

During testing and validation, the environment generated process creation events for:

* notepad.exe
* powershell.exe
* cmd.exe
* msedge.exe
* splunkd.exe
* splunk-regmon.exe
* splunk-netmon.exe

These events were successfully collected from DC01, Client01, and Client02.

## Why It Matters

Process creation events are one of the most valuable sources of telemetry for threat hunting and incident response.

Attackers frequently execute tools such as PowerShell, Command Prompt, Windows Script Host, and other native binaries to perform malicious actions. Monitoring Event ID 1 activity allows security analysts to detect suspicious execution patterns, investigate endpoint activity, and identify potential compromises.

This query served as a foundational threat-hunting search throughout the Enterprise SOC Lab project.

## Skills Demonstrated

* Threat Hunting
* Splunk SPL
* Sysmon Analysis
* Process Monitoring
* Endpoint Visibility
* Security Operations
* SIEM Administration
* Incident Investigation

# Full Notepad Process Investigation

## Query

```spl id="7b7vnn"
sourcetype="XmlWinEventLog:Microsoft-Windows-Sysmon/Operational"
| rex "<EventID>(?<EventID>\d+)</EventID>"
| rex "<Data Name='Image'>(?<Image>[^<]+)</Data>"
| rex "<Data Name='CommandLine'>(?<CommandLine>[^<]+)</Data>"
| rex "<Data Name='ParentImage'>(?<ParentImage>[^<]+)</Data>"
| search EventID=1 Image="*notepad.exe*"
| table _time host Image CommandLine ParentImage
| sort -_time
```

## Purpose

This query performed a deeper investigation into Notepad.exe execution by extracting additional process metadata from Sysmon Event ID 1 records.

The investigation expanded beyond simple detection and provided context needed for process analysis and threat hunting.

## Data Extracted

The query extracted:

* Timestamp
* Host Name
* Executable Image
* Command Line Arguments
* Parent Process

## Example Findings

### Process Executed

```text id="pl8sdb"
notepad.exe
```

### Parent Process

```text id="tny3zf"
explorer.exe
```

### Monitored Systems

* DC01 (Windows Server 2025)
* Client01 (Windows 11 Pro)
* Client02 (Windows 11 Pro)

## Investigation Workflow

The investigation followed a standard SOC analyst methodology:

1. Detect process creation activity.
2. Identify the executable launched.
3. Review command-line arguments.
4. Determine the parent process responsible for execution.
5. Correlate activity across multiple endpoints.
6. Assess whether execution is legitimate or suspicious.

## Why It Matters

This workflow mirrors how Security Operations Center (SOC) analysts investigate suspicious process activity in enterprise environments.

By examining parent-child process relationships and command-line arguments, analysts can identify:

* Malware execution
* Living-off-the-land techniques
* Suspicious scripting activity
* Unauthorized applications
* Persistence mechanisms
* Potential attacker behavior

Although Notepad.exe was used as a safe test application, the same methodology can be applied to investigate potentially malicious executables.

## Skills Demonstrated

* Splunk Enterprise
* Sysmon Event Analysis
* Process Investigation
* Parent-Child Process Analysis
* Threat Hunting
* Endpoint Monitoring
* Security Operations
* SIEM Administration

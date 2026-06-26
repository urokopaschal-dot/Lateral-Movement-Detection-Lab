# Lateral Movement Detection Lab

## Project Overview

This project demonstrates how a Security Operations Center (SOC) analyst can investigate Windows authentication events that may indicate lateral movement. Using Splunk and Windows Security logs, the lab analyzes successful and failed logon events, identifies logon types, and builds a timeline of authentication activity.

---

# Lab Environment

- Windows 10 Virtual Machine
- Splunk Enterprise
- Windows Security Event Logs
- Sysmon
- PowerShell

---

# Objective

The objective of this lab was to:

- Generate Windows authentication events.
- Detect successful and failed logons.
- Investigate logon types.
- Build an authentication timeline.
- Map findings to the MITRE ATT&CK framework.
- Document the investigation.

---

# Attack Simulation

The simulation consisted of:

- Locking the workstation.
- Performing multiple failed login attempts.
- Logging in successfully.
- Collecting Windows Security Event Logs.
- Investigating authentication activity in Splunk.

---

# Detection

## Successful Logons

```spl
index=wineventlog EventCode=4624
| table _time Account_Name Logon_Type Workstation_Name host
| sort -_time
```

## Failed Logons

```spl
index=wineventlog EventCode=4625
| table _time Account_Name Failure_Reason Workstation_Name host
| sort -_time
```

## Logon Type Analysis

```spl
index=wineventlog EventCode=4624
| stats count by Logon_Type
```

## Authentication Timeline

```spl
index=wineventlog (EventCode=4624 OR EventCode=4625)
| table _time EventCode Account_Name Logon_Type host
| sort _time
```

---

# Investigation Findings

The investigation identified both successful and failed authentication attempts. Windows Security logs recorded Event ID 4624 for successful logons and Event ID 4625 for failed logons. Splunk queries were used to analyze authentication activity, review logon types, and build a timeline of events.

This activity demonstrates how authentication logs can be used to investigate suspicious login behavior and potential lateral movement.

---

# MITRE ATT&CK Mapping

| Tactic | Technique | Technique ID |
|---------|-----------|--------------|
| Lateral Movement | Remote Services | T1021 |

---

# Skills Demonstrated

- Splunk Log Analysis
- Windows Event Log Investigation
- Authentication Analysis
- Timeline Analysis
- Threat Hunting
- MITRE ATT&CK Mapping
- Incident Investigation
- SOC Analyst Workflow

---

# Project Structure

```text
Lateral-Movement-Detection-Lab
├── README.md
├── Screenshots
├── Queries
├── Reports
└── MITRE
```

---

# Screenshots

Include:

- Successful Logons
- Failed Logons
- Logon Type Analysis
- Authentication Timeline
- Event Investigation

---

# Lessons Learned

This lab demonstrated how Windows authentication events can be investigated to identify suspicious login activity. Monitoring successful and failed logons, understanding logon types, and building authentication timelines are essential skills for SOC analysts investigating potential lateral movement.

---

# Conclusion

This project demonstrated the investigation of authentication activity using Splunk and Windows Security logs. By analyzing successful and failed logons, reviewing logon types, and constructing a timeline, the lab reflects a practical SOC workflow for investigating potential lateral movement.

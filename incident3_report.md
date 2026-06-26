# Incident Report

## Executive Summary

Authentication events were generated in a controlled lab environment to simulate login activity and investigate potential indicators of lateral movement.

---

## Detection

Splunk detected successful (Event ID 4624) and failed (Event ID 4625) logon events recorded in the Windows Security log.

---

## Investigation

The investigation included:

- Successful authentication review
- Failed authentication review
- Logon type analysis
- Timeline construction
- User account verification

The activity was confirmed to be a controlled simulation performed for security monitoring and detection practice.

---

## MITRE ATT&CK

T1021 – Remote Services

---

## Conclusion

Windows authentication logs successfully recorded the simulated login activity. Splunk queries enabled efficient investigation and timeline analysis, demonstrating a practical SOC workflow for monitoring authentication events.
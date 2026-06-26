# Splunk Queries

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

## Timeline

```spl
index=wineventlog (EventCode=4624 OR EventCode=4625)
| table _time EventCode Account_Name Logon_Type host
| sort _time
```
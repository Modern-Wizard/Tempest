# Tempest
Conducted an investigation from a workstation affected by a full attack chain.

## 1.Introduction
This project aims to introduce the process of analysing endpoint and network logs from a compromised asset. Given the artefacts, it will aim to uncover the incident from the Tempest machine. In this scenario, we will focus on handling and analysing the captured artefacts of a compromised machine.

## 2.Preparation - Log Analysis
### Log Analysis
Log analysis is the process of understanding events generated by a computer to identify anomalies such as security threats, application bugs, system performance, or other risks that may impact the organisation. 

A log file is an audit trail of events or activities within the applications and systems of an organisation. Logs automatically audit any activity configured, such as system messages, authentication attempts, and network traffic generated. In addition, every log entry is audited with a timestamp of when the event occurred, which deeply aids in an investigation.

### Event Correlation
Event correlation identifies significant relationships from multiple log sources, such as application logs, endpoint logs, and network logs.

Event correlation deals with identifying significant artefacts co-existing from different log sources and connecting each related artefact. For example, a network connection log may exist in various log sources, such as Sysmon logs (Event ID 3: Network Connection) and Firewall logs. Firewall logs may provide the source and destination IP, source and destination port, protocol, and the action taken. In contrast, Sysmon logs may give the process that invoked the network connection and the user running the process.

With this information, we can connect the dots of each artefact from the two data sources:

    Source and Destination IP
    Source and Destination Port
    Action Taken
    Protocol
    Process name
    User Account
    Machine Name

Event correlation can build the puzzle pieces to complete the exact scenario from an investigation.

## 3.Preparation - Tools and Artifacts
In this task, we will prepare the artefacts and introduce the tools needed for the investigation.

### Compare by hash
Before conducting the investigation, one of the most important steps is to compare the artefacts by their hashes. It is a common practice to verify if the artefacts are expected as it is. 

<div>
<img src="https://github.com/Modern-Wizard/Tempest/blob/main/ss1.png" />
</div>

You can get the hashes of each artefact by running Powershell from the taskbar.

### Toolset
The toolset needed for this task is focused on analysing Sysmon Logs, Windows Event Logs, and Packet Capture.

### Endpoint Logs
To analyse Windows artefacts such as Windows Event Logs and Sysmon logs, we will use the following tools:

    EvtxEcmd
    Timeline Explorer
    SysmonView
    Event Viewer

### Network Logs
To analyse the provided packet capture, we will use the following tools:

    Wireshark
    Brim

### EvtxEcmd & Timeline Explorer
Eric Zimmerman has created a set of forensic tools used to analyse Windows artefacts called EZTools (Eric Zimmerman's Tools). For this task, we will focus on EvtxEcmd and Timeline Explorer, as these tools are mainly used for parsing and analysing Evtx logs.

﻿EvtxEcmd is a command-line tool which parses Windows Event Logs into different formats such as CSV, JSON, XML, etc. You may use this tool in conjunction with Timeline Explorer, created by the same author. Timeline Explorer is a GUI-based tool that functions as a data filtering and navigating application to ease incident responders in handling raw data.

To parse the provided logs, we need first to convert the EVTX logs into CSV using EvtxEcmd and then feed it into Timeline Explorer.






# Windows Event Log Analysis with EvtxECmd

## Project Overview
This project demonstrates practical Windows Event Log analysis using **EvtxECmd**,
a DFIR command-line tool developed by Eric Zimmerman.

The focus is on offline parsing of `.evtx` files, structured output generation,
and preparation of logs for forensic investigation and SOC-level analysis.

Video reference:
https://www.youtube.com/watch?v=iy3Ljoi-BVA

---

## Summary
EvtxECmd is a core DFIR tool for Windows Event Log analysis.
This project highlights practical usage aligned with SOC Analyst
and Digital Forensics roles, emphasizing clarity, scalability,
and forensic soundness.

---

## Objectives
- Parse Windows Event Logs outside the source system
- Convert EVTX files into structured, analyzable formats
- Enable scalable log analysis for SOC and DFIR workflows
- Demonstrate hands-on familiarity with industry-standard DFIR tooling

---

## Tool Used
**EvtxECmd**
- Author: Eric Zimmerman
- Purpose: Windows Event Log parsing
- Output formats: CSV, JSON, XML
- Use cases: Forensics, Incident Response, Threat Hunting

---

## Data Source
Windows Event Log files (.evtx) collected from a Windows system.

Default log location:

    C:\Windows\System32\winevt\Logs

---

## Installation
1. Download EvtxECmd from:
   https://ericzimmerman.github.io/
2. Extract EvtxECmd.exe to a working directory

---

## Methodology

### Step 1 – Single Log Parsing
Convert a single EVTX file to CSV format:

    EvtxECmd.exe -f Security.evtx --csv output --csvf security.csv

### Step 2 – Bulk Log Parsing
Parse all EVTX files in a directory:

    EvtxECmd.exe -d logs --csv output --csvf all_logs.csv

### Step 3 – Structured Output
The generated CSV files are ready for:
- Timeline creation
- Event correlation
- Further ingestion into SIEM or forensic tools

---

## EvtxECmd Command Cheat Sheet

Show help:

    EvtxECmd.exe -h

Parse single EVTX file:

    EvtxECmd.exe -f <file.evtx> --csv <output_path> --csvf output.csv

Parse directory of EVTX files:

    EvtxECmd.exe -d <evtx_directory> --csv <output_path> --csvf output.csv

Overwrite existing output:

    EvtxECmd.exe -f <file.evtx> --csv <output_path> --csvf output.csv --overwrite

Export to JSON:

    EvtxECmd.exe -f <file.evtx> --json <output_path>

Export to XML:

    EvtxECmd.exe -f <file.evtx> --xml <output_path>

Include specific Event IDs:

    EvtxECmd.exe -f <file.evtx> --csv <output_path> --inc 4624,4625,4688

Exclude specific Event IDs:

    EvtxECmd.exe -f <file.evtx> --csv <output_path> --exc 4624,4625

Use mapping files:

    EvtxECmd.exe -f <file.evtx> --csv <output_path> --maps

---

## Outcome
This project demonstrates the ability to:
- Work with raw Windows forensic artifacts
- Use DFIR tooling in a structured workflow
- Prepare log data for SOC analysis and investigation
- Apply practical, hands-on skills relevant to blue team operations

---

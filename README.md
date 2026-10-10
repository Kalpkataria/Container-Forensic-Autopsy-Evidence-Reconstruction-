#CLOUD CONTAINER SECURITY & FORENSICS

**Developing a cloud-native container forensics system to capture ephemeral artifacts, container metadata, and process activity.
A Docker container forensics framework** designed to capture and preserve volatile forensic evidence from compromised containers before they are terminated or deleted.

The project collects container-level artifacts, correlates them across processes, files, and network activity, and reconstructs an **attack timeline** to support container-based incident investigation.

---

## Problem Statement

Containers are designed to be **ephemeral**. When a compromised container is stopped or deleted, valuable forensic evidence such as running processes, temporary files, network connections, and executed commands can disappear.

```text
Container Created
       ↓
Malicious Activity
       ↓
Evidence Generated
       ↓
Container Terminated
       ↓
Evidence Lost
```

This project addresses the problem by collecting and preserving relevant forensic artifacts **before the evidence disappears**.

---

## Project Objective

The primary objective is to provide investigators with a structured way to:

- Capture volatile container evidence
- Preserve forensic artifacts
- Identify suspicious container activity
- Correlate artifacts from multiple sources
- Reconstruct attack timelines
- Support incident investigation and analysis

---

## Key Features

### Container Metadata Collection

Collects information such as:

- Container ID
- Container name
- Image name
- Image hash
- Creation and execution timestamps
- Container status
- Network configuration

### Process Analysis

Captures running processes inside the container to identify:

- Suspicious processes
- Unexpected commands
- Malicious scripts
- Unusual process execution

### Network Forensics

Collects and analyzes:

- Active network connections
- Source and destination addresses
- Open ports
- Network-related container activity

This helps identify suspicious or unauthorized network communication.

### File-System Analysis

Tracks relevant file-system activity such as:

- Newly created files
- Modified files
- Deleted files
- Suspicious executable or script files

### Command & Environment Analysis

Collects:

- Executed commands
- Environment variables
- Container configuration
- Relevant Docker API activity

### Evidence Correlation

The framework correlates artifacts using the following investigation model:

```text
IMAGE
  ↓
CONTAINER
  ↓
PROCESS
  ↓
FILE
  ↓
NETWORK
  ↓
ATTACK
```

This correlation helps investigators understand how an incident occurred.

---

## Attack Reconstruction Example

A simulated compromised container may perform:

```text
Container Started
       ↓
Suspicious Command Executed
       ↓
Malicious File Downloaded
       ↓
Malware Process Started
       ↓
External Network Connection
       ↓
Container Deleted
```

The framework attempts to preserve the relevant artifacts and reconstruct the incident:

```text
Image
 ↓
Container
 ↓
Command
 ↓
Process
 ↓
File
 ↓
Network Connection
 ↓
Attack Timeline
```

---

## System Architecture

```text
              Docker Host
                   │
                   ↓
          Container Environment
                   │
        ┌──────────┼──────────┐
        ↓          ↓          ↓
     Processes   Files     Network
        │          │          │
        └──────────┼──────────┘
                   ↓
           Forensic Collector
                   ↓
          Evidence Storage
                   ↓
          Artifact Correlation
                   ↓
          Timeline Reconstruction
                   ↓
          Forensic Dashboard
```

---

## Technology Stack

| Category | Technologies |
|---|---|
| Programming | Python |
| Containerization | Docker |
| Operating System | Linux |
| Database | SQLite |
| Container Interface | Docker API |
| Security | Digital Forensics, Network Forensics |
| Investigation | Incident Response, Artifact Correlation |

---

## Project Structure

```text
container-forensic-autopsy/
│
├── collector/
│   ├── container.py
│   ├── process.py
│   ├── network.py
│   ├── filesystem.py
│   └── docker_api.py
│
├── analysis/
│   ├── correlation.py
│   ├── timeline.py
│   └── risk_analysis.py
│
├── dashboard/
│   └── app.py
│
├── evidence/
│   └── README.md
│
├── database/
│   └── schema.sql
│
├── tests/
│
├── requirements.txt
├── README.md
└── LICENSE
```

*The structure can be adjusted according to the final implementation.*

---

## Investigation Workflow

```text
1. Detect Container
       ↓
2. Collect Evidence
       ↓
3. Preserve Artifacts
       ↓
4. Analyze Processes
       ↓
5. Analyze Files
       ↓
6. Analyze Network Activity
       ↓
7. Correlate Artifacts
       ↓
8. Build Timeline
       ↓
9. Identify Suspicious Activity
       ↓
10. Generate Investigation Report
```

---

## Example Forensic Evidence

The system can produce structured evidence such as:

```text
Container ID: abc123
Image: web-app
Image Hash: sha256:xxxx

Process:
PID: 421
Command: suspicious.sh

File:
Path: /tmp/suspicious.sh
Action: CREATED

Network:
Source: 172.17.0.2
Destination: x.x.x.x
Port: 443

Risk: HIGH
```

---

## Forensic Timeline

Example reconstructed timeline:

```text
10:21:03  Container started
10:21:15  Suspicious command executed
10:21:18  File created
10:21:22  Suspicious process started
10:21:31  External network connection detected
10:22:04  Container terminated
```

This allows an investigator to understand **what happened, when it happened, and which artifacts are related**.

---

## Security Use Cases

The framework can assist with investigations involving:

- Compromised Docker containers
- Malware execution
- Unauthorized network connections
- Suspicious process execution
- Container-based attacks
- File manipulation
- Incident response
- Container security investigations

---

## Future Enhancements

Planned improvements include:

- Automated malware/hash analysis
- MITRE ATT&CK technique mapping
- YARA-based file analysis
- Elasticsearch integration
- Advanced forensic timeline visualization
- Container lineage tracking
- Automated incident reports
- SIEM integration
- Kubernetes container forensics

---

## Disclaimer

This project is developed for **educational, research, and authorized security investigation purposes**. Testing should only be performed on systems and containers for which you have permission.

---

## Author

**Kalp Kataria**

M.Sc. Digital Forensics & Information Security  
Cybersecurity | Digital Forensics | Cloud Security

---

## Project Status

**Status:** Ongoing

The project is currently under development, with additional forensic collection, artifact correlation, and investigation capabilities planned.

# ElevateLabs Task 1 – Local Network Port Scanning

## Objective

To identify active devices on a local network and scan the discovered hosts for open TCP ports and service information using Nmap.

## Environment

- Operating System: Kali Linux
- Platform: VirtualBox
- Tool: Nmap 7.99
- Network: 10.0.2.0/24
- Kali IP: 10.0.2.15
- Gateway: 10.0.2.2

## Method

First, Nmap host discovery was performed on the local network using:

`sudo nmap -sn 10.0.2.0/24`

Two other active hosts were identified:

- 10.0.2.2
- 10.0.2.3

A service and version scan was then performed against these hosts using:

`sudo nmap -sV 10.0.2.2 10.0.2.3`

## Findings

Nmap identified four open TCP ports on 10.0.2.2:

- 135/tcp – Microsoft Windows RPC
- 445/tcp – Microsoft-DS
- 5357/tcp – HTTP / Microsoft HTTPAPI 2.0
- 16992/tcp – HTTP / Intel Active Management Technology

For 10.0.2.3, the 1,000 TCP ports scanned were reported as filtered, with no open ports identified.

The complete Nmap output is available in `nmap-scan.txt`.

## Note

Service identification is based on Nmap's scan results and may require further verification.

## Evidence

Screenshots and the final lab report will be added to this repository.


## Service Research, Risks, and Recommended Actions

The scan identified four open TCP ports on host `10.0.2.2`. An open port indicates that a network service is listening and reachable from the scanning environment; it does **not, by itself, confirm a security vulnerability**.

| Port          | Service           | Potential Risk                                                                                                                            | Recommended Action                                                                                                                      |
| ------------- | ----------------- | ----------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------- |
| **135/tcp**   | Microsoft RPC     | May increase the attack surface by exposing RPC functionality.                                                                            | Restrict RPC access with firewall rules to trusted systems where possible.                                                              |
| **445/tcp**   | Microsoft-DS/SMB  | May expose file-sharing services to unauthorized access, misconfigured shares, weak authentication, or SMB-related vulnerabilities.       | Restrict SMB access to trusted systems, review shared resources and authentication controls, and keep Windows security updates current. |
| **5357/tcp**  | Microsoft HTTPAPI | May provide unnecessary network exposure if the associated service is not required.                                                       | Verify whether the service is required and restrict or disable it when operationally appropriate.                                       |
| **16992/tcp** | Intel AMT         | Remote-management functionality may introduce additional risk if improperly configured or exposed beyond the intended management network. | Restrict Intel AMT access to authorized management systems/networks and verify that AMT is properly configured and updated.             |

### Assessment

These are **potential security risks, not confirmed vulnerabilities**. Confirming a specific vulnerability would require additional authorized testing, configuration review, and vulnerability assessment.

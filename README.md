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

# Cowrie Honeypot Lab

## Overview
This Project demonstrates the deployment of an SSH honeypot using Cowrie to capture and analyze attacker behavior. The honeypot simulates a vulnerable system and records all interactions for security analysis.

## Architecture
Arracker(SSH)->Port 2222(Docker)->Cowrie Honeypot (Fake SSH Server)->Capture Logs(Commands, Sessions)->Analysis & Insights

## Setup & Configuration
### install Docker
sudo apt update
sudo apt install docker.io -y

### Ran Cowrie container
sudo docker run -d -p 2222:2222 --name cowrie cowrie/cowrie

### Verify Container
sudo docker ps

## Attack Simulation
### Simulated attacker access using SSH
ssh root@localhost -p 2222

## logs
sudo docker logs cowrie > cowrie_logs.txt

## Screenshots
### Cowrie logs
![Cowrie Logs](screenshots/cowrie_logs.png)

## Log Analysis

Captured attacker session revealed:

- successful login attempt using username `root`
- Attacker performed basic reconnaissance:
	- `ls` -> listed files
	- `pwd` -> checked working directory
	- `whoami` -> confirmed user identity
- Session lasted ~5 min before disconnection

### Insights
This behavior indicates a typical early-stage attack where the attacker explores the system after gaining access.

## Key Learnings
. Honeypots can capture real attacker behavior
. Attackers typically begin with system reconnaissance
. Logs provide valuable forensic and detection data
. Containerization simplifies deployment of security tools

## Skills Demonstraated
. Linux Administration
. Docker & Containerization
. SSH Protocol Understanding
. Log Analysis
. Cybersecurity Fundamentals

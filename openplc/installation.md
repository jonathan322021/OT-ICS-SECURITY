
## Asset Information

Hostname: openplc

IP: 192.168.20.10

Zone: OT

Purdue Level: 1

## Purpose

Industrial Controller (PLC)

## Installation Steps

1. Installed Ubuntu Server
2. Assigned static IP
3. Installed OpenPLC
4. Verified Web Interface

## IEC 62443 Mapping

- Asset Identification
- Zones
- Conduits
- Restricted Data Flow
## Installation Issue #001

OpenPLC installation failed due to CMake compatibility requirements.

### Error

Compatibility with CMake < 3.5 has been removed.

### Actions

- Verified network connectivity
- Updated Ubuntu packages
- Investigating OpenPLC build requirements

### Lessons Learned

Industrial software often has dependency constraints and may require specific operating system versions.

## Status
4
 
5
In Progress
6
 
7
## Issue Encountered
8
 
9
OpenPLC installation failed on Ubuntu 26.04.1 LTS.
10
 
11
### Error
12
 
13
Compatibility with CMake < 3.5 has been removed.
14
 
15
### Root Cause
16
 
17
OpenPLC v3 build scripts are not fully compatible with CMake 4.2.3.
18
 
19
### Resolution
20
 
21
Deploy OpenPLC using Ubuntu 22.04 LTS.

## Installation Issue #002

OpenPLC webserver failed to start due to Python dependency conflicts.

Error:

ImportError: cannot import name 'Markup' from 'jinja2'

Root Cause:

Version incompatibility between Flask, Jinja2 and MarkupSafe.

Resolution:

Create dedicated Python virtual environment and install compatible package versions.

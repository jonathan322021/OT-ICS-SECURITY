
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

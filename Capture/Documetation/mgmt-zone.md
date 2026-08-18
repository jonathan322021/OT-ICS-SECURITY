# Management Zone

## Purpose

Provide secure administration access to OT assets.

## Components

- pfSense OPT2
- Ubuntu Jump Server

## Addressing

MGMT Network:
192.168.30.0/24

pfSense:
192.168.30.1

Jump Server:
192.168.30.10

## Validation

- Jump Server can ping pfSense.
- pfSense can ping Jump Server.

## IEC 62443 Concepts

- Zones
- Conduits
- Restricted Data Flow
- Defense in Depth
- Secure Remote Access

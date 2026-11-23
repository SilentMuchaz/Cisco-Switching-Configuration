# Cisco Switching Configuration — Technical Case Study

## Project objective

Design and document a multi-switch Cisco Packet Tracer lab demonstrating VLAN segmentation, EtherChannel link aggregation, centralized VLAN management through VTP, trunking, and access-port security.

## Network environment

- **Platform:** Cisco Packet Tracer.
- **Documented devices:** SW1 through SW8 (eight switches).
- **VTP roles:** SW1 server; SW2–SW8 clients.
- **VTP settings:** Version 2; domain `cisco.com`.
- **Departmental VLANs:** VLAN 10 (HR), VLAN 20 (ICT), VLAN 30 (FIN).
- **Link aggregation:** LACP and PAgP EtherChannel, with trunking on port-channels.

### Network topology

![Network topology](https://imgur.com/fK2paHG.png)

## Implementation and technical evidence

### 1. VLAN segmentation and VTP

Created departmental VLAN definitions on SW1 and documented VTP client distribution across the remaining switches. The intended design separates HR, ICT, and Finance into distinct Layer 2 broadcast domains.

![VTP settings](https://imgur.com/707RfWQ.png)

![Departmental VLANs](https://imgur.com/5azKhkG.png)

### 2. EtherChannel and trunking

The configuration notes describe multiple aggregated inter-switch links using LACP and PAgP. Port-channels are described as trunks for carrying VLAN traffic between switches.

![EtherChannel settings](https://imgur.com/euR9JNH.png)

![Trunking settings](https://imgur.com/1SMLSet.png)

### 3. Port security

Configured the access-layer security policy described in the project notes:

- Maximum **two** learned MAC addresses per secured port.
- **Sticky** MAC address learning.
- **Shutdown** on a port-security violation.

![Port security](https://imgur.com/ONDg5EO.png)

### 4. VLAN pruning

The notes describe a VLAN 20 restriction on Port-Channel 1, configured from SW1. The intended purpose is to limit unnecessary VLAN traffic across selected links. Pruning should not be described as complete VLAN isolation without confirming the forwarding state and test results.

## Testing and documented results

| Area | Check recorded in project notes | Status of available evidence |
|---|---|---|
| EtherChannel | `show etherchannel` | Verification command documented; no exported output in archive |
| VTP | `show vtp status` | Verification command documented; screenshot link provided |
| VLAN distribution | `show vlan` | VLAN definitions documented; screenshot link provided |
| Port security | `show port-security` | Security settings documented; screenshot link provided |
| Connectivity | Intra-VLAN ping and cross-VLAN separation | Results described in notes; no raw ping transcript included |
| VLAN 20 traffic | Pruning / restricted traffic across selected links | Requires direct confirmation in the simulation |

The documentation reports successful communication between hosts in the same VLAN and lack of communication between hosts in different VLANs. These are **reported lab results**, not independently reproduced tests.

## Configuration validation notes

The written project material contains a few inconsistencies that should be resolved by opening the included `.pkt` file:

1. The introduction says **four switches**, while the device list identifies **SW1–SW8**. This case study follows the device list.
2. Two link entries say **`LAGP`**; Cisco EtherChannel negotiation protocols are **LACP** and **PAgP**. The intended protocol for those links needs confirmation.
3. Some physical interface ranges are repeated across different connections in the connection table, so the port-to-port mapping should be checked against the actual topology.
4. A table labels an IPv4 address range as a *port range*; address assignments and switch interface assignments should be documented separately.
5. VTP pruning and a blocked VLAN on a trunk can have different effects. The final allowed/forwarding VLAN state should be checked directly.

These are documentation-validation items, not claims that the Packet Tracer configuration is broken.

## Outcome

The project brings together Cisco switching fundamentals and Layer 2 security in one simulated network. The documented work covers VLAN design, VTP roles, aggregated trunk links, access-port security, and a set of verification checks. The `.pkt` file allows the configuration and traffic behavior to be examined directly.

## Supporting project file

- [Screenshot index](evidence/README.md)

**Environment note:** The project notes use shared lab passwords. These are not suitable production security settings.

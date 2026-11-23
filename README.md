# Cisco Switching Configuration — VLANs, EtherChannel & Port Security

Designed and configured a multi-switch network in **Cisco Packet Tracer** to practice Layer 2 segmentation, link aggregation, VLAN administration, trunking, and access-port security. The documented topology identifies **eight switches (SW1–SW8)**, with SW1 serving as the VTP server and the remaining switches configured as clients.

## Configuration highlights

| Technology | Implementation documented |
|---|---|
| **VLANs** | VLAN 10 (HR), VLAN 20 (ICT), and VLAN 30 (FIN) |
| **VTP** | Version 2, domain `cisco.com`; SW1 server, SW2–SW8 clients |
| **EtherChannel** | Inter-switch link aggregation using LACP and PAgP |
| **Trunking** | Port-channel trunk links to carry VLAN traffic |
| **Port security** | Sticky MAC learning, maximum two MAC addresses, shutdown on violation |
| **VLAN traffic control** | VLAN 20 pruning/restriction documented for Port-Channel 1 |

## Configuration evidence

### Network topology

Built the switching topology in Packet Tracer with inter-switch connections and end devices representing the departmental VLANs.

![Cisco Packet Tracer multi-switch topology](https://i.imgur.com/fK2paHG.png)

*Figure 1 — Multi-switch Packet Tracer topology.*

### EtherChannel configuration

Configured aggregated links between switches using **LACP and PAgP**, with port-channels intended to carry trunk traffic. The configuration screenshot documents the link-aggregation work; operational status should be checked with `show etherchannel summary` in the `.pkt` simulation.

![Cisco EtherChannel configuration](https://i.imgur.com/euR9JNH.png)

*Figure 2 — EtherChannel configuration in the switching lab.*

### VTP and departmental VLANs

Configured **VTP version 2** and created departmental VLAN definitions for HR, ICT, and Finance. The screenshots document the VTP and VLAN configuration work.

![Cisco VTP configuration](https://i.imgur.com/707RfWQ.png)

*Figure 3 — VTP configuration.*

![Cisco departmental VLAN configuration](https://i.imgur.com/5azKhkG.png)

*Figure 4 — Departmental VLAN definitions.*

### Access-port security

Applied a port-security policy using **sticky MAC learning**, a **two-address maximum**, and **shutdown** on a violation.

![Cisco switch port-security configuration](https://i.imgur.com/ONDg5EO.png)

*Figure 5 — Access-port security configuration.*

A separate [trunking configuration screenshot](https://i.imgur.com/1SMLSet.png) documents the trunk setup.

## Testing and observations

The project notes describe checking EtherChannel, VTP, VLAN propagation, port security, and host connectivity. They report successful communication between hosts in the same VLAN and lack of communication between hosts in different VLANs in the tested design.

| Area | Verification command or check | Evidence status |
|---|---|---|
| EtherChannel | `show etherchannel summary` | Configuration screenshot available; exported operational output not included |
| VTP | `show vtp status` | VTP screenshot available |
| VLANs | `show vlan brief` | VLAN screenshot available |
| Port security | `show port-security` | Configuration screenshot available |
| Connectivity | Intra-VLAN and cross-VLAN ping tests | Results described in project notes; raw ping output not included |

**Validation note:** The written notes contain inconsistent switch counts and two `LAGP` protocol labels. The device list identifies SW1–SW8; the two protocol labels and specific interface assignments should be confirmed directly in Packet Tracer. VLAN pruning alone should not be treated as proof of complete traffic isolation.

## Project outcome

This project documents hands-on configuration of a **segmented Cisco switching environment**, combining departmental VLANs, VTP, EtherChannel, trunking, and access-port security. The Packet Tracer file is included for inspecting the configurations and repeating the validation checks.

## Project files

- [Cisco Packet Tracer simulation](Cisco%20Switching%20Networking.pkt)
- [Technical case study — Markdown](Cisco-Switching-Case-Study.md)
- [Technical case study — PDF](reports/01-cisco-switching-case-study.pdf)

*The screenshots are hosted externally. The original image files were not included in the uploaded repository archive.*

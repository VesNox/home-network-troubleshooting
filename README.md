# home-network-troubleshooting
Hands on home network troubleshooting project documenting connectivity issues, latency and packet loss analysis, diagnostic testing, and practical mitigation strategies.
## Project Overview

This project documents a hands-on investigation into intermittent connectivity, high latency, packet loss, and wireless connection failures within a residential network using Spectrum internet equipment.

The objective was to identify where connectivity problems occurred, compare network performance across devices, test potential solutions, and implement a practical mitigation while preserving accurate evidence of unresolved issues.

## Network Environment

| Component              | Equipment / Role                                         |
| ---------------------- | -------------------------------------------------------- |
| Internet service       | Spectrum 2 Gig                                           |
| Primary router         | Spectrum CBE1V1K                                         |
| Wireless extender      | Spectrum Wi-Fi 7 extender                                |
| Affected device        | LG webOS Smart TV (50UN6950ZUF)                          |
| Diagnostic workstation | Lenovo Windows laptop                                    |
| Diagnostic tools       | Windows PowerShell, ping, network settings, Spectrum app |

## Problem Description

The LG Smart TV experienced severe latency and intermittent packet loss while connected to the home wireless network. The device later failed to establish a Wi-Fi connection to the Spectrum access point.

The TV successfully connected to a separate mobile hotspot, indicating that its wireless functionality was not universally unavailable. Other local network clients also showed substantially better latency and packet-loss results.

## Troubleshooting Methodology

1. Identified the network equipment and affected endpoints.
2. Used Windows PowerShell to run ICMP echo tests against local network devices.
3. Compared latency, packet loss, and connectivity across the router, extender, TV, and other clients.
4. Tested a temporary 2.4 GHz wireless setup.
5. Relocated the wireless extender to evaluate whether placement improved connectivity.
6. Tested the TV using a separate mobile hotspot.
7. Connected the TV by Ethernet to the wireless extender as a practical workaround.
8. Verified that the TV reported an active internet connection and observed improved local ping responses.

## Diagnostic Results

| Test target / condition     | Packets sent | Packets lost | Average latency | Maximum latency |
| --------------------------- | -----------: | -----------: | --------------: | --------------: |
| Extender near router        |        5,740 |    5 (0.09%) |            6 ms |          175 ms |
| LG TV over Wi-Fi            |        2,185 |    50 (2.3%) |        1,346 ms |        3,995 ms |
| Extender relocated upstairs |          593 |    1 (0.17%) |           16 ms |          144 ms |

The TV exhibited substantially worse latency and packet loss than the extender. Moving the extender did not restore the TV's ability to join the Spectrum Wi-Fi network.

Other tested 2.4 GHz clients generally showed low packet loss and average latency around 15–17 ms, suggesting that the problem was not a complete failure of all 2.4 GHz connectivity.

## Mitigation Implemented

An Ethernet cable was connected between the LG Smart TV and a LAN port on the Spectrum wireless extender.

The extender retained its wireless connection to the main router, while the TV used Ethernet for its final network connection.

Following this change:

* The TV reported that it was connected to the internet.
* The TV obtained a new local network address through DHCP.
* Subsequent local ping responses were typically in the single-digit to low-double-digit millisecond range, with observed responses around 3–16 ms and occasional higher values.
* The TV's functional network connectivity was restored through the wired-to-extender arrangement.

This was a successful operational mitigation, not proof that the original Wi-Fi association issue was permanently resolved.

## Findings and Limitations

The evidence identified a device-specific connectivity problem involving the TV's connection to the Spectrum wireless network. Possible contributors include wireless compatibility, access-point configuration, or device-side connection behavior, but the available testing did not establish a definitive root cause.

Separately, Spectrum identified instability involving the modem's signal or physical connection. This issue required provider-side follow-up and should not be assumed to explain the TV's wireless association failure without additional evidence.

ICMP ping results measure reachability and response times during the test period. They do not independently establish the cause of wireless failures or guarantee long-term stability.

## Skills Demonstrated

* Network troubleshooting and fault isolation
* ICMP diagnostics and latency analysis
* Packet-loss measurement and comparison
* Wireless networking and extender placement testing
* Ethernet connectivity and DHCP verification
* Technical documentation and evidence-based conclusions
* Distinguishing mitigation from root-cause resolution

## Next Steps

* Review results of Spectrum's physical-line and modem diagnostics.
* Monitor the TV's connectivity through the Ethernet-to-extender setup.
* Investigate wireless security, compatibility, and access-point settings if supported by the equipment or provider.
* Add appropriately redacted screenshots of diagnostic commands and results.
* Update the project when further testing confirms or rules out potential causes.

## Project Status

**Functional connectivity restored through mitigation. Original Wi-Fi root cause remains unconfirmed.**

---

*Documented by Vesperyn Noctyre | VesNox*

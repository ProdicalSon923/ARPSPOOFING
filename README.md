# Kali Linux & Windows ARP Spoofing (MITM) Lab

This repository documents a hands-on cybersecurity lab where a Kali Linux virtual machine and a Windows virtual machine were configured on the same network using VMware. The purpose of this lab was to understand basic networking concepts, how ARP works, and how ARP spoofing can be used to perform a man-in-the-middle (MITM) attack in a controlled environment.

---

## Lab Setup

- Host System: Windows
- Virtualization Software: VMware Workstation
- Attacker Machine: Kali Linux
- Victim Machine: Windows 10
- Network Type: NAT (VMnet8)

Both virtual machines were configured to be on the same subnet and verified using IP addressing and connectivity tests.

---

## Network Verification

The following checks were performed to confirm proper communication between the VMs:
- IP addresses were verified using `ip a` on Kali and `ipconfig` on Windows
- Connectivity was tested using ICMP (ping)
- The default gateway was identified using the ARP table

These steps confirmed that both machines were on the same local network.

---

## ARP Analysis

The `arp -a` command was used to inspect the ARP cache and map IP addresses to MAC addresses. This helped identify:
- The Windows virtual machine
- The VMware NAT gateway
- Normal ARP behavior before manipulation

---

## ARP Spoofing (MITM)

ARP spoofing was performed from the Kali machine using `arpspoof` to poison the ARP cache of both the Windows machine and the default gateway. This resulted in both devices associating the attacker’s MAC address with each other’s IP addresses, placing the Kali machine in the middle of the communication.

IP forwarding was enabled to ensure traffic continued flowing normally through the attacker.

---

## Cleanup and Recovery

After the test was completed:
- ARP spoofing was stopped
- IP forwarding was disabled
- ARP caches were flushed on both systems
- Network services were restarted

This restored the lab environment to a normal and stable state.

---

## Disclaimer

This lab was conducted in a private virtual environment for educational purposes only. No real or unauthorized networks were targeted.

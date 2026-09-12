<div align="center">

# 🔐 Cybersecurity Lab Environment Setup

**Building an isolated virtual lab for penetration testing and ethical hacking practice**
</div>

<p align="center">
  <img src="https://img.shields.io/badge/Skill-Cybersecurity-404040?style=flat-square&labelColor=C00000" />
  <img src="https://img.shields.io/badge/Ver-Virtualbox%20v7.2-0070C0?style=flat-square&labelColor=000000" />
  <img src="https://img.shields.io/badge/Kali%20Linux-v2026.2-E87500?style=flat-square&labelColor=000000&logo=kalilinux&logoColor=white" />
  <img src="https://img.shields.io/badge/Windows-10-0078D6?style=flat-square&labelColor=000000&logo=windows&logoColor=white" />
  <img src="https://img.shields.io/badge/Android--x86-9.0-3DDC84?style=flat-square&labelColor=000000&logo=android&logoColor=white" />
  <img src="https://img.shields.io/badge/Skill-Linux-404040?style=flat-square&labelColor=C00000" />
  <img src="https://img.shields.io/badge/Network-10.0.0.0%2F24-238F89?style=flat-square&labelColor=000000" />
  <img src="https://img.shields.io/badge/Penetration%20Testing-C00000?style=flat-square&labelColor=000000&logo=kalilinux&logoColor=white" />
  <img src="https://img.shields.io/badge/Skill-Virtualization-404040?style=flat-square&labelColor=C00000" />
  <img src="https://img.shields.io/badge/GitHub-404040?style=flat-square&labelColor=0070C0&logo=github&logoColor=white" />
  <img src="https://img.shields.io/badge/NetworkWalks-404040?style=flat-square&labelColor=C00000" />
  <img src="https://img.shields.io/badge/Ethical%20Hacking-E87500?style=flat-square&labelColor=000000&logo=kalilinux&logoColor=white" />
  <img src="https://img.shields.io/badge/Networkwalks%20-C00000?style=flat-square" />
</p>

---

## 📌 Project Overview

This project focuses on building a **multi-machine virtual cybersecurity and penetration-testing laboratory** using VirtualBox.

The lab consists of three virtual machines — **Kali Linux** (attacker/security machine), **Windows 10**, and **Android-x86 9.0** — all connected on a shared, isolated **NAT Network**. The goal is to configure static IP addressing on each machine and verify full bi-directional connectivity between all of them, along with outbound internet access.

This environment provides a safe, repeatable, isolated space to practice reconnaissance, scanning, and other security-testing activities without touching any real production network.

---

## 🎯 Objectives

- Install and configure VirtualBox as the hypervisor.
- Create a private **NAT Network** (10.0.0.0/24) for the lab.
- Install/import Kali Linux and configure it as the primary attacking machine.
- Install and configure a Windows 10 VM on the same network.
- Install and configure an Android-x86 9.0 VM on the same network.
- Assign consistent static IP addresses to all three machines.
- Verify bi-directional connectivity between all VMs.
- Verify internet access from each VM.
- Document the full setup process, issues, and solutions encountered.
- Take clean VM snapshots for recovery.

---

## 🛡️ Purpose of the Lab

This lab provides an isolated, controlled environment for cybersecurity learning and authorized security testing. It can be used for activities such as:

- Network reconnaissance and port scanning
- Vulnerability assessment
- Packet analysis
- Cross-platform (Linux/Windows/Android) network testing
- Security-tool experimentation

⚠️ **Important:** This laboratory must only be used for systems that you own or have explicit permission to test. Do not use the lab or its tools to attack unauthorized systems.

---

## 🏗️ Lab Architecture

<img width="1847" height="1010" alt="Screenshot 2026-09-12 213918" src="https://github.com/user-attachments/assets/8965a409-1587-4f02-914d-432725695681" />
SCREENSHOT: overall VirtualBox Manager view showing all 3 VMs.

All three virtual machines sit on the same VirtualBox NAT Network and can reach one another directly, as well as reach the internet through the NAT gateway.

---

## ⚙️ Lab Configuration

| 🧩 Component        | ⚙️ Configuration        |
| -------------------- | ------------------------ |
| 🖥️ Host OS          | Windows 10               |
| 🧰 Hypervisor        | VirtualBox 7.2           |
| 🐉 Kali Linux        | Kali Linux 2026.2        |
| 🪟 Windows VM        | Windows 10               |
| 🤖 Android VM        | Android-x86 9.0          |
| 🌐 Virtual Network   | NAT Network (NatNetwork) |
| 📡 Network Address   | 10.0.0.0/24              |
| 🐧 Kali IP Address   | 10.0.0.2/24              |
| 🪟 Windows IP Address| 10.0.0.10/24             |
| 🤖 Android IP Address| 10.0.0.9/24              |
| 🚪 Default Gateway   | 10.0.0.1                 |
| 🌍 DNS Server        | 8.8.8.8                  |

---

# 🪜 Lab Setup Procedure

## Step 1. Install VirtualBox

VirtualBox 7.2 was installed as the hypervisor for the whole lab.

---

## Step 2. Create the NAT Network

A dedicated NAT Network was created in VirtualBox so that all lab VMs can communicate with each other and reach the internet.

```text
Network Name: NatNetwork
IPv4 Prefix:  10.0.0.0/24
DHCP:         Enabled
IPv6:         Disabled
```
<img width="1847" height="997" alt="Screenshot 2026-09-12 214505" src="https://github.com/user-attachments/assets/24974ab3-aa5b-4558-b9d8-b2f3b6030304" />
SCREENSHOT: VirtualBox > Network > NAT Networks tab

A **NAT Network** (rather than plain NAT) was used specifically because it allows multiple VMs to see and reach each other on the same virtual subnet, while still providing outbound internet access — required for connecting Kali, Windows, and Android together.

---

## Step 3. Kali Linux Setup

The Kali Linux virtual machine was imported into VirtualBox and attached to the NAT Network.

```text
Adapter 1
Attached to:  NAT Network
Network:      NatNetwork
Adapter Type: Intel PRO/1000 MT Desktop
Promiscuous Mode: Allow All
RAM: 2048 MB
```

<img width="1476" height="902" alt="Screenshot 2026-09-12 142743" src="https://github.com/user-attachments/assets/97cbd086-2a76-4ea5-a54b-999c1b273a49" />
SCREENSHOT: Kali VM network settings


### Static IP Configuration

```text
IP Address:  10.0.0.2
Subnet Mask: 255.255.255.0
Gateway:     10.0.0.1
DNS:         8.8.8.8
```

<img width="1273" height="895" alt="Screenshot 2026-09-12 144002" src="https://github.com/user-attachments/assets/d6e08875-500d-4e28-9f5c-8c018387f82e" />
SCREENSHOT: Kali IP settings via GUI / ip a output

---

## Step 4. Windows 10 Setup

A Windows 10 VM was created and attached to the same NAT Network as Kali.

```text
Adapter 1
Attached to:  NAT Network
Network:      NatNetwork
Adapter Type: Intel PRO/1000 MT Desktop
RAM: 4096 MB
```

<img width="1387" height="847" alt="Screenshot 2026-09-12 173201" src="https://github.com/user-attachments/assets/da6eac21-fa09-445f-948c-926d34489f26" />
SCREENSHOT: Windows VM network settings

### Static IP Configuration

```text
IP Address:      10.0.0.10
Subnet Mask:     255.255.255.0
Default Gateway: 10.0.0.1
Preferred DNS:   8.8.8.8
```

<img width="1011" height="866" alt="Screenshot 2026-09-12 182515" src="https://github.com/user-attachments/assets/fbc5afa4-01a6-482f-a1d2-cda4356f564a" />
SCREENSHOT: Windows TCP/IPv4 properties 

---

## Step 5. Android-x86 9.0 Setup

An Android-x86 9.0 VM was created and attached to the same NAT Network.

```text
Adapter 1
Attached to:  NAT Network
Network:      NatNetwork
RAM: 2048 MB
Display:
  3D Acceleration: Disabled
  Graphics Controller: VBoxVGA
```

<img width="1532" height="911" alt="Screenshot 2026-09-12 152825" src="https://github.com/user-attachments/assets/0ce105d3-14e1-43da-9f28-fc1adbbd2788" />
SCREENSHOT: Android VM display/network settings

Few extra things to note:
Attach the ISO and start install
• Go to Settings > Storage
• Click the empty disk icon under Controller
• Choose the Android-x86 9.0 ISO you downloaded
• Go to Settings > Display, set Video Memory to at least 64 MB, and enable 3D
Acceleration , here if the Android gets stuck on the "Android" screen its better to disable 3D acceleartions and choose VBoxSVGA or VBoxVGA.
<img width="965" height="632" alt="Screenshot 2026-09-12 230144" src="https://github.com/user-attachments/assets/d4685184-3297-4a37-ba65-ff3bdde92ccb" />

• Start the VM — the Android-x86 boot menu will appear
<img width="777" height="460" alt="Screenshot 2026-09-12 152223" src="https://github.com/user-attachments/assets/7a3a9ed5-358d-4afe-adc0-64b16f12b58e" />

• Choose Installation - Install Android-x86 to harddisk
• Create/modify partitions, select the virtual disk, choose ext4 filesystem, confirm
<img width="793" height="453" alt="Screenshot 2026-09-12 152412" src="https://github.com/user-attachments/assets/54c4d09f-3078-4550-8036-90f76b4b8dfb" />

• Choose to install GRUB and make the system writable (yes to both)
<img width="772" height="442" alt="Screenshot 2026-09-12 152451" src="https://github.com/user-attachments/assets/bdaecdf2-1cea-456e-a7d4-bddadb569e26" />
<img width="840" height="467" alt="Screenshot 2026-09-12 152507" src="https://github.com/user-attachments/assets/1e202ffb-702b-4a25-8957-3c966ef910f6" />

• Let it install, then reboot when prompted
<img width="781" height="458" alt="Screenshot 2026-09-12 152514" src="https://github.com/user-attachments/assets/371ff664-5a4b-44e8-a9a4-67fd2f316a35" />


### Static IP Configuration

Android-x86 in VirtualBox exposes its network as a simulated Wi-Fi adapter (**VirtWifi**) rather than a physical Ethernet interface, so the static IP was set via **Settings > Network & Internet > Wi-Fi > VirtWifi**:

```text
IP Address:           10.0.0.9
Gateway:              10.0.0.1
Network prefix length: 24
DNS 1:                8.8.8.8
```

<img width="1015" height="852" alt="Screenshot 2026-09-12 225324" src="https://github.com/user-attachments/assets/793fcaf2-3f26-4aeb-928e-34f3b5ba920c" />
SCREENSHOT: Android VirtWifi static IP screen

---


# 🔎 Lab Verification

| ✅ Test                          | 🧾 Command (run on)                 | 🎯 Expected Result        |
| -------------------------------- | ------------------------------------ | -------------------------- |
| 🌐 Check Kali IP                 | `ip a` (Kali)                        | 10.0.0.2/24 shown          |
| 🌐 Check Windows IP              | `ipconfig` (Windows)                 | 10.0.0.10 shown            |
| 🌐 Check Android IP              | Settings > Wi-Fi > VirtWifi (Android)| 10.0.0.9 shown             |
| 📡 Kali → Windows ping           | `ping 10.0.0.10` (Kali)              | 0% packet loss             |
| 📡 Windows → Kali ping           | `ping 10.0.0.2` (Windows)            | 0% packet loss             |
| 📡 Kali → Android ping           | `ping 10.0.0.9` (Kali)               | 0% packet loss             |
| 📡 Android → Kali ping           | `ping -c 4 10.0.0.2` (Android)       | 0% packet loss             |
| 📡 Windows → Android ping        | `ping 10.0.0.9` (Windows)            | 0% packet loss             |
| 🌍 Internet check (all VMs)      | `ping 8.8.8.8`                       | Successful replies         |

### Screenshots — Connectivity Proof

<img width="1253" height="682" alt="Screenshot 2026-09-12 202129" src="https://github.com/user-attachments/assets/f50bb818-24e8-4b5d-8bed-66e48603fcbd" />
<!-- SCREENSHOT: Kali terminal pinging 10.0.0.10 and 10.0.0.9 -->

<img width="1022" height="758" alt="Screenshot 2026-09-12 211628" src="https://github.com/user-attachments/assets/4f3f561b-388d-497c-81cd-ffbeeacb2702" />
<!-- SCREENSHOT: Android console/terminal pinging 10.0.0.2 and 10.0.0.10 -->

<img width="1016" height="858" alt="Screenshot 2026-09-12 211440" src="https://github.com/user-attachments/assets/47c09d01-1c32-41b1-96f2-f2e457c03a99" />
<!-- SCREENSHOT: Windows Command Prompt pinging 10.0.0.2 and 10.0.0.9 -->

---

# 🐞 Problems Encountered & Solutions

## Problem 1. Android-x86 had no "Ethernet" option in Settings

**Issue:** Following the standard guide, Settings > Network & Internet was expected to show an Ethernet entry for static IP configuration — it never appeared, even after changing the VirtualBox adapter type or disabling Wi-Fi via shell (`svc wifi disable`).

**Cause:** Android-x86 running under VirtualBox binds its virtual network card through a simulated Wi-Fi service (**VirtWifi**) rather than exposing a true Ethernet interface (`eth0`), regardless of the adapter type selected in VirtualBox.

**Solution:** Configured the static IP directly through **Settings > Network & Internet > Wi-Fi > VirtWifi > network details**, setting IP/Gateway/Prefix/DNS there instead of looking for an Ethernet tab. This matched the working configuration and resolved the issue.

---

## Problem 2. Mixing shell (`ip addr` / `ip route`) commands with GUI network settings caused connectivity loss

**Issue:** After repeatedly running `ip addr add`, `ip addr flush`, and `ip route add` commands on different interfaces (`wifi_eth`, `wlan0`, `eth0`) to troubleshoot, the Android VM lost its IP entirely and returned "Network unreachable."

**Cause:** Shell-level interface commands conflicted with the Android network manager GUI, which kept overriding or re-flushing the interface Android's system service was actually using.

**Solution:** Rebooted the VM, cleared any stale shell-assigned IP with a single `ip addr flush`, and then configured the static IP **only** through the GUI (VirtWifi settings) without further shell commands. Connectivity was restored immediately.

---

## Problem 3. 100% packet loss between Kali and Windows despite correct IP configuration

**Issue:** `ping` between Kali and Windows initially failed in one direction.

**Cause:** Windows Defender Firewall blocks inbound ICMP Echo Requests by default, so Windows would not reply to pings even though outbound pings from Windows worked fine.

**Solution:** Enabled the *File and Printer Sharing (Echo Request - ICMPv4-In)* inbound rule in Windows Defender Firewall with Advanced Security, which allowed Windows to reply to ping requests from Kali and Android.

---

# 💡 What I Learned

### 1. NAT Network vs. standard NAT
A NAT Network allows multiple VMs on the same virtual switch to communicate directly with each other while still providing outbound internet access — essential for a multi-machine lab like this one.

### 2. Cross-platform static IP configuration
I learned how static IP addressing differs across Linux (Kali), Windows, and Android-x86, and how to configure each one correctly through their respective network settings screens.

### 3. Android-x86 networking quirks in VirtualBox
Android-x86 exposes its network through a Wi-Fi emulation layer (VirtWifi) rather than a standard Ethernet interface — an important platform-specific detail that isn't obvious from documentation written for physical Android devices.

### 4. Host firewall behavior
I learned that Windows blocks inbound ICMP by default, which can look like a network configuration problem when it's actually a firewall rule.

### 5. Keeping configuration methods consistent
Mixing shell commands and GUI network configuration tools on the same interface can cause conflicting state. Sticking to one method (GUI, in this case) resolved repeated connectivity issues.

### 6. Documentation and troubleshooting habits
Documenting each problem and its resolution — not just the final working state — is what makes a lab writeup genuinely useful to others working through the same exercise.

---

# 🔐 Security & Ethical Use

This laboratory is intended strictly for education and authorized testing purposes only. All machines, IP addresses, and configurations described here exist solely within an isolated virtual lab environment that I own and control.

---

# 🔗 Tools & Resources

- **VirtualBox:** [https://virtualbox.org/wiki/Downloads](https://virtualbox.org/wiki/Downloads)
- **Kali Linux:** [https://kali.org/get-kali](https://kali.org/get-kali)
- **Android-x86:** [https://www.android-x86.org/](https://www.android-x86.org/)
- **Windows 10 ISO:** [https://www.microsoft.com/en-us/software-download/windows10](https://www.microsoft.com/en-us/software-download/windows10)

---

# 👤 Author

**Bithin Krishna Radhakrishnan**
Cybersecurity Intern, Batch B083

LinkedIn: www.linkedin.com/in/bkr95

---

## 📌 Project Information

**Program Name:** Cybersecurity at Networkwalks | **Week:** 01 | **Project:** Cybersecurity & Pentesting Lab Setup (Kali + Windows 10 + Android-x86) | **Repository:** GitHub

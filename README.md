<div align="center">

# 🔐 Cybersecurity Lab Environment Setup

**Designing and configuring a virtual laboratory for cybersecurity learning and practical security testing.**
</div>

<p align="center">
  <img src="https://img.shields.io/badge/Skill-Cybersecurity-404040?style=flat-square&labelColor=C00000" />
  <img src="https://img.shields.io/badge/Ver-Virtualbox%20v7.2-0070C0?style=flat-square&labelColor=000000" />
  <img src="https://img.shields.io/badge/Kali%20Linux-v2026.2-E87500?style=flat-square&labelColor=000000&logo=kalilinux&logoColor=white" />
  <img src="https://img.shields.io/badge/Skill-Linux-404040?style=flat-square&labelColor=C00000" />
  <img src="https://img.shields.io/badge/Network-10.0.0.0%2F24-238F89?style=flat-square&labelColor=000000" />
  <img src="https://img.shields.io/badge/Penetration%20Testing-C00000?style=flat-square&labelColor=000000&logo=kalilinux&logoColor=white" />
  <img src="https://img.shields.io/badge/Skill-Virtualization-404040?style=flat-square&labelColor=C00000" />
  <img src="https://img.shields.io/badge/GitHub-404040?style=flat-square&labelColor=0070C0&logo=github&logoColor=white" />
  <img src="https://img.shields.io/badge/Kali%20Linux-404040?style=flat-square&labelColor=C00000&logo=kalilinux&logoColor=white" />
  <img src="https://img.shields.io/badge/NetworkWalks-404040?style=flat-square&labelColor=C00000" />
  <img src="https://img.shields.io/badge/Ethical%20Hacking-E87500?style=flat-square&labelColor=000000&logo=kalilinux&logoColor=white" />
  <img src="https://img.shields.io/badge/Waqas%20Karim%20CCIE-C00000?style=flat-square" />
</p>

---

## 📌 Project Overview

This project involved establishing a virtual cybersecurity laboratory using Oracle VirtualBox and Kali Linux. The objective was to prepare a dedicated environment where I could explore cybersecurity concepts, become familiar with security tools, and perform practical exercises without directly affecting my host operating system.
The laboratory uses a virtual NAT Network to provide network connectivity to the Kali Linux machine while allowing additional virtual machines to be introduced for future practical exercises.
Through this setup, I gained practical experience in virtualization, Linux networking, IP addressing, network connectivity verification, and virtual machine recovery.

---

## 🎯 Objectives

The key objectives of this exercise were to:

- Set up Oracle VirtualBox as the virtualization platform.
- Download and deploy Kali Linux as a virtual machine.
- Establish a dedicated NAT Network for the laboratory.
- Configure the Kali Linux network adapter.
- Assign a consistent IPv4 address to the virtual machine.
- Verify communication between Kali Linux and its virtual gateway.
- Test external network connectivity and DNS resolution.
- Create a virtual machine snapshot to preserve the initial configuration.
- Document the installation and configuration process for future reference.

---

## 🛡️ Purpose of the Lab

The laboratory serves as a controlled environment for developing practical cybersecurity skills.

It provides a foundation for future exercises involving:

Network reconnaissance and discovery.
Port scanning.
Vulnerability assessment.
Packet analysis.
Web application security testing.
Security tool configuration and experimentation.
Authorized penetration-testing exercises.

⚠️**Ethical consideration:** All security-testing activities performed using this environment must be restricted to systems that I own or have explicit authorization to assess.

---

## 🏗️ Lab Architecture

![](1-screenshot-title-image.png)


Additional virtual machines can be connected to the same NAT Network in future exercises to support controlled communication and security testing between systems.

   
---

## ⚙️ Lab Configuration

| 🧩 Component       | ⚙️ Configuration   |
| ------------------ | ------------------  |
| 🖥️ Host OS         | Windows 10         |
| 🧠 Host RAM        | 16 GB               |
| ⚡ Processor       | Intel Core i7, 7th Generation      |
| 🧰 Hypervisor      | VirtualBox 7.2  |
| 🐉 Security OS     | Kali Linux 2026.2  |
| 🧠 Kali RAM        | 2048 MB            |
| 🌐 Virtual Network | NAT Network        |
| 📡 Network Address | 10.0.0.0/24        |
| 🐧 Kali IP Address | 10.0.0.2/24        |
| 🚪 Default Gateway | 10.0.0.1           |
| 🌍 DNS Server      | 8.8.8.8            |
| 🔮 Future VM Range | 10.0.0.3–10.0.0.99 |

---

# 🪜 Lab Setup Procedure

## Step 1. Install 7-Zip

7-Zip was installed to extract the Kali Linux virtual-machine package, which may be distributed as a `.7z` archive.

**Tool:** 7-Zip

---

## Step 2. Install Oracle VirtualBox

VirtualBox was installed as the hypervisor.

---

## Step 3. Create a Dedicted NAT Network

A dedicated NAT Network was created in VirtualBox.

Configuration:
Network Name: NatNetwork
IPv4 Prefix:  10.0.0.0/24
DHCP:         Enabled
IPv6:         Disabled

![](2-screenshot-network-settings-1.png)

A **NAT Network** was selected because multiple virtual machines connected to the same NAT Network can communicate with one another while also having outbound network connectivity.

This will allow future attacker and target VMs to communicate within the lab.


---

## Step 4. Import and configure Kali Linux

The Kali Linux virtual machine was downloaded from the official Kali Linux website and imported into VirtualBox.

The VM network adapter was configured as follows:

```text
Adapter 1
Attached to: NAT Network
Network:     NatNetwork
Adapter Type: Intel PRO/1000 MT Desktop
```

The VM was allocated:

```text
RAM: 2048 MB
```
![](3-screenshot-kali-linux.png)
A shared folder was also configured for transferring required files between the host operating system and the Kali VM.



---

## Step 5. Configure the Kali Linux Network

The Kali Linux network configuration was checked and configured with a consistent IPv4 address.

Example configuration:

```text
IP Address: 10.0.0.2
Subnet Mask: 255.255.255.0
Gateway: 10.0.0.1
DNS: 8.8.8.8
```

A consistent IP address makes it easier to document the lab and reference the Kali machine in future exercises.

![](4-screenshot-kali-network-settings.png)

---

## Step 6. Create a Clean VM Snapshot

After completing the initial configuration, a VirtualBox snapshot was created.

Example snapshot name:

```text
My Fresh Kali - Setup
```

The snapshot represents the clean baseline of the laboratory.

If a future exercise changes or damages the VM configuration, the machine can be restored to this baseline.


---

# 🔎 Lab Verification

| ✅ Test                        | 🧾 Command                      | 🎯 Expected Result              |
| ----------------------------- | ------------------------------- | ------------------------------- |
| 🌐 IP address verification    | `ip a`                          | kali address 10.0.0.2/24        |
| 📡 Test gateway               | `ping 10.0.0.1`                 | Successful replies              |
| 🌍 Test Internet connectivity | `ping 8.8.8.8`                  | Successful replies              |
| 🔎 Test DNS resolution        | `nslookup networkwalks.com`     | Domain resolves                 |
| 🧰 Verify Nmap                | `nmap --version`                | Nmap version displayed          |
| 🔄 Verify snapshot            | Restore snapshot and run `ip a` | Baseline configuration restored |

### Example Results

```text
IP Address:
10.0.0.2/24

Gateway:
10.0.0.1

DNS:
8.8.8.8
```

---

# 🐞 Problems Encountered & Solutions

Documenting problems is an important part of the project.

## Problem 1. Hardware Virtualization Disabled

During the initial setup, hardware virtualization was disabled in the laptop's BIOS/UEFI settings. This prevented VirtualBox from starting the virtual machine as expected.

**Resolution**

The issue was addressed by enabling Intel Virtualization Technology (Intel VT-x) through the system firmware settings.

The following procedure was followed:
1)Restart the laptop.
2)Enter the BIOS/UEFI configuration interface.
3)ocate the hardware virtualization setting.
4)Enable Intel Virtualization Technology (VT-x).
5)Save the changes and exit the BIOS.
6)Restart the computer and launch the Kali Linux virtual machine again.

After enabling hardware virtualization, the virtual machine was able to start successfully.

---

## Problem 2. DNS Resolution Failure

Although the Kali virtual machine could successfully communicate with its gateway and an external IP address, the initial DNS lookup failed.
The error indicated that the configured DNS server (10.0.0.1) was refusing requests on port 53.

**Troubleshooting**

To isolate the problem, the DNS lookup was repeated using Google's public DNS server (8.8.8.8).

```bash
nslookup networkwalks.com 8.8.8.8
```
The request returned a successful domain resolution.

This demonstrated that the alternative DNS server could resolve the domain, while the originally configured DNS server remained unresponsive to the lookup request.

**Further improvement**: The persistent DNS configuration can be updated to use a working DNS server and verified with another lookup using the default nslookup command.

---

# 💡 **What I Learned**

This exercise provided practical experience in preparing a virtual environment for cybersecurity activities.

The main concepts and skills developed include:

**1. Virtualization**
I gained a better understanding of how virtualization allows multiple operating systems to run independently on one physical computer.
I also learned the importance of enabling hardware virtualization before deploying virtual machines.

**2. NAT and NAT Network**
I learned that VirtualBox provides different networking modes for virtual machines.
A NAT Network is particularly useful when multiple virtual machines need to communicate with one another while maintaining outbound network connectivity.

**3. IPv4 Network Configuration**
I gained practical experience configuring an IPv4 address, subnet mask, default gateway, and DNS server within Kali Linux.
I also learned how to inspect network interfaces using the ip a command.

**4. Network Connectivity Testing**
Using ping, I verified communication between the Kali virtual machine and its gateway, as well as its ability to reach an external IP address.
The DNS troubleshooting exercise also helped me understand the difference between IP connectivity and domain-name resolution.

**5. Virtual Machine Snapshots**
I learned the importance of creating a baseline snapshot before carrying out experiments that could change or affect the virtual machine's configuration.
This provides a practical recovery option during future exercises.

**6. Technical Documentation**
I gained experience documenting installation procedures, network settings, verification commands, observed results, and troubleshooting activities.
Accurate documentation makes technical work easier to reproduce, review, and improve.

---

# 🔐 Security & Ethical Use

This laboratory was established for educational purposes and authorized cybersecurity practice.

All future scanning, testing, and experimentation will be conducted only against systems that I own or have explicit permission to assess.

---

# 🔗 Tools & Resources

- **7-Zip:** [https://7-zip.org/download.html](https://7-zip.org/download.html)
- **VirtualBox:** [https://virtualbox.org/wiki/Downloads](https://virtualbox.org/wiki/Downloads)
- **Kali Linux:** [https://kali.org/get-kali](https://kali.org/get-kali)

---

# 👤 Author

**Kamara Divine**\
Cybersecurity Trainee

LinkedIn: [https://www.linkedin.com/in/divine-kamara/](https://www.linkedin.com/in/divine-kamara/)

---

## 📌 Project Information

**Program Name:** Cybersecurity at Networkwalks | **Week:** 01 | **Project:** Cybersecurity & Pentesting Lab Setup | **Repository:** GitHub

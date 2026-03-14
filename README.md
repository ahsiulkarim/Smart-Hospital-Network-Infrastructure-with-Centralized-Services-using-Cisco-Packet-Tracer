# 🏥 Smart Hospital Network Infrastructure with Centralized Services
### Using Cisco Packet Tracer

---

**Institution:** East West University  
**Department:** Computer Science and Engineering (CSE)  
**Semester:** Summer 2025 — B.Sc. in CSE  
**Course:** CSE405 — Computer Networks | Section: 6  
**Submission Date:** 1st September, 2025  
**Course Teacher:** Rabea Khatun  

| Name | Student ID |
|------|------------|
| Ahsiul Karim | 2022-3-60-074 |
| Sourav Roy | 2020-3-60-028 |
| Nasrullah Kaisher Sijan | 2023-1-60-204 |

---

## 📋 Table of Contents

1. [Introduction](#1-introduction)
   - [Overview](#11-overview)
   - [Motivation](#12-motivation)
   - [Objectives](#13-objectives)
2. [Design / Implementation](#2-designdevelopmentimplementation)
   - [Project Details & Topology](#21-project-details)
   - [IP Configuration](#221-ip-configuration)
   - [FTP Server Setup](#222-ftp-server-setup)
   - [Email & DNS Server Configuration](#223-email--dns-server-configuration)
   - [Routing Configuration](#224-routing-configuration)
3. [Results & Discussion](#3-results-and-discussion)
   - [Network Connectivity](#31-network-connectivity)
   - [FTP Access Testing](#32-ftp-access-testing)
   - [Email Communication](#33-email-communication)
4. [Conclusion](#4-conclusion)

---

## 1. Introduction

### 1.1 Overview

This project designs a **secure, scalable smart hospital network** using Cisco Packet Tracer. It connects departments and administration under centralized services, including FTP with role-based access and email communication.

### 1.2 Motivation

The project aims to simulate a real-world hospital network that enhances efficiency, security, and interdepartmental communication while supporting centralized digital services.

### 1.3 Objectives

- Design and implement a secure, scalable hospital-wide network infrastructure for a smart healthcare system using Cisco Packet Tracer.
- Seamlessly support **patient record management**, **real-time medical device monitoring**, and **efficient departmental communication**.
- Ensure prioritized delivery of critical services across all departments.

---

## 2. Design/Development/Implementation

### 2.1 Project Details

The network is structured as a **hierarchical campus network**, where individual departments function as independent LANs connected via core routers. Each LAN contains user PCs and a local switch, while interdepartmental connectivity is handled through interconnected routers using serial links. The admin section serves as a centralized service hub.

**Full Network Topology Overview:**

![Network Topology Overview](images/topology_overview.png)

> *Figure: Departmental Network Topology — Full Hospital Infrastructure*

![Departmental Network Topology](images/img_01_page4.jpeg)

> *Figure: Departmental Network Topology (from Report)*

---

#### Topology Layers and Components

**Core Routers (Router Layer):**
- Five **2811 Routers** interconnect the departmental LANs using serial interfaces.
- The routers form a **mesh-like connection**, facilitating robust communication between department subnets.
- Serial links are used for establishing connectivity between routers.

**Departmental LANs:**
| Department | Subnet | Gateway | Assigned IPs |
|---|---|---|---|
| Emergency Department | 192.168.30.0/24 | 192.168.30.6 | 192.168.30.1 – 192.168.30.4 |
| Outpatient Department (OPD) | 192.168.31.0/24 | 192.168.31.6 | 192.168.31.1 – 192.168.31.4 |
| Pharmacy Department | 192.168.32.0/24 | 192.168.32.6 | 192.168.32.1 – 192.168.32.5 |
| Radiology Department | 192.168.33.0/24 | 192.168.33.6 | 192.168.33.1 – 192.168.33.5 |
| Laboratory Department | 192.168.34.0/24 | 192.168.34.6 | 192.168.34.1 – 192.168.34.5 |
| Administration Section | 192.168.35.0/24 | 192.168.35.6 | 192.168.35.1 – 192.168.35.5 |
| IT / Server Room | 192.168.36.0/24 | 192.168.36.9 | 192.168.36.1 – 192.168.36.9 |

---

### 2.2 Implementation

#### 2.2.1 IP Configuration

**For Routers (CLI):**

```bash
Router> enable
Router# configure terminal
Router(config)# interface [Interface_Type]
Router(config-if)# ip address [IP_Address] [Subnet_Mask]
Router(config-if)# no shutdown
Router(config-if)# exit
```

![IP Assignment of Router](images/img_02_page6.jpeg)

> *Figure: IP Assignment of Router*

---

**For PCs & Servers:**

- Click on **PC or Server → Desktop → IP Configuration**
- Assign the appropriate **IPv4 Address**, **Subnet Mask**, and **Default Gateway** as per the IP Addressing Table.

![IP Assignment of PC](images/img_03_page7.jpeg)

> *Figure: IP Assignment of PC*

---

#### 2.2.2 FTP Server Setup

The FTP server was configured with **role-based access control**:
- **AdminHead** — Full permissions: Read, Write, Delete, Rename, List
- **Admin users** — Read-only access
- **Department users** — Read-only access

![FTP Server Configuration](images/img_04_page8.jpeg)

> *Figure: Configuration of FTP Server — Admin User Setup*

![FTP Server Configuration for PC Admin](images/img_05_page8.jpeg)

> *Figure: Configuration of FTP Server for PC Admin (Emergency Department)*

![FTP Server Configuration Extended](images/img_06_page8.jpeg)

> *Figure: Configuration of FTP Server — Extended User List*

---

#### 2.2.3 Email & DNS Server Configuration

**PC Email Setup:**
- Click any PC → **Desktop tab → Email**
- Assign: Name, Email Address, Incoming Mail Server, Outgoing Mail Server, Username, Password → click **Save**

![Email Server Configuration](images/img_07_page9.jpeg)

> *Figure: Configuration of Email Server — User List*

---

**DNS Server Setup:**

![DNS Server Configuration](images/img_08_page10.jpeg)

> *Figure: Configuration of DNS Server (gmail.com → 192.168.36.8)*

---

**Mail Server Input/Output Setup:**

![Email Service Configuration](images/img_09_page10.jpeg)

> *Figure: Configuration of Email Service — Mail Server Settings*

---

#### 2.2.4 Routing Configuration

**RIP Dynamic Routing via CLI:**

```bash
Router> enable
Router# configure terminal
Router(config)# router rip
Router(config-router)# network [Network_Address]
Router(config-router)# exit
```

Networks advertised: `192.168.30.0`, `192.168.31.0`, `192.168.32.0`, `192.168.33.0`, `192.168.34.0`, `192.168.35.0`, `192.168.36.0`

![Dynamic Routing Configuration](images/img_10_page11.jpeg)

> *Figure: Dynamic Routing (RIP) Configuration*

---

## 3. Results and Discussion

### 3.1 Network Connectivity

A comprehensive set of connectivity tests were conducted to verify the network's functionality. Using the **ping command**, each PC was able to communicate successfully with others both within and outside its subnet. This confirmed proper IP assignments and functional routing configurations across all routers.

![Connectivity Check - Ping Between Networks](images/img_11_page12.jpeg)

> *Figure: Connectivity Check — Pinging Between Networks (192.168.31.1 and 192.168.32.2)*

![Connectivity Check - Additional Ping](images/img_12_page13.jpeg)

> *Figure: Connectivity Check — Pinging 192.168.34.2 (Laboratory Department)*

---

### 3.2 FTP Access Testing

The FTP server was accessed using multiple user profiles:
- **AdminHead / Admin users** — tested for full privileges: uploading, renaming, deleting files ✅
- **Department PCs** — tested for read-only access, verifying restrictions were properly enforced ✅

**FTP Upload (put command):**

![FTP Commands - Upload](images/img_13_page14.jpeg)

> *Figure: FTP Commands — Connecting and Uploading a File (EmergencyHead.txt)*

**FTP Download (get command):**

![FTP Commands - Download](images/img_14_page14.jpeg)

> *Figure: FTP Commands — Downloading a File from Server*

**FTP Rename:**

![FTP Commands - Rename](images/img_15_page15.jpeg)

> *Figure: FTP Commands — Renaming a File (EmergencyHead.txt → Emergency1.txt)*

**FTP Directory Listing:**

![FTP Directory Listing](images/img_16_page15.jpeg)

> *Figure: FTP Directory Listing — All Files on Server*

**FTP Delete:**

![FTP Delete](images/img_17_page16.jpeg)

> *Figure: FTP Commands — Deleting a File (abc.txt) Successfully*

---

### 3.3 Email Communication

Each PC was configured with an email client and tested by sending messages across various departments. Messages were **successfully delivered and received** without delay or error, confirming the email server configuration was effective and reliable.

**Sending an Email:**

![Sending Mail](images/img_18_page18.jpeg)

> *Figure: Sending Mail — Emergency2 composing email to Emergency1@gmail.com*

**Receiving an Email:**

![Receiving Mail](images/img_19_page19.jpeg)

> *Figure: Receiving Mail — Emergency1 inbox showing successfully received message*

---

## 4. Conclusion

The implementation of a network infrastructure for a hospital-wide network using Cisco Packet Tracer demonstrated key networking concepts and best practices:

- Each department was designed as a **separate LAN with its own subnet**, enabling organized communication.
- LANs were interconnected through routers using **RIP dynamic routing**, allowing seamless data exchange between departments.
- The project emphasized **logical IP addressing and subnetting**, ensuring traffic separation and easier management.
- Testing confirmed successful **connectivity**, **service availability** (FTP, Email, DNS), and **routing**.

Overall, the design offers a **scalable, secure, and educationally relevant** model for campus/hospital network deployment and provided valuable hands-on experience in designing, configuring, and managing a complete enterprise-level network infrastructure.

---

## 🛠 Technologies Used

| Tool / Protocol | Purpose |
|---|---|
| Cisco Packet Tracer | Network simulation environment |
| 2811 Routers | Inter-departmental routing |
| 2950/2960 Switches | Intra-departmental switching |
| RIP (Routing Information Protocol) | Dynamic routing between subnets |
| FTP (File Transfer Protocol) | Centralized file access with RBAC |
| SMTP / POP3 | Email communication between departments |
| DNS | Domain name resolution (gmail.com) |
| IPv4 /24 Subnetting | Structured IP address management |

---

> 📁 **Note:** Due to the large number of devices, only sample configuration screenshots are included. All devices were configured with appropriate IP settings, roles, and services as reflected in the simulation file. The complete topology and functional results validate the successful implementation.

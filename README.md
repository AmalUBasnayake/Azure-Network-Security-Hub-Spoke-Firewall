<p align="center">
  <h1 align="center">🔥 Azure Enterprise Network Security</h1>
  <h3 align="center">Hub-and-Spoke Architecture with Centralized Azure Firewall</h3>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Azure-Firewall-blue?logo=microsoftazure" />
  <img src="https://img.shields.io/badge/Architecture-Hub--Spoke-purple" />
  <img src="https://img.shields.io/badge/Security-Zero%20Trust-red" />
  <img src="https://img.shields.io/badge/Networking-Enterprise-success" />
  <img src="https://img.shields.io/badge/Status-Lab%20Validated-brightgreen" />
</p>

---

# 📌 Project Overview

This project demonstrates an **enterprise-grade network security architecture** in Microsoft Azure using a **Hub-and-Spoke topology** with centralized traffic inspection via **Azure Firewall**.

The design enforces:

- Centralized inbound traffic control (DNAT)
- Outbound internet filtering (FQDN-based rules)
- Forced tunneling using User Defined Routes (UDR)
- Zero public exposure of internal workloads
- Centralized monitoring via Log Analytics

This mirrors real-world enterprise cloud network design patterns.

---

# 🎯 Business Objective

Traditional flat network architectures introduce:

- Uncontrolled east-west traffic
- Direct public exposure of workloads
- Limited outbound filtering
- Reduced visibility into network activity

This solution enforces:

> 🔐 Segmentation → 🔍 Inspection → 🚦 Controlled Access → 📊 Monitoring

---

# 🏗️ High-Level Architecture

## 🌐 Network Layout

```mermaid
flowchart LR
Internet --> FW[Azure Firewall Public IP]
FW -->|DNAT| VM[Private VM - Spoke VNet]
VM -->|Outbound via UDR| FW
FW --> Internet


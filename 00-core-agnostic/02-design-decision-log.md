---
id: 02-design-decision-log
title: Design Decision Log — Architettura OT Agnostica
sidebar_label: 🛡 00_02 — Design Decision Log
sidebar_position: 2
description: Registro Ufficiale delle Decisioni Tecniche per Conformità IEC 62443 SL-2
---

# Design Decision Log — Architettura OT Agnostica

| Campo | Dettaglio |
|---|---|
| **Obiettivo** | Conformità SL-2 (IEC 62443-3-3, 4-2) e Governance CSMS (2-1) |
| **Revisione** | 1.1 |
| **Data** | 23 Aprile 2026 |
| **Stato** | Documento Base Integrale |

---

## 🧱 1. Protezione Perimetrale (FR 5)

| Decisione | SR | Descrizione | Razionale |
|---|---|---|---|
| **D 1.1** | SR 5.2 | **Firewall Stateful "Deny-by-default"** — blocca ogni comunicazione non autorizzata. Management da WAN inibito. | Previene intrusioni dall'ambiente IT aziendale. |
| **D 1.2** | SR 4.1 | **Topology Hiding & Authorized Conduits** — NAT/Alias IP + unico conduit OPC-UA (TCP 4840). | Impossibile per un attaccante mappare PLC e HMI. |

---

## 🔑 2. Gestione Accessi e Identificazione (FR 1 & FR 2)

| Decisione | SR | Descrizione | Razionale |
|---|---|---|---|
| **D 2.1** | SR 7.8 | **Selettore a Chiave Wi-Fi** — accesso attivato solo tramite selettore fisico a bordo quadro. | Misura compensativa critica in assenza di prese RJ45 esterne. |
| **D 2.2** | SR 2.1 | **Captive Portal & Session Control** — VLAN 300 con Captive Portal, idle-timeout 30 min, limite sessione 4 ore. | Previene l'uso di PC lasciati incustoditi. |

---

## ✅ 3. Integrità e Inventario Asset (FR 7)

| Decisione | SR | Descrizione | Razionale |
|---|---|---|---|
| **D 3.1** | SR 7.8 | **MAC Locking (Port Lock)** — ogni porta switch vincolata al MAC del dispositivo registrato. Azione "Drop" su sconosciuti. | Protegge l'integrità fisica delle porte PLC/HMI. |
| **D 3.2** | SR 7.8 | **Asset Inventory Passivo** — polling API verso la Dashboard Tecnopack senza disturbare il traffico. | Visibilità totale senza impatto sulla produzione. |

---

## 🚨 4. Logging e Monitoraggio (FR 6)

| Decisione | SR | Descrizione | Razionale |
|---|---|---|---|
| **D 4.1** | SR 2.8 | **Syslog centralizzato** — ogni evento inviato a Wazuh. In Air-Gap: buffer locale su SD/Disk. | Tracciabilità completa degli eventi di sicurezza. |

---

## 🏛 5. CSMS Lite — Governance (IEC 62443-2-1)

### Decisione 5.1: Vulnerability & Patch Management
- **Monitoring:** Dashboard Tecnopack interroga costantemente CVE/NVD/CISA per ogni asset.
- **SLA Valutazione:** ogni nuova vulnerabilità analizzata entro **15 giorni**.
- **SLA Patching:** patch critiche applicate entro **30 giorni**, o al primo fermo macchina utile.

### Decisione 5.2: Incident Response Protocol
1. **Rilevazione:** Notifica immediata al team OT Security.
2. **Contenimento:** Disattivazione fisica AP (via chiave) e isolamento porta WAN.
3. **Recovery:** Ripristino "Golden Image" (Backup conforme SR 7.3).

### Decisione 5.3: Formazione & Awareness
**Training Annuale Obbligatorio** per tutti i tecnici e softwaristi Tecnopack sull'igiene cyber.

---

> *Documento di proprietà del Dipartimento OT Security — Tecno Pack S.p.A.*

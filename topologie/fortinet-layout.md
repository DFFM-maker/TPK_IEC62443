---
id: fortinet-layout
title: Network Layout — Fortinet (Premium IT)
sidebar_label: 🔴 Fortinet Layout
sidebar_position: 2
---

# Network Layout — Fortinet (Premium IT-Driven)

Soluzione IT-Driven — Deep Packet Inspection, gestione unificata FortiLink.

---

## Macchina Singola

```
Internet
    │
[Secomea 1549] ──── IT Customer
    │
[FortiGate Rugged]  Firewall · NAT · DPI
    │
    ├── VLAN 200 Supervisione 172.16.224.0/24
    │       └── [FSR-108F] → PLC · HMI
    │
    └── VLAN 300 External Interface con NAC
```

## Linea Complessa

```
[FortiGate Rugged]  DPI · NAT · NTP
    │  FortiLink
[FSR-108F Master]  802.1Q trunk
    │  FortiLink (10G)
[FSR-108F N1] ... [FSR-108F N...]
```

| Feature | Dettaglio |
|---|---|
| Hardware | FortiGate Rugged 40F/70G + FortiSwitch FSR-108F |
| Sicurezza | DPI su OPC-UA, Modbus, Profinet |
| Gestione | Single Pane of Glass via FortiLink |
| Intelligence | FortiGuard OT — aggiornamenti cloud real-time |
| OPEX | ~ 430 € / anno |

:::warning OPEX
Richiede abbonamenti annuali FortiGuard. Vedi [Analisi Costi](../00-core-agnostic/03-analisi-costi) per il confronto TCO.
:::

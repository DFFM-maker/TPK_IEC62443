---
id: mikrotik-layout
title: Network Layout — MikroTik (Lean)
sidebar_label: 🟢 MikroTik Layout
sidebar_position: 1
---

# Network Layout — MikroTik (Lean)

Soluzione standard Tecnopack — Dorsali 10G SFP+, zero costi di licenza.

---

## Macchina Singola

```
Internet
    │
[Secomea 1549] ──── IT Customer
    │
[MikroTik RB5009]  Firewall · NAT · RBAC
    │
    ├── VLAN 200 Supervisione 172.16.224.0/24
    │       └── [CSS610] → PLC · HMI · 3°pt
    │
    ├── VLAN 300 Manutenzione · Captive Portal
    │       └── [mAP lite] Wi-Fi
    │
    └── I/O 172.16.0.0/17
```

## Linea Complessa (Master + Periferici)

```
Internet          IT Customer
    └── [Secomea] ──┘
              │
    [RB5009]  FW · NAT · NTP · RBAC
              │
    [CSS610 Master]  802.1Q trunk
    ├── VLAN 200 · 300 · 100 (I/O)
              │  Trunk DAC SFP+ 10G
    ┌─────────┴─────────┐
[CSS610 N1]         [CSS610 N...]
 PLC · HMI · 3°pt    PLC · HMI · 3°pt
```

| Feature    | Dettaglio                                  |
| ---------- | ------------------------------------------ |
| Hardware   | RB5009UG+S+IN + CSS610-8G-2S+IN            |
| Throughput | 10Gbps dorsali DAC SFP+                    |
| Wi-Fi      | mAP lite su VLAN 300 con Captive Portal    |
| Gestione   | REST API + `.rsc` — Infrastructure as Code |
| OPEX       | **Zero licenze**                           |



> [!TIP] Config Template
> 
> [RouterOS Template v1.4][def] — firewall completo, VLAN, Hotspot, logging.



[def]: ../config/routeros-template
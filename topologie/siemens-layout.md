---
id: siemens-layout
title: Network Layout — Siemens (Premium OT)
sidebar_label: 🟡 Siemens Layout
sidebar_position: 3
---

# Network Layout — Siemens (Premium OT-Driven)

Soluzione OT-Driven — Hardware ultra-rugged, integrazione TIA Portal, Profinet.

---

## Macchina Singola

```
Internet
    │
[Secomea 1549] ──── IT Customer
    │
[Scalance SC622-2C]  FW · NAT · NTP · RBAC
    │
    ├── VLAN 200 Supervisione 172.16.224.0/24
    │       └── [Scalance XC208] → PLC · HMI
    │
    └── VLAN 300 Manutenzione · Captive Portal
            └── [mAP lite] Wi-Fi
```

## Linea Complessa

```
[Scalance SC622-2C]  FW · NAT · NTP
    │
[Scalance XC208 Master]  802.1Q trunk
    │  Trunk DAC SFP+ 10G
[XC208 N1] ... [XC208 N...]
```

| Feature | Dettaglio |
|---|---|
| Hardware | Scalance SC622-2C + Scalance XC208 |
| Ruggedness | Certificazioni estreme (temperatura, vibrazioni, EMI) |
| Integrazione | TIA Portal — diagnostica su HMI |
| Protocolli | Profinet nativo, ridondanza MRP, 802.1X |

:::info TIA Portal
Con XC208 la configurazione di rete è visibile direttamente in TIA Portal — stessi strumenti del PLC.
:::

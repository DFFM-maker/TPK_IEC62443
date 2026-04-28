---
id: 04-hardware-bom
title: Hardware BOM — Matrice e Distinta Base
sidebar_label: ⚙️ 00_04 — Hardware BOM
sidebar_position: 4
---

# Hardware BOM — Matrice e Distinta Base Integrale

**Revisione** 1.1 · 23 Aprile 2026 · IEC 62443 SL-2

---

## ⚙️ 1. Scenario A: Macchina Singola

| Componente | Fortinet | Siemens | MikroTik |
|---|---|---|---|
| **Edge Firewall** | FortiGate Rugged 40F | Scalance SC622-2C | MikroTik hEX S |
| **Switch (8 Porte)** | FSR-108F | Scalance XC208 | CSS610-8G-2S+IN |
| **Wi-Fi Maint.** | FortiAP 222E | Scalance W774 | mAP lite |

## ⚙️ 2. Scenario B: Linea Complessa (Master + Periferici)

| Ruolo | Fortinet | Siemens | MikroTik |
|---|---|---|---|
| **Firewall Master** | FortiGate Rugged 70G | Scalance SC632-2C | RB5009UG+S+IN |
| **Switch Periferici** | 3x FSR-108F | 3x Scalance XC208 | 3x CSS610-8G-2S+IN |
| **Interconnessione** | Ethernet | Ethernet | DAC SFP+ 10G |

:::info Nota Secomea
In ogni configurazione il punto di accesso per la teleassistenza è il **gateway Secomea 1549** (eccetto Profilo Barilla, delegato al PAM cliente).
:::

---

## 📖 3. Profili Vendor

| Vendor | Posizionamento | OPEX |
|---|---|---|
| 🟢 **MikroTik** | Standard Lean — produzione di serie, budget ottimizzato | Zero licenze |
| 🟡 **Siemens** | Premium OT — ambienti estremi, integrazione TIA Portal | Incluso HW |
| 🔵 **Fortinet** | Premium IT — DPI, gestione unificata IT/OT | ~ 430 € / anno |

---

> *Dipartimento OT Security — Tecno Pack S.p.A.*

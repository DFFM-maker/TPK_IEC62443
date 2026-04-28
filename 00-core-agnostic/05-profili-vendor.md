---
id: 05-profili-vendor
title: Profili Vendor-Ready — Analisi Comparativa Strategica
sidebar_label: 🟢 00_05 — Profili Vendor
sidebar_position: 5
---

# Profili Vendor-Ready — Analisi Comparativa Strategica

**Approccio "Agnostico"** — protezione indipendente dal brand del PLC (Omron, Rockwell, Siemens, Schneider).

---

## 🟢 1. MikroTik (Standard Tecnopack Lean)

| Caratteristica | Dettaglio | Valore |
|---|---|---|
| **Hardware** | RouterOS (hEX S / RB5009) + SwOS (CSS610) | DIN + alimentazione 24V, investimento minimo |
| **Licenze** | **Zero ricorrenti** | Conformità CRA senza abbonamenti |
| **Automazione** | IaC via REST API + `.rsc` scripting | Deploy automatizzato, -70% tempo messa in servizio |
| **Performance** | Latenza ultra-bassa + dorsali 10Gbps DAC SFP+ | Ideale per traffico di processo critico |

**Risparmio certificato: > 8.400 € su 5 anni.**

---

## 🔵 2. Fortinet (Premium IT-Driven)

| Caratteristica | Dettaglio |
|---|---|
| **Hardware** | FortiGate Rugged + FortiSwitch Rugged (FortiLink) |
| **Sicurezza** | Deep Packet Inspection (DPI) su protocolli OT |
| **Gestione** | Single Pane of Glass — switch gestito dal firewall |
| **Intelligence** | FortiGuard OT — aggiornamenti cloud real-time |

**Ideale per:** clienti con ecosistema Fortinet IT, massima protezione contro malware avanzato.

---

## 🟡 3. Siemens (Premium OT-Driven)

| Caratteristica | Dettaglio |
|---|---|
| **Hardware** | Scalance SC-600 + Scalance XC-200 |
| **Diagnostica** | Integrazione TIA Portal — rete come asset di automazione |
| **Affidabilità** | Certificazioni industriali estreme (temperatura, vibrazioni, EMI) |
| **Integrazione** | 802.1X nativo — ideale per PAM enterprise (Profilo Barilla) |

---

## ❌ 4. Profili Esclusi

| Vendor | Motivazione |
|---|---|
| **Teltonika** (RUT) | Dipendenza cloud obbligatoria (RMS). Firewall rule-based troppo semplice per RBAC SL-2. |
| **Ubiquiti** (UniFi/EdgeRouter) | Linee EdgeRouter EOL. Controller esterno obbligatorio. Alimentazione non ottimizzata per quadri industriali. |

---

## 🏁 5. Raccomandazioni

1. **Standard di Default:** MikroTik — miglior TCO, indipendenza totale da canoni.
2. **Integrazione Enterprise:** Siemens o Fortinet solo se richiesto esplicitamente.
3. **Agnosticismo Permanente:** qualunque vendor scelto, seguire il [Design Decision Log](./02-design-decision-log).

---

> *Documento tecnico a cura del Dipartimento OT Security — Tecno Pack S.p.A.*

---
id: 01-manuale-integrated-barilla
title: Manuale Integrale — Profilo Enterprise (Barilla Ready)
sidebar_label: 🤝 02_01 — Manuale Integrated v1.3
sidebar_position: 1
---

# Manuale Integrale — Profilo Integrated (Enterprise & Barilla Ready)

| Campo | Dettaglio |
|---|---|
| **Revisione** | 1.3 — Scenario Enterprise & Barilla Ready |
| **Data** | 22 Aprile 2026 |

---

## 🚀 1. Filosofia: Agnosticismo Tecnico

Tecnopack non vende una marca di firewall, vende una **Garanzia di Conformità Normativa**. In contesti strutturati come Barilla, la nostra architettura si integra con quella del cliente.

---

## 🏭 2. Il Profilo Enterprise (Caso Barilla)

### 2.1 Demarcazione delle Responsabilità

| Fornitore | Responsabilità |
|---|---|
| **Tecnopack** | Switch Siemens XC208 configurato con VLAN ("mura di cinta"). |
| **Barilla** | Sistema di autenticazione e accesso remoto (PAM/VPN). |

### 2.2 Addio Secomea: Integrazione PAM

Per Barilla **non installiamo Secomea**. L'assistenza avviene tramite:
1. **VPN Barilla:** tecnico Tecnopack autenticato sui server Barilla.
2. **PAM (Privileged Access Management):** scrivania virtuale (VDI) con visibilità limitata alla sola macchina specifica.

### 2.3 Zero-Wireless: Sicurezza Fisica Totale

**Nessun Wi-Fi.** Ogni comunicazione avviene tramite cavo fisico. Elimina alla radice il rischio di attacchi tramite segnali radio.

---

## 🧱 3. Strategia Tecnica: Switching e 802.1X

| VLAN | Nome | Contenuto | Accesso |
|---|---|---|---|
| **200** | Produzione | PLC e HMI | Protetta — nessuno entra senza invito |
| **300** | Maintenance | Tecnici | Richiede permesso firewall Barilla |

**802.1X:** quando si inserisce un cavo PC nella porta di manutenzione, lo switch chiede al server: *"Questo PC è autorizzato?"* — se no, porta spenta.

**Port Lock:** tutte le porte inutilizzate disattivate via software.

---

## ⚙️ 4. Matrice Hardware

| Componente | Lean | Premium | **Profilo Barilla** |
|---|---|---|---|
| Edge Device | MikroTik hEX S | FortiGate Rugged 40F | MikroTik hEX S |
| Teleassistenza | Secomea 1549 | Secomea 1549 | **PAM CLIENTE** |
| Wi-Fi | mAP lite | FortiAP 222E | **ASSENTE** |

---

## 📝 5. Dichiarazione di Conformità Enterprise

```
Costruttore: Tecno Pack S.p.A.
Oggetto: Infrastruttura di Rete Integrata Enterprise
Target: SL-2

Misure:
  1. VLAN: Isolamento fisico/logico su hardware Siemens.
  2. Accessi: PAM Enterprise + 802.1X.
  3. Integrità: Porte inutilizzate disattivate. No Wi-Fi.

Firma: _________________________ Data: _________________
```

---

> *Dipartimento OT Security — Tecno Pack S.p.A.*

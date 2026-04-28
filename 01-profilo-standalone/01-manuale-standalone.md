---
id: 01-manuale-standalone
title: Manuale Integrale — StandAlone Profile
sidebar_label: 🧱 01_01 — Manuale StandAlone
sidebar_position: 1
---

# Manuale Integrale — StandAlone Profile

| Campo | Dettaglio |
|---|---|
| **Revisione** | 1.1 — Integrale |
| **Data** | 20 Aprile 2026 |
| **Classificazione** | Documentazione Tecnica — Solo uso interno e cliente autorizzato |

---

## 🚀 1. Introduzione

### 1.1 Agnosticismo Tecnico (No Vendor Lock-in)
La nostra architettura di sicurezza è uno "scudo" esterno che protegge la macchina indipendentemente dalla marca del PLC. Che la linea utilizzi **Siemens, Omron, Rockwell o Schneider**, i protocolli di protezione rimangono costanti e certificati.

### 1.2 Percorso di Certificazione
1. **Definizione Requisiti:** mappatura sulle SR della norma.
2. **Scelta Standard:** Lean vs Premium in base a budget e richieste IT.
3. **Configurazione IaC:** template scriptati certificati — zero errore umano.
4. **Test FAT:** verifica fisici dei blocchi di sicurezza.
5. **Certificazione:** emissione [Dichiarazione di Conformità](../00-core-agnostic/06-dichiarazione-conformita).

---

## 🛡 2. Decisioni Architetturali

### 2.1 Protezione Perimetrale
- **Firewall "Deny-by-default":** solo le comunicazioni necessarie (es. OPC-UA con il MES) vengono autorizzate.
- **Topology Hiding (NAT):** dall'esterno la linea appare come un unico IP.

### 2.2 Gestione Accessi
- **Selettore a Chiave Wi-Fi:** No chiave = No segnale = Sicurezza totale.
- **Captive Portal:** sessione scade dopo **30 minuti** di inattività.

### 2.3 Integrità
- **MAC Locking (Port Lock):** dispositivo sconosciuto = porta disattivata istantaneamente.

---

## 📊 3. Analisi Economica

| | Fortinet | Siemens | **MikroTik** |
|---|---|---|---|
| Macchina Singola | ~ 1.550 € | ~ 1.400 € | **~ 195 €** |
| Linea Complessa | ~ 3.800 € | ~ 3.400 € | **~ 590 €** |
| **TCO 5 anni (linea)** | **~ 9.000 €** | **~ 3.400 €** | **~ 590 €** |

---

## ⚙️ 4. Implementazione Hardware

Il punto di accesso per la teleassistenza è sempre il **gateway Secomea 1549**.

| Componente | Fortinet | Siemens | MikroTik |
|---|---|---|---|
| Edge Firewall | FortiGate Rugged 40F | Scalance SC622-2C | MikroTik hEX S |
| Switch OT | FSR-108F | Scalance XC208 | CSS610-8G-2S+IN |
| AP Manutenzione | FortiAP 222E | Scalance W774 | mAP lite |

---

## 🗺 5. Topologie di Rete

| Colore | Elemento |
|---|---|
| 🔴 Rosso | Firewall |
| 🟠 Arancione | PLC / HMI / Switch OT |
| 🔵 Blu scuro | Secomea / Gateway |
| 🟣 Viola | Rete I/O |
| 🟢 Verde | Rete IT cliente |

→ [MikroTik Layout](../topologie/mikrotik-layout) · [Fortinet Layout](../topologie/fortinet-layout) · [Siemens Layout](../topologie/siemens-layout)

---

## 🚨 6. Case Study — Linea X

**Rischio principale:** contagio Ransomware via PC esterno su presa RJ45 libera nel quadro.

| | Valore |
|---|---|
| Impatto | **Massimo** (Blocco totale linea) |
| Probabilità | **Media** (Manutentori esterni) |
| Contromisura | Port Lock + VLAN 300 isolation |

| IP | Dispositivo | Vendor | Criticità |
|---|---|---|---|
| 172.16.224.11 | PLC Master | Omron | ALTA |
| 172.16.224.31 | Pannello HMI | Hakko | MEDIA |
| 172.16.239.254 | Router Sicurezza | Secomea | ALTA |

---

> *Documento prodotto dal Dipartimento OT Security — Tecno Pack S.p.A.*

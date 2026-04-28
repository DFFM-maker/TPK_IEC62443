---
id: intro
title: Guida alla Consultazione
slug: /iec62443
sidebar_position: 1
description: Mappa e Indice del Dossier Tecnico IEC 62443 SL-2 — Tecnopack OT Security Blueprint
---

# 🗺 Guida alla Consultazione

**Tecnopack OT Security Blueprint** — Rev. 1.2 · Aprile 2026

| Campo               | Dettaglio                                                                |
| ------------------- | ------------------------------------------------------------------------ |
| **Progetto**        | Mappa e Indice del Dossier Tecnico (IEC 62443 SL-2)                      |
| **Obiettivo**       | TCO a 5 anni con standard MikroTik Lean, piena conformità IEC 62443 SL-2 |
| **Redatto da**      | OT Security / Engineering — Tecno Pack S.p.A                             |
| **Data**            | 23 Aprile 2026                                                           |
| **Classificazione** | Documento Guida di Apertura                                              |

---

## 🚀 Benvenuti nel Blueprint Tecnopack

Questo dossier rappresenta lo **standard ufficiale** di Tecno Pack S.p.A. per la protezione delle infrastrutture di automazione industriale. Il materiale è organizzato con una codifica numerica per guidare il lettore dal concetto teorico all'implementazione sul campo.

---

## 📁 Organizzazione del Repository

| Codice | Area                   | Contenuto                                                         |
| ------ | ---------------------- | ----------------------------------------------------------------- |
| **00** | **Core Agnostic**      | Le fondamenta. Documenti validi per ogni macchina e ogni cliente. |
| **01** | **StandAlone Profile** | Lo standard di mercato per macchine indipendenti.                 |
| **02** | **Integrated Profile** | La soluzione Enterprise per grandi gruppi (es. Barilla).          |

---

## 📑 Indice Analitico

| Codice                                                            | Titolo                      | Cartella               |
| ----------------------------------------------------------------- | --------------------------- | ---------------------- |
| [00_01](00-core-agnostic/01-guida-iec62443.md)                    | 📖 Guida IEC 62443 per Tutti | 00_Core_Agnostic/      |
| [00_02](00-core-agnostic/02-design-decision-log.md)               | 🛡 Design Decision Log Base  | 00_Core_Agnostic/      |
| [00_03](./00-core-agnostic/03-analisi-costi.md)                   | 📊 Analisi Costi Hardware    | 00_Core_Agnostic/      |
| [00_04](./00-core-agnostic/04-hardware-bom.md)                    | ⚙️ Hardware BOM Completa     | 00_Core_Agnostic/      |
| [00_05](./00-core-agnostic/05-profili-vendor.md)                  | 🟢 Vendor-Ready Profiles     | 00_Core_Agnostic/      |
| [00_06](./00-core-agnostic/06-dichiarazione-conformita.md)        | ✅ Dichiarazione Conformità  | 00_Core_Agnostic/      |
| [01_01](./01-profilo-standalone/01-manuale-standalone.md)         | 🧱 Manuale StandAlone v1.1   | 01_Profile_StandAlone/ |
| [02_01](./02-profilo-integrated/01-manuale-integrated-barilla.md) | 🤝 Manuale Integrated v1.3   | 02_Profile_Integrated/ |

---

## 🗺 Topologie di Rete

| Profilo    | File                                              | Contenuto                           |
| ---------- | ------------------------------------------------- | ----------------------------------- |
| StandAlone | [MikroTik Layout](./topologie/mikrotik-layout.md) | Soluzione Lean con dorsali 10G SFP+ |
| StandAlone | [Fortinet Layout](./topologie/fortinet-layout.md) | Soluzione IT-Driven con DPI         |
| StandAlone | [Siemens Layout](./topologie/siemens-layout.md)   | Soluzione OT-Driven con TIA Portal  |

---

## 🔄 Workflow di Lettura Consigliato

1. **Fase Concettuale** → [00_01 Guida IEC 62443](./00-core-agnostic/01-guida-iec62443.md) + [00_02 Design Decision Log](./00-core-agnostic/02-design-decision-log.md)
2. **Fase Economica** → [00_03 Analisi Costi](./00-core-agnostic/03-analisi-costi.md)
3. **Fase Esecutiva** → [01_01 StandAlone](./01-profilo-standalone/01-manuale-standalone.md) oppure [02_01 Integrated](./02-profilo-integrated/01-manuale-integrated-barilla.md) + Topologia di Rete

---

> *Dipartimento OT Security — Tecno Pack S.p.A. — La sicurezza è un processo, non un prodotto.*

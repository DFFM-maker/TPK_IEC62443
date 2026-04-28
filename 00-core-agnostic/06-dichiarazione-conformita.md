---
id: 06-dichiarazione-conformita
title: Dichiarazione di Conformità Cybersecurity (IEC 62443)
sidebar_label: ✅ 00_06 — Dichiarazione Conformità
sidebar_position: 6
---

# Dichiarazione di Conformità — Cybersecurity (IEC 62443)

| Campo | Dettaglio |
|---|---|
| **Costruttore** | Tecno Pack S.p.A. |
| **Oggetto** | Infrastruttura di Controllo e Rete (SUC) |
| **Security Level Target** | **SL-2 (Security Level 2)** |
| **Data** | 23 Aprile 2026 |

---

## 1. Attestazione di Conformità

Si dichiara che la macchina/linea è progettata secondo il **Tecnopack OT Security Blueprint**, soddisfacendo i requisiti **IEC 62443-3-3** e **IEC 62443-4-2** per il livello **SL-2**.

---

## 2. Requisiti Implementati

| FR | Misura |
|---|---|
| **FR 1 / FR 2** | MFA remota (Secomea/Azure AD) e Captive Portal locale, timeout 30 minuti. |
| **FR 3** | Protezione sorgenti PLC/HMI e Audit Trail attivo. |
| **FR 4** | TLS per comunicazioni esterne via Secomea VPN. |
| **FR 5** | Stateful Firewall Deny-by-default + VLAN segmentate. |
| **FR 6 / FR 7** | Logging centralizzato (Wazuh ready), Port Lock, Disaster Recovery via IaC. |

---

## 3. Responsabilità Asset Owner

:::warning
- La **violazione fisica dei quadri** (apertura senza autorizzazione) invalida la conformità.
- La **gestione delle password locali** è a carico esclusivo del cliente finale.
:::

---

## 4. Modello — Da Firmare e Allegare al Fascicolo Tecnico

```
Costruttore: Tecno Pack S.p.A.
Security Level Target: SL-2

Misure implementate:
  1. Segmentazione: Stateful Firewall con blocco totale in ingresso.
  2. Accessi: Captive Portal e timeout automatico.
  3. Integrità: Port Lock e protezione sorgenti software.
  4. Monitoraggio: Logging centralizzato.

Firma Responsabile OT Security: _________________________
Data: _________________
```

---

> *Documento tecnico — Dipartimento OT Security — Tecno Pack S.p.A.*

---
id: 01-guida-iec62443
title: Guida IEC 62443 per Tutti
sidebar_label: 📖 00_01 — Guida IEC 62443
sidebar_position: 1
description: Capire e implementare la cybersecurity industriale in Tecnopack
---

# Guida Ultra-Integrale — La Norma IEC 62443 per Tutti

| Campo | Dettaglio |
|---|---|
| **Progetto** | Capire e Implementare la Cybersecurity Industriale in Tecnopack |
| **Revisione** | 1.2 |
| **Data** | 23 Aprile 2026 |
| **Classificazione** | Documento Tecnico di Riferimento — Uso Interno e Cliente |

---

## 🚀 1. Il Problema: Perché la Cybersecurity ci Riguarda?

Nelle fabbriche moderne, le macchine non sono più entità isolate. Sono sistemi complessi controllati da PLC e HMI connessi costantemente per teleassistenza e scambio dati con i sistemi gestionali del cliente.

**Cosa rischiamo senza una protezione adeguata?**

| Rischio | Impatto |
|---|---|
| 🛑 **Fermo Produzione** | Un attacco può bloccare la linea. Ogni minuto di stop costa migliaia di euro. |
| ⚠️ **Pericolo Safety** | Un malintenzionato potrebbe disattivare le sicurezze o manomettere i motori. |
| 🍳 **Furto di Ricette** | I parametri di processo sono il "cuore" del business. |
| 🌉 **Effetto Ponte** | Una macchina non protetta è la porta per entrare nei sistemi amministrativi. |

> La norma **IEC 62443** è il "Manuale di Istruzioni" mondiale che insegna come costruire macchine blindate.

---

## 📖 2. Glossario: Parlare la Lingua della Sicurezza

| Termine | Cos'è in parole povere |
|---|---|
| **PLC** | Il "cervello" della macchina. Muove i motori e gestisce la logica. |
| **HMI** | Il "volto" della macchina. Il pannello dove l'operatore preme Start. |
| **VLAN** | Un "recinto virtuale". Separa i dispositivi affinché non si disturbino. |
| **Firewall** | Il "guardiano del cancello". Decide chi può entrare in una zona. |
| **SL (Security Level)** | Il "livello di scudo". Tecnopack punta al livello SL-2. |
| **CSMS** | Il "regolamento di bordo". Le regole scritte su chi fa cosa in caso di emergenza. |

---

## 🔑 3. I 7 Pilastri della Sicurezza (Foundational Requirements)

| Icona | Pilastro | Domanda Fondamentale | Implementazione Tecnopack |
|---|---|---|---|
| 🔑 | **FR 1: Identificazione** | "Sei chi dici di essere?" | Accesso con password personali e codici univoci. Niente account anonimi. |
| 🚫 | **FR 2: Controllo Accessi** | "Cosa hai il permesso di fare?" | Ogni utente accede solo alla sua zona di lavoro. |
| ✅ | **FR 3: Integrità** | "Il programma è originale?" | Proteggiamo il software da modifiche non autorizzate. |
| 🔒 | **FR 4: Riservatezza** | "I dati sono segreti?" | Tunnel criptati (VPN) per le comunicazioni esterne. |
| 🧱 | **FR 5: Segmentazione** | "Se entra un virus, si diffonde?" | Zone isolate — un virus in un PC non arriva mai al PLC. |
| 🚨 | **FR 6: Monitoraggio** | "Me ne accorgo se succede?" | Ogni tentativo di accesso errato genera un allarme istantaneo. |
| 🔄 | **FR 7: Disponibilità** | "Possiamo ripartire subito?" | Backup automatici. Ripristino in pochi minuti. |

---

## 🛡 4. Security Level 2 (SL-2): Il Nostro Standard

Tecnopack progetta **esclusivamente per il livello SL-2**.

- **Cosa significa?** Proteggiamo la macchina da attacchi condotti da hacker opportunisti o dipendenti scontenti con mezzi comuni e risorse moderate.
- **Il valore:** Non costruiamo un bunker nucleare (SL-4), ma mettiamo porte blindate, allarmi e sorveglianza h24.

---

## 🧱 5. Architettura Logica: Zone e Condotti

- **Le Zone (Stanze):** La "Stanza Produzione" (VLAN 200) dove vivono i PLC e la "Stanza Manutenzione" (VLAN 300) per i tecnici. Sono separate e non si vedono tra loro.
- **I Condotti (Corridoi):** Gli unici passaggi autorizzati tra le stanze. Il corridoio OPC-UA (Porta 4840) permette al PLC di inviare i dati al cliente senza correre rischi.

---

## 👷 6. Impatto Pratico per Ruolo

**Per il Tecnico di Cablaggio**
- **Port Lock:** Non scambiare i cavi tra le porte dello switch. Se sbagli, la porta si blocca.
- **Selettore a Chiave:** Il Wi-Fi si attiva solo girando fisicamente la chiave sul quadro.

**Per il Software Engineer**
- **Captive Portal:** Login su pagina web dedicata. Sessione scade dopo 30 minuti di inattività.
- **Agnosticismo:** Lo scudo funziona con qualsiasi PLC (Omron, Rockwell, Siemens).

**Per il Project Manager e il Venditore**
- **Vantaggio Economico:** Con lo standard Lean (MikroTik) il cliente risparmia oltre **8.400 € in 5 anni**.
- **Fascicolo Tecnico:** La "Dichiarazione di Conformità" deve essere sempre firmata e consegnata.

---

## ✅ 7. Checklist Finale di Conformità

- [ ] **Firewall:** Regole "Deny-by-default" attive
- [ ] **VLAN:** Zona OT (200) e Zona Manutenzione (300) isolate
- [ ] **Autenticazione:** Captive Portal funzionante con timeout a 30 minuti
- [ ] **Port Lock:** MAC-Locking attivo su tutte le porte dello switch
- [ ] **Wi-Fi:** Selettore a chiave funzionante e attivo
- [ ] **Logging:** Eventi inviati correttamente alla Dashboard di monitoraggio
- [ ] **Dichiarazione:** Modello IEC 62443 compilato e firmato

---

> *Dipartimento OT Security — Tecno Pack S.p.A. — La sicurezza è una responsabilità di tutti.*

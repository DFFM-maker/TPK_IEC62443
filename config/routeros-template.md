---
id: routeros-template
title: RouterOS Configuration Template v1.4
sidebar_label: RouterOS Template v1.4
sidebar_position: 1
description: Template MikroTik RouterOS per IEC 62443 SL-2 — RB5009 / hEX S
---

# RouterOS Configuration Template v1.4

| Hardware | MikroTik RouterOS (RB5009 / hEX S) |
|---|---|
| **Target** | IEC 62443 SL-2 |
| **Fix v1.4r1** | Aggiunto `in-interface=VLAN300_Maintenance` su INPUT per manutentori (chiude vettore da WAN/VLAN200) |

---

## 1. Identità Dispositivo

```bash
/system identity set name=TecnoPack-Master-001
```

---

## 2. VLAN e Bridge

```bash
/interface bridge add name=bridge1 vlan-filtering=yes

/interface vlan
add interface=bridge1 name=VLAN200_Supervision  vlan-id=200
add interface=bridge1 name=VLAN300_Maintenance  vlan-id=300

/ip address
add address=172.16.224.1/24 interface=VLAN200_Supervision
add address=10.0.30.1/24    interface=VLAN300_Maintenance
```

---

## 3. Firewall — Chain INPUT (SR 3.3 / SR 4.4)

```bash
/ip firewall filter

add chain=input connection-state=established,related action=accept \
    comment="INPUT: Accept established/related"

add chain=input connection-state=invalid action=drop \
    comment="INPUT: Drop invalid"

add chain=input in-interface=ether1_WAN action=drop \
    comment="INPUT: Block ALL from WAN (SR 4.4)"

add chain=input in-interface=VLAN200_Supervision action=drop \
    comment="INPUT: Block management from PLC zone"

add chain=input \
    src-address-list=authorized_maintenance \
    in-interface=VLAN300_Maintenance \
    protocol=tcp dst-port=22,8729 \
    action=accept \
    comment="INPUT: Allow SSH/API to authenticated techs on VLAN300 (SR 1.1)"

add chain=input action=drop \
    comment="INPUT: Default Deny (SR 4.4)"
```

---

## 4. Firewall — Chain FORWARD (SR 5.1 / SR 5.2)

```bash
add chain=forward connection-state=established,related action=accept \
    comment="FORWARD: Accept established/related"

add chain=forward \
    dst-address=172.16.224.11 dst-port=4840 protocol=tcp \
    in-interface=ether1_WAN \
    action=accept \
    comment="FORWARD: Conduit MES->PLC OPC-UA (SR 5.2)"

add chain=forward \
    src-address-list=authorized_maintenance \
    out-interface=VLAN200_Supervision \
    action=accept \
    comment="FORWARD: RBAC techs -> PLC zone (SR 1.1 / SR 2.1)"

add chain=forward action=drop \
    comment="FORWARD: Default Deny (SR 5.2)"
```

---

## 5. NAT — Topology Hiding (SR 4.1)

```bash
/ip firewall nat
add chain=dstnat \
    dst-address=192.168.250.225 dst-port=4840 protocol=tcp \
    action=dst-nat to-addresses=172.16.224.11 to-ports=4840 \
    comment="NAT: OPC-UA alias -> PLC Master (Topology Hiding)"
```

---

## 6. Hotspot & RBAC (SR 1.1 / SR 2.1)

```bash
/ip hotspot profile
add name=TP_Profile hotspot-address=10.0.30.1 use-radius=no

/ip hotspot user profile
add name=tech \
    address-list=authorized_maintenance \
    session-timeout=4h idle-timeout=30m keepalive-timeout=none \
    comment="RBAC: max 4h, idle 30m (SR 2.1)"

/ip hotspot
add interface=VLAN300_Maintenance name=Hotspot_TP profile=TP_Profile
```

---

## 7. Hardening Servizi

```bash
/ip service
set telnet disabled=yes
set ftp    disabled=yes
set www    disabled=yes
set api    disabled=yes
set winbox disabled=yes
set api-ssl certificate=dashboard_cert disabled=no
```

---

## 8. Logging & NTP (SR 2.8 / SR 6.1 / SR 2.9)

```bash
/system logging action
add name=Dashboard target=remote remote=172.16.224.50 \
    comment="Syslog -> Dashboard Tecnopack (SR 2.8)"

/system logging
add action=Dashboard topics=firewall,account,critical,info

/system ntp client set enabled=yes
/system ntp client servers add address=192.168.250.1

/system ntp server set enabled=yes broadcast=no multicasting=no \
    comment="NTP server locale per PLC/HMI (SR 2.9)"
```

---

## 9. Port Lock CSS610 (SR 7.8)

:::warning WebUI su ogni switch periferico
Tab `System` → `Static Hosts` → aggiungere MAC di ogni PLC/HMI
con opzione **"Lock on Unknown MAC"** e azione **"Drop"**
:::

---

## Mappa SR Coperti

| SR | Misura | Sezione |
|---|---|---|
| SR 1.1 | Hotspot + address-list | §6 |
| SR 2.1 | RBAC FORWARD via address-list | §6 |
| SR 2.8 | Syslog centralizzato | §8 |
| SR 2.9 | NTP server locale | §8 |
| SR 4.1 | NAT Topology Hiding | §5 |
| SR 4.4 | api-ssl ON, telnet/www/winbox OFF | §7 |
| SR 5.2 | Default Deny FORWARD + OPC-UA conduit | §4 |
| SR 7.8 | MAC Locking CSS610 | §9 |

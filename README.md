# 🌐 Projet Réseau Segmenté avec VLANs et Routage Statique

## 📖 Présentation générale
Ce projet consiste à concevoir, configurer et valider un **réseau d’entreprise segmenté**
en utilisant des **VLANs**, le **routage inter-VLAN (Router-on-a-Stick)**,
l’**agrégation de liens EtherChannel (LACP)** et le **routage statique** entre plusieurs sites.

L’objectif principal est de mettre en œuvre une infrastructure réseau **structurée,
sécurisée et évolutive**, tout en respectant les bonnes pratiques professionnelles.

Le projet a été réalisé à l’aide de **Cisco Packet Tracer** dans un contexte pédagogique
(formation réseaux / CCNA).

---

## 🎯 Objectifs du projet
- Segmenter le réseau en plusieurs VLANs
- Mettre en place le routage inter-VLAN
- Optimiser la liaison entre switchs avec EtherChannel
- Interconnecter des sites distants via routage statique
- Tester et valider la connectivité de bout en bout
- Documenter le projet pour publication sur GitHub

---

## 🏗️ Topologie du réseau

### 📌 Équipements utilisés
| Type | Nom | Rôle |
|-----|-----|-----|
| Switch | S1 | Switch principal (accès utilisateurs) |
| Switch | S2 | Switch secondaire |
| Routeur | R1 | Routage inter-VLAN + cœur du réseau |
| Routeur | R2 | Site distant PC7 |
| Routeur | R3 | Site distant PC8 |
| PC | PC1–PC6 | Utilisateurs VLANs |
| PC | PC7 | Site distant 1 |
| PC | PC8 | Site distant 2 |

---

## 🧩 VLANs configurés

| VLAN ID | Nom | Réseau | Masque | Passerelle |
|-------|------|--------|--------|-----------|
| 10 | Utilisateurs_A | 172.18.10.0 | 255.255.255.240 | 172.18.10.14 |
| 20 | Utilisateurs_B | 172.18.20.0 | 255.255.255.240 | 172.18.20.14 |
| 30 | Utilisateurs_C | 172.18.30.0 | 255.255.255.240 | 172.18.30.14 |
| 50 | VLAN Natif | 172.18.50.0 | 255.255.255.240 | 172.18.50.14 |
| 60 | Administration | 172.18.60.0 | 255.255.255.240 | 172.18.60.14 |

📌 La **dernière adresse IP** de chaque réseau est utilisée comme **passerelle**.

---

## 🌍 Plan d’adressage WAN (Sites distants)

| Lien / Réseau | Adresse réseau | Masque | IP Routeur |
|---------------|--------------|--------|-----------|
| PC8 LAN | 10.0.30.128 | /27 | R3: 10.0.30.158 |
| PC7 LAN | 10.0.30.160 | /28 | R2: 10.0.30.174 |
| R1 ↔ R2 | 10.0.30.176 | /30 | R1: .177 / R2: .178 |
| R1 ↔ R3 | 10.0.30.180 | /30 | R1: .181 / R3: .182 |
| R2 ↔ R3 | 10.0.30.184 | /30 | R2: .185 / R3: .186 |

---

## 🔧 Technologies et concepts utilisés
- VLAN (Virtual LAN)
- Trunk 802.1Q
- EtherChannel (LACP)
- Router-on-a-Stick
- Routage statique
- Cisco IOS
- Cisco Packet Tracer

---

## 🛠️ Étapes de réalisation
1. Analyse du besoin et planification IP
2. Création et configuration des VLANs
3. Affectation des ports en mode access
4. Mise en place d’un EtherChannel entre S1 et S2
5. Configuration des trunks (VLAN natif 50)
6. Configuration du routage inter-VLAN sur R1
7. Configuration des interfaces WAN
8. Mise en place du routage statique
9. Tests et validation de la connectivité

---

## ✅ Tests de validation
- Ping entre VLANs
- Ping VLAN → site distant (PC7)
- Ping site distant (PC8) → VLAN
- Accès aux interfaces de gestion des switchs (VLAN 60)

Tous les tests confirment une **connectivité complète et stable**.


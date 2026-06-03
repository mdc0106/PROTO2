# 🎮 Hub de Gestion Connecté : Minecraft, Node-RED & Discord (Raspberry Pi 5)

## 📝 Présentation
Ce projet consiste à créer un écosystème interconnecté autour d'un serveur **Minecraft** hébergé sur un **Raspberry Pi 5**. Via **Node-RED**, le serveur interagit en temps réel avec une interface web (**Dashboard**), **Discord** et le kit physique **Digilab**, qui intègre un **ruban de LEDs RVB adressables WS2812** contrôlé directement par les broches GPIO du Pi 5.

---

## 💡 Fonctionnalités Majeures & Animations LEDs

### 1. 🎟️ Système de Support / Tickets (Minecraft ⇄ Discord ⇄ Digilab)
*Un système d'assistance automatisé avec notification visuelle dans le monde réel.*
* Un joueur tape `!report [Message]` dans le tchat Minecraft.
* Node-RED intercepte le message, l'affiche sur le Dashboard et **crée automatiquement un salon privé** sur Discord (ex: `#ticket-joueurXYZ`) pour les admins.
* **Effet LED WS2812 :** Le ruban de LEDs s'allume en **Orange avec un effet de respiration (pulsation)** pour alerter l'administrateur qu'un ticket est en attente. Il redevient **Vert** dès que le ticket est fermé.

### 2. 🚨 Alerte d'Intrusion ou d'Événement (Virtuel ⇄ Physique)
* Si un joueur entre dans une zone interdite sur Minecraft (ou si un raid commence), Node-RED déclenche les alertes :
  * **Digilab :** Le ruban de LEDs WS2812 flash en **Rouge et Bleu (effet gyrophare de police)**.
  * **Discord / Dashboard :** Envoi d'une notification d'urgence instantanée aux admins.

### 3. 🌤️ Miroir du Cycle Jour/Nuit (Minecraft ⇄ Digilab)
* Node-RED suit en temps réel l'heure virtuelle du serveur Minecraft.
* **Effet LED WS2812 :** Le ruban de LEDs imite l'ambiance du jeu dans la pièce réelle. Il s'allume en **Blanc/Jaune éclatant** pendant le jour Minecraft, passe au **Orange chaud** au coucher du soleil, et devient **Bleu nuit foncé** durant la nuit du jeu.

### 4. 📊 Jauge Matérielle du Raspberry Pi 5
* Le Dashboard Web affiche l'utilisation CPU, RAM et la température du Raspberry Pi 5.
* **Effet LED WS2812 :** Une partie du ruban sert de jauge physique de température. Si le Pi 5 est à bonne température, les LEDs restent **Vertes**. Si le processeur chauffe ou est surchargé, la jauge passe dynamiquement au **Jaune**, puis au **Rouge fixe**.

---

## 🛠️ Technologies & Plugins utilisés
* **Matériel :** Raspberry Pi 5 + Kit Digilab avec **ruban de LEDs WS2812**.
* **Orchestration Node-RED :** * `@tomsith/node-red-contrib-ws2812-pi5` (Contrôle direct des LEDs via GPIO du Pi 5).
  * `node-red-dashboard` (Interface Web de contrôle).
* **Serveur Jeu :** Minecraft (Spigot/Paper) + Plugins de Tom (WebSockets / RCON).
* **Communication :** API Bot Discord (`node-red-contrib-discord-advanced`).

---

## 📅 Planning Express (Objectif 3 Semaines)
* **Semaine 1 :** Installation du Pi 5, du serveur Minecraft et configuration de base du ruban de LEDs WS2812 avec le nœud de Tom.
* **Semaine 2 :** Création du Dashboard Web et codage des premières animations de LEDs (Jour/Nuit et jauge CPU).
* **Semaine 3 :** Intégration du Bot Discord, logique du système de tickets et tests finaux pour la démonstration.


EN version

# 🎮 Connected Management Hub: Minecraft, Node-RED & Discord (Raspberry Pi 5)

## 📝 Overview
This project builds an interconnected ecosystem around a **Minecraft** server hosted on a **Raspberry Pi 5**. Using **Node-RED** as the core orchestrator, the game interacts in real-time with the physical world (**Digilab** kit), a web interface (**Dashboard**), and **Discord**.

---

## 💡 Key Features

### 1. 🎟️ Automated Support Ticket System (Minecraft ⇄ Discord)
*A professional-grade helpdesk system built for server management.*
* A player types `!report [Message]` in the Minecraft in-game chat.
* Node-RED intercepts the text and **automatically creates a private Discord channel** (e.g., `#ticket-playerXYZ`) for the admin team.
* A physical LED lights up on the Digilab as long as a ticket remains open.

### 2. 🚨 Intrusion Alert System (Virtual ⇄ Physical)
* If a player enters a restricted area inside Minecraft, Node-RED triggers immediate alerts:
  * **Digilab:** The physical buzzer sounds and a red LED blinks.
  * **Discord / Dashboard:** Direct emergency notifications are pushed to the admins.

### 3. 🌤️ Environmental Syncing (Digilab ⇄ Minecraft)
* Physical sensors directly influence the game environment.
* If the Digilab light sensor detects darkness in the real room (or is covered), Node-RED instantly forces night-time inside Minecraft (`/time set night`).

### 4. 📊 Monitoring & Control Dashboard
* A web interface to track the Raspberry Pi 5's live CPU load, RAM usage, and temperature.
* Displays online players and includes quick-action admin buttons (Kick, Change Weather, Restart Server).

---

## 🛠️ Tech Stack
* **Hardware:** Raspberry Pi 5 + Digilab Kit (LEDs, Buzzer, Sensors).
* **Software:** Node-RED (Orchestration & Dashboard UI).
* **Game Server:** Minecraft (Spigot/Paper) + RCON/Websockets protocol.
* **Communication:** Discord Bot API.

---

## 📅 Express Roadmap (3-Week Target)
* **Week 1:** Raspberry Pi 5 setup, Minecraft server deployment, and core Node-RED connectivity.
* **Week 2:** Web Dashboard UI design and Digilab hardware sensor/LED integration.
* **Week 3:** Discord Bot API implementation, ticket system logic coding, and final testing.
* 

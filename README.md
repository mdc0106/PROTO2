# 🎮 Hub de Gestion Connecté : Minecraft, Node-RED & Discord (Raspberry Pi 5)

## 📝 Présentation du Projet
Ce projet consiste à concevoir et déployer un écosystème interconnecté complet autour d'un serveur **Minecraft** hébergé sur un **Raspberry Pi 5**. Grâce à **Node-RED**, le serveur interagit en temps réel avec le monde physique (via le kit **Digilab**), une plateforme de communication externe (**Discord**), et une interface d'administration Web (**Dashboard**).

L'objectif est de lier le virtuel et le réel tout en développant une solution de supervision et de contrôle de niveau professionnel.

---

## 💡 Fonctionnalités Majeures

### 1. 🎟️ Système de Support / Tickets (Minecraft ⇄ Discord ⇄ Écran LCD)
*Un système d'assistance automatisé avec suivi textuel sur le matériel réel.*
* **Scénario :** Un joueur rencontre un problème en jeu et tape la commande `!report [son message]` dans le tchat Minecraft.
* **Automatisation :** Node-RED intercepte le message, l'envoie sur le Dashboard et **crée automatiquement un salon textuel privé dédié** sur Discord (ex: `#ticket-joueurXYZ`) pour l'équipe d'administration.
* **Action Digilab :** L'**écran LCD 16x2** affiche instantanément une alerte physique (Ligne 1 : `⚠️ NOUVEAU TICKET`, Ligne 2 : `Par: [Nom]`). Un voyant connecté sur une broche GPIO reste allumé tant que le ticket n'est pas résolu.

### 2. 🛡️ Surveillance de la Zone Sécurisée / Safe Zone (Virtuel ⇄ Physique)
*Suivi en temps réel des mouvements des joueurs dans les zones protégées (Spawn, zone de commerce, etc.).*
* **Scénario :** Lorsqu'un joueur pénètre dans la **Safe Zone** définie sur la carte Minecraft, Node-RED détecte immédiatement le déclencheur.
* **Action Digilab :** L'écran LCD 16x2 affiche en direct l'arrivée (ex: `🟢 EN SAFE ZONE:` / `[NomDuJoueur]`). Une LED verte s'allume ou un court signal sonore (buzzer) retentit via les broches GPIO pour indiquer une entrée pacifique.
* **Discord & Dashboard :** Le bot met à jour le statut du serveur et enregistre le log dans le salon de suivi des administrateurs.

### 3. 🌤️ Statut du Serveur en Direct sur l'Écran LCD
*Surveillance du serveur directement sur le boîtier physique du Raspberry Pi 5.*
* En temps normal, l'écran LCD 16x2 alterne l'affichage de deux blocs d'informations clés toutes les quelques secondes :
  * L'heure virtuelle et la météo actuelle de Minecraft (ex: `Minecraft: Jour` / `Météo: Soleil`).
  * Le nombre de joueurs connectés (ex: `Joueurs en ligne:` / `3 joueurs`).

### 4. 📊 Interface Web d'Administration (Dashboard)
*Une console d'administration complète et interactive pour gérer le serveur à distance sans toucher au terminal.*
* **Visualisation des données en direct :** * Compteur et liste nominative des joueurs actuellement connectés.
  * **Uptime (Time On) :** Durée d'activité en continu du serveur Minecraft et du Raspberry Pi 5 depuis leur dernier démarrage.
  * Télémétrie hardware : Graphiques d'utilisation CPU, RAM et température du Pi 5 (accessible sur l'écran LCD via un bouton poussoir GPIO).
* **Boutons d'action rapides (Commandes RCON) :**
  * **Kick / Ban :** Un menu déroulant permet de sélectionner un joueur en ligne pour l'exclure (Kick) ou le bannir définitivement (Ban) du serveur en un clic.
  * **Redémarrage (Restart) :** Un bouton sécurisé pour redémarrer proprement le serveur Minecraft à distance en cas de ralentissement.

---

## 🛠️ Architecture Technique & Plugins

* **Matériel :** Raspberry Pi 5 + Kit Digilab (Écran LCD 16x2, Boutons poussoirs, LEDs, Buzzer).
* **Orchestrateur Node-RED :**
  * `node-red-contrib-raspi5-lcd-16x2` (Pilote pour l'écran LCD sur Raspberry Pi 5).
  * `node-red-node-pi-gpio` (Gestion des broches d'entrées/sorties physiques du Pi 5).
  * `node-red-dashboard` (Conception de l'interface d'administration Web).
* **Serveur de Jeu :** Minecraft (Spigot/Paper) connecté à Node-RED via protocoles **RCON / WebSockets**.
* **Communication :** Bot Discord géré via l'API `node-red-contrib-discord-advanced`.

---

## 📅 Planning de Réalisation (Objectif 3 Semaines)

* **Semaine 1 : Fondations, Minecraft & Matériel**
  * Configuration du Raspberry Pi 5 et installation du serveur Minecraft.
  * Configuration de Node-RED et des nœuds `pi-gpio` et `lcd-16x2`.
  * Tests de l'affichage de texte fixe

## Version EN

# 🎮 Connected Management Hub: Minecraft, Node-RED & Discord (Raspberry Pi 5)

## 📝 Overview
This project builds an interconnected ecosystem around a **Minecraft** server hosted on a **Raspberry Pi 5**. Using **Node-RED** as the core orchestrator, the game interacts in real-time with a web interface (**Dashboard**), **Discord**, and the physical **Digilab** kit using a dedicated **16x2 LCD screen** and direct GPIO hardware controls.

The goal is to bridge the gap between virtual events and physical responses while creating a professional-grade server monitoring solution.

---

## 💡 Key Features

### 1. 🎟️ Support Ticket System (Minecraft ⇄ Discord ⇄ LCD Display)
*A professional-grade helpdesk system with real-time text notifications on physical hardware.*
* **Scenario:** A player encounters an issue in-game and types the `!report [message]` command in the Minecraft chat.
* **Automation:** Node-RED intercepts the message, displays it on the Web Dashboard, and **automatically creates a private Discord channel** (e.g., `#ticket-playerXYZ`) for the admin team.
* **Digilab Action:** The **16x2 LCD screen** instantly prints a physical alert (Line 1: `⚠️ NEW TICKET`, Line 2: `From: [Name]`). A physical status light triggered via GPIO stays lit until the ticket is resolved.

### 2. 🛡️ Safe Zone Monitoring (Virtual ⇄ Physical)
*Real-time tracking of players entering the server's protected area (Spawn, Marketplace, etc.).*
* **Scenario:** When a player enters the designated **Safe Zone** inside Minecraft, Node-RED immediately detects the event trigger.
* **Digilab Action:** The 16x2 LCD screen instantly outputs the arrival (e.g., `🟢 IN SAFE ZONE:` / `[PlayerName]`). It lights up a green status LED or emits a short chime (buzzer) via GPIO pins to indicate a peaceful entry.
* **Discord & Dashboard:** Logs the movement into the admin tracking channel and updates the web dashboard control grid.

### 3. 🌤️ Live Server Status on LCD Screen
*Monitor the server directly from the Pi 5 physical casing without an external monitor.*
* In normal conditions, the 16x2 LCD screen cycles through crucial game stats every few seconds:
  * In-game time and weather conditions (e.g., `Minecraft: Day` / `Weather: Clear`).
  * Total number of online players (e.g., `Players Online:` / `3 Players`).

### 4. 📊 Web Administration Control Center (Dashboard)
*A complete, interactive web console to manage the server remotely without ever opening a terminal.*
* **Live Data Visualization:**
  * **Online Players:** Real-time counter and guest list of currently connected players.
  * **Server Uptime (Time On):** Live tracker showing exactly how long the Minecraft server and the Pi 5 have been running since the last reboot.
  * Hardware Telemetry: Live charts for CPU load, RAM usage, and core temperature (also printable on the LCD via a physical GPIO push-button).
* **Quick Action Controls (via RCON):**
  * **Kick & Ban Buttons:** A dynamic dropdown menu to select an online player and instantly Kick or permanently Ban them with a single click.
  * **Server Restart:** A secured button (requiring confirmation) to safely and cleanly reboot the Minecraft server remotely if lag occurs.

---

## 🛠️ Tech Stack & Plugins

* **Hardware:** Raspberry Pi 5 + Digilab Kit (16x2 LCD Display, Push-buttons, LEDs, Buzzer).
* **Node-RED Orchestration:**
  * `node-red-contrib-raspi5-lcd-16x2` (Direct 16x2 LCD screen driver for Pi 5).
  * `node-red-node-pi-gpio` (Standard Raspberry Pi GPIO pin management).
  * `node-red-dashboard` (Web UI dashboard builder).
* **Game Server:** Minecraft (Spigot/Paper) connected via **RCON / WebSockets** protocols.
* **Communication:** Discord Bot API managed via `node-red-contrib-discord-advanced`.

---

## 📅 Express Roadmap (3-Week Target)

* **Week 1: Foundations, Minecraft & Hardware**
  * Raspberry Pi 5 setup and Minecraft server deployment.
  * Node-RED installation and configuration of `pi-gpio` and `lcd-16x2` nodes.
  * Basic testing by printing static text onto the LCD screen.
* **Week 2: Dashboard & Display Logic**
  * Web Dashboard UI design (CPU charts, player list, *Time On* calculation).
  * Programming the automated LCD display cycle (Weather, Players, Safe Zone status).
  * Integrating admin control buttons (Kick, Ban, Restart) via RCON.
* **Week 3: Discord Intelligence & Ticket System**
  * Creating and connecting the Discord Bot API with Node-RED.
  * Coding the backend logic for automatic channel creation on `!report`.
  * Intensive testing phase, bug hunting, and final project optimization.

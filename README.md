# 🐝 Organisation SemiSteria - BeeFootFlow

Bienvenue dans l'organisation **SemiSteria**, le centre de développement du projet **BeeFootFlow**, un système d'analyse connecté pour Baby-Foot.

Ce document présente une vue d'ensemble des différents dépôts (repositories) de l'organisation et explique comment lancer l'environnement de développement.

---

## 🎯 Le Projet : BeeFootFlow
**BeeFootFlow** est une solution IoT complète conçue pour digitaliser l'expérience du baby-foot. Le système utilise des capteurs ultrasons (ESP32) pour détecter les buts, calculer la vitesse de la balle en temps réel, et gérer un classement compétitif complet (MMR/Elo) via une plateforme web complète.

---

## 📂 Architecture des Dépôts

L'organisation contient de multiples dépôts principaux répartis en plusieurs catégories :

### 💻 Applications (Frontend & Backend)
* **`BeeFootFlow_Front`** : L'interface utilisateur Web. Développée en Vue.js 3 (Composition API) avec TypeScript et Vite.
* **`BeeFootFlow_Back`** : Le dépôt prévu pour le Backend (Node.js/Express). *(Note : Le dépôt semble actuellement vide ou non initialisé ici, le code pourrait être dans une autre branche ou hébergé ailleurs).*
* **`esp_Judge`** : Le code embarqué pour le microcontrôleur ESP32 (gestion des capteurs HC-SR04 et communication avec l'API / MQTT).

### 🗄️ Infrastructure & Données
* **`dataBase`** : Schémas et scripts d'initialisation PostgreSQL (`init.sql`). Inclut des Triggers PL/pgSQL automatisés pour le calcul du MMR/Elo à la fin des matchs.
* **`SMTP_server`** : Configuration du serveur mail de l'infrastructure.

### 🚀 Déploiement & GitOps (Kubernetes / ArgoCD)
L'infrastructure utilise massivement K3s, Helm et ArgoCD pour une approche GitOps :
* **`BeeFootFlow_Deploy`** & **`Test-Deploiement`** : Manifestes et configurations Kubernetes pour le déploiement des applications.
* **`postgres_deploiement`** : Fichiers YAML (manifestes Kubernetes) pour le déploiement de la base de données PostgreSQL.
* **`gitops-monitoring`** : Configuration du monitoring de l'infrastructure globale.
* **`security-vps`** : Scripts et configurations liés à la sécurisation du VPS hébergeant le cluster k3s.

### 📚 Documentation & Gestion de Projet
* **`Documentation`** : Documentation générale du projet et schémas d'architecture.
* **`comptesRendu`** : Suivi du projet et comptes-rendus des différentes étapes.
* **`semisteria-Challenge-48h`** : Dépôts liés au hackathon / Challenge Ynov 48h initiateur du projet.

---

## 🚦 Comment lancer l'application en développement ?

### 1. Frontend (`BeeFootFlow_Front`)
Le frontend est une application Vue.js propulsée par Vite.
```bash
# 1. Se rendre dans le sous-dossier contenant l'application Vue
cd BeeFootFlow_Front/frontend

# 2. Installer les dépendances Node.js
npm install

# 3. Lancer le serveur de développement
npm run dev
```
L'application sera accessible localement par défaut à l'adresse **`http://localhost:5173`**.

### 2. Backend & Base de données
* **Backend** : En attendant l'arrivée du code dans `BeeFootFlow_Back`, la stack prévoit normalement un backend Node.js classique associant `npm install` et `npm run dev`.
* **Base de données** : Le dépôt `dataBase` fournit la structure initiale. Pour développer localement, vous pouvez initialiser une instance PostgreSQL :
```bash
# Placer le terminal dans le dossier dataBase
cd dataBase

# Importer manuellement le schéma dans votre Postgres local
psql -U votre_utilisateur -d beefootflow_db -f init.sql
```

### 3. IoT (`esp_Judge`)
Le code C++/Arduino doit être téléversé sur le microcontrôleur ESP32 (via l'IDE Arduino ou PlatformIO). Assurez-vous d'avoir configuré les bons identifiants Wi-Fi et les URLs de la bonne API dans les fichiers sources avant le flash.

---
*Fichier généré pour structurer le dossier de l'organisation locale SemiSteria.*

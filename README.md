# 📬 InboxGuard - Action Service

Ce module est responsable d'exécuter automatiquement des **actions de sécurité** sur des emails, en fonction d'un **score de phishing** généré par un modèle d'IA.

Il fait partie du projet **InboxGuard**, un système complet de détection et réaction au phishing email.

---

## 🔧 Fonctionnement

Le script principal est écrit en **Bash**, et appelle un script **Python** (`imaplib`) pour interagir avec la boîte mail via **IMAP**.

En fonction du score IA attribué à chaque email, une action est déclenchée :

| Score (%)   | Action appliquée                |
|-------------|---------------------------------|
| 0–30%       | ✅ Aucun changement (`safe`)     |
| 31–60%      | ⚠️ Marqué comme important (`flag`) |
| 61–85%      | 🏷️ Déplacé dans `Suspect` (`tag`)  |
| 86–100%     | ❌ Déplacé dans `Spam` (`quarantine`) |

---

## 📂 Structure du module

action-service/
├── inboxguard_actions.sh # Script Bash principal
├── imap_action.py # Script Python pour actions IMAP
├── emails/ # Dossier de test local
├── quarantine/ # Dossier local pour simuler la quarantaine
├── logs/ # Fichier de log généré automatiquement
└── README.md # Ce fichier

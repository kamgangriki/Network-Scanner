# 🌐 Network-Scanner

Script PowerShell de scan réseau complet. Détecte toutes les machines actives sur un réseau local, analyse leurs ports ouverts et génère un rapport HTML professionnel avec identification des machines à risque.

> 💡 Projet développé dans le cadre de ma formation en Mastère 2 Architecte Système Réseau et Sécurité, pour simuler les audits réseau réalisés en entreprise.

---

## 📋 Fonctionnalités

| Fonctionnalité | Description |
|----------------|-------------|
| 🔍 **Scan réseau** | Détecte toutes les machines actives sur une plage IP |
| 📡 **Ping & latence** | Mesure le temps de réponse de chaque machine |
| 🏷️ **Résolution DNS** | Récupère le hostname de chaque machine |
| 🔒 **Scan de ports** | Vérifie les ports 21, 22, 80, 443, 445, 3306, 3389, 8080 |
| ⚠️ **Détection risques** | Identifie automatiquement les ports dangereux |
| 📊 **Rapport HTML** | Génère un rapport visuel complet en un clic |

---

## 📁 Structure du projet
Network-Scanner/
│
├── scripts/
│   └── Invoke-NetworkScan.ps1     # Script principal de scan
└── reports/
└── network-scan.html          # Rapport HTML généré automatiquement

---

## ⚙️ Prérequis

- Windows 10 / 11
- PowerShell 5.1 ou PowerShell 7+
- Droits administrateur recommandés
- Aucune dépendance externe — fonctionne nativement

---

## 🚀 Installation

```powershell
# Cloner le repo
git clone https://github.com/kamgangriki/Network-Scanner.git
cd Network-Scanner

# Autoriser l'exécution des scripts
Set-ExecutionPolicy -Scope CurrentUser -ExecutionPolicy RemoteSigned
```

---

## 📖 Utilisation

### Scan basique

```powershell
cd scripts
.\Invoke-NetworkScan.ps1
```

### Scan avec paramètres personnalisés

```powershell
# Scanner une plage spécifique
.\Invoke-NetworkScan.ps1 -Network "192.168.1" -StartIP 1 -EndIP 50

# Changer le réseau cible
.\Invoke-NetworkScan.ps1 -Network "10.0.0" -StartIP 1 -EndIP 254

# Spécifier un fichier de sortie
.\Invoke-NetworkScan.ps1 -Network "192.168.1" -OutputHtml "C:\rapports\scan.html"
```

**Résultat dans le terminal :**
=== Network Scanner ===
Réseau cible : 192.168.1.0/24
✅ 192.168.1.1 (router.local) — Latence: 2ms — Ports: 80, 443
✅ 192.168.1.10 (nas.local) — Latence: 5ms — Ports: 80, 443, 445
✅ 192.168.1.17 (SR) — Latence: 1ms — Ports: 80, 443, 3389
✅ 192.168.1.30 (desktop-rh.local) — Latence: 3ms — Ports: 3389, 445
✅ Machines trouvées : 6
✅ Rapport généré : ..\reports\network-scan.html
=== Scan terminé ! ===

---

## 📊 Aperçu du rapport HTML

Le rapport généré affiche :

- 📊 **4 cartes de statistiques** : machines détectées, avec ports ouverts, à risque, IPs scannées
- 🖥️ **Tableau complet** : IP, hostname, statut, latence, ports ouverts, niveau de risque
- 🟡 **Mise en évidence** des machines à risque (fond jaune)
- 🟢 **Badge "En ligne"** pour chaque machine détectée

### Ports surveillés comme dangereux

| Port | Service | Risque |
|------|---------|--------|
| 21 | FTP | Transfert non chiffré |
| 3389 | RDP | Accès distant exposé |
| 445 | SMB | Vulnérable aux ransomwares |
| 1433 | SQL Server | Base de données exposée |

---

## 🛠️ Technologies utilisées

![PowerShell](https://img.shields.io/badge/PowerShell-5391FE?style=for-the-badge&logo=powershell&logoColor=white)
![Windows](https://img.shields.io/badge/Windows-0078D6?style=for-the-badge&logo=windows&logoColor=white)
![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=for-the-badge&logo=html5&logoColor=white)
![Network](https://img.shields.io/badge/Network-Scanner-blue?style=for-the-badge&logo=cisco&logoColor=white)

---

## 🔮 Évolutions prévues

- [ ] Export du rapport en PDF
- [ ] Scan UDP en plus de TCP
- [ ] Détection du système d'exploitation (OS fingerprinting)
- [ ] Alertes email pour les ports à risque détectés
- [ ] Comparaison avec un scan précédent
- [ ] Interface graphique PowerShell (WPF)

---

## 👤 Auteur

**Riki Kamgang**
- 📧 rikikamgang@gmail.com
- 💼 [LinkedIn](https://linkedin.com/in/rikikamgang)
- 🐙 [GitHub](https://github.com/kamgangriki)
- 🎓 Mastère 2 Architecte Système Réseau et Sécurité — PMN Paris

---

## 📄 Licence

Ce projet est sous licence MIT — libre d'utilisation et de modification.

# AZ-400 - Section 030 : Design and Implement a Source Control Strategy

## 1. Understanding Source Control

### Définition
Les systèmes de contrôle de source sont essentiels pour permettre aux équipes de travailler conjointement sur le code, en suivant les modifications et en gérant les contributions efficacement.

### Rôle dans DevOps
- **Collaborative Coding** : Permettre à plusieurs équipes (Team A, B, C, D) de modifier et gérer le code
- **Codebase Snapshots** : Capturer l'état du projet à différents points dans le temps
- **Version Control** : Offrir un historique détaillé et la flexibilité de revenir à des états précédents
- **Risk Mitigation** : Protection contre les disruptions sévères ou erreurs progressives introduites par erreur humaine

---

## 2. Benefits of Source Control

### Streamlined Development Processes
- Création de workflows structurés
- Amélioration de l'efficience

### Version Management
- Facilite le travail avec différentes versions du code
- Garantit des transitions fluides et des points de référence clairs

### Enhanced Teamwork
- Pivot pour une collaboration d'équipe efficace
- Fournit un environnement de codage synchronisé

### Change Log
- Maintient un journal complet de tous les changements
- Chaque modification est tracée et accessible

### Task Automation
- Intégration avec des outils pour automatiser diverses tâches
- Augmente la productivité et réduit les erreurs

---

## 3. Best Practices pour Source Control

### 1. Incremental Updates
Effectuer des commits réguliers et petits plutôt que des gros changements monolithiques

### 2. Keep Personal Files Separate
Séparer les fichiers personnels du code partagé

### 3. Prevent Conflicts with Regular Updates
Synchroniser régulièrement avec le dépôt central pour éviter les conflits

### 4. Quality Assurance Pre-Push
Tester et valider le code avant de le pousser vers le dépôt partagé

### 5. Informative Commit Messages
Écrire des messages de commit clairs et descriptifs

### 6. Associate Changes with Tasks
Lier les commits aux work items ou tâches correspondantes

### 7. Collaboration Over Convention
Établir des conventions d'équipe et les suivre de manière cohérente

---

## 4. Types of Source Control Systems

### Centralized Source Control

**Caractéristiques :**
- Un seul repository central qui est le hub pour tout le code
- Les développeurs soumettent leurs modifications directement au hub central
- Les systèmes incluent : Team Foundation Version Control (TFVC), CVS, SVN, Perforce Helix Core

**Avantages :**
1. **Scalability** : Gère efficacement de grandes codebases
2. **Access Management** : Contrôle détaillé des permissions
3. **Usage Oversight** : Permet le suivi des interactions des utilisateurs avec le repository
4. **Exclusive Control** : Supporte le verrouillage de fichiers pour prévenir les éditions concurrentes

**Cas d'usage idéaux :**
- **Unified Code Repositories** : Idéal pour de grandes codebases singulières nécessitant l'uniformité
- **Detailed Oversight** : Fournit des pistes d'audit complètes et gestion d'accès au niveau fichier
- **Complex File Merging** : Adapté aux scénarios avec des types de fichiers difficiles à merger

---

### Distributed Source Control

**Caractéristiques :**
- Chaque développeur maintient sa propre copie complète du repository
- Chaque copie contient l'historique complet du projet
- Améliore l'autonomie individuelle et la redondance
- Exemples : Git, Mercurial

**Avantages clés :**
1. **Flexibility Across Environments** : Compatible avec divers systèmes d'exploitation
2. **Community-Centric Development** : Favorise la revue collaborative via pull requests, populaire dans l'open-source
3. **Full Functionality Offline** : Possibilité de travailler sans connexion internet
4. **History On-the-Go** : Permet de transporter l'historique complet du projet
5. **Growing Popularity** : Communauté d'utilisateurs en expansion rapide

**Cas d'usage idéaux :**
- **Efficient for Compact Codebases** : Idéal pour projets modulaires avec empreintes digitales plus petites
- **Open-Source Projects** : Encourage et supporte le modèle open-source
- **Remote Collaboration** : S'adapte bien aux équipes distribuées géographiquement
- **Cross-Platform Development** : Facilite les équipes opérant sur plusieurs plateformes
- **New Projects** : Excellent pour démarrer de nouveaux projets sans contraintes de code précédent

---

## 5. Git vs Team Foundation Version Control (TFVC)

### Git (Distributed)
- Approche décentralisée de la gestion du contrôle de source
- Les développeurs maintiennent le repository complet localement sur leurs systèmes

### TFVC (Centralized)
- Framework centralisé de contrôle de version
- Une seule version de chaque fichier sur les workstations

**Workspaces TFVC :**
- **Server workspace** : Fichiers checked out depuis un serveur central
- **Local workspace** : Copie personnelle de la dernière codebase pour travail offline

---

## 6. Selecting Git for Source Control - Reasons

### 1. Branching for Features
- Git facilite la création de branches dédiées pour de nouvelles features
- Isole le travail de développement de la codebase principale

```
Feature Branch
    ●——●
        ╲
Main     ●——●——●
```

### 2. Decentralized Repositories
- Git fournit à chaque développeur un repository de projet complet
- Supporte l'autonomie complète dans la gestion du code

### 3. Integration via Pull Requests
- Les développeurs peuvent demander de merger leurs feature branches dans la codebase principale via pull requests
- Sert également de plateforme pour code reviews et discussions

### 4. Collaboration With the Community
- La nature distribuée de Git encourage un environnement collaboratif
- Les contributions peuvent être facilement mergées de divers membres de la communauté

### 5. Feedback-Driven Releases
- Git supporte l'intégration et la livraison continues
- Permet des cycles de release réguliers incorporant le feedback rapidement et efficacement

---

## 7. Objections to Using Git

### 1. History Management
**Problème :** Les erreurs dans Git peuvent conduire à des problèmes de réécriture d'historique, causant potentiellement des disputes de code

**Mitigation :** 
- Établir des branch protection rules
- Utiliser des PR reviews obligatoires
- Former les équipes aux bonnes pratiques Git

### 2. Handling of Voluminous Files
**Problème :** Git est optimisé pour les repositories plus petits. Pour gérer de gros fichiers ou binaires, l'intégration de Git avec Large File Storage (LFS) est conseillée

**Solution :**
```bash
# Installer Git LFS
git lfs install

# Tracker les gros fichiers
git lfs track "*.psd"
git lfs track "*.mp4"
```

### 3. Educational Investment
**Problème :** La courbe d'apprentissage initiale pour Git peut être abrupte, nécessitant de la formation pour les nouveaux utilisateurs et potentiellement un upskilling pour les développeurs expérimentés

**Solution :**
- Investir dans la formation Git
- Créer de la documentation interne
- Utiliser des outils GUI pour simplifier les opérations courantes
- Établir des workflows standardisés

---

## 8. Demo: Working with Git Locally

### Commandes Git Essentielles

```bash
# Initialiser un repository
git init

# Cloner un repository existant
git clone <url>

# Vérifier le statut
git status

# Ajouter des fichiers au staging
git add <file>
git add .

# Committer les changements
git commit -m "Message descriptif"

# Voir l'historique
git log
git log --oneline --graph

# Créer une branche
git branch <branch-name>
git checkout -b <branch-name>

# Merger une branche
git checkout main
git merge <branch-name>

# Pousser vers remote
git push origin <branch-name>

# Récupérer les changements
git pull
```

---

## 9. Working With Azure Repos and GitHub

### Azure Repos Features
- **Development Environment Compatibility** : Options de connexion faciles pour diverses configurations de développement
- **Branch Security Policies** : Gestion policy-driven pour sauvegarder l'intégrité des branches
- **Version Control Variants Offered** :
  - **Git** : Modèle de contrôle distribué pour collaboration flexible
  - **TFVC** : Modèle de contrôle centralisé pour gestion stricte des versions

### GitHub Features

**1. End-to-End Automation**
- Rationalise les workflows du développement au déploiement

**2. Collective Security**
- Améliore les mesures de sécurité avec des efforts collaboratifs

**3. Effortless Code Reviews**
- Facilite des évaluations de code approfondies et faciles à gérer

**4. Unified Workspace**
- Consolide le code et sa documentation en un seul emplacement pour meilleure accessibilité

**5. Synchronization**
- Synchronise sans effort les activités à travers diverses facettes du projet

**6. Team Management**
- Fournit des outils pour organisation et coordination efficaces d'équipe

---

## 10. Transitioning From TFVC to Git

### Approches de Migration

#### 1. Branch-Level Migration (Tip Migration)
**Approche :**
- Initier le mouvement avec un transfert de branche unique vers Git
- Transfère seulement l'itération de code la plus récente
- L'enregistrement historique reste accessible sur le serveur original

**Avantages :**
- Migration rapide et simple
- Pas besoin de convertir tout l'historique
- Bon pour fresh starts

#### 2. Comprehensive Sync With Git-TFS (Full History Transfer)
**Approche :**
- Utiliser git-tfs pour une migration à échelle complète
- Maintient la cohérence entre les historiques TFVC et Git
- Vise à répliquer l'historique des versions dans Git

**Commandes git-tfs :**
```bash
# Installer git-tfs
choco install gittfs

# Cloner un repository TFVC
git tfs clone http://tfs:8080/tfs/DefaultCollection $/Project

# Synchroniser les changements
git tfs pull
```

**Avantages de la migration Tip uniquement :**
- La migration est simplifiée car TFVC capture des changesets, tandis que Git préserve des snapshots
- Les structures de branchement varient : TFVC applique un branchement basé sur dossiers, tandis que le branchement de Git englobe le repository complet
- Rend une simple migration tip plus pratique

---

## 11. Innovating With GitHub Codespaces

### Définition
GitHub Codespaces est un environnement de développement cloud hébergé par GitHub.

### Caractéristiques Clés

**1. Eliminates Legacy Limitations**
- Contourner les défis associés à une infrastructure ou logiciel obsolète
- Passage à un environnement de développement cloud

**2. Enhanced Flexibility**
- Liberté de coder de n'importe où grâce à la portabilité du cloud

**3. Safeguards for Creativity**
- Fonctionnalités de sécurité robustes pour prévenir la diffusion non autorisée de code propriétaire

**4. Familiar IDE Experience**
- Interface basée sur Visual Studio Code
- Transition transparente

**5. Device Agnostic**
- Accès depuis une large gamme d'appareils : PCs, tablets, Chromebooks

**6. Direct Integration**
- Lier votre Visual Studio Code local avec Codespaces pour une expérience de codage intégrée

### Configuration Codespaces

```yaml
# .devcontainer/devcontainer.json
{
  "name": "My Project",
  "image": "mcr.microsoft.com/devcontainers/typescript-node:18",
  "features": {
    "ghcr.io/devcontainers/features/azure-cli:1": {}
  },
  "customizations": {
    "vscode": {
      "extensions": [
        "ms-azuretools.vscode-azurefunctions"
      ]
    }
  }
}
```

---

## 12. Points Clés pour l'Examen AZ-400

### Source Control Strategy doit inclure :
1. ✅ Choix entre centralisé (TFVC) vs distribué (Git)
2. ✅ Branch strategy claire (GitFlow, GitHub Flow, trunk-based)
3. ✅ Code review process avec pull requests
4. ✅ Branch protection policies
5. ✅ Integration avec CI/CD pipelines
6. ✅ Gestion des secrets et fichiers sensibles (.gitignore)

### Scénarios d'Examen Typiques :
- **"L'équipe travaille avec de gros fichiers binaires"** → Git LFS
- **"Migration depuis TFVC"** → Considérer tip migration vs full history
- **"Équipe distribuée géographiquement"** → Git (distributed)
- **"Besoin de file locking"** → TFVC ou Git LFS avec locking
- **"Open source project"** → Git + GitHub
- **"Environnement de dev standardisé"** → GitHub Codespaces

### Commandes Git Essentielles à Connaître :
```bash
git clone, git add, git commit, git push, git pull
git branch, git checkout, git merge
git rebase, git cherry-pick
git stash, git reset, git revert
```

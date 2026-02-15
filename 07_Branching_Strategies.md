# AZ-400 - Section 050 : Planning and Implementing Branching Strategies for Source Code

## 1. Monorepo vs Multiple Repos - Comparative Analysis

### Définitions

**Monorepo (Monolithic Repository)**
- Version control strategy qui centralise tout le code source dans un seul repository
- Inclut tout le code, libraries, et fichiers de configuration pour différentes applications et services
- Les équipes travaillent dans le même repository mais peuvent organiser le code en répertoires séparés
- Tous les projets partagent un historique de version commun
- Tout le code coexiste dans un seul repository

**Multiple Repositories Structure**
- Le code est divisé en repositories indépendants pour différents segments de projet
- Chaque repository est dédié à des segments de projet spécifiques
- Gestion de code complètement indépendante
- Gestion modulaire des dépendances
- Pipelines CI/CD isolés
- Contrôle de version décentralisé

---

## 2. Monorepo - Avantages et Inconvénients

### Avantages du Monorepo

#### 1. Easier Code Sharing
- Tout est au même endroit
- Simple pour les membres de l'équipe d'accéder et collaborer sur le code
- Partage de code facilité entre projets

#### 2. Consistent Code Style
- Tout le monde travaille dans le même repository
- Plus facile d'appliquer les standards de codage à travers toute la codebase
- Style uniforme garanti

#### 3. Simplified Dependency Updates
- Mise à jour des dépendances à travers tout le projet en une fois
- Pas besoin de mettre à jour plusieurs repositories séparément
- Cohérence des versions de dépendances

#### 4. Easier Refactoring
- Changements massifs à travers toute la codebase
- Pas besoin de coordonner les mises à jour à travers plusieurs repos
- Vision globale facilitée

#### 5. Unified CI/CD Process
- Un seul pipeline pour build, test, et déploiement du code
- Workflow simplifié
- Configuration centralisée

---

### Inconvénients du Monorepo

#### 1. Large Repo Size
- La codebase peut devenir très large
- Plus difficile à gérer au fur et à mesure de la croissance
- Performance potentiellement impactée

#### 2. Complex Access Control
- Tout est au même endroit
- Difficile de définir des permissions granulaires pour différentes parties de la codebase
- Gestion des accès plus complexe

#### 3. Risk of Merge Conflicts
- Beaucoup de personnes travaillent dans le même repository
- Probabilité augmentée de changements conflictuels
- Coordination d'équipe nécessaire

#### 4. Slower Build Times
- Au fur et à mesure que le repository grandit
- Builder toute la codebase peut prendre plus de temps
- Impact sur la productivité

#### 5. Harder to Scale
- Gérer un large repository unique requiert planification et ressources soigneuses
- Complexité croissante avec la taille
- Tooling spécifique souvent nécessaire

---

## 3. Multiple Repos - Avantages et Inconvénients

### Avantages des Multiple Repos

#### 1. Modular Development
- Chaque projet ou service peut être développé indépendamment
- Flexibilité accrue
- Isolation des changements

#### 2. Granular Access Control
- Permissions spécifiques pour chaque repository
- Contrôle précis sur qui peut accéder et modifier différentes parties de la codebase
- Sécurité renforcée

#### 3. Independent CI/CD
- Chaque repository peut avoir son propre pipeline CI/CD
- Les changements dans un repo n'affectent pas les build/deployment des autres
- Déploiements indépendants

#### 4. Faster Builds
- Chaque repo est plus petit et plus focalisé
- Build times généralement plus rapides comparés à un large monorepo
- Feedback loops plus courts

#### 5. Easier Scaling
- Ajout et gestion de repositories au fur et à mesure de la croissance des projets
- Approche de développement plus scalable
- Distribution de la charge

---

### Inconvénients des Multiple Repos

#### 1. Complex Dependency Management
- Garder la trace des dépendances à travers plusieurs repositories
- Coordination soigneuse nécessaire
- Risque de versions incompatibles

#### 2. Inconsistent Code Styles
- Différentes équipes travaillent dans des repos séparés
- Maintenir un style de code uniforme à travers les projets peut être difficile
- Standards potentiellement divergents

#### 3. Duplication of Effort
- Fonctionnalités similaires peuvent être implémentées plusieurs fois
- Redondance à travers différents repositories
- Waste de ressources

#### 4. Complicated Integration
- Rassembler le code de plusieurs repositories pour une application unifiée
- Peut être challengeant et time-consuming
- Complexité d'orchestration

#### 5. Multiple CI/CD Pipelines
- Chaque repository requiert son propre pipeline
- Overhead accru pour setup et maintenance
- Duplication de configuration

---

## 4. Choosing the Right Approach

### Facteurs de Décision

#### 1. Project Size and Complexity
**Question :** Est-ce une petite app ou un système enterprise massif ?
- Plus le projet est grand et complexe, plus de structure peut être nécessaire dans la stratégie de branching

#### 2. Team Size and Structure
**Question :** Êtes-vous un petit groupe de 5, ou étalés sur plusieurs départements ?
- La taille et structure de l'équipe peut vraiment influencer quelle approche fonctionnera le mieux

#### 3. Dependency Management Needs
**Question :** Comment est enchevêtré votre web de libraries et frameworks ?
- Certaines stratégies gèrent mieux la gestion des dépendances que d'autres

#### 4. Build and Deployment Requirements
**Question :** À quelle fréquence poussez-vous de nouvelles versions ? Daily ? Weekly ?
- Votre cycle de release peut aider à déterminer la meilleure approche de branching

#### 5. Long-term Maintenance
**Question :** Quelle stratégie facilitera votre vie à long terme ?
- Vous voulez une stratégie qui facilitera la maintenance future, pas qui donnera des maux de tête à chaque mise à jour

---

### Points Clés à Retenir

**01 - Understanding Repositories**
- Les repositories servent de place pour stocker l'historique de votre travail
- Ce n'est pas juste stocker le code qui compte, mais tracker les changements

**02 - Flexibility in Azure DevOps**
- Azure DevOps projects peuvent être organisés comme monorepos ou multiple repos
- S'aligne avec diverses stratégies organisationnelles

**03 - Deciding Factor**
- Votre choix devrait ultimement supporter la vélocité et collaboration de votre équipe
- C'est le grand facteur décisif

---

## 5. Creating an Effective Change Log

### Purpose of a Change Log

Un Change Log monitore l'évolution d'un projet en documentant les mises à jour spécifiques à chaque version :

**01 - Addition of New Features**
- Nouvelles fonctionnalités ajoutées

**02 - Modifications to Existing Features**
- Modifications apportées aux fonctionnalités existantes

**03 - Deletion of Outdated Features**
- Suppression de fonctionnalités obsolètes

---

### Best Practices pour Change Logs

#### 1. Clarity Over Quantity
- Viser la clarté plutôt que la quantité
- Un log verbeux peut être contre-productif

#### 2. A Well-Curated Log
- Concis et libre d'entrées superflues
- Facile à lire et comprendre

---

### Strategies for Change Log Generation

#### 1. Manual Entries
- Entrées manuelles pour clarté sur mesure
- Contrôle total sur le contenu

#### 2. Automated Population
- Population automatisée pour l'efficacité
- Utilisation d'outils comme `git log`

#### 3. Hybrid Methods
- Méthodes hybrides combinant automation avec supervision personnelle
- Balance entre efficacité et qualité

---

### Tools to Assist

#### 1. Standard git log
**Usage :** Entrées direct en ligne de commande
```bash
git log
```

#### 2. gitchangelog and github_changelog_generator
**Usage :** Solutions automatisées
```bash
# Installer gitchangelog
pip install gitchangelog

# Générer changelog
gitchangelog > CHANGELOG.md
```

---

### Command for Automation

```bash
git log --pretty=format:"%h - %s (%an, %ar)" v1.2.0..v1.3.0 | script-to-format-changelog > projectchangelogs/1.3.0.md
```

**Explication des paramètres :**
- `--pretty=format:"%h - %s (%an, %ar)"` : Customise la sortie du log pour montrer le commit hash, description, nom d'auteur, et date relative d'auteur
- `v1.2.0..v1.3.0` : Spécifie la plage de tags à comparer
- `script-to-format-changelog` : Placeholder pour votre script actuel qui formate le changelog
- `projectchangelogs/1.3.0.md` : Le chemin où le changelog pour la version 1.3.0 sera sauvegardé, en format markdown pour lisibilité

---

## 6. Types of Branch Workflows

### Dedicated Feature Branches

**Principe :**
Isoler le développement de nouvelles features dans des branches séparées, loin de la branche principale pour maintenir la stabilité.

**Workflow :**
```
Main ────●────●────●────●
              │         │
Little Feature│         │
        ●─────┘         │
                        │
Big Feature             │
            ●───●───●───┘
```

**Avantages :**
- Stabilité de la branche principale préservée
- Développement isolé
- Facilite les tests de features

---

### Forking Model

**Définition :**
Chaque contributeur opère sur sa copie du repository sur le serveur, assurant l'autonomie individuelle.

**Caractéristiques :**

#### 1. Personal Repository Space
- Le fork workflow alloue un repository server-side unique pour chaque développeur

#### 2. Dual Repository Setup
- Les contributeurs gèrent un duo de repositories :
  - Leur repository local privé
  - Un repository public sur le serveur

#### 3. Common in Open-Source
- Cette approche est un pilier dans les projets open-source
- Favorise la participation large

#### 4. Decentralized Contributions
- Permet de merger des contributions dans le projet principal
- Sans accès push direct à un repository central unique

**Workflow :**
```
Cloud Repository (Other's)
        │
        │ Fork
        ▼
Your Cloud Repository
        │
        │ Clone
        ▼
Local Repository
        │ Edit
        │
        │ Push
        ▼
Your Cloud Repository
```

---

### Branch Workflow Types - Considerations

Lors du choix d'un workflow de branching, considérer :

#### 1. Scalability
**Question :** Le workflow est-il adaptable au fur et à mesure que l'équipe s'étend ?
- Assurer que le workflow peut croître avec l'équipe

#### 2. Error Correction
**Question :** Quelle est la facilité de rectifier les erreurs dans le workflow ?
- Capacité de rollback et correction

#### 3. Cognitive Load
**Question :** Le workflow introduit-il de la complexité qui pourrait impacter l'efficacité de l'équipe ?
- Simplicité vs fonctionnalité

---

## 7. Navigating Feature Branch Workflow

### Le Processus en 6 Étapes

#### 01 - Branch Creation
**Action :** Commencer par établir une nouvelle branche spécifiquement pour la nouvelle feature, loin de la ligne de code main

**Commande :**
```bash
git checkout -b feature/new-feature
```

#### 02 - Committing Work
**Action :** Committer régulièrement vos changements à cette branche pour sauvegarder le progrès

**Commande :**
```bash
git add .
git commit -m "Implement new feature functionality"
```

#### 03 - Pull Request Initiation
**Action :** Quand prêt, créer une pull request comme proposition formelle pour intégration et plateforme pour feedback

**Process :**
- Push vers remote
- Ouvrir PR dans Azure DevOps ou GitHub
- Fournir description détaillée

#### 04 - Code Discussion
**Action :** Utiliser la pull request pour engager une révision détaillée et discussion des changements de code proposés

**Best Practices :**
- Reviews constructives
- Discussions techniques
- Suggestions d'amélioration

#### 05 - Code Deployment
**Action :** Déployer la feature pour testing dans un environnement isolé

**Environnements :**
- Dev environment
- Staging environment
- Integration testing

#### 06 - Integration/Merge
**Action :** Finalement, intégrer la feature dans la branche main, assurant aucune disruption à la codebase main

**Commande :**
```bash
git checkout main
git merge feature/new-feature
git push origin main
```

---

## 8. The GitHub Flow Process

### Processus Simplifié en 6 Étapes

**Caractéristique :** Reconnu pour sa simplicité, GitHub Flow est un workflow basé sur les branches qui est conçu pour être intuitif pour les contributeurs de tous niveaux techniques, pas exclusivement les développeurs.

#### 01 - Create New Branch
```bash
git checkout -b feature-name
```

#### 02 - Make Changes
```bash
git add .
git commit -m "Description of changes"
```

#### 03 - Initiate Pull Request
- Push vers repository remote
- Ouvrir PR pour review

#### 04 - Collaborate
- Discussion et review
- Feedback et itérations

#### 05 - Merge Your Pull Request
```bash
# Après approval
git checkout main
git merge feature-name
```

#### 06 - Delete Your Branch
```bash
git branch -d feature-name
git push origin --delete feature-name
```

---

## 9. Exploring Fork Workflow

### Caractéristiques du Fork Workflow

#### 1. Personal Repository Space
- Le fork workflow alloue un repository server-side unique pour chaque développeur

#### 2. Dual Repository Setup
- Les contributeurs gèrent un duo de repositories :
  - Leur repository local privé
  - Un repository public sur le serveur

#### 3. Common in Open-Source
- Approche pilier dans les projets open-source
- Favorise la participation large

#### 4. Decentralized Contributions
- Permet de merger des contributions dans le projet principal
- Sans accès push direct à un repository central unique

---

## 10. Collaborating With Pull Requests

### Le Processus en 3 Étapes

#### Branch Out
**Action :** Engager le développement de feature dans une branche dédiée et initier une pull request pour peer review

**Workflow :**
```bash
git checkout -b feature/improvement
# Make changes
git push origin feature/improvement
# Create PR
```

#### Collaborate
**Action :** Faciliter les conversations et consensus sur les changements proposés à travers l'interface de pull request

**Features :**
- Comments et discussions
- Code reviews
- Suggestions de changements
- Approval workflow

#### Merge
**Action :** Finaliser le processus en mergeant la branche reviewée facilement avec une simple action

**Options de Merge :**
- Merge commit
- Squash and merge
- Rebase and merge

---

### Enhancing Teamwork via Pull Requests

**Pull requests as communication tools**
- Servent de plateforme pour informer et discuter des altérations avec l'équipe

**The essence of shared development**
- Les pull requests sont centrales à l'esprit collaboratif dans le Shared Repository Model

**Code management best practices**
- Assurer d'offrir du feedback constructif
- Mettre en place des policy safeguards pour les branches

---

## 11. GitHub Mobile - Streamlining Pull Request Approvals on the Go

### Features

#### 01 - Rich Content Compatibility
Le mobile app affiche adeptement :
- Markdown
- Images
- PDFs
Pour une review de contenu comprehensive

#### 02 - Pull Request Management
- Superviser et gérer les pull requests avec facilité directement depuis l'app
- Notifications en temps réel

#### 03 - Interactive Communication
- Engager dans le processus de review en commentant sur les pull requests
- Utiliser emoji shortcodes pour feedback expressif
- Quick approvals

**Benefits :**
- Review et approval on-the-go
- Pas besoin d'être au bureau
- Faster feedback loops

---

## 12. Demystifying Git Hooks

### Définition

**Git Hooks** sont des scripts customizables qui s'exécutent automatiquement à des points spécifiques durant le workflow de Git, comme des triggers.

### Purpose and Power of Git Hooks

#### 01 - Prevent Problems
**Action :** Exécuter des tests ou checks avant qu'un commit soit finalisé pour attraper les erreurs tôt

**Exemples :**
- Linting
- Unit tests
- Code formatting

#### 02 - Enforce Standards
**Action :** Assurer que les commits rencontrent les standards de codage et policies de votre équipe avant de push

**Exemples :**
- Commit message format
- Code quality gates
- Security scans

#### 03 - Streamline Workflows
**Action :** Automatiser les tâches de build et déploiement post-merge pour sauver du temps et réduire les erreurs manuelles

**Exemples :**
- Automated builds
- Deployment triggers
- Notification systems

---

### Types de Git Hooks

#### Client-Side Hooks
**Définition :** Opèrent sur votre machine locale, aidant à attraper les issues avant qu'elles n'atteignent le repository

**Exemples :**
- **pre-commit** : Checks avant qu'un commit soit fait
- **commit-msg** : Validation des messages de commit
- **prepare-commit-msg** : Préparer le message de commit
- **post-commit** : Actions après commit

**Location :** `.git/hooks/`

#### Server-Side Hooks
**Définition :** Agissent sur le serveur, où le repository central réside, pour un contrôle plus large

**Exemples :**
- **pre-receive** : Checking des commits pushés
- **post-receive** : Notification ou actions de déploiement après un push
- **update** : Hook pour chaque branche mise à jour

---

### Git Hooks - Code Quality Control

#### Pre-Commit Hook
**Question :** "Is my code a team player?"

**Fonction :**
- Assure que vos changements harmonisent avec la codebase existante
- N'introduit pas de bugs de code

**Exemple de script :**
```bash
#!/bin/sh
# .git/hooks/pre-commit

# Run tests
npm test
if [ $? -ne 0 ]; then
    echo "Tests must pass before commit!"
    exit 1
fi

# Run linter
npm run lint
if [ $? -ne 0 ]; then
    echo "Linting errors found!"
    exit 1
fi
```

#### Pre-Push Hook
**Question :** "Am I upholding our standards?"

**Fonction :**
- Valide que votre code adhère aux standards de qualité avant de le partager avec les autres

**Exemple de script :**
```bash
#!/bin/sh
# .git/hooks/pre-push

# Run full test suite
npm run test:full
if [ $? -ne 0 ]; then
    echo "Full test suite must pass before push!"
    exit 1
fi
```

---

### Git Hooks - Defense Against Disruption

#### Pre-Receive Hook
**Question :** "Are we welcoming a friend or a foe?"

**Fonction :**
- Cette sentinelle server-side scrutinize le code entrant pour protéger contre les changements disruptifs

**Exemple de script :**
```bash
#!/bin/sh
# Server-side pre-receive hook

while read oldrev newrev refname; do
    # Check commit message format
    # Run security scans
    # Validate code quality
done
```

#### Post-Merge Hook
**Question :** "Has anything slipped through the cracks?"

**Fonction :**
- Check si le nouveau code joue bien avec l'existant
- Maintien de l'intégrité de votre travail

---

### Git Hooks Workflow Diagram

```
Client Side                          Server Side
                                    
Changes to     Commit      Push     Repo Update
Commit    ──►    │    ──►   │  ──►      │
                 │          │           │
          Pre-commit   Pre-receive  Post-receive
          Commit-msg      update
     Prepare-commit-msg
        Post-commit
```

---

## 13. Embracing Inner Source With Forking Workflow

### Définition

**Inner Source** applique les pratiques open-source en interne, récoltant les bénéfices de développement collaboratif, innovant, et transparent sans exposition externe.

### Principes Clés

#### 01 - Empower Every Contributor
**Principe :** Avec un système de pull request basé sur fork, chaque membre de l'équipe peut proposer des changements

**Avantages :**
- Invite tout le monde à la table
- Assure une gamme diverse d'idées et solutions
- Démocratise le processus de développement

#### 02 - Open Source's Best Inside Your Company
**Principe :** Applique les pratiques open-source en interne

**Bénéfices :**
- Développement collaboratif
- Innovation encouragée
- Transparence
- Sans exposition externe

#### 03 - Forking in Corporate
**Principe :** Idéal pour équipes expansives avec niveaux variés d'engagement

**Caractéristiques :**
- Adapte pour inclure contributions des contributeurs réguliers et moins fréquents
- Exploite la sagesse collective
- Sans submerger le projet core

---

## 14. Implementing Fork Workflow

### Le Processus en 5 Étapes

#### 01 - Forking
**Action :** Commencer par forker le repository. C'est comme faire votre copie personnelle du projet pour bricoler.

**Commande Azure DevOps :**
- Aller dans le repository
- Cliquer "Fork"
- Sélectionner le projet de destination

#### 02 - Cloning
**Action :** Cloner le fork sur votre machine locale. Cela vous donne un workspace local où votre codage créatif commence.

**Commande :**
```bash
git clone https://dev.azure.com/your-org/your-project/_git/forked-repo
cd forked-repo
```

#### 03 - Branching and Coding
**Action :** Créer une feature branch dans votre repo local pour expérimentation sûre. C'est ici que vos changements prennent vie.

**Commandes :**
```bash
git checkout -b feature/my-improvement
# Make your changes
git add .
git commit -m "Implement improvement"
```

#### 04 - Pull Request (PR)
**Action :** Une fois votre masterpiece prêt, pusher la branche vers votre fork et ouvrir une pull request. C'est votre moment pour showcaser et proposer vos améliorations au projet original.

**Commandes :**
```bash
git push origin feature/my-improvement
# Créer PR dans Azure DevOps interface
```

#### 05 - Stay Updated
**Action :** Garder votre fork en sync avec le projet original en fetchant les updates depuis upstream. Cela assure que vous buildez toujours sur la version la plus récente du software.

**Commandes :**
```bash
# Ajouter upstream remote
git remote add upstream https://dev.azure.com/original-org/original-project/_git/original-repo

# Fetch updates
git fetch upstream

# Merge updates dans votre main
git checkout main
git merge upstream/main

# Push updates vers votre fork
git push origin main
```

---

## 15. Points Clés pour l'Examen AZ-400

### Branching Strategies doit inclure :

1. ✅ Choix entre Monorepo vs Multiple Repos
2. ✅ Branch workflow approprié (Feature Branch, GitFlow, GitHub Flow, Fork)
3. ✅ Pull Request process avec reviews
4. ✅ Change log management
5. ✅ Git hooks pour quality et automation
6. ✅ Inner source practices

---

### Scénarios d'Examen Typiques

**"L'équipe a besoin de collaboration maximale avec code partagé"**
→ Monorepo avec Feature Branch workflow

**"Projet open-source avec contributeurs externes"**
→ Fork workflow avec pull requests

**"Besoin de pipelines CI/CD indépendants par service"**
→ Multiple repos avec isolation

**"Équipe distribuée avec niveaux variés d'engagement"**
→ Fork workflow + inner source practices

**"Automatiser quality checks avant commit"**
→ Git hooks (pre-commit, pre-push)

**"Maintenir changelog automatiquement"**
→ Utiliser gitchangelog ou github_changelog_generator

---

### Commandes Git Essentielles pour Branching

```bash
# Feature Branch workflow
git checkout -b feature/new-feature
git add .
git commit -m "Descriptive message"
git push origin feature/new-feature

# Sync avec upstream (fork workflow)
git remote add upstream <original-repo-url>
git fetch upstream
git merge upstream/main

# Change log generation
git log --pretty=format:"%h - %s (%an, %ar)" v1.0..v2.0

# Git hooks
# Créer hook file dans .git/hooks/
chmod +x .git/hooks/pre-commit
```

---

### Best Practices Résumées

**Repository Strategy :**
- Choisir basé sur taille d'équipe, complexité de projet, et besoins de dépendances
- Monorepo pour collaboration étroite
- Multiple repos pour autonomie d'équipe

**Branching Strategy :**
- Feature branches pour isolation de développement
- Pull requests pour code review
- Protection policies sur branches principales

**Automation :**
- Git hooks pour quality gates
- Automated changelog generation
- CI/CD integration avec branching strategy

**Collaboration :**
- Pull requests comme outil de communication
- Code reviews obligatoires
- Documentation dans change logs

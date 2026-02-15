# AZ-400 - Section 040 : Activity Traceability

## 1. Traceability - Introduction

### Définition
**Activity traceability** fait référence à la capacité de suivre et analyser la séquence d'événements ou d'activités qui se produisent durant un processus de développement logiciel. Cela inclut tout, des changements de code aux déploiements et releases.

### Objectif dans Azure DevOps
Permet de comprendre comment le code circule à travers le pipeline et où des problèmes potentiels peuvent survenir.

### Importance
**Pourquoi la Traceability est Importante :**

En comprenant comment chaque activité contribue au processus global, vous pouvez :
- ✅ Identifier les bottlenecks et zones d'amélioration
- ✅ Optimiser l'allocation des ressources
- ✅ Améliorer la collaboration entre membres d'équipe
- ✅ Réduire les erreurs et le rework

---

## 2. Dashboards

### Vue d'Ensemble
Les dashboards fournissent une vue centralisée de toutes vos données de projet.

**Caractéristiques :**
- Customisables et mises à jour en temps réel
- Supportent plusieurs équipes et projets
- Permettent la visualisation de métriques clés

### Types de Widgets Disponibles

#### 1. Charts
**Usage :** Visualiser les tendances de données
- Line charts, bar charts, pie charts
- Burndown/burnup charts
- Cumulative flow diagrams

#### 2. Queries
**Usage :** Filtrer des données spécifiques
- Work items par assigné
- Bugs par priorité
- Features par état

#### 3. Burndown/Burnup
**Usage :** Suivre le progrès
- Sprint burndown
- Release burnup
- Vélocité d'équipe

#### 4. Test Plans
**Usage :** Monitorer les efforts de testing
- Test execution status
- Test results trends
- Code coverage

---

### Best Practices pour Dashboards

#### 1. Keep Dashboards Up to Date
- Configurer des refresh automatiques
- Réviser régulièrement la pertinence des widgets
- Retirer les métriques obsolètes

#### 2. Avoid Overcrowding with Widgets
- Maximum 8-12 widgets par dashboard
- Regrouper les informations connexes
- Utiliser plusieurs dashboards pour différentes audiences

#### 3. Utilize Interactive Features
- Drill-down capabilities
- Filtres dynamiques
- Liens vers work items

---

## 3. Documentation With Azure Wikis

### Creating a New Wiki

**Options disponibles :**
1. **Create Project Wiki** : Wiki provisionné directement dans Azure DevOps
2. **Publish Code as Wiki** : Publier du code existant comme wiki

### Provisioned Wiki

**Caractéristiques :**
- Interface d'édition intégrée
- Support Markdown et HTML
- Insertion et redimensionnement d'images
- Attachement de fichiers

**Options disponibles :**
- Add sub-pages
- Copy page path
- Move page
- Edit
- Delete
- Open in new tab
- Print
- Link work items
- View revisions

### Published Code as a Wiki

**Avantages :**
1. **Organize Content into a Hierarchy**
   - Structure en dossiers/fichiers
   - Table des matières automatique

2. **Browse and Filter Table of Contents**
   - Navigation facile
   - Recherche intégrée

3. **Publish New Versions of the Content**
   - Versioning via branches
   - Release tags

4. **Manage Content Like Code**
   - Pull requests pour modifications
   - Code reviews pour documentation
   - CI/CD pour validation

5. **Search the Wiki**
   - Recherche full-text
   - Filtres par tag/catégorie

**Configuration :**
```yaml
# Publish code as wiki configuration
Repository: <your-repo>
Branch: main
Folder: /wiki
Wiki name: Portal Wiki
```

---

## 4. Azure DevOps Boards

### Introduction
Azure DevOps Boards est un outil puissant de gestion de projet et de collaboration qui permet aux équipes de :
- Rationaliser leurs workflows
- Améliorer la productivité
- Obtenir des insights précieux sur le progrès du projet

### Hub Central pour Gérer les Work Items
Les boards offrent une compréhension partagée à travers :
- **Tasks** : Unités de travail individuelles
- **Bugs** : Défauts à corriger
- **User Stories** : Features du point de vue utilisateur

---

### Core Concepts

#### 1. Work Items
Représentent les tâches individuelles ou unités de travail qui peuvent être créées, assignées et suivies dans Azure DevOps Boards.

**Types de Work Items :**

| Work Item Type | Description |
|----------------|-------------|
| **User Story** | Décrit une feature du point de vue utilisateur |
| **Bug** | Rapporte un défaut ou issue qui doit être corrigé |
| **Task** | Représente une unité de travail plus petite au sein d'un item plus large |
| **Feature** | Décrit une nouvelle capacité ou amélioration du produit |

#### 2. Backlogs
Listes ordonnées de work items utilisées pour prioriser et gérer le travail à travers le projet.

**Caractéristiques :**
- Drag-and-drop pour re-priorisation
- Mapping aux sprints
- Effort estimation

#### 3. Sprints
Itérations timeboxed pour délivrer de la valeur, utilisées pour suivre le progrès et gérer la vélocité au sein du projet.

**Composants :**
- Sprint planning
- Daily standups
- Sprint review
- Sprint retrospective

#### 4. Boards
Fournissent une représentation visuelle du workflow, permettant aux équipes de voir le statut des work items et de gérer le progrès global.

**Colonnes typiques :**
- To Do
- In Progress
- In Review
- Done

**Features :**
- Customized columns
- Swimlanes pour catégorisation
- Work item progression
- WIP (Work In Progress) limits

#### 5. Queries
Permettent aux équipes de filtrer, rechercher et analyser les work items basés sur divers critères pour obtenir des insights et prendre des décisions informées.

**Types de queries :**
- Flat list of work items
- Work items and direct links
- Tree of work items

---

### Backlogs - Détails

#### Kanban Board Overview
Représentation visuelle du workflow avec colonnes pour différentes étapes du processus.

#### Customized Columns
Définir des étapes de workflow personnalisées pour correspondre au processus unique de votre équipe.

#### Swimlanes for Categorization
Regrouper les work items par catégorie ou priorité en utilisant des swimlanes horizontales.

#### Work Item Progression
Visualiser le mouvement des work items à travers les différentes étapes du workflow.

#### Limiting Work in Progress (WIP Limits)
Définir des limites WIP pour optimiser le flow et prévenir les bottlenecks dans le processus.

**Exemple de WIP Limits :**
```
Development    Test       Deploy
    [4]        [4]         [2]
    
IN PROGRESS
Per Person ← Limite
```

---

### Sprints - Planning and Execution

#### 1. Defining Sprint Goals and Timeframes
- Établir des objectifs clairs et timeline pour le sprint à venir
- Aligner l'équipe sur ce qui doit être accompli dans la durée du sprint

#### 2. Selecting Work Items from the Backlog
- Réviser le product backlog priorisé
- Choisir les work items les plus importants et réalisables à compléter durant le sprint

#### 3. Tracking Progress on the Sprint Board
- Visualiser le progrès des work items sur le sprint board
- Les déplacer à travers différentes étapes de workflow au fur et à mesure que l'équipe les complète

#### 4. Monitoring Burn-Down and Velocity
- Analyser le sprint burn-down chart
- Suivre la vélocité de l'équipe pour identifier les problèmes potentiels
- Assurer que l'équipe est sur la bonne voie pour atteindre les objectifs du sprint

**Métriques Clés :**
- **Velocity** : Nombre de story points complétés par sprint
- **Burn-down** : Travail restant vs temps restant
- **Burn-up** : Travail complété vs scope total

---

### Queries

**Fonctionnalités :**
1. **Saved Queries** : Sauvegarder les queries fréquemment utilisées
2. **Customizable Reports** : Créer des rapports personnalisés
3. **Burndown Charts** : Visualiser le progrès du sprint
4. **Velocity Tracking** : Suivre la vélocité de l'équipe

**Exemple de Query :**
```sql
SELECT [System.Id], [System.Title], [System.State]
FROM WorkItems
WHERE [System.WorkItemType] = 'Bug'
AND [System.State] <> 'Closed'
AND [System.AssignedTo] = @Me
```

---

### Best Practices pour Azure DevOps Boards

#### 1. Establish Clear Workflows
- Définir des étapes de workflow claires
- Documenter les critères de transition
- Former l'équipe sur le processus

#### 2. Promote Collaboration
- Utiliser @mentions dans les commentaires
- Lier les work items connexes
- Partager les boards avec stakeholders

#### 3. Optimize Backlogs
- Maintenir un backlog priorisé
- Grooming régulier du backlog
- Limiter le WIP

#### 4. Use Dashboards and Queries
- Créer des dashboards pour différents rôles
- Sauvegarder les queries courantes
- Monitorer les métriques clés

#### 5. Leverage Integrations
- Intégrer avec Azure Repos pour traçabilité code
- Connecter avec Azure Pipelines pour CI/CD
- Utiliser Azure Test Plans pour testing

---

## 5. Azure Dashboards

### Introduction
Azure Dashboards sont des outils interactifs de visualisation de données qui permettent de :
- Créer des dashboards personnalisés
- Monitorer et analyser les données de divers services Azure
- Fournir une vue centralisée de l'infrastructure cloud

### The Hub for Cloud Monitoring
**Objectif :** Fournir une vue centralisée de vos ressources cloud, permettant de suivre et analyser :
- Performance
- Utilization
- Health metrics
- Across entire Azure infrastructure

### Empowering DevOps Teams With Actionable Insights
**Bénéfices :**
- Intégration transparente avec les outils DevOps
- Visualisation et partage de données critiques
- Identification des tendances
- Prise de décisions informées pour améliorer performance application/infrastructure

### Accelerating Cloud Migration and Optimization
**Avantages :**
- Visibilité sur l'utilisation des ressources cloud
- Coûts et tendances
- Décisions data-driven pour optimiser environnement cloud
- Facilite l'adoption cloud réussie

---

### Features des Azure Dashboards

#### 1. Centralized Monitoring
Vue centralisée de l'environnement Azure, permettant de suivre :
- Key metrics
- Logs
- Alerts
- De multiples sources en un seul endroit

#### 2. Customizable Layouts
Création de layouts et configurations personnalisés pour organiser et présenter les données de la manière qui convient le mieux aux besoins de monitoring et reporting.

#### 3. Integrated Data Sources
Intégration de données depuis une large gamme de services Azure :
- Azure Monitor
- Log Analytics
- Application Insights
- Et plus

**Vue complète de l'infrastructure cloud.**

#### 4. Sharing and Collaboration
Les dashboards peuvent être partagés avec d'autres utilisateurs, permettant un monitoring collaboratif et une prise de décision au sein de l'organisation.

#### 5. Automation and Scripting
Possibilité d'automatiser et de scripter les dashboards, permettant de créer et mettre à jour les dashboards programmatiquement dans les workflows DevOps.

---

### Use Cases pour Azure Dashboards

#### 1. Monitoring CI/CD Pipelines
Suivre la santé et le statut des pipelines CI/CD Azure DevOps, incluant :
- Build stages
- Test stages
- Deployment stages

#### 2. Visualizing Application Metrics
Afficher des métriques en temps réel et données de performance pour applications hébergées sur Azure :
- Response times
- Error rates
- Resource utilization

#### 3. Tracking Infrastructure Health
Monitorer la santé et disponibilité de l'infrastructure Azure :
- Virtual machines
- Web apps
- Databases

#### 4. Reporting KPIs and SLIs
Créer des dashboards pour suivre les indicateurs clés de performance (KPIs) et indicateurs de niveau de service (SLIs) pour les processus DevOps :
- Deployment frequency
- Mean time to resolution
- Customer satisfaction

#### 5. Sharing Insights with Stakeholders
Présenter les dashboards Azure aux stakeholders, executives et équipes cross-fonctionnelles pour communiquer :
- La santé des applications Azure
- Le statut de l'infrastructure

---

### Azure Dashboards for Monitoring

**Intégration avec Azure Monitor et Log Analytics :**

Les dashboards Azure s'intègrent de manière transparente avec Azure Monitor et Log Analytics, fournissant un hub centralisé pour :
- Suivre les métriques clés
- Visualiser les logs
- À travers l'infrastructure cloud

**Bénéfices :**
- Insights plus profonds sur la santé et performance des ressources Azure
- Troubleshooting plus efficace
- Résolution proactive des problèmes

---

### Best Practices pour Azure Dashboards

#### 1. Dashboard Design
- Assurer que le layout du dashboard est intuitif et visuellement attrayant
- Organisation claire des métriques et widgets

#### 2. Metric Selection
- Choisir des métriques pertinentes et actionnables
- Fournir des insights significatifs aux stakeholders

#### 3. Data Sources
- Intégrer des données de divers services et applications
- Fournir une vue complète de l'environnement

#### 4. Access Controls
- Implémenter des contrôles d'accès basés sur les rôles
- Assurer que les informations sensibles ne sont accessibles qu'aux utilisateurs autorisés

#### 5. Dashboard Sharing
- Activer les fonctionnalités de partage et collaboration
- Permettre aux membres de l'équipe de visualiser et interagir avec le dashboard

---

## 6. Points Clés pour l'Examen AZ-400

### Activity Traceability doit inclure :
1. ✅ Dashboards pour visualiser les métriques clés
2. ✅ Wikis pour documentation centralisée
3. ✅ Boards pour tracking des work items
4. ✅ Queries pour analyser les données
5. ✅ Intégration entre tous les outils Azure DevOps

### Scénarios d'Examen Typiques :

**"L'équipe a besoin de suivre le progrès du sprint"**
→ Utiliser Sprint Boards avec burn-down charts

**"Documentation technique dispersée"**
→ Créer un Wiki Azure DevOps (provisioned ou published)

**"Besoin de visibilité sur performance des pipelines"**
→ Configurer des dashboards Azure avec widgets appropriés

**"Stakeholders veulent des rapports KPI"**
→ Créer des dashboards partagés avec métriques business

### Métriques DevOps Importantes :
- **Deployment Frequency** : Combien souvent déploie-t-on en prod ?
- **Lead Time** : Temps entre commit et déploiement en prod
- **Mean Time to Recovery (MTTR)** : Temps moyen pour récupérer d'un incident
- **Change Failure Rate** : % de déploiements causant des incidents

### Configuration Best Practices :
```yaml
# Example dashboard configuration
widgets:
  - type: build-status
    pipeline: main-ci
  - type: deployment-status
    environment: production
  - type: work-item-chart
    query: active-bugs
  - type: velocity-chart
    iterations: last-6-sprints
```

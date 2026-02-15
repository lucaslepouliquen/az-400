# AZ-400 Section 61 - Implémentation d'une solution d'automatisation d'orchestration

## Vue d'ensemble du cours

Ce cours couvre les aspects essentiels de l'automatisation et de l'orchestration dans Azure Pipelines :

- **Dependency and Security Scanning** (Analyse des dépendances et de la sécurité)
- **Local tests, Unit Tests, Integration Tests, Load Tests** (Tests locaux, tests unitaires, tests d'intégration, tests de charge)
- **Understanding Code Coverage** (Comprendre la couverture de code)

---

## 1. Dependency and Security Scanning

### Introduction

L'analyse des dépendances identifie les bibliothèques et dépendances obsolètes ou vulnérables dans le code avant exploitation. Cette pratique est essentielle pour maintenir la sécurité des applications.

### Fonctionnement avec Azure Pipelines

Azure Pipelines intègre divers outils pour automatiser ce processus, garantissant que les applications utilisent des composants sécurisés et à jour.

### Outils pour l'analyse des dépendances

#### 1. WhiteSource Bolt

- Détecte automatiquement les vulnérabilités open-source
- Génère des rapports complets sur les dépendances
- S'intègre nativement avec Azure DevOps

#### 2. Snyk

- Fournit des insights détaillés sur la correction ou l'atténuation des vulnérabilités
- Offre des recommandations de remédiation
- Supporte de nombreux langages et gestionnaires de packages

#### 3. OWASP Dependency Check

- Outil open-source conçu pour détecter les vulnérabilités publiquement divulguées
- Utilise la base de données CVE (Common Vulnerabilities and Exposures)
- Gratuit et extensible

### Configuration dans Azure Pipelines

**Étapes de mise en œuvre :**

1. **Choisir un outil** d'analyse adapté aux besoins du projet
2. **Installer et configurer** l'outil dans Azure Pipelines
3. **Établir un planning** pour des analyses régulières (quotidiennes, hebdomadaires)
4. **Réviser et répondre** aux résultats rapidement pour corriger les vulnérabilités

---

## 2. Security Scanning (Analyse de sécurité)

### Introduction

L'analyse de sécurité est une mesure proactive pour identifier les faiblesses de sécurité et vulnérabilités dans le code et l'infrastructure avant qu'elles ne soient exploitées.

### Intégration avec Azure Pipelines

Les analyses de sécurité sont intégrées dans les pipelines CI/CD pour faciliter la détection et la résolution précoces des problèmes de sécurité, selon le principe du "shift-left security".

### Outils pour l'analyse de sécurité

#### 1. SonarQube

Analyse le code source pour :
- Vulnérabilités de sécurité
- Qualité du code
- Dette technique
- Bugs et code smells

**Avantages :**
- Rapports détaillés et dashboards
- Intégration native avec Azure DevOps
- Supporte plus de 25 langages

#### 2. Aqua Security

- Spécialisé dans la sécurité des conteneurs et Kubernetes
- Garantit que les images Docker sont exemptes de vulnérabilités avant déploiement
- Analyse runtime pour détecter les comportements anormaux

#### 3. Fortify

- Tests de sécurité d'application statiques (SAST) et dynamiques (DAST)
- Identifie les failles de sécurité dans le code source et les applications en cours d'exécution
- Couvre OWASP Top 10 et autres standards de sécurité

### Bonnes pratiques

- Automatiser les scans de sécurité à chaque commit
- Définir des seuils de qualité (quality gates) pour bloquer les déploiements non sécurisés
- Former les équipes aux résultats et à la remédiation
- Intégrer les résultats dans les tableaux de bord de l'équipe

---

## 3. Types de tests dans Azure Pipelines

### Local Tests (Tests locaux)

Tests exécutés sur la machine du développeur avant de pousser le code vers le repository.

**Avantages :**
- Détection rapide des problèmes
- Réduction du temps de feedback
- Moins de builds cassés dans le pipeline

### Unit Tests (Tests unitaires)

Tests qui vérifient le bon fonctionnement de petites unités de code (fonctions, méthodes, classes) de manière isolée.

**Caractéristiques :**
- Rapides à exécuter
- Indépendants les uns des autres
- Testent une seule fonctionnalité à la fois

**Frameworks populaires :**
- .NET : xUnit, NUnit, MSTest
- JavaScript : Jest, Mocha, Jasmine
- Python : pytest, unittest
- Java : JUnit, TestNG

### Integration Tests (Tests d'intégration)

Tests qui vérifient que différents modules ou services fonctionnent correctement ensemble.

**Objectifs :**
- Valider l'interaction entre composants
- Tester les appels API
- Vérifier les connexions aux bases de données
- Valider les flux de données

**Dans Azure Pipelines :**
- Peuvent nécessiter des services auxiliaires (bases de données, queues, etc.)
- Souvent exécutés dans des environnements de staging
- Plus lents que les tests unitaires

### Load Tests (Tests de charge)

Tests qui évaluent les performances et la scalabilité d'une application sous différentes charges.

**Objectifs :**
- Identifier les goulots d'étranglement
- Vérifier la capacité de l'application à gérer le trafic attendu
- Mesurer les temps de réponse sous charge

**Outils Azure :**
- Azure Load Testing
- Apache JMeter
- k6
- Gatling

**Métriques clés :**
- Temps de réponse
- Throughput (requêtes par seconde)
- Taux d'erreur
- Utilisation des ressources (CPU, mémoire)

---

## 4. Code Coverage (Couverture de code)

### Qu'est-ce que la couverture de code ?

La couverture de code mesure le pourcentage de code source exécuté lors des tests automatisés.

### Types de couverture

1. **Line Coverage** (Couverture de ligne) : Pourcentage de lignes de code exécutées
2. **Branch Coverage** (Couverture de branche) : Pourcentage de branches conditionnelles testées
3. **Function Coverage** (Couverture de fonction) : Pourcentage de fonctions appelées
4. **Statement Coverage** (Couverture d'instruction) : Pourcentage d'instructions exécutées

### Pourquoi la couverture de code est importante

- **Qualité** : Aide à identifier le code non testé
- **Confiance** : Augmente la confiance dans les changements de code
- **Maintenance** : Facilite les refactorings et évolutions
- **Documentation** : Les tests servent de documentation vivante

### Outils de couverture de code

- **.NET** : Coverlet, dotCover
- **JavaScript** : Istanbul, nyc
- **Python** : Coverage.py
- **Java** : JaCoCo, Cobertura

### Intégration dans Azure Pipelines

```yaml
# Exemple pour .NET
- task: DotNetCoreCLI@2
  displayName: 'Run tests with coverage'
  inputs:
    command: test
    arguments: '--collect:"XPlat Code Coverage"'
    projects: '**/*Tests.csproj'

- task: PublishCodeCoverageResults@1
  displayName: 'Publish code coverage'
  inputs:
    codeCoverageTool: 'Cobertura'
    summaryFileLocation: '$(Agent.TempDirectory)/**/*.cobertura.xml'
```

### Bonnes pratiques

- **Ne pas viser 100%** : La couverture à 100% n'est pas toujours nécessaire ni souhaitable
- **Cible raisonnable** : Viser 70-80% pour les projets critiques
- **Qualité > Quantité** : Des tests de qualité avec 60% de couverture valent mieux que des tests superficiels à 90%
- **Mesurer les tendances** : Suivre l'évolution de la couverture dans le temps
- **Bloquer les régressions** : Empêcher les PRs qui diminuent significativement la couverture

### Métriques et rapports

Azure Pipelines génère automatiquement des rapports de couverture incluant :
- Pourcentage global de couverture
- Couverture par fichier/module
- Lignes non couvertes
- Tendances historiques

---

## 5. Orchestration et automatisation complète

### Pipeline CI/CD complet

Un pipeline d'orchestration complet dans Azure Pipelines devrait inclure :

1. **Build** : Compilation du code
2. **Dependency Scan** : Analyse des dépendances
3. **Security Scan** : Analyse de sécurité (SAST)
4. **Unit Tests** : Exécution des tests unitaires
5. **Code Coverage** : Calcul de la couverture
6. **Integration Tests** : Tests d'intégration
7. **Artifact Publication** : Publication des artefacts
8. **Deployment** : Déploiement vers les environnements
9. **Load Tests** : Tests de performance (optionnel)
10. **DAST** : Tests de sécurité dynamique (optionnel)

### Exemple de structure YAML

```yaml
trigger:
  - main

pool:
  vmImage: 'ubuntu-latest'

stages:
  - stage: Build
    jobs:
      - job: BuildAndTest
        steps:
          - task: DotNetCoreCLI@2
            displayName: 'Restore dependencies'
            inputs:
              command: restore
          
          - task: DotNetCoreCLI@2
            displayName: 'Build'
            inputs:
              command: build
              arguments: '--configuration Release'
          
          - task: DotNetCoreCLI@2
            displayName: 'Run unit tests'
            inputs:
              command: test
              arguments: '--collect:"XPlat Code Coverage"'
          
          - task: PublishCodeCoverageResults@1
            displayName: 'Publish coverage'
            inputs:
              codeCoverageTool: 'Cobertura'
              summaryFileLocation: '$(Agent.TempDirectory)/**/*.cobertura.xml'

  - stage: SecurityScan
    dependsOn: Build
    jobs:
      - job: DependencyCheck
        steps:
          - task: dependency-check-build-task@6
            displayName: 'OWASP Dependency Check'
          
      - job: SAST
        steps:
          - task: SonarQubePrepare@5
            displayName: 'Prepare SonarQube'
          
          - task: SonarQubeAnalyze@5
            displayName: 'Run SonarQube'
          
          - task: SonarQubePublish@5
            displayName: 'Publish SonarQube results'

  - stage: Deploy
    dependsOn: SecurityScan
    condition: succeeded()
    jobs:
      - deployment: DeployToStaging
        environment: 'staging'
        strategy:
          runOnce:
            deploy:
              steps:
                - task: AzureWebApp@1
                  displayName: 'Deploy to Azure App Service'
                  inputs:
                    azureSubscription: 'Azure-Connection'
                    appName: 'my-app-staging'

  - stage: LoadTest
    dependsOn: Deploy
    jobs:
      - job: PerformanceTest
        steps:
          - task: AzureLoadTest@1
            displayName: 'Run load tests'
```

---

## Conclusion

L'implémentation d'une solution d'automatisation et d'orchestration complète dans Azure Pipelines nécessite :

- Une combinaison d'outils d'analyse de dépendances et de sécurité
- Une stratégie de test multi-niveaux (unitaires, intégration, charge)
- Un suivi rigoureux de la couverture de code
- Une approche "shift-left" pour la sécurité
- Une automatisation complète du pipeline CI/CD

Ces pratiques garantissent des déploiements sécurisés, fiables et de haute qualité.
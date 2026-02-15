# AZ-400 - Cycles et Frameworks DevOps

## 1. Value Stream

**Définition :** Processus complet de transformation d'idées/requêtes en produits/services qui apportent de la valeur aux clients.

**Flow :** Idea → Development → Testing → Deployment → Operations

**Objectif :** Réduire le temps entre l'idée et la livraison de valeur.

---

## 2. Cycle OODA Loop

Framework pour rester compétitif (originellement pour pilotes de chasse, adapté au DevOps) :

1. **Observe** - Surveiller le marché, besoins users, données tech
2. **Orient** - Brainstorm, générer des idées, tester des hypothèses
3. **Decide** - Choisir ce qu'on va construire
4. **Act** - Build et déployer le software

**Principe clé :** Ce n'est pas un one-shot, c'est un cycle continu d'amélioration.

---

## 3. Validated Learning & Cycle Time

### Validated Learning

**Règle statistique importante :**
- ~1/3 des projets n'aident pas vraiment le business
- ~1/3 sont des winners
- ~1/3 ont peu d'impact

**Stratégie :** Identifier rapidement les duds, doubler sur les winners.

**Méthode :** "Pivot or Persevere" basé sur des données réelles, pas des gut feelings.

### Cycle Time

**Définition :** Temps nécessaire pour compléter un cycle OODA complet.

**Impact :** Plus le cycle time est court, plus vite tu reçois du feedback, plus vite tu peux décider du prochain pivot/persevere.

**Comment réduire le cycle time :**
- Smaller batches
- Plus d'automation
- Release pipeline plus robuste
- Meilleure telemetry
- Déployer plus fréquemment

**Bénéfice :** Plus d'opportunités d'expérimentation = plus de "pivot or persevere" moments = learning accéléré = valeur cumulée maximisée.

---

## 4. Application Lifecycle DevOps

### Les 4 Phases (interconnectées, non role-specific)

1. **Plan**
   - Review du backlog
   - Décision features à accepter/rejeter
   - Brainstorm et définition
   - Critères d'acceptance
   - Outils : Agile, Azure Boards

2. **Develop**
   - Coding, testing, integration
   - Vitesse maximale SANS sacrifier qualité/sécurité/stabilité
   - Outils : Azure Repos, Git

3. **Deliver**
   - Déploiement en production
   - Stages contrôlés avec gates et processus
   - Outils : Azure Pipelines (CI/CD)

4. **Operate**
   - Maintenance et monitoring
   - High availability et reliability
   - Outils : Azure Monitor, Application Insights

**Point clé :** C'est un cycle infini (Infinity Loop), pas une séquence linéaire.

---

## 5. Infinity Loop DevOps

**Cycle continu :**
Plan → Build → Continuous Integration → Deploy → Operate → Continuous Feedback → (retour à Plan)

**Deux côtés :**
- **Gauche (Collaboration) :** Plan, Build, Continuous Integration
- **Droite (Collaboration) :** Deploy, Operate, Continuous Feedback

---

## 6. Terminologie Clé

**CI (Continuous Integration) :**
- Merge fréquent du code dans shared repository
- Build et tests automatiques
- Détection rapide des problèmes

**CD (Continuous Delivery) :**
- Code toujours dans un état deployable
- Déploiement automatisé vers staging
- Déploiement production sur decision manuelle

**CD (Continuous Deployment) :**
- Comme Continuous Delivery mais déploiement production automatique
- Aucune intervention manuelle

**Telemetry :**
- Collection automatique de données depuis applications/infrastructure
- Métriques, logs, traces
- Base du monitoring et de l'observability

**Value Stream :**
- Flow complet idea → production
- Inclut tous les steps et handoffs
- Objectif : optimiser pour réduire le time-to-value

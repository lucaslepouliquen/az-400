# AZ-400 - Fondamentaux DevOps

## 1. Définition et Principes DevOps

### Qu'est-ce que DevOps ?

**Définition Microsoft (officielle pour l'examen) :**
DevOps est **l'union de people, processes, et products pour délivrer rapidement de la VALEUR aux utilisateurs**.

**Point critique :** L'objectif n'est pas juste de livrer du software plus vite, mais de **délivrer de la valeur**. Si le logiciel ne résout pas les problèmes des utilisateurs, la vitesse ne compte pas.

### Les 3 Piliers

1. **People (Personnes)**
   - Collaboration cross-fonctionnelle complète
   - Plus qu'un simple merge Dev + Ops : intégration totale
   - Équipes partageant les mêmes objectifs
   - Fin du "throw it over the wall"

2. **Processes**
   - Workflows agiles et efficaces
   - Utilisation de data pour analyser ce qui fonctionne
   - Ajustements constants basés sur les métriques
   - Élimination des gaspillages (waste)

3. **Products (Outils)**
   - Automation maximale
   - Observability
   - Continuous Integration & Continuous Delivery (CI/CD)
   - Azure DevOps est l'outil Microsoft central

---

## 2. Les 3 Ways - Principes Fondamentaux DevOps

### First Way : Flow (Flux)

**Objectif :** Mouvement fluide et rapide du travail de bout en bout, sans délais, bottlenecks ou blocages.

**Actions concrètes :**
- Mapper et mesurer la value stream
- Identifier les zones de gaspillage et contraintes
- Éliminer les hard stops
- Assurer un fast path to production
- Optimiser le workflow

**Implémentation :**
- Travailler en smaller batches
- Augmenter l'automation
- Renforcer le release pipeline
- Améliorer la telemetry
- Déployer plus souvent

### Second Way : Feedback

**Objectif :** Monitorer et identifier les échecs rapidement, puis "swarmer" les équipes autour du problème.

**Sources de feedback :**
- Humains (users, stakeholders)
- Machines (monitoring, logs, telemetry)

**Actions :**
- Automatiser la détection d'échecs
- Réaction immédiate aux problèmes
- Intégrer les retours utilisateurs dans le cycle
- Créer des boucles de feedback courtes

### Third Way : Experimentation & Learning

**Objectif :** Établir un environnement où les gens peuvent essayer de nouvelles idées.

**Principes :**
- Run experiments si tu penses que ça améliore le flow ou la qualité
- Embrace failure comme opportunité d'apprentissage
- Investir constamment dans ce processus
- Utiliser la méthode scientifique
- "Pivot or persevere" basé sur les données

---

## 3. Histoire DevOps (contexte pour l'examen)

### Avant DevOps (Waterfall Era)

**Problème :** 
- Dev et Ops complètement séparés (silos)
- Devs "throw it over the wall" aux Ops
- Ops renvoient "over the wall" aux Devs quand problème
- Cycle de 6 mois pour une feature = trop lent

**Catalyseurs du changement :**
- Applications de plus en plus complexes
- Cloud computing
- Infrastructure as Code
- Besoin de vitesse ET fiabilité

### 2009 : Naissance de DevOps

**Objectif :** Casser le mur entre Dev et Ops.

**Résultat :** Dev et Ops travaillent avec les mêmes objectifs, collaborent directement.

---

## 4. Différence Waterfall vs DevOps

| Waterfall | DevOps |
|-----------|--------|
| Séquentiel, phases rigides | Cyclique, itératif |
| Requirements → Design → Implementation → Testing → Deployment → Maintenance | Plan → Develop → Deliver → Operate (en boucle) |
| Handoffs entre équipes | Équipes intégrées |
| 6 mois pour une feature | Déploiements multiples par jour possibles |
| Dev et Ops séparés | Dev et Ops collaborent |

---

## 5. DevOps ≠ Juste Rapidité

**Mauvaise compréhension :** DevOps = livrer du code plus vite

**Bonne compréhension :** DevOps = livrer de la **VALEUR** plus vite, avec **qualité, sécurité, et stabilité**

---

## 6. Anti-Patterns à Éviter (pour l'examen)

**Choses que DevOps n'est PAS :**
- Juste merger Dev + Ops sans vraie collaboration
- Sacrifier la qualité pour la vitesse
- Automation sans stratégie
- Déploiements rapides sans monitoring
- Ignorer le feedback

**Red flags dans les scénarios d'examen :**
- Absence de tests automatisés
- Pas de rollback strategy
- Déploiements sans approval gates pour prod
- Aucun monitoring post-deployment
- Silos persistants entre équipes

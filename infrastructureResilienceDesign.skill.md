# Infrastructure Resilience Design

## Objectif
Concevoir des architectures de haute disponibilité (HA) et des plans de continuité (PRA/PCA) on-prem : clustering, load balancing, failover, définition RTO/RPO, stratégies de disaster recovery testables.

## Quand l'utiliser (triggers)
- « haute disponibilité », « HA on-prem », « PRA », « PCA », « RTO RPO », « failover », « clustering », « disaster recovery ».
- Exigence de disponibilité élevée (> 99.9%) on-prem.
- Besoin de plan de continuité formalisé et testé.
- Refonte infra pour éliminer SPoF (single points of failure).

## Hors périmètre
- PRA/PCA cloud (AWS multi-region, Azure Site Recovery) → l'agent d'architecture cloud.
- Implémentation clustering OS-spécifique (WSFC, Pacemaker) → Sysadmin Windows/Linux.
- Configuration load balancing détaillée → l'agent réseau.

## Inputs requis
- Services critiques et leurs dépendances.
- Exigences RTO (Recovery Time Objective : délai max reprise) et RPO (Recovery Point Objective : perte données max tolérée).
- Contraintes (budget, sites disponibles, bande passante inter-sites).
- Charge applicative et pics de trafic.

## Sorties attendues
- Architecture HA cible (clustering actif/actif ou actif/passif, load balancing).
- Schéma résilience (failover automatique, réplication stockage, sites de secours).
- RTO/RPO définis par service critique (alignés exigences business ET faisabilité technique).
- Plan de disaster recovery (procédures de bascule, tests de failover, runbooks).
- Identification et mitigation des SPoF (redondance composants, chemins réseau multiples).

## Workflow recommandé
1. Identifier services critiques et leurs dépendances (cartographie flux).
2. Clarifier exigences RTO/RPO par service (demander si non fourni).
3. Analyser SPoF actuels (composants uniques, chemins réseau uniques).
4. Proposer architecture HA cible (recommandé : actif/passif pour simplicité, actif/actif si charge élevée).
5. Définir stratégie de réplication stockage (synchrone si RPO=0, asynchrone si RPO > 5min).
6. Concevoir plan de disaster recovery (procédures bascule site primaire → secondaire, tests trimestriels).
7. Chiffrer coût (redondance = +30-50% coût infra) et valider avec utilisateur.

## Garde-fous
- RTO/RPO réalistes : alignés avec budget et architecture. Si RTO=5min demandé mais budget limité → challenger exigence ou augmenter budget.
- Tests de failover obligatoires : plan PRA non testé = plan inexistant. Tests au minimum trimestriels.
- Redondance ≠ complexité inutile : pas de sur-ingénierie (ex: clustering 5 nodes si 2 nodes suffisent).
- Documentation runbooks : procédures de bascule manuelles ET automatiques documentées, accessibles 24/7.
- Réplication stockage synchrone si RPO=0 (perte données intolérable), asynchrone acceptable si RPO > 5-15min.

## Template d'entrée (copier/coller)
```text
[Contexte]
- Services critiques : ...
- Exigences RTO/RPO : ...
- Sites disponibles : primaire + secondaire / mono-site

[Objectif]
- Disponibilité cible : ... %
- Budget : ...
```

## Template de sortie (copier/coller)
```text
[Architecture HA]
- Clustering : actif/actif ou actif/passif
- Load balancing : ...
- Réplication stockage : synchrone / asynchrone

[RTO/RPO par service]
- Service A : RTO=... , RPO=...
- Service B : RTO=... , RPO=...

[Mitigation SPoF]
- SPoF identifiés : ...
- Redondance proposée : ...

[Plan disaster recovery]
- Procédures bascule : ...
- Tests : trimestriels
- Runbooks : ...

[Coût]
- Redondance : +... % coût infra

[Hypothèses]
- ...

[Risques]
- ...
```

## Métriques de succès
- RTO/RPO validés par test de disaster recovery (simulation documentée).
- Zéro SPoF non mitigé ou non documenté.
- Taux de disponibilité réel ≥ cible (ex: 99.9% mesuré sur 12 mois).
- Tests de failover réalisés au minimum trimestriellement avec rapports.

## Checklist QA interne
- Les objectifs RTO/RPO et la disponibilité cible sont validés par les responsables métier.
- Les dépendances critiques, points uniques de défaillance et sauvegardes sont identifiés.
- Les scénarios de bascule/restauration disposent de critères observables et d'un plan de retour.

## Definition of done
- Le design de résilience relie chaque risque identifié à une mesure et à un owner.
- Les tests et preuves nécessaires pour valider les objectifs RTO/RPO sont précisés.
- Les hypothèses, limites et risques résiduels sont explicitement documentés.

## Exemples d'usage

### Exemple 1 : Définir le PRA d'un service de gestion de dossiers
**Contexte** : Le service dépend d'une base de données, d'un stockage de fichiers et d'un annuaire; les objectifs de reprise ne sont pas encore confirmés par le métier.  
**Input** : Cartographie des dépendances, criticité métier, sauvegardes, sites disponibles, contraintes réseau et propositions de RTO/RPO.  
**Output** : Questions de validation des objectifs, SPoF identifiés, options de redondance et scénario de reprise testable; les objectifs restent provisoires jusqu'à validation.

### Exemple 2 : Préparer un exercice de bascule d'un cluster
**Contexte** : Un cluster actif/passif existe, mais les équipes n'ont jamais démontré le temps de reprise réel.  
**Input** : Architecture et runbook actuels, fenêtre d'exercice autorisée, mesures de réplication, dépendances et contacts d'escalade.  
**Output** : Plan d'exercice non destructif avec étapes, critères de succès/arrêt, collecte des temps et pertes de données observés, puis écarts à corriger.

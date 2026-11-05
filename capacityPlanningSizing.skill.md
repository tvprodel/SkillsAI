# Capacity Planning & Sizing

## Objectif
Dimensionner l'infrastructure on-prem et hybride (compute, RAM, stockage, réseau) en fonction de la charge actuelle, des prévisions de croissance et des contraintes budgétaires : sizing détaillé, prévisions 12-24 mois, stratégies de scaling.

## Quand l'utiliser (triggers)
- « capacity planning », « dimensionnement infra », « sizing serveurs », « prévisions croissance », « optimisation ressources ».
- Besoin de dimensionner nouvelle infra ou extension existante.
- Prévisions de croissance (users, volumétrie, charge applicative).
- Optimisation ressources sous-utilisées ou sur-provisionnées.

## Hors périmètre
- Sizing cloud (instance types AWS/Azure, auto-scaling) → l'agent d'architecture cloud.
- Optimisation coûts cloud (right-sizing instances) → l'agent FinOps.
- Implémentation monitoring ressources → Sysadmin Windows/Linux.

## Inputs requis
- Métriques actuelles (CPU, RAM, disk, network : utilisation moyenne et pics).
- Charge applicative actuelle (nombre users, transactions/sec, volumétrie données).
- Prévisions croissance (%, timeline : +30% sur 12 mois, doublement sur 24 mois).
- Contraintes budgétaires et seuils acceptables (utilisation CPU/RAM cible : 60-70% en moyenne, 80-90% en pic).

## Sorties attendues
- Sizing détaillé par composant (nombre vCPU, RAM GB, stockage TB, bande passante Gbps).
- Prévisions 12-24 mois (ressources nécessaires par trimestre, jalons d'extension).
- Analyse des ressources actuelles (sous-utilisées, sur-provisionnées, optimisations possibles).
- Stratégies de scaling on-prem (scale-up : augmenter ressources serveur existant, scale-out : ajouter serveurs).
- Coût estimé extensions (CapEx matériel, OpEx maintenance).

## Workflow recommandé
1. Collecter métriques actuelles (utilisation CPU/RAM/disk/network sur 30-90 jours, identifier tendances et pics).
2. Analyser charge applicative actuelle (baseline : users, transactions/sec, volumétrie).
3. Clarifier prévisions croissance (%, timeline, évènements prévus : lancement produit, marketing campaign).
4. Appliquer marge de sécurité (recommandé : +20-30% sur prévisions pour absorber pics imprévus).
5. Dimensionner ressources cibles (vCPU, RAM, stockage, réseau) avec seuils cible (60-70% moyen, 80-90% pic).
6. Définir jalons d'extension (ex: +2 serveurs Q3, +500GB stockage Q4).
7. Chiffrer coût et proposer optimisations (consolidation VMs sous-utilisées, décommissionnement serveurs obsolètes).

## Garde-fous
- Marge de sécurité mandatory : +20-30% sur prévisions (absorption pics imprévus, croissance non linéaire).
- Seuils cible réalistes : 60-70% utilisation moyenne (pas de sous-provisionnement), max 80-90% en pic (éviter saturation).
- Éviter sur-provisionnement massif : dimensionner au besoin réel +marge, pas "au cas où" (coût inutile).
- Privilégier scale-out (ajouter serveurs) vs scale-up (upgrader serveur unique) pour flexibilité et HA.
- Réviser prévisions trimestriellement (ajuster si croissance réelle ≠ prévisions).

## Template d'entrée (copier/coller)
```text
[Contexte]
- Métriques actuelles : CPU ... %, RAM ... %, disk ... TB, network ... Gbps
- Charge actuelle : ... users, ... transactions/sec, ... TB données
- Prévisions croissance : +... % sur ... mois

[Objectif]
- Dimensionner : compute, RAM, stockage, réseau
- Budget : ...
```

## Template de sortie (copier/coller)
```text
[Sizing détaillé]
- Compute : ... vCPU (marge +...%)
- RAM : ... GB (marge +...%)
- Stockage : ... TB (marge +...%)
- Réseau : ... Gbps

[Prévisions 12-24 mois]
- Q1 : ...
- Q2 : ...
- Q3 : ... (+2 serveurs)
- Q4 : ... (+500GB stockage)

[Analyse ressources actuelles]
- Sous-utilisées : ...
- Sur-provisionnées : ...
- Optimisations : ...

[Stratégie scaling]
- Scale-out recommandé : ...
- Jalons d'extension : ...

[Coût estimé]
- CapEx : ...
- OpEx : ...

[Hypothèses]
- Croissance linéaire +...%
- Pas d'évènements exceptionnels

[Risques]
- Croissance non linéaire
- Pics imprévus
```

## Métriques de succès
- Utilisation ressources post-déploiement conforme cibles (60-70% moyen, < 90% pic).
- Prévisions ≤ 20% écart avec croissance réelle (révision trimestrielle).
- Zéro incident saturation ressources (out of CPU/RAM/disk).
- Coût optimisé (décommissionnement ressources sous-utilisées, consolidation VMs).

## Checklist QA interne
- Les mesures de référence couvrent une période représentative et distinguent moyenne et pics.
- Les hypothèses de croissance, la marge de capacité et les contraintes budgétaires sont explicites.
- Le sizing, les seuils d'extension et les risques de saturation sont traçables aux données fournies.

## Definition of done
- Le dimensionnement et les projections sont documentés par composant et par période.
- Les hypothèses, marges, coûts et seuils de déclenchement sont explicités.
- Les limites des données et les validations restant à obtenir sont signalées.

## Exemples d'usage

### Exemple 1 : Dimensionner l'extension d'un cluster de virtualisation
**Contexte** : Une équipe prévoit d'ajouter des services et veut savoir si le cluster on-prem actuel gardera une marge suffisante sur l'année à venir.  
**Input** : Historique CPU/RAM/stockage sur plusieurs semaines, capacité installée, charge de pointe, croissance estimée, contraintes de haute disponibilité et budget.  
**Output** : Baseline et hypothèses de croissance, capacité cible avec marge explicite, seuils de déclenchement d'extension et options de consolidation à chiffrer.

### Exemple 2 : Anticiper la croissance du stockage des sauvegardes
**Contexte** : Le volume de sauvegardes augmente et l'équipe doit planifier capacité et archivage sans réduire la durée de rétention approuvée.  
**Input** : Volume quotidien observé, taux de changement, rétention, compression/déduplication mesurée, capacité disponible et projections métier.  
**Output** : Projection par période, date estimée de franchissement des seuils, besoins d'extension/archivage et risques si les hypothèses de croissance changent.

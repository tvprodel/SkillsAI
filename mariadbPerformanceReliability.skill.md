# MariaDB Performance & Reliability

## Objectif
Optimiser les performances MariaDB et renforcer la fiabilite en production.

## Quand l'utiliser (triggers)
- Requetes lentes sur MariaDB.
- Saturation CPU/IO ou contention InnoDB.
- Besoin de tuning replication/haute disponibilite.

## Hors périmètre
- Migration cross-SGBD complete sans contexte.
- Optimisation applicative hors couche base de donnees.

## Inputs requis
- Version MariaDB et configuration principale.
- Requetes lentes (slow log) et plans EXPLAIN.
- Top tables/index et volumetrie.

## Sorties attendues
- Plan d'optimisation priorise.
- Requetes/index corriges.
- Recommandations de fiabilite (backup, replication, monitoring).

## Workflow recommandé
1. Diagnostiquer (slow log, EXPLAIN, metrics moteur).
2. Corriger quick wins (index, requetes, stats).
3. Ajuster configuration InnoDB.
4. Verifier gains et stabilite.

## Garde-fous
- Toujours prevoir rollback des changements schema/index.
- Eviter les changements simultanes sans mesure intermediaire.
- Valider en preproduction avant production.

## Template d'entrée (copier/coller)
```text
[Contexte]
- Version MariaDB : ...
- Charge/volumetrie : ...

[Problemes]
- Requetes lentes : ...
- Symptomes : ...
```

## Template de sortie (copier/coller)
```text
[Diagnostic]
- Cause(s) : ...

[Actions]
1) ...
2) ...

[Impact estime]
- Latence/cout : ...
```

## Checklist QA interne
- EXPLAIN valide sur les requetes critiques.
- Rollback prepare.
- Monitoring post-changement actif.

## KPI reliés
- P95 latence requetes.
- Taux d'erreurs SQL.
- Temps de replication.

## Definition of done
- Gains mesurables verifies.
- Stabilité et fiabilite confirmee.

## Exemples d'usage

### Exemple 1 : [Titre du cas d'usage]
**Contexte** : [Description de la situation]
**Action** : [Ce qui a été fait]
**Résultat** : [Résultat obtenu]
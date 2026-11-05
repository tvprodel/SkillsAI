# PostgreSQL Advanced Tuning

## Objectif
Optimiser PostgreSQL sur les plans requetes, index, maintenance et configuration.

## Quand l'utiliser (triggers)
- Latence elevee sur requetes complexes.
- Bloat important / autovacuum insuffisant.
- Besoin d'optimisation avancee (index partiels, GIN/BRIN).

## Hors périmètre
- Refonte applicative complete.
- Changement de SGBD sans justification.

## Inputs requis
- Version PostgreSQL et config cle.
- EXPLAIN (ANALYZE, BUFFERS) des requetes lentes.
- Statistiques pg_stat_statements / volumetrie.

## Sorties attendues
- Plan de tuning priorise.
- SQL/index/config ajustes.
- Strategie maintenance (VACUUM/ANALYZE) adaptee.

## Workflow recommandé
1. Diagnostiquer plans et stats runtime.
2. Optimiser SQL/index (partiels, GIN, BRIN selon cas).
3. Ajuster maintenance/config.
4. Valider gains et stabilite.

## Garde-fous
- Toujours mesurer avant/apres.
- Encadrer tout changement de parametre global.
- Prevoir retour arriere des changements critiques.

## Template d'entrée (copier/coller)
```text
[Contexte]
- Version PostgreSQL : ...
- Charge : ...

[Probleme]
- Requete(s) : ...
- EXPLAIN ANALYZE : ...
```

## Template de sortie (copier/coller)
```text
[Diagnostic]
- Cause(s) : ...

[Plan de tuning]
1) ...
2) ...

[Verification]
- KPI avant/apres : ...
```

## Checklist QA interne
- EXPLAIN ANALYZE compare avant/apres.
- Maintenance planifiee.
- Risques de regression identifies.

## KPI reliés
- P95 latence SQL.
- Hit ratio cache.
- Bloat / frequence autovacuum.

## Definition of done
- Gains de performance verifies.
- Stabilite de production maintenue.

## Exemples d'usage

### Exemple 1 : [Titre du cas d'usage]
**Contexte** : [Description de la situation]
**Action** : [Ce qui a été fait]
**Résultat** : [Résultat obtenu]
# MySQL Query Optimization

## Objectif
Ameliorer durablement les performances de requetes MySQL.

## Quand l'utiliser (triggers)
- Requetes SQL lentes recurrentes.
- Degradation de SLA applicatif.
- Croissance de donnees non absorbee.

## Hors périmètre
- Refonte produit hors couche SQL.
- Migration complete vers un autre SGBD.

## Inputs requis
- Version MySQL, schema, index actuels.
- Slow query log et EXPLAIN/ANALYZE.
- Contraintes metier (lecture/ecriture/transactions).

## Sorties attendues
- Requetes reecrites si necessaire.
- Strategie d'indexation cible.
- Plan de validation perf + rollback.

## Workflow recommandé
1. Identifier top requetes couteuses.
2. Lire plan d'execution.
3. Optimiser SQL et index.
4. Mesurer avant/apres.

## Garde-fous
- Eviter sur-indexation et regressions ecriture.
- Valider cardinalites et selectivites.
- Documenter impacts transactionnels.

## Template d'entrée (copier/coller)
```text
[Contexte]
- Version MySQL : ...
- Tables critiques : ...

[Requete]
- SQL : ...
- EXPLAIN : ...
```

## Template de sortie (copier/coller)
```text
[Diagnostic]
- Goulot principal : ...

[Correctifs]
1) ...
2) ...

[Mesure]
- Avant/apres : ...
```

## Checklist QA interne
- Requete optimisee testee.
- Index verifies en charge.
- Rollback documente.

## KPI reliés
- P95/P99 latence SQL.
- QPS stable.
- Temps CPU DB.

## Definition of done
- Requetes critiques sous seuil cible.
- Aucune regression fonctionnelle observee.

## Exemples d'usage

### Exemple 1 : [Titre du cas d'usage]
**Contexte** : [Description de la situation]
**Action** : [Ce qui a été fait]
**Résultat** : [Résultat obtenu]
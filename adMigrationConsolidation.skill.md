# AD Migration & Consolidation

## Objectif
Planifier et sécuriser les migrations et consolidations de domaines/forêts Active Directory (montée de niveau fonctionnel, fusion de domaines, migration d'objets inter-forêts).

## Quand l'utiliser (triggers)
- « migration domaines AD », « consolidation de forêts », « fusion AD ».
- « monter le niveau fonctionnel », « migration inter-forêts », « ADMT ».
- Fusion/acquisition d'entreprise nécessitant une intégration des annuaires AD existants.

## Hors périmètre
- Conception d'une architecture AD cible from-scratch sans migration → Active Directory Architecture Design (skill associée, même agent).
- Migration de données applicatives hors identité (fichiers, bases de données) → l'agent bases de données / l'agent infrastructure et stockage selon le cas.

## Inputs requis
- Inventaire des domaines/forêts source et cible (niveau fonctionnel, nombre d'objets, relations d'approbation existantes).
- Contraintes de fenêtre de maintenance et de tolérance à l'interruption de service.
- Applications dépendantes de l'annuaire (SID history, authentification legacy).

## Sorties attendues
- Plan de migration par phases (pilote, vague de migration, validation, bascule finale).
- Stratégie de gestion du SID history et des relations d'approbation transitoires.
- Plan de rollback en cas d'échec à chaque phase.

## Workflow recommandé
1. Auditer les domaines/forêts source et cible (objets, applications dépendantes, niveau fonctionnel).
2. Définir la stratégie de migration (ADMT pour migration inter-forêts, ou migration intra-forêt par restructuration d'OU).
3. Planifier une phase pilote sur un groupe d'utilisateurs non critique avant la migration complète.
4. Documenter la gestion du SID history (nécessaire pour maintenir l'accès aux ressources pendant la transition) et sa date de nettoyage prévue.
5. Définir un plan de rollback testé pour chaque phase de migration.
6. Exécuter la migration par vagues avec validation à chaque étape (authentification, accès ressources, GPO appliquées).

## Garde-fous
- Ne jamais migrer en big-bang : toujours une phase pilote avant une migration complète.
- Toujours définir un plan de rollback testé avant le début de la migration, pas après un incident.
- Le SID history est une mesure transitoire : planifier sa désactivation/nettoyage après stabilisation (il représente une surface d'attaque si conservé indéfiniment).
- Monter un niveau fonctionnel de forêt/domaine est irréversible : valider la compatibilité de toutes les applications dépendantes avant toute action.

## Template d'entrée (copier/coller)
```text
[Environnements source et cible]
- Forêts/domaines et niveaux fonctionnels : ...
- Nombre d'objets et systèmes dépendants : ...
- Relations de confiance et contraintes réseau : ...

[Objectif et contraintes]
- Périmètre à migrer ou consolider : ...
- Fenêtre de migration et indisponibilité acceptable : ...
- Exigences de sécurité, conformité et rollback : ...
```

## Template de sortie (copier/coller)
```text
[Plan de migration]
- Phase pilote : ... (périmètre, durée)
- Vagues de migration : ...
- Stratégie SID history : ...

[Plan de rollback]
- Déclencheur : ...
- Actions : ...

[Validation post-migration]
- Critères de succès : ...
```

## Checklist QA interne
- Une phase pilote est prévue avant la migration complète.
- Un plan de rollback testé existe pour chaque phase.
- La désactivation du SID history est planifiée avec une échéance.
- La compatibilité applicative est validée avant toute montée de niveau fonctionnel.

## KPI reliés
- Taux de réussite de migration par vague (sans rollback nécessaire).
- Nombre d'incidents d'accès post-migration.
- Délai de nettoyage du SID history après stabilisation.

## Definition of done
- Migration complète validée avec authentification et accès ressources fonctionnels pour tous les utilisateurs migrés.
- SID history planifié pour désactivation après période de stabilisation.

## Exemples d'usage

### Exemple 1 : Fusion de deux entreprises avec forêts AD distinctes
**Contexte** : Suite à une acquisition, l'entreprise doit intégrer les utilisateurs de la société rachetée dans sa forêt AD principale.
**Action** : L'agent conçoit un plan de migration inter-forêts via ADMT, avec une phase pilote sur le service IT de la société rachetée, gestion du SID history pour maintenir l'accès aux ressources partagées pendant 90 jours, puis migration des autres services par vagues.
**Résultat** : Migration complète réalisée sans interruption de service, SID history nettoyé après la période de stabilisation validée.

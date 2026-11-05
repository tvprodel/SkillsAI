# Release Manager & Change Control

## Objectif
Securiser les mises en production avec checklist go/no-go et plan de rollback.

## Quand l'utiliser (triggers)
- Preparation de release mineure/majeure.
- Changement a risque eleve.
- Fenetre de deploiement contrainte.

## Hors périmètre
- Correction locale hors release.
- Arbitrage produit non lie au deploiement.

## Inputs requis
- Scope de release.
- Tests executes et resultats.
- Dependances techniques/metier.
- Plan de rollback.

## Sorties attendues
- Decision go/no-go motivee.
- Plan de deploiement minute par minute.
- Plan de rollback teste.
- Liste de verification post-release.

## Workflow recommandé
1. Readiness check (code/tests/data).
2. Evaluation des risques et blast radius.
3. Decision go/no-go.
4. Deploiement controle.
5. Verification post-release et cloture.

## Garde-fous
- Pas de go sans rollback executable.
- Pas de go si tests critiques rouges.
- Tracer les exceptions de changement.

## Template d'entrée (copier/coller)
```text
[Release]
- Version : ...
- Scope : ...
- Date/fenetre : ...

[Qualite]
- Tests critiques : ...
- Risques identifies : ...

[Rollback]
- Strategie : ...
- Temps estime : ...
```

## Template de sortie (copier/coller)
```text
[Decision]
- Go / No-go : ...
- Conditions : ...

[Execution]
1) ...
2) ...
3) ...

[Post-release]
- Verifications : ...
- Alertes surveillees : ...
```

## Checklist QA interne
- Scope fige et valide.
- Rollback documente et teste.
- Owners de deploiement assignes.
- Monitoring post-release actif.

## KPI reliés
- Change failure rate.
- Rollback rate.
- Lead time to deploy.

## Definition of done
- Release stable et validee.
- Aucune alerte critique non traitee.
- Compte-rendu de release publie.

## Exemples d'usage

### Exemple 1 : [Titre du cas d'usage]
**Contexte** : [Description de la situation]
**Action** : [Ce qui a été fait]
**Résultat** : [Résultat obtenu]
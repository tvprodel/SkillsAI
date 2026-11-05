# Disaster Recovery Design

## Objectif
Concevoir des stratégies de résilience et de reprise (PRA/PCA) adaptées aux objectifs RTO/RPO fournis.

## Quand l'utiliser (triggers)
- « plan de reprise », « PRA/PCA cloud », « définis le RTO/RPO ».
- Renforcement de la résilience d'une plateforme critique.
- Préparation d'un test de bascule.

## Hors périmètre
- Optimisation de coûts pure → skill Cloud Cost Optimization.
- Observabilité runtime / alerting → Observability Engineer.

## Inputs requis
- Objectifs RTO/RPO par service.
- Architecture actuelle et points de défaillance.
- Budget résilience et contraintes de conformité.

## Sorties attendues
- Architecture de résilience (patterns : actif/passif, actif/actif, backup/restore).
- Matrice RTO/RPO par composant.
- Procédure de bascule et de retour à la normale.

## Workflow recommandé
1. Recueillir RTO/RPO par service critique.
2. Identifier les points uniques de défaillance.
3. Choisir un pattern de reprise par composant (coût vs objectif).
4. Définir la procédure de bascule et un plan de test.

## Garde-fous
- Aligner le coût de résilience sur la criticité réelle.
- Toute stratégie DR doit être testable.
- Documenter le retour à la normale, pas seulement la bascule.

## Template d'entrée (copier/coller)
```text
[Contexte]
- Services critiques : ...
- RTO/RPO cibles : ...

[Objectif]
- Budget résilience : ...
```

## Template de sortie (copier/coller)
```text
[Architecture de résilience]
- Pattern par composant : ...

[Matrice RTO/RPO]
- Composant 1 : RTO ... | RPO ...

[Procédure de bascule]
1) ...
```

## Checklist QA interne
- Chaque composant critique a un RTO/RPO cible.
- La procédure de bascule est testable.
- Le retour à la normale est documenté.

## KPI reliés
- Écart RTO/RPO réel vs cible lors des tests.
- Fréquence des tests de bascule.
- Couverture des points uniques de défaillance.

## Definition of done
- Architecture de résilience et matrice RTO/RPO publiées.
- Procédure de bascule et plan de test fournis.
- Risques résiduels documentés.

## Exemples d'usage

### Exemple 1 : [Titre du cas d'usage]
**Contexte** : [Description de la situation]
**Action** : [Ce qui a été fait]
**Résultat** : [Résultat obtenu]
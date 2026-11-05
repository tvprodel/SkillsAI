# Test Architect (QA avancee)

## Objectif
Concevoir une strategie de tests optimale selon criticite et risques.

## Quand l'utiliser (triggers)
- Defauts en production malgre tests.
- Couverture desequilibree.
- Flaky tests en hausse.

## Hors périmètre
- Audit securite complet.
- Planification produit long terme.

## Inputs requis
- Features et criticite metier.
- Historique defects.
- Etat actuel de la suite de tests.

## Sorties attendues
- Pyramide de tests cible.
- Plan de couverture par risque.
- Strategie anti-flaky.
- Criteres d'acceptation renforces.

## Workflow recommandé
1. Cartographier risques.
2. Prioriser tests critiques.
3. Definir execution et gates CI.
4. Suivre et reduire la dette de tests.

## Garde-fous
- Tester d'abord les chemins critiques.
- Ne pas maximiser la couverture au detriment de la valeur.
- Isoler les tests instables.

## Template d'entrée (copier/coller)
```text
[Contexte]
- Domaine : ...
- Risques principaux : ...

[Etat actuel]
- Suite tests : ...
- Defects recents : ...
```

## Template de sortie (copier/coller)
```text
[Strategie cible]
- Unitaires : ...
- Integration : ...
- E2E : ...

[Plan 30 jours]
1) ...
2) ...

[KPI]
- ...
```

## Checklist QA interne
- Risques critiques couverts.
- Gates CI explicites.
- Plan de deflaking present.

## KPI reliés
- Defect leakage.
- Flaky rate.
- Couverture des parcours critiques.

## Definition of done
- Strategie test validee et adoptee.
- Reduction mesurable des defects echappes.

## Exemples d'usage

### Exemple 1 : [Titre du cas d'usage]
**Contexte** : [Description de la situation]
**Action** : [Ce qui a été fait]
**Résultat** : [Résultat obtenu]
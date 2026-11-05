# Data Governance & Quality

## Objectif
Garantir qualite, coherences et tracabilite des donnees critiques.

## Quand l'utiliser (triggers)
- KPI incoherents.
- Incidents data repetes.
- Absence de proprietaires des donnees.

## Hors périmètre
- Optimisation SQL ponctuelle sans gouvernance.
- Conformite juridique pure sans qualite data.

## Inputs requis
- Schemas et flux data.
- Regles qualite existantes.
- Historique anomalies.

## Sorties attendues
- Regles qualite formalisees.
- Contrats de donnees.
- Plan de controles automatiques.
- Tableau de score data quality.

## Workflow recommandé
1. Definir dimensions qualite (exactitude, completude, fraicheur).
2. Poser controles et seuils.
3. Mesurer, alerter, corriger.
4. Piloter l'amelioration continue.

## Garde-fous
- Un owner par dataset critique.
- Seuils de qualite explicites.
- Tracabilite des corrections.

## Template d'entrée (copier/coller)
```text
[Donnees]
- Dataset(s) : ...
- Usages critiques : ...

[Problemes]
- Anomalies : ...
- Impact : ...
```

## Template de sortie (copier/coller)
```text
[Regles de qualite]
- R1 : ...
- R2 : ...

[Plan de controle]
1) ...
2) ...

[Remediation]
- Owner : ...
- Echeance : ...
```

## Checklist QA interne
- Owners nommes.
- Controles automatises priorises.
- SLA correction defini.

## KPI reliés
- Data quality score.
- Taux d'anomalies critiques.
- Delai moyen de correction.

## Definition of done
- Regles et controles actifs.
- Baisse mesurable des anomalies critiques.

## Exemples d'usage

### Exemple 1 : [Titre du cas d'usage]
**Contexte** : [Description de la situation]
**Action** : [Ce qui a été fait]
**Résultat** : [Résultat obtenu]
# Cloud Migration Strategy

## Objectif
Définir une stratégie de migration cloud (6R), son séquencement, la gestion des dépendances et les critères de bascule/rollback.

## Quand l'utiliser (triggers)
- « plan de migration », « migre vers le cloud », « lift-and-shift / replatform / refactor ».
- Sortie de datacenter ou consolidation multi-cloud.
- Modernisation progressive d'un legacy.

## Hors périmètre
- Conception de l'architecture cible → skill Cloud Architecture Design.
- Implémentation applicative du refactor → l'agent de développement back-end.

## Inputs requis
- Inventaire des applications et dépendances.
- Contraintes de disponibilité et fenêtres de bascule.
- Objectifs (coût, délai, modernisation).

## Sorties attendues
- Choix de stratégie par application (6R : rehost, replatform, refactor, repurchase, retire, retain).
- Plan de migration phasé et séquencé.
- Risques identifiés et critères de rollback.

## Workflow recommandé
1. Inventorier applications et dépendances.
2. Classer chaque application selon la grille 6R.
3. Séquencer les vagues de migration (dépendances, risques).
4. Définir critères de succès et de rollback par vague.

## Garde-fous
- Toujours prévoir un critère de rollback par vague.
- Ne pas migrer une application sans cartographie de ses dépendances.
- Signaler les applications candidates au retrait (retire).

## Template d'entrée (copier/coller)
```text
[Contexte]
- Applications : ...
- Contraintes de bascule : ...

[Objectif]
- Délai / coût / modernisation : ...
```

## Template de sortie (copier/coller)
```text
[Stratégie 6R]
- App 1 : rehost | replatform | refactor | ...
- App 2 : ...

[Plan phasé]
- Vague 1 : ... | Rollback : ...
- Vague 2 : ...
```

## Checklist QA interne
- Chaque application a une stratégie 6R.
- Chaque vague a un critère de rollback.
- Les dépendances sont cartographiées.

## KPI reliés
- Taux d'applications migrées sans incident.
- Respect des fenêtres de bascule.
- Nombre de rollbacks déclenchés.

## Definition of done
- Stratégie 6R et plan phasé publiés.
- Risques et critères de rollback documentés.
- Prêt pour validation par l'agent de coordination.

## Exemples d'usage

### Exemple 1 : [Titre du cas d'usage]
**Contexte** : [Description de la situation]
**Action** : [Ce qui a été fait]
**Résultat** : [Résultat obtenu]
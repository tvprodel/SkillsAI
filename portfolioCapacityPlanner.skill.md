# Portfolio / Capacity Planner

## Objectif
Aligner capacite equipe agents avec priorites business multi-sprints.

## Quand l'utiliser (triggers)
- Surcharge recurrente.
- Trop de taches en parallele.
- Retards lies aux dependances.

## Hors périmètre
- Micro-planification journaliere.
- Arbitrage technique detaille.

## Inputs requis
- Backlog priorise.
- Capacite disponible (par role/agent).
- Dependances et contraintes calendrier.

## Sorties attendues
- Plan capacitaire.
- Limites WIP.
- Arbitrages explicites.
- Sequencement des dependances.

## Workflow recommandé
1. Evaluer charge et capacite.
2. Identifier goulots.
3. Arbitrer et prioriser.
4. Replanifier et monitorer.

## Garde-fous
- Eviter sur-engagement par sprint.
- Rendre explicites les renoncements.
- Maintenir marge pour incidents.

## Template d'entrée (copier/coller)
```text
[Backlog]
- Items prioritaires : ...

[Capacite]
- Disponibilites : ...

[Contraintes]
- Dates fixes : ...
```

## Template de sortie (copier/coller)
```text
[Plan capacitaire]
- Sprint N : ...
- Sprint N+1 : ...

[Arbitrages]
1) ...
2) ...

[Risques]
- ...
```

## Checklist QA interne
- Capacite realisticement estimee.
- WIP limite defini.
- Dependances critiques adressees.

## KPI reliés
- Throughput.
- WIP age.
- Taux de blocage planning.

## Definition of done
- Plan soutenable valide.
- Arbitrages documentes et partages.

## Exemples d'usage

### Exemple 1 : [Titre du cas d'usage]
**Contexte** : [Description de la situation]
**Action** : [Ce qui a été fait]
**Résultat** : [Résultat obtenu]
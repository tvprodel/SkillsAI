# Observability Engineer

## Objectif
Rendre les systemes observables via logs, metrics, traces et alerting actionnable.

## Quand l'utiliser (triggers)
- Pannes difficiles a diagnostiquer.
- Alertes bruyantes ou insuffisantes.
- Besoin de SLI/SLO formels.

## Hors périmètre
- Feature produit sans enjeu de fiabilite.
- Audit securite pur sans signaux runtime.

## Inputs requis
- Architecture des services.
- Incidents recents.
- Metriques existantes et seuils actuels.

## Sorties attendues
- Matrice SLI/SLO.
- Plan d'instrumentation priorise.
- Dashboard minimum viable.
- Regles d'alerting ciblees.

## Workflow recommandé
1. Identifier parcours critiques.
2. Definir SLI/SLO pertinents.
3. Instrumenter logs/metrics/traces.
4. Mettre en place alertes faibles bruits.

## Garde-fous
- Eviter les dashboards sans decisions associees.
- Preferer alertes symptomatiques aux alertes techniques brutes.
- Limiter les faux positifs.

## Template d'entrée (copier/coller)
```text
[Contexte]
- Service(s) : ...
- Incident(s) recents : ...

[Objectif]
- SLO cible : ...
- Delai de detection souhaite : ...
```

## Template de sortie (copier/coller)
```text
[SLI/SLO]
- SLI 1 : ...
- SLO 1 : ...

[Instrumentation]
1) ...
2) ...

[Alerting]
- Regle 1 : ...
- Seuil : ...
```

## Checklist QA interne
- Chaque alerte a un owner.
- Chaque SLO est mesurable.
- Dashboards orientes decision.

## KPI reliés
- MTTD.
- MTTR.
- Taux de faux positifs alertes.

## Definition of done
- SLI/SLO publies.
- Alertes utiles en production.
- Dashboard principal adopte par l'equipe.

## Exemples d'usage

### Exemple 1 : [Titre du cas d'usage]
**Contexte** : [Description de la situation]
**Action** : [Ce qui a été fait]
**Résultat** : [Résultat obtenu]
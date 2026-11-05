# Incident Commander (SRE / Runbook)

## Objectif
Piloter la reponse aux incidents critiques, coordonner les parties prenantes et reduire le MTTR.

## Quand l'utiliser (triggers)
- Incident prod P1/P2.
- Degradation majeure (latence, erreurs, indisponibilite).
- Blocage cross-equipes sans owner clair.

## Hors périmètre
- Refactor technique long terme sans incident actif.
- Strategie produit non liee a un incident.

## Inputs requis
- Symptomes observes.
- Fenetre temporelle et scope impacte.
- Services/composants potentiellement touches.
- Logs/alertes disponibles.

## Sorties attendues
- Plan de reponse immediate (0-60 min).
- Timeline d'incident.
- Decision de mitigation/rollback.
- Postmortem structure (RCA + actions preventives).

## Workflow recommandé
1. Qualifier severite et impact.
2. Designer owner et cellule de crise.
3. Stabiliser (contournement/rollback).
4. Resoudre la cause racine.
5. Cloturer avec postmortem et plan de prevention.

## Garde-fous
- Prioriser restauration service avant perfection technique.
- Ne pas modifier plusieurs variables critiques en meme temps.
- Tracer chaque decision horodatee.

## Template d'entrée (copier/coller)
```text
[Contexte incident]
- Debut observe : ...
- Services impactes : ...
- Impact utilisateur : ...

[Symptomes]
- Erreurs/latence : ...
- Signaux observabilite : ...

[Contraintes]
- SLA/SLO : ...
- Fenetre de changement : ...
```

## Template de sortie (copier/coller)
```text
[Etat]
- Severite : ...
- Impact confirme : ...
- Statut : Mitige / En cours / Resolue

[Actions 0-60 min]
1) ...
2) ...

[Decision]
- Mitigation/rollback retenu : ...
- Justification : ...

[Postmortem]
- Cause racine : ...
- Actions preventives : ...
- Owners / Echeances : ...
```

## Checklist QA interne
- Impact quantifie.
- Owner unique designe.
- Decision rollback explicite.
- Postmortem complete avec echeances.

## KPI reliés
- MTTR.
- Taux d'incidents recurrents.
- Taux d'incidents sans RCA sous 48h.

## Definition of done
- Service stabilise.
- Cause racine documentee.
- Actions preventives planifiees et assignees.

## Exemples d'usage

### Exemple 1 : [Titre du cas d'usage]
**Contexte** : [Description de la situation]
**Action** : [Ce qui a été fait]
**Résultat** : [Résultat obtenu]
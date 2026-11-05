# Cost Governance (FinOps elargi)

## Objectif
Piloter les couts IA/data de facon continue et previsible.

## Quand l'utiliser (triggers)
- Derive budgetaire.
- Cout par workflow non maitrise.
- Arbitrages qualite/cout non formalises.

## Hors périmètre
- Ajustement technique mineur sans impact cout.
- Decision produit sans contrainte budget.

## Inputs requis
- Budget cible.
- Consommation historique.
- Contraintes qualite/latence.

## Sorties attendues
- Guardrails budgetaires.
- Seuils d'alerte.
- Plan d'optimisation priorise.
- Suivi showback/chargeback.

## Workflow recommandé
1. Etablir baseline de couts.
2. Definir envelopes et quotas.
3. Mettre alerting et revue mensuelle.
4. Iterer sur optimisations.

## Garde-fous
- Ne pas degrader brutalement la qualite.
- Prioriser ROI mesurable.
- Tracer exceptions budgetaires.

## Template d'entrée (copier/coller)
```text
[Budget]
- Cible mensuelle : ...
- Seuil alerte : ...

[Consommation]
- Top couts : ...
- Variance : ...
```

## Template de sortie (copier/coller)
```text
[Guardrails]
- Regle 1 : ...

[Optimisations]
1) ... (gain estime)
2) ... (gain estime)

[Suivi]
- KPI mensuel : ...
```

## Checklist QA interne
- Budget et seuils publies.
- Gains estimes quantifies.
- Owners de suivi designes.

## KPI reliés
- Cout par tache/workflow.
- Variance budget.
- ROI optimisation.

## Definition of done
- Budget stabilise avec visibilite mensuelle.
- Plan d'optimisation en execution.

## Exemples d'usage

### Exemple 1 : [Titre du cas d'usage]
**Contexte** : [Description de la situation]
**Action** : [Ce qui a été fait]
**Résultat** : [Résultat obtenu]
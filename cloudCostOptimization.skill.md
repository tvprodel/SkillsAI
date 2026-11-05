# Cloud Cost Optimization

## Objectif
Réduire la facture cloud via right-sizing, achats optimisés (reserved/savings plans) et élimination des ressources orphelines, sans dégrader le SLA.

## Quand l'utiliser (triggers)
- « optimise les coûts », « audit FinOps », « pourquoi la facture cloud augmente ».
- Dérive de coûts inexpliquée.
- Préparation d'un engagement reserved/savings plan.

## Hors périmètre
- Coûts IA/LLM (tokens, modèles) → l'agent FinOps.
- Refonte d'architecture → skill Cloud Architecture Design.

## Inputs requis
- Inventaire des ressources et dimensionnement actuel.
- Données de facturation / utilisation.
- SLA et contraintes de disponibilité.

## Sorties attendues
- Liste priorisée d'actions d'optimisation.
- Estimation d'économie par action (€/mois).
- Effort de mise en œuvre et risque associé.

## Workflow recommandé
1. Cartographier les coûts par service et par usage.
2. Identifier sous-utilisation, orphelins et sur-dimensionnement.
3. Prioriser par ratio économie/effort.
4. Recommander achats engagés (reserved/savings) si pertinents.

## Garde-fous
- Ne pas dégrader le SLA pour économiser.
- Chiffrer chaque recommandation (économie + effort).
- Distinguer économies récurrentes et ponctuelles.

## Template d'entrée (copier/coller)
```text
[Contexte]
- Périmètre facturé : ...
- SLA à préserver : ...

[Objectif]
- Cible d'économie : ...
```

## Template de sortie (copier/coller)
```text
[Actions priorisées]
1) Action : ... | Économie : ... €/mois | Effort : ...
2) ...

[Achats engagés]
- Recommandation : ...
```

## Checklist QA interne
- Chaque action est chiffrée.
- SLA préservé.
- Priorisation économie/effort explicite.

## KPI reliés
- Économie mensuelle réalisée.
- Taux de ressources orphelines éliminées.
- Couverture reserved/savings.

## Definition of done
- Plan d'optimisation priorisé et chiffré.
- Risques sur le SLA identifiés.
- Passage de relais recommandé au FinOps pour le suivi récurrent.

## Exemples d'usage

### Exemple 1 : [Titre du cas d'usage]
**Contexte** : [Description de la situation]
**Action** : [Ce qui a été fait]
**Résultat** : [Résultat obtenu]
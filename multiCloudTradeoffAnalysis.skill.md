# Multi-Cloud Tradeoff Analysis

## Objectif
Fournir une analyse comparative objective entre providers (AWS vs Azure vs GCP) ou stratégies (mono vs multi-cloud) sur des critères explicites.

## Quand l'utiliser (triggers)
- « compare AWS vs Azure vs GCP », « faut-il rester multi-cloud ».
- Choix ou remise en question d'un provider stratégique.
- Évaluation du risque de lock-in.

## Hors périmètre
- Décision stratégique finale → escalade à l'agent de coordination / décision humaine.
- Conception détaillée de l'architecture cible → skill Cloud Architecture Design.

## Inputs requis
- Critères de décision pondérés (coût, écosystème, lock-in, compétences internes).
- Contraintes de conformité et de résidence.
- Compétences et outillage existants de l'équipe.

## Sorties attendues
- Tableau comparatif par critère.
- Recommandation argumentée.
- Risques du choix (dont lock-in) et conditions de réversibilité.

## Workflow recommandé
1. Formaliser et pondérer les critères de décision.
2. Évaluer chaque provider/stratégie par critère.
3. Synthétiser en tableau comparatif.
4. Recommander en explicitant risques et réversibilité.

## Garde-fous
- Rester objectif : pas de biais provider non justifié.
- Distinguer faits vérifiables et hypothèses.
- Ne pas trancher une décision de gouvernance : escalader à l'agent de coordination.

## Template d'entrée (copier/coller)
```text
[Contexte]
- Critères pondérés : ...
- Contraintes : ...

[Objectif]
- Décision à éclairer : ...
```

## Template de sortie (copier/coller)
```text
[Tableau comparatif]
| Critère | AWS | Azure | GCP |
|---------|-----|-------|-----|
| ...     | ... | ...   | ... |

[Recommandation]
- Choix : ...
- Risques / réversibilité : ...
```

## Checklist QA interne
- Critères pondérés et explicites.
- Faits distingués des hypothèses.
- Risque de lock-in évalué.

## KPI reliés
- Nombre de critères objectivés.
- Adéquation choix vs compétences internes.
- Réversibilité estimée du choix.

## Definition of done
- Tableau comparatif et recommandation publiés.
- Risques et réversibilité documentés.
- Escalade l'agent de coordination préparée si décision de gouvernance.

## Exemples d'usage

### Exemple 1 : [Titre du cas d'usage]
**Contexte** : [Description de la situation]
**Action** : [Ce qui a été fait]
**Résultat** : [Résultat obtenu]
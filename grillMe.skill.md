# Grill Me (Clarification Socratique)

## ⚠️ Distinction importante avec « Roast My Idea »
Cette skill est **différente** de la skill [Roast My Idea (Feedback Tough Love)](./roastMyIdea.skill.md), qui évalue et critique une idée déjà formulée avec un verdict tranché. **Grill Me** fait l'inverse : elle **n'émet aucun jugement**, elle interroge méthodiquement l'utilisateur pour construire une compréhension partagée d'un plan **avant** de l'exécuter. Ne pas confondre les deux déclencheurs.

## Origine
Reproduction fidèle du skill `/grill-me` créé par **Matt Pocock** (formateur reconnu Claude/Cursor), devenu viral en 2026. Source : [aihero.dev/my-grill-me-skill-has-gone-viral](https://www.aihero.dev/my-grill-me-skill-has-gone-viral), [repo GitHub officiel](https://github.com/mattpocock/skills).

## Objectif
Interroger l'utilisateur sans relâche sur chaque aspect d'un plan ou d'un design, jusqu'à atteindre une compréhension partagée, en descendant branche par branche l'arbre de décision et en résolvant les dépendances entre décisions une par une. Ce n'est **pas** du « roasting » : le but est la clarification, pas l'évaluation.

## Quand l'utiliser (triggers)
- « /grill-me », « grill me », « grillme ».
- « interroge-moi sur ce plan », « stress-teste mon design par des questions », « aide-moi à clarifier ce plan avant de le réaliser ».

## Hors périmètre
- Ne critique pas, n'évalue pas, ne donne aucun verdict Go/No-Go → utiliser [Roast My Idea (Feedback Tough Love)](./roastMyIdea.skill.md) si un jugement tranché est souhaité.
- Ne remplace pas une revue technique formelle multi-domaines (renvoyer vers l'agent spécialisé concerné si le plan touche à un domaine expert précis).

## Inputs requis
- Le plan, le design ou le projet à clarifier.
- Accès au contexte disponible (codebase, documentation existante) si pertinent — à explorer avant de questionner si une réponse peut en être déduite.

## Sorties attendues
- Une série de questions, une par branche/dépendance du plan, jusqu'à couverture complète de l'arbre de décision.
- Pour chaque question posée, une **réponse recommandée** proposée par l'agent (l'utilisateur valide ou corrige).
- Une synthèse finale de compréhension partagée une fois toutes les branches résolues.

## Workflow recommandé
1. Identifier l'arbre de décision du plan/design soumis (les grandes branches et leurs dépendances).
2. Explorer la codebase/le contexte disponible **avant** de poser une question si la réponse peut en être déduite directement.
3. Interroger l'utilisateur branche par branche, une dépendance à la fois — jamais un bloc de questions en vrac.
4. Pour chaque question, proposer une réponse recommandée argumentée, que l'utilisateur peut valider ou corriger.
5. Poursuivre jusqu'à résolution complète de toutes les branches du design.
6. Synthétiser la compréhension partagée finale (pas de jugement, uniquement un récapitulatif validé).

## Garde-fous
- Aucun jugement de valeur sur le plan — uniquement des questions et des recommandations de réponse.
- Une question à la fois, jamais une liste exhaustive envoyée d'un bloc (respecter le principe "branche par branche").
- Toujours proposer une réponse recommandée avec chaque question (ne pas se contenter d'interroger sans apporter de valeur ajoutée).
- Si le contexte permet de répondre soi-même à une question (exploration de code/doc), le faire plutôt que de solliciter l'utilisateur inutilement.

## Template d'entrée (copier/coller)
```text
[Plan / Design à clarifier]
- Description : ...
- Contexte disponible (codebase, doc) : ...
```

## Template de sortie (copier/coller)
```text
[Question N — Branche : <nom de la branche/dépendance>]
- Question : ...
- Réponse recommandée : ...

[...répéter branche par branche...]

[Synthèse de compréhension partagée]
- Récapitulatif des décisions validées : ...
```

## Checklist QA interne
- Aucun verdict ou jugement de valeur émis (pure clarification).
- Chaque question est accompagnée d'une réponse recommandée argumentée.
- Les questions progressent branche par branche, pas en vrac.
- Le contexte disponible a été exploré avant de solliciter l'utilisateur si possible.

## KPI reliés
- Taux de plans clarifiés sans aller-retour supplémentaire après la session Grill Me.
- Nombre de dépendances/ambiguïtés résolues avant le début de l'exécution.

## Definition of done
- Toutes les branches identifiées du plan ont été explorées et validées avec l'utilisateur.
- Une synthèse de compréhension partagée finale a été produite.

## Exemples d'usage

### Exemple 1 : Clarification d'un plan de refonte agent
**Contexte** : L'utilisateur propose de refondre la structure de délégation d'un agent sans détailler les cas limites.
**Action** : l'agent de coordination explore d'abord le fichier agent existant, puis interroge branche par branche : gestion des agents feuilles, cas de boucle de délégation, format de sortie — avec une réponse recommandée à chaque question.
**Résultat** : Le plan est validé point par point avant toute modification de fichier.

### Exemple 2 : Clarification d'un plan de migration technique
**Contexte** : L'utilisateur veut migrer un script sans préciser la stratégie de compatibilité ascendante.
**Action** : l'agent de coordination interroge sur la gestion des appelants existants, la stratégie de rollback, le format de sortie attendu — une question à la fois avec proposition de réponse.
**Résultat** : Compréhension partagée établie avant le début de l'implémentation.

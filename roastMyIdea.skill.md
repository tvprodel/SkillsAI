# Roast My Idea (Feedback Tough Love)

## ⚠️ Distinction importante avec « Grill Me »
Cette skill est **différente** de la skill [Grill Me (Clarification Socratique)](./grillMe.skill.md), qui interroge l'utilisateur pour clarifier un plan avant de le réaliser. **Roast My Idea** fait l'inverse : elle **évalue et critique** une idée déjà formulée, avec un verdict tranché. Ne pas confondre les deux déclencheurs.

## Objectif
Fournir une critique franche, directe et sans complaisance sur une idée, un brief ou un projet, façon investisseur/VC qui évalue un pitch, en exposant sans filtre ses faiblesses, ses angles morts et ses risques, pour muscler la réflexion avant l'action.

## Quand l'utiliser (triggers)
- « /roast-my-idea », « roast mon idée/projet/startup », « grille-moi ça » (usage courant FR, distinct du skill anglophone `/grill-me`).
- « sois brutal/cash avec moi », « critique sans filtre », « avis sans complaisance », « tacle mon idée ».
- « trouve les failles », « joue l'avocat du diable », « challenge mon plan », « évalue comme un investisseur ».

## Hors périmètre
- Validation technique approfondie multi-domaines (renvoyer vers l'agent spécialisé concerné : sécurité, architecture, légal, etc.).
- Ne remplace pas un audit sécurité/qualité formel (l'agent de sécurité, l'agent qualité).
- Ne remplace pas la skill [Grill Me (Clarification Socratique)](./grillMe.skill.md) : si l'utilisateur veut être interrogé point par point pour clarifier un plan (pas jugé), rediriger vers cette skill.
- Aucune attaque personnelle : la critique porte uniquement sur l'idée/le livrable, jamais sur la personne.

## Inputs requis
- L'idée, le brief ou le projet à challenger.
- Le contexte : objectif visé, contraintes connues, public cible.
- Niveau de dureté souhaité (optionnel, défaut : direct mais constructif).
- Posture de jugement souhaitée (optionnel, défaut : investisseur/VC évaluant un pitch).

## Sorties attendues
- **Score global /10**, avec justification synthétique (inspiré du pattern « Roast My Startup »).
- Liste des faiblesses et angles morts identifiés, classés par gravité.
- Objections les plus fortes (posture avocat du diable / investisseur).
- Questions qui feraient échouer le projet si elles restent sans réponse.
- Verdict global explicite (Go / Non-Go / À retravailler).
- 1 à 3 recommandations concrètes et actionnables.

## Workflow recommandé
1. Reformuler l'idée/le projet en une phrase pour valider la compréhension.
2. Adopter la posture de jugement choisie (par défaut : investisseur évaluant un pitch de financement).
3. Identifier les hypothèses non vérifiées et les angles morts.
4. Chercher activement les objections les plus solides (posture avocat du diable).
5. Prioriser les failles détectées par impact potentiel.
6. Attribuer un score /10 justifié.
7. Rendre un verdict clair assorti de recommandations actionnables.

## Garde-fous
- Chaque critique doit être argumentée : jamais de jugement gratuit ou non justifié.
- Critiquer l'idée/le travail, jamais la personne ; ton direct mais toujours respectueux et professionnel.
- Ne jamais édulcorer pour « faire plaisir » : la valeur du skill est la franchise.
- Toujours terminer par au moins une piste d'amélioration concrète (pas de critique stérile).
- Le score /10 est toujours accompagné d'une justification (jamais un chiffre seul).

## Template d'entrée (copier/coller)
```text
[Idée / Brief / Projet à challenger]
- Description : ...
- Objectif visé : ...
- Contraintes connues : ...

[Niveau de dureté souhaité]
- Standard (direct et constructif) / Sans filtre (très cash)

[Posture de jugement souhaitée] (optionnel)
- Investisseur/VC (défaut) / Avocat du diable senior / Client final exigeant
```

## Template de sortie (copier/coller)
```text
[Score global]
- /10 — Justification synthétique : ...

[Verdict]
- Statut : Go / Non-Go / À retravailler

[Failles identifiées] (par gravité)
1) ... (impact : ...)
2) ...

[Objections les plus fortes]
- ...

[Questions qui feraient échouer le projet sans réponse]
- ...

[Recommandations concrètes]
1) ...
2) ...
```

## Checklist QA interne
- Chaque critique est argumentée, pas d'opinion gratuite.
- Aucune attaque personnelle : uniquement sur le fond.
- Score /10 justifié et cohérent avec les failles listées.
- Au moins une recommandation actionnable fournie.
- Verdict clair rendu (Go / Non-Go / À retravailler).

## KPI reliés
- Taux d'idées/briefs améliorés après passage au « roast ».
- Nombre de failles majeures détectées en amont (évitées en aval du projet).

## Definition of done
- Score, verdict et recommandations livrés dans le format de sortie standard.
- Aucune faille majeure connue laissée sans mention.

## Exemples d'usage

### Exemple 1 : Brief produit challengé
**Contexte** : Un utilisateur propose de lancer une nouvelle fonctionnalité sans donnée de validation marché.
**Action** : l'agent de coordination adopte la posture investisseur, questionne la taille du marché cible, le ROI attendu et pointe l'absence de validation utilisateur. Score attribué : 4/10.
**Résultat** : L'utilisateur revoit son brief en ajoutant une phase de test utilisateur avant développement.

### Exemple 2 : Plan de migration technique
**Contexte** : Un plan de migration serveur est proposé sans stratégie de rollback ni fenêtre de test.
**Action** : l'agent de coordination relève l'absence de plan de rollback et l'optimisme du planning, pose les questions qui feraient échouer la migration. Score attribué : 5/10.
**Résultat** : Un plan de contingence et une fenêtre de test sont ajoutés avant validation finale.

## Contraintes et références
- Pattern « Roast My Startup/Idea », largement documenté : [roastgpt.ai](https://roastgpt.ai/roasts/roast-my-startup), [theresanaiforthat.com](https://theresanaiforthat.com/gpt/roast-my-startup/), [roastmystartup.ai](https://roastmystartup.ai/), [roastidea.com](https://www.roastidea.com/roast).

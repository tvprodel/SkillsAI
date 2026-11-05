# Notarial Appointment Preparation

## Objectif
Aider l'utilisateur à préparer un rendez-vous avec un notaire en clarifiant son objectif, en organisant ses questions et en résumant les points à confirmer, sans donner d'avis juridique individualisé.

## Quand l'utiliser (triggers)
- L'utilisateur prépare un rendez-vous ou un appel avec un notaire en Belgique.
- Il souhaite écrire un ordre du jour ou un résumé de situation à transmettre au notaire.
- Il veut formuler des questions sur les étapes, pièces, délais ou coûts à confirmer.

## Hors périmètre
- Répondre aux questions de droit propres au dossier à la place du notaire.
- Recommander une option patrimoniale, successorale ou contractuelle.
- Rédiger ou réviser un acte, testament, contrat ou clause à signer.
- Déterminer les frais, taxes, conséquences ou délais applicables à une situation individuelle.

## Inputs requis
- Objectif du rendez-vous, formulé de manière générale.
- Éléments factuels que l'utilisateur souhaite communiquer, anonymisés et non interprétés.
- Questions ou documents que l'utilisateur souhaite évoquer.
- Date ou échéance du rendez-vous, si utile pour prioriser le contact avec l'étude.

## Sorties attendues
- Résumé neutre de l'objectif et des faits que l'utilisateur choisit de présenter.
- Questions ouvertes regroupées par thème.
- Liste des pièces et échéances à confirmer avec l'étude.
- Rappel que le notaire doit donner les réponses et conseils propres au dossier.

## Workflow recommandé
1. Clarifier le résultat pratique attendu du rendez-vous.
2. Organiser les faits rapportés sans ajouter d'interprétation juridique.
3. Regrouper les questions sur procédure, documents, délais, coûts et options juridiques.
4. Formuler les points propres au dossier comme questions à poser au notaire, et non comme conclusions.
5. Faire vérifier à l'utilisateur que le résumé reflète ses propos.
6. Pour une échéance urgente, conseiller de contacter immédiatement l'étude au lieu d'attendre le rendez-vous ou une réponse de l'agent.

## Garde-fous
- Ne pas transformer des faits en droits, obligations ou recommandations.
- Ne pas préjuger de la réponse du notaire ni promettre qu'une option est préférable.
- Ne pas inclure de données identifiantes dans le résumé.
- Ne pas retarder une prise de contact urgente avec l'étude.
- Toute interprétation d'un acte ou choix juridique doit être demandé au notaire chargé du dossier.

## Template d'entrée (copier/coller)
```text
Objectif général du rendez-vous :
Faits à présenter (sans identifiants) :
Questions déjà identifiées :
Documents ou délais à clarifier :
Date du rendez-vous (facultatif) :
```

## Template de sortie (copier/coller)
```text
Résumé neutre :

Questions à poser :
1. Procédure :
2. Documents :
3. Délais et coûts :
4. Options et conséquences juridiques :

À confirmer avec l'étude :
Rappel : seul le notaire chargé du dossier peut répondre pour la situation individuelle.
```

## Checklist QA interne
- [ ] Le résumé conserve une formulation neutre et fidèle aux faits fournis.
- [ ] Les questions sont ouvertes et destinées au notaire, sans proposer de réponse.
- [ ] Aucun choix juridique ou patrimonial n'est recommandé.
- [ ] Les informations identifiantes ont été supprimées ou évitées.
- [ ] Une échéance urgente entraîne une recommandation de contacter l'étude immédiatement.

## KPI reliés
- Proportion de préparations contenant des questions concrètes, neutres et organisées.
- Nombre de recommandations juridiques individualisées (cible : zéro).
- Proportion de résumés vérifiés par l'utilisateur comme fidèles à ses propos.

## Definition of done
- [ ] L'utilisateur dispose d'un ordre du jour ou de questions prêtes à poser.
- [ ] Les faits sont présentés sans interprétation juridique.
- [ ] Les points propres au dossier sont explicitement réservés au notaire.
- [ ] Les données sensibles inutiles sont absentes.

## Exemples d'usage
### Exemple 1 : Rendez-vous sur une donation
**Contexte** : L'utilisateur a un rendez-vous prochainement et veut comparer les questions à poser sans recevoir de recommandation.  
**Input** : « Prépare une liste neutre de questions sur la procédure, les coûts à confirmer et les conséquences à discuter avec mon notaire. »  
**Output** : Un ordre du jour organisé, qui invite le notaire à expliquer les options et conséquences adaptées au dossier sans recommander une option.

### Exemple 2 : Échéance proche
**Contexte** : L'utilisateur doit répondre prochainement à un courrier d'une étude et ne comprend pas une échéance.  
**Input** : « J'ai une date limite cette semaine; aide-moi à préparer les questions pour le notaire. »  
**Output** : Recommander de contacter directement l'étude sans attendre, puis fournir une courte liste de questions sur la date, les documents attendus et les conséquences à faire expliquer.

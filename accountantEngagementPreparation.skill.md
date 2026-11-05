# Accountant Meeting & Document Preparation

## Objectif
Aider particuliers, indépendants et PME à préparer un échange avec leur comptable en organisant les questions et documents utiles, sans valider une déclaration ou un traitement professionnel.

## Quand l'utiliser (triggers)
- L'utilisateur prépare un rendez-vous ou un premier contact avec un expert-comptable en Belgique.
- Il veut organiser une liste de pièces demandées ou préparer une clôture.
- Il souhaite résumer une situation financière anonymisée et formuler des questions.

## Hors périmètre
- Garantir qu'une liste de pièces est exhaustive ou suffisante pour une obligation légale.
- Interpréter définitivement un document fiscal, comptable ou juridique.
- Rédiger, déposer ou certifier des comptes, déclarations ou rapports réglementaires.
- Recommander une décision fiscale, financière ou patrimoniale.

## Inputs requis
- Objectif et date de l'échange, si disponible.
- Type général de contribuable ou d'entité (particulier, indépendant, société).
- Liste des documents demandés et disponibles, par intitulé uniquement.
- Questions ou événements à discuter, formulés sans données identifiantes.

## Sorties attendues
- Ordre du jour concis et questions regroupées par thème.
- Checklist des documents demandés, disponibles et à confirmer.
- Résumé neutre de la situation communiqué par l'utilisateur.
- Rappel des éléments à transmettre de façon sécurisée directement au comptable.

## Workflow recommandé
1. Clarifier le résultat attendu du rendez-vous et l'échéance.
2. Classer les pièces selon leur statut : demandées, disponibles, à confirmer.
3. Regrouper les questions en comptabilité, TVA/fiscalité, clôture et prochaines actions.
4. Reformuler les faits sans interprétation ni conclusion de conformité.
5. Vérifier auprès de l'utilisateur que le résumé est fidèle et ne contient pas de données superflues.
6. Diriger les documents sensibles vers le canal sécurisé indiqué par le professionnel.

## Garde-fous
- Présenter toute checklist comme indicative, sauf si elle reproduit la liste fournie par le comptable.
- Ne pas ajouter de pièces présentées comme obligatoires sans source ou confirmation professionnelle.
- Ne pas demander de documents complets lorsqu'un intitulé anonymisé suffit.
- Ne pas exposer de numéro national, identifiant d'entreprise, donnée bancaire ou information salariale nominative.
- Ne pas retarder une échéance : recommander de contacter directement le professionnel ou l'administration concernée.

## Template d'entrée (copier/coller)
```text
Objectif du rendez-vous :
Type général d'entité :
Date/échéance (facultatif) :
Pièces demandées par le comptable (intitulés uniquement) :
Pièces déjà disponibles (intitulés uniquement) :
Questions à poser :
```

## Template de sortie (copier/coller)
```text
Résumé neutre :
Ordre du jour :
Checklist indicative :
- Demandé par le comptable :
- Disponible :
- À confirmer :
Questions prioritaires :
Canal sécurisé de transmission à confirmer :
```

## Checklist QA interne
- [ ] Les faits sont restitués sans interprétation comptable ou fiscale.
- [ ] Les pièces demandées par le comptable sont distinguées des suggestions.
- [ ] Les éléments propres au dossier restent des questions à poser.
- [ ] Les informations identifiantes et financières sensibles sont minimisées.
- [ ] Les échéances proches entraînent une recommandation de contact direct.

## KPI reliés
- Proportion de préparations présentant des questions concrètes et organisées.
- Nombre de checklists présentées comme exhaustives sans confirmation (cible : zéro).
- Nombre de données identifiantes ou financières sensibles reproduites (cible : zéro).

## Definition of done
- [ ] L'utilisateur dispose d'un ordre du jour ou d'une checklist utilisable.
- [ ] Les pièces et exigences non confirmées sont clairement signalées.
- [ ] Les conseils propres au dossier sont réservés au professionnel qualifié.
- [ ] Les documents sensibles sont dirigés vers un canal sécurisé.

## Exemples d'usage
### Exemple 1 : Première rencontre
**Contexte** : Une personne qui lance une activité indépendante veut préparer son premier échange avec un comptable.  
**Input** : « Aide-moi à organiser mes questions sur la tenue de comptabilité et les documents à demander, sans supposer quelles obligations s'appliquent à mon activité. »  
**Output** : Un ordre du jour et une checklist indicative, avec les points de régime, calendrier et pièces à faire confirmer par le comptable.

### Exemple 2 : Clôture annuelle
**Contexte** : Une PME rassemble les pièces pour sa clôture annuelle et veut suivre ce qui manque.  
**Input** : « Voici les titres anonymisés demandés par notre comptable; transforme-les en checklist avec statuts et questions de suivi. »  
**Output** : Une checklist qui reprend la demande du professionnel sans l'étendre, identifie les éléments manquants et rappelle d'utiliser le canal sécurisé de l'étude.

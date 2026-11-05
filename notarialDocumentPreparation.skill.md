# Notarial Document Preparation

## Objectif
Aider à organiser et anonymiser les documents avant un échange avec une étude notariale, sans prétendre établir une liste exhaustive de pièces obligatoires.

## Quand l'utiliser (triggers)
- L'utilisateur veut préparer des pièces pour une démarche notariale belge.
- Il demande une checklist indicative avant de contacter son notaire.
- Il souhaite organiser un dossier ou comprendre à qui demander une pièce.

## Hors périmètre
- Garantir qu'une liste de documents est complète ou juridiquement suffisante.
- Examiner les documents pour déterminer les droits ou obligations de l'utilisateur.
- Modifier, rédiger ou valider un acte, une déclaration ou un contrat.
- Demander le partage non anonymisé d'actes, identifiants ou données financières.

## Inputs requis
- Type général de démarche notariale.
- État du dossier (prise de contact, préparation du rendez-vous ou demande de pièces reçue).
- Liste de documents déjà détenus, sans contenu identifiant.
- Région ou situation locale seulement si nécessaire à la recherche d'une exigence officielle.

## Sorties attendues
- Liste de préparation indicative et organisée par catégorie.
- Questions à poser à l'étude sur les pièces manquantes, formats et modalités de transmission.
- Rappel des informations qui doivent être confirmées selon le dossier.
- Conseils de minimisation et d'anonymisation des documents partagés avec l'assistant.

## Workflow recommandé
1. Identifier la démarche et l'étape du dossier.
2. Si une checklist spécifique est requise, consulter les consignes officielles de l'étude ou une source belge fiable.
3. Classer les pièces envisagées en « demandées par l'étude », « déjà disponibles » et « à confirmer ».
4. Éviter d'inférer des obligations à partir d'une simple liste indicative.
5. Proposer des questions concrètes sur l'original, la copie, la traduction, la validité et le canal de transmission.
6. Rappeler de transmettre les pièces sensibles directement à l'étude via le canal sécurisé qu'elle indique.

## Garde-fous
- Toute liste produite est indicative tant que l'étude notariale ne l'a pas confirmée.
- Ne pas inventer qu'une pièce est obligatoire ou qu'un document est suffisant.
- Ne pas recevoir des pièces contenant des numéros nationaux, données bancaires ou adresses si un résumé anonymisé suffit.
- Ne pas conseiller de modifier une pièce ou de faire une déclaration juridique sans confirmation du notaire.
- En cas de délai court, recommander de contacter directement l'étude plutôt que de supposer les exigences.

## Template d'entrée (copier/coller)
```text
Démarche concernée :
Étape actuelle du dossier :
Pièces déjà demandées par l'étude (titres uniquement) :
Pièces déjà disponibles (titres uniquement) :
Question à confirmer :
```

## Template de sortie (copier/coller)
```text
Checklist indicative :
- Demandé/confirmé par l'étude :
- À vérifier :
- Déjà disponible :

Questions à poser à l'étude :
Canal de transmission à confirmer :
Rappel : la checklist doit être confirmée par le notaire chargé du dossier.
```

## Checklist QA interne
- [ ] La liste est clairement présentée comme indicative si elle n'a pas été fournie par l'étude.
- [ ] Les pièces exigées par l'étude sont distinguées des suggestions générales.
- [ ] Les modalités de transmission et les délais sont renvoyés à l'étude.
- [ ] Aucun contenu personnel sensible n'est répété inutilement.
- [ ] Aucun document n'est déclaré juridiquement suffisant ou valide.

## KPI reliés
- Proportion de checklists distinguant les pièces confirmées de celles à vérifier.
- Nombre de réponses affirmant une liste exhaustive sans source de l'étude (cible : zéro).
- Nombre de données identifiantes répétées dans la sortie (cible : zéro).

## Definition of done
- [ ] L'utilisateur dispose d'une liste organisée des éléments à confirmer ou à rassembler.
- [ ] Les limites de la checklist sont explicites.
- [ ] Les questions de transmission et d'échéance sont dirigées vers l'étude.
- [ ] La réponse n'expose ni ne sollicite de données personnelles superflues.

## Exemples d'usage
### Exemple 1 : Préparer un premier contact
**Contexte** : L'utilisateur souhaite envoyer un premier message à une étude notariale pour une démarche immobilière.  
**Input** : « Aide-moi à lister les catégories de documents que je peux préparer et les questions à poser; ne suppose pas lesquels sont obligatoires. »  
**Output** : Des catégories indicatives de pièces à évoquer, avec une demande de confirmation auprès de l'étude et des questions sur les formats et l'envoi sécurisé.

### Exemple 2 : Répondre à une demande de pièces
**Contexte** : L'étude a envoyé une liste et l'utilisateur veut organiser son suivi.  
**Input** : « Voici les intitulés non sensibles des pièces demandées; aide-moi à faire une checklist sans examiner les documents. »  
**Output** : Une checklist reprenant les éléments de l'étude, des colonnes de statut et des questions de clarification, sans ajouter de pièces prétendument obligatoires.

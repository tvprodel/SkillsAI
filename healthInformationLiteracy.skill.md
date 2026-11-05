# Health Information Literacy

## Objectif
Fournir une explication accessible et prudente d'informations générales sur la santé, en distinguant les connaissances générales des décisions cliniques individuelles.

## Quand l'utiliser (triggers)
- L'utilisateur demande une explication générale d'un terme, d'un concept ou d'une information de santé.
- Il souhaite trouver ou comparer des sources publiques fiables.
- Il veut comprendre une information médicale sans demander un diagnostic ou un plan de traitement personnel.

## Hors périmètre
- Diagnostiquer une maladie ou déterminer la cause d'un symptôme.
- Prescrire, recommander un dosage ou conseiller de commencer, arrêter ou modifier un traitement.
- Remplacer une évaluation par un professionnel de santé.
- Interpréter un examen individuel comme une conclusion clinique.

## Inputs requis
- Question ou terme à expliquer.
- Public visé et niveau de détail souhaité, si cela influence la réponse.
- Pays ou juridiction, si l'accès aux services ou les recommandations locales sont pertinents.
- Source ou extrait anonymisé, si l'utilisateur demande une explication d'un document.

## Sorties attendues
- Explication en langage clair et à portée générale.
- Limites, incertitudes et facteurs personnels susceptibles de modifier l'interprétation.
- Sources publiques fiables, avec liens et dates lorsqu'une recherche web est nécessaire.
- Prochaine étape prudente lorsque la question concerne une situation personnelle.

## Workflow recommandé
1. Reformuler la demande pour vérifier qu'elle est informative et non diagnostique.
2. Répondre avec des termes simples, en définissant les notions techniques.
3. Vérifier l'actualité des informations lorsque le sujet est susceptible d'évoluer ou dépend de recommandations locales.
4. Privilégier des sources d'autorités de santé publiques, d'organismes médicaux reconnus ou de publications professionnelles.
5. Citer les sources réellement consultées et séparer les faits des incertitudes.
6. Recommander un professionnel de santé pour toute décision individualisée.

## Garde-fous
- Ne jamais déduire un diagnostic à partir d'un symptôme, d'un résultat ou d'un texte isolé.
- Ne pas présenter une moyenne ou une recommandation générale comme applicable à chaque personne.
- Ne pas inventer de source, de date, de statistique ou de recommandation.
- Éviter les affirmations absolues et la fausse assurance.
- Ne pas demander d'identifiants ni d'informations médicales qui ne sont pas nécessaires.
- Si un danger immédiat est décrit, cesser l'explication ordinaire et orienter immédiatement vers les services d'urgence locaux.

## Template d'entrée (copier/coller)
```text
Question d'information générale :
Terme ou extrait anonymisé (facultatif) :
Pays (si pertinent) :
Niveau de détail souhaité :
```

## Template de sortie (copier/coller)
```text
Explication générale :
Ce que cela ne permet pas de conclure :
Incertitudes ou facteurs individuels :
Sources consultées (titre, organisme, date, lien) :
Prochaine étape prudente :
```

## Checklist QA interne
- [ ] La réponse explique une information générale sans conclure sur le cas individuel.
- [ ] Les limites et incertitudes sont visibles.
- [ ] Les références citées ont réellement été consultées.
- [ ] Les sources sont appropriées et suffisamment actuelles pour le sujet.
- [ ] Aucun renseignement personnel non nécessaire n'est demandé ou exposé.

## KPI reliés
- Proportion de réponses sourcées lorsque la recherche web est requise.
- Nombre de réponses contenant une conclusion clinique individualisée (cible : zéro).
- Proportion de réponses mentionnant les limites pertinentes.

## Definition of done
- [ ] La question a reçu une explication claire, générale et compréhensible.
- [ ] Les limites de l'information disponible sont explicites.
- [ ] Les sources ont été vérifiées ou l'absence de source vérifiée est déclarée.
- [ ] Toute décision clinique individuelle est renvoyée à un professionnel habilité.

## Exemples d'usage
### Exemple 1 : Comprendre un terme
**Contexte** : L'utilisateur rencontre le terme « tension artérielle » dans une brochure de santé.  
**Input** : « Explique-moi simplement ce que signifie la tension artérielle, sans interpréter mes mesures. »  
**Output** : Une définition générale, une explication de l'objectif des mesures et une précision qu'un professionnel doit interpréter les valeurs individuelles dans leur contexte.

### Exemple 2 : Vérifier une source
**Contexte** : L'utilisateur veut lire une information récente sur la vaccination dans son pays.  
**Input** : « Où trouver une source fiable en Belgique sur les recommandations vaccinales actuelles ? »  
**Output** : Des liens vérifiés vers les autorités compétentes, la date de consultation et une note indiquant que les recommandations peuvent évoluer.

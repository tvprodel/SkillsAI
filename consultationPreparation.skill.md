# Medical Consultation Preparation

## Objectif
Aider l'utilisateur à organiser les informations qu'il souhaite partager et préparer des questions pour un professionnel de santé, sans orienter le diagnostic ni le traitement.

## Quand l'utiliser (triggers)
- L'utilisateur prépare un rendez-vous médical ou souhaite mieux utiliser le temps de consultation.
- Il veut résumer ses observations ou organiser une chronologie de symptômes.
- Il cherche des questions à poser sur un terme, un examen ou un document médical.

## Hors périmètre
- Diagnostiquer ou suggérer une cause probable.
- Déterminer si un traitement doit être commencé, arrêté ou modifié.
- Remplacer la consultation ou interpréter un résultat médical individuel.
- Demander, conserver ou reproduire des identifiants personnels ou un dossier médical complet.

## Inputs requis
- Objectif du rendez-vous ou question principale.
- Observations que l'utilisateur souhaite transmettre, avec dates approximatives si utiles.
- Traitements et antécédents uniquement si l'utilisateur les juge pertinents pour préparer ses questions.
- Document ou résultat anonymisé, seulement si une explication générale est demandée.

## Sorties attendues
- Résumé neutre des éléments fournis par l'utilisateur.
- Liste de questions ouvertes à poser au professionnel.
- Rappel des documents ou informations à apporter, si pertinent.
- Limites claires : le professionnel reste responsable de l'évaluation et des décisions cliniques.

## Workflow recommandé
1. Demander le but du rendez-vous et le format souhaité (liste courte, résumé chronologique, questions).
2. Organiser les éléments rapportés sans ajouter d'interprétation ni de causalité.
3. Distinguer les faits observés, les perceptions de l'utilisateur et les questions encore ouvertes.
4. Proposer des questions neutres, par exemple sur le sens d'un résultat, les options possibles, les bénéfices/risques, le suivi et le moment de recontacter le professionnel.
5. Rappeler de ne pas retarder un recours urgent pour préparer le rendez-vous.
6. Inviter l'utilisateur à vérifier l'exactitude du résumé et à retirer les données identifiantes.

## Garde-fous
- Utiliser les mots de l'utilisateur sans transformer les symptômes en diagnostic.
- Ne pas proposer un traitement ou influencer la décision clinique.
- Ne pas recopier de données identifiantes dans le résumé; demander une version anonymisée si un document est partagé.
- Ne pas faire croire qu'une checklist remplace l'entretien clinique.
- Si une urgence potentielle apparaît pendant la préparation, basculer immédiatement vers l'orientation urgente.

## Template d'entrée (copier/coller)
```text
Objectif du rendez-vous :
Question principale :
Observations à partager (dates approximatives si utiles) :
Questions ou documents à clarifier :
Format souhaité :
```

## Template de sortie (copier/coller)
```text
Résumé neutre à présenter :
- Motif :
- Observations et chronologie :
- Questions non résolues :

Questions à poser au professionnel :
Documents à apporter (si pertinents) :
Limite : ce résumé ne constitue pas une évaluation ni un avis médical.
```

## Checklist QA interne
- [ ] Le résumé reprend les faits fournis sans les interpréter.
- [ ] Les questions proposées sont neutres et ouvertes.
- [ ] Les décisions cliniques sont laissées au professionnel de santé.
- [ ] Les données personnelles inutiles sont absentes ou masquées.
- [ ] Une éventuelle urgence est orientée immédiatement plutôt que reportée au rendez-vous.

## KPI reliés
- Proportion de résumés validés par l'utilisateur comme fidèles à ses propos.
- Nombre de résumés contenant une interprétation diagnostique (cible : zéro).
- Proportion de réponses contenant des questions concrètes adaptées au but du rendez-vous.

## Definition of done
- [ ] L'utilisateur dispose d'un résumé clair et neutre ou d'une liste de questions.
- [ ] Les limites de la préparation sont explicites.
- [ ] Les informations personnelles non nécessaires ont été exclues.
- [ ] Aucun élément urgent n'a été relégué à un rendez-vous futur.

## Exemples d'usage
### Exemple 1 : Préparer une première consultation
**Contexte** : L'utilisateur veut décrire au médecin une gêne récurrente sans savoir comment organiser ses notes.  
**Input** : « Aide-moi à préparer un résumé avec le début, la fréquence et ce qui aggrave ou améliore la gêne; ne cherche pas de cause. »  
**Output** : Un canevas chronologique neutre et des questions à poser, sans hypothèse diagnostique.

### Exemple 2 : Préparer des questions sur un examen
**Contexte** : L'utilisateur a reçu un compte rendu et veut interroger son médecin à ce sujet.  
**Input** : « Quelles questions générales puis-je poser pour comprendre ce compte rendu ? Je vais masquer mon nom et les numéros de dossier. »  
**Output** : Une liste de questions sur la signification du document, les incertitudes, les prochaines étapes éventuelles et le moment de recontacter le cabinet, sans interpréter le résultat.

# Belgian VAT & Tax Orientation

## Objectif
Orienter vers des informations officielles belges sur la TVA et les obligations fiscales courantes, et aider à formuler les questions à poser à un professionnel qualifié sans trancher un dossier fiscal individuel.

## Quand l'utiliser (triggers)
- L'utilisateur demande une explication générale de la TVA ou des obligations fiscales en Belgique.
- Un indépendant ou une PME veut repérer les informations officielles à vérifier.
- Il souhaite préparer des questions sur une déclaration, une échéance ou un régime fiscal.

## Hors périmètre
- Calculer l'impôt ou la TVA dus dans une situation individuelle.
- Choisir un régime fiscal, une qualification ou une position déclarative pour l'utilisateur.
- Rédiger, soumettre ou valider une déclaration fiscale ou une demande contraignante.
- Donner un avis juridique, fiscal ou de planification patrimoniale individualisé.
- Présenter une information fiscale d'une autre juridiction comme règle belge.

## Inputs requis
- Pays et, si pertinent, région concernée.
- Type général de contribuable ou d'activité, sans numéro d'entreprise ni identifiants.
- Sujet général (TVA, impôt, déclaration, échéance ou régime).
- Date de la question ou période fiscale, si l'information peut évoluer.

## Sorties attendues
- Explication générale sourcée et datée, en distinguant les règles fédérales et régionales si nécessaire.
- Liens vers les pages officielles consultées.
- Liste des faits ou documents à vérifier avant une décision de déclaration.
- Questions à soumettre au comptable ou conseiller fiscal qui connaît le dossier.

## Workflow recommandé
1. Confirmer qu'il s'agit d'une question concernant la Belgique et identifier le sujet.
2. Déterminer si la demande est générale ou exige une décision/calcul individuel.
3. Rechercher les sources officielles belges les plus récentes, notamment le SPF Finances; vérifier la portée régionale lorsque pertinente.
4. Résumer uniquement ce que les sources établissent et préciser leur date et leurs limites.
5. Ne pas calculer ni recommander le traitement applicable au dossier; orienter les cas individuels vers un professionnel qualifié.
6. Fournir des questions ciblées et les prochaines vérifications à effectuer.

## Garde-fous
- Ne jamais inventer un taux, une exemption, un seuil, un délai ou une obligation déclarative.
- Vérifier l'année, la date d'effet et la juridiction de chaque information fiscale.
- Ne pas déduire l'éligibilité à un régime à partir d'informations partielles.
- Ne pas demander de numéro national, numéro d'entreprise, identifiants de portail ou données bancaires.
- Signaler explicitement toute incertitude ou divergence entre sources.
- Pour une décision ayant un effet déclaratif ou financier, renvoyer vers le comptable ou conseiller fiscal qualifié.

## Template d'entrée (copier/coller)
```text
Pays/région :
Type général de contribuable ou d'activité :
Période fiscale :
Sujet général (TVA, impôt, déclaration, échéance) :
Question générale :
Source officielle déjà consultée (facultatif) :
```

## Template de sortie (copier/coller)
```text
Explication générale :
Juridiction et période couvertes :
Points dépendant du dossier :
Questions à poser au comptable/conseiller fiscal :
Sources officielles consultées (organisme, titre, date, lien) :
```

## Checklist QA interne
- [ ] La réponse porte bien sur la juridiction et la période indiquées.
- [ ] Les règles évolutives sont sourcées et datées.
- [ ] Aucun calcul ou choix fiscal individuel n'est présenté comme certain.
- [ ] Les règles fédérales et régionales ne sont pas confondues.
- [ ] Les données sensibles ne sont ni demandées ni répétées.

## KPI reliés
- Proportion de réponses fiscales générales accompagnées de sources officielles datées.
- Nombre de taux, seuils ou délais affirmés sans source (cible : zéro).
- Nombre de décisions fiscales individualisées rendues par l'agent (cible : zéro).

## Definition of done
- [ ] L'utilisateur reçoit une orientation générale exacte au regard des sources consultées.
- [ ] La date, la juridiction et les limites des sources sont indiquées.
- [ ] Les éléments propres à la déclaration ou au dossier sont renvoyés à un professionnel qualifié.
- [ ] Les questions de suivi sont formulées sans divulgation de données sensibles.

## Exemples d'usage
### Exemple 1 : Chercher une source TVA
**Contexte** : Une petite entreprise veut comprendre où vérifier une information générale sur ses obligations TVA.  
**Input** : « Où trouver les informations officielles belges sur la TVA et quels éléments dois-je confirmer avec mon comptable ? »  
**Output** : Des liens effectivement consultés vers les ressources officielles du SPF Finances, leur date ou période utile et une courte liste de points à confirmer, sans déterminer le traitement du dossier.

### Exemple 2 : Échéance de déclaration
**Contexte** : Un indépendant s'interroge sur une échéance applicable à sa prochaine déclaration.  
**Input** : « Comment vérifier la date limite officielle pour ma période, sans supposer mon régime ? »  
**Output** : Une orientation vers la page officielle pertinente et une recommandation de confirmer le régime et l'échéance personnalisée avec son comptable ou le SPF Finances.

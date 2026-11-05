# Urgent Care Navigation

## Objectif
Aider à choisir une prochaine étape de recours aux soins de façon prudente, en faisant passer la sécurité immédiate avant toute explication ou collecte de contexte.

## Quand l'utiliser (triggers)
- L'utilisateur demande si une situation de santé nécessite une aide urgente.
- Il décrit des symptômes soudains, sévères ou qui s'aggravent rapidement.
- Il demande comment contacter des soins d'urgence ou un service de garde local.

## Hors périmètre
- Diagnostiquer ou exclure une urgence médicale.
- Remplacer les opérateurs des urgences, un professionnel de santé ou les protocoles locaux.
- Fournir un traitement ou des instructions de dosage.
- Garantir qu'une situation est sans danger à distance.

## Inputs requis
- Description courte de la situation, uniquement si cela ne retarde pas l'aide.
- Pays/région pour orienter vers les services ou numéros locaux, si connus.
- Indication si la personne est seule ou ne peut pas contacter elle-même les secours, lorsque pertinent.

## Sorties attendues
- Action immédiate clairement formulée si un danger potentiel est signalé.
- Orientation vers le numéro d'urgence local, les urgences ou un service de soins non urgents selon la situation décrite, sans présenter cela comme un diagnostic.
- Consigne de ne pas attendre une réponse en ligne en cas de risque immédiat.
- Mention explicite de l'incertitude et des limites de l'évaluation à distance.

## Workflow recommandé
1. Rechercher d'abord tout indice de danger immédiat, de situation potentiellement vitale ou d'aggravation rapide.
2. Si un tel indice est présent, recommander d'appeler immédiatement les services d'urgence locaux; ne pas demander de détails avant cette recommandation.
3. Si l'utilisateur précise qu'il est en Belgique et qu'une urgence est possible, indiquer le 112; sinon, utiliser uniquement un numéro local vérifié ou lui demander son pays si cela ne crée aucun délai.
4. Pour une situation qui ne semble pas immédiatement dangereuse, proposer de contacter rapidement un professionnel de santé ou un service de garde local plutôt que d'essayer d'établir un diagnostic.
5. Vérifier que le message ne crée pas de fausse assurance et ne retarde pas le recours aux soins.

## Garde-fous
- L'agent ne peut pas exclure une urgence sur la base d'un échange textuel.
- En cas de danger immédiat, ne pas poursuivre une collecte de données ni une recherche web avant de donner l'orientation urgente.
- Ne jamais suggérer d'attendre pour « voir si ça passe » lorsque la personne décrit un risque potentiellement vital.
- Ne pas donner de conseil de conduite ou de déplacement qui pourrait accroître le danger; encourager l'aide d'un tiers ou les secours si nécessaire.
- N'indiquer un numéro local qu'après avoir vérifié le pays ou la région; ne pas supposer que la personne se trouve en Belgique parce qu'elle écrit en français.
- Ne pas fournir de diagnostic, prescription ou consigne de modification de traitement.

## Template d'entrée (copier/coller)
```text
Pays/région (si connu) :
Situation décrite en quelques mots :
Début et évolution (si cela ne retarde pas l'aide) :
La personne peut-elle contacter les secours maintenant ?
```

## Template de sortie (copier/coller)
```text
Niveau d'action recommandé :
Action immédiate :
Service local à contacter (si vérifié) :
Limites de l'évaluation :
```

## Checklist QA interne
- [ ] L'orientation urgente est donnée avant toute question si un danger immédiat est évoqué.
- [ ] La réponse ne prétend pas diagnostiquer ni exclure un problème grave.
- [ ] Les numéros de téléphone correspondent au lieu confirmé et sont vérifiés.
- [ ] Aucun délai inutile ni demande de données sensibles n'est introduit.
- [ ] La prochaine action est compréhensible et réalisable.

## KPI reliés
- Taux de messages urgents où l'action immédiate apparaît dans la première phrase (cible : 100 %).
- Nombre de réponses qui retardent ou découragent un recours urgent (cible : zéro).
- Taux de numéros locaux cités après vérification de la localisation.

## Definition of done
- [ ] Le message propose une prochaine action claire et prudente.
- [ ] Toute urgence potentielle est orientée vers les services locaux sans délai.
- [ ] Les limites et l'absence de diagnostic sont indiquées sans diluer le message urgent.
- [ ] Aucun renseignement inutile n'est demandé.

## Exemples d'usage
### Exemple 1 : Difficulté respiratoire soudaine
**Contexte** : L'utilisateur écrit qu'un proche éprouve soudainement une forte difficulté à respirer.  
**Input** : « Il respire très difficilement depuis quelques minutes. Est-ce que je dois attendre ? »  
**Output** : Conseiller d'appeler immédiatement les services d'urgence locaux et de ne pas attendre une réponse en ligne; ne pas tenter de diagnostiquer.

### Exemple 2 : Trouver le bon recours local
**Contexte** : L'utilisateur en Belgique cherche le numéro à appeler en cas d'urgence médicale.  
**Input** : « Je suis en Belgique et je pense qu'il s'agit d'une urgence. Qui appeler ? »  
**Output** : Indiquer d'appeler immédiatement le 112 et de suivre les consignes de l'opérateur, sans demander d'informations supplémentaires d'abord.

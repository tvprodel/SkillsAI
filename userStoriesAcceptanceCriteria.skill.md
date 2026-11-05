# User Stories & Acceptance Criteria

## Objectif
Formuler des user stories centrées sur un résultat utilisateur et des critères d'acceptation observables afin de rendre le périmètre compréhensible et vérifiable.

## Quand l'utiliser (triggers)
- « user story », « critères d'acceptation », « Gherkin », « backlog fonctionnel ».
- Besoins validés à découper en unités de valeur utilisateur suffisamment précises.
- Préparation d'une revue métier ou d'un transfert vers une équipe de développement et de QA.

## Hors périmètre
- Priorisation du backlog, roadmap et arbitrage valeur/coût → l'agent de stratégie produit.
- Estimation technique, architecture ou découpage par composants → l'agent d'architecture logicielle et équipe de développement.
- Plan de test, couverture de tests et scénarios de non-régression → l'agent qualité.
- Rédaction de microcopie finale accessible → l'agent UX writing.

## Inputs requis
- Besoin métier validé et utilisateur ou rôle ciblé.
- Résultat attendu, contexte de réalisation et règles métier liées.
- Contraintes, dépendances, cas limites et décisions connues.
- Source de vérité du backlog et convention d'identification utilisée par l'équipe.

## Sorties attendues
- User stories au format rôle / besoin / bénéfice, chacune reliée à une exigence source.
- Critères d'acceptation mesurables et observables, au besoin formulés en Given/When/Then.
- Hypothèses, dépendances, exclusions et questions à faire trancher.
- Proposition de découpage fonctionnel sans estimation ni priorité arbitraire.

## Workflow recommandé
1. Vérifier le rôle utilisateur et le bénéfice attendu à partir du besoin source.
2. Rédiger une story centrée sur un résultat, pas sur une tâche d'implémentation.
3. Définir les critères couvrant le parcours nominal, les règles métier et les cas d'erreur importants.
4. Vérifier indépendance, taille fonctionnelle, cohérence et traçabilité de chaque story.
5. Présenter les ambiguïtés, dépendances et questions au bon owner avant de déclarer la story prête.
6. Transmettre les critères à la QA pour conception des tests et au l'agent produit pour priorisation.

## Garde-fous
- Ne pas fixer priorité, estimation ou ordre de livraison sans mandat du l'agent produit.
- Un critère d'acceptation décrit un résultat observable, non une méthode technique interne.
- Ne pas confondre critères d'acceptation et suite exhaustive de tests.
- Éviter les critères vagues (« rapide », « simple », « intuitif ») sans seuil validé.
- Ne pas considérer une story comme prête si une règle métier critique reste ambiguë.
- Employer des termes cohérents avec le glossaire et la langue des utilisateurs concernés.
- Les règles d'accès aux données personnelles doivent être validées par l'expert compétent.
- Privilégier les formats ouverts et les outils libres; justifier les outils propriétaires requis.
- Ne pas introduire de dépendances ou versions logicielles obsolètes ou EOL.

## Template d'entrée (copier/coller)
```text
[Besoin source]
- ID :
- Utilisateur / rôle :
- Résultat attendu :
- Bénéfice métier :
- Source / exigence validée :
- Règles métier :
- Dépendances :
- Contraintes et cas limites :
- Questions ouvertes :
```

## Template de sortie (copier/coller)
```text
[Story]
- ID :
- En tant que [rôle]
- Je veux [capacité / action]
- Afin de [bénéfice métier]
- Source / exigence parent :
- Dépendances :
- Hors périmètre :
- Questions ouvertes :

[Critères d'acceptation]
```
```gherkin
Scénario: [résultat observable]
  Étant donné [contexte et préconditions]
  Quand [action ou événement]
  Alors [résultat attendu vérifiable]
```

## Checklist QA interne
- [ ] Le rôle, l'action et le bénéfice sont explicites.
- [ ] La story est reliée à une exigence ou à une source métier validée.
- [ ] Chaque critère est observable, non ambigu et sans détail d'implémentation superflu.
- [ ] Les cas nominal, erreur et limite pertinents sont représentés.
- [ ] Les dépendances, exclusions et questions non résolues sont visibles.

## KPI reliés
- Part des stories reliées à une exigence ou un besoin validé.
- Part des stories acceptées en revue sans clarification majeure.
- Nombre de retours de développement dus à une ambiguïté fonctionnelle.
- Taux de critères d'acceptation vérifiables lors de la revue QA.

## Definition of done
- [ ] Story exprimée comme résultat utilisateur avec source et bénéfice.
- [ ] Critères couvrant les comportements attendus et cas limites pertinents.
- [ ] Aucune priorité ou estimation non autorisée n'est introduite.
- [ ] Questions ouvertes et dépendances ont un owner ou un statut explicite.

## Exemples d'usage
### Exemple 1 : Sauvegarder une recherche
**Contexte** : Les utilisateurs répètent les mêmes filtres chaque jour.  
**Action** : Décrire story, bénéfice, conditions de sauvegarde et comportement si le nom existe déjà.  
**Résultat** : Critères vérifiables sans imposer la technologie de stockage.

### Exemple 2 : Soumettre un formulaire incomplet
**Contexte** : Un utilisateur tente d'envoyer une demande sans les informations requises.  
**Action** : Décrire les champs concernés, le résultat attendu et la possibilité de corriger.  
**Résultat** : Critères clairs pour la revue métier et la conception des tests QA.

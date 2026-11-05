# Functional Specification & Traceability

## Objectif
Transformer les besoins validés en spécifications fonctionnelles structurées et traçables, compréhensibles par les métiers, l'architecture, le développement et la QA.

## Quand l'utiliser (triggers)
- « spécification fonctionnelle », « exigences système », « règles métier », « matrice de traçabilité ».
- Besoin de décrire comportements, états, validations, erreurs ou échanges attendus sans choisir l'implémentation.
- Préparation d'une évolution logicielle, d'une recette ou d'un appel d'offres fonctionnel.

## Hors périmètre
- Architecture, choix de composants, API ou modèle de données technique → l'agent d'architecture logicielle ou l'agent bases de données.
- Implémentation du code et configuration du système → équipe de développement compétente.
- Stratégie de tests, cas de test détaillés et plan de non-régression → l'agent qualité.
- Manuel utilisateur final ou documentation publique → l'agent de rédaction technique.

## Inputs requis
- Besoins validés et leurs sources, identifiants ou priorités métier disponibles.
- Acteurs, événements déclencheurs, règles métier et scénarios connus.
- Contraintes métier, légales, opérationnelles et critères non fonctionnels connus.
- Documents existants et décisions d'architecture déjà approuvées, s'il y en a.

## Sorties attendues
- Spécification fonctionnelle décrivant acteurs, préconditions, parcours nominal, alternatives et erreurs.
- Règles métier explicites avec identifiants, conditions, résultat attendu et owner.
- Matrice de traçabilité besoin → exigence → scénario / critère d'acceptation.
- Liste de questions, hypothèses, dépendances et décisions à confirmer.

## Workflow recommandé
1. Vérifier l'identifiant, la source, le statut et le périmètre de chaque besoin d'entrée.
2. Structurer les acteurs, déclencheurs, préconditions, résultats et règles sans imposer une solution technique.
3. Décrire les scénarios nominaux, alternatifs, limites et erreurs observables par l'utilisateur ou le métier.
4. Attribuer des identifiants stables et relier chaque exigence à sa source et à un moyen de vérification.
5. Contrôler cohérence, complétude, ambiguïté et doublons; indiquer les exigences non confirmées.
6. Faire relire les règles par leurs owners métier et transmettre les questions techniques à l'architecte.

## Garde-fous
- Une exigence doit décrire un comportement ou une contrainte vérifiable, pas une solution technique non validée.
- Préserver la traçabilité dans les deux sens; ne pas laisser d'exigence sans source ni besoin sans statut.
- Distinguer exigences fonctionnelles et non fonctionnelles; ne pas inventer de seuils de performance ou SLA.
- Identifier les règles réglementaires comme à valider par l'expert conformité/juridique compétent.
- Documenter toute modification de périmètre, décision, hypothèse et dépendance.
- Utiliser des identifiants stables et un langage métier cohérent.
- Ne pas inclure d'informations confidentielles non nécessaires à la spécification.
- Privilégier des outils et formats ouverts; justifier les outils propriétaires indispensables.
- Exclure les dépendances, standards ou versions logicielles obsolètes ou EOL.

## Template d'entrée (copier/coller)
```text
[Besoin source]
- ID :
- Objectif métier :
- Partie prenante / rôle :
- Résultat attendu :
- Source / preuve :
- Contraintes connues :
- Owner de validation :
```

## Template de sortie (copier/coller)
```text
[Exigence]
- ID :
- Titre :
- Source / besoin parent :
- Acteur :
- Déclencheur :
- Préconditions :
- Comportement attendu :
- Variantes / erreurs :
- Règles métier :
- Priorité et statut :
- Vérification attendue :
- Owner de validation :

[Matrice de traçabilité]
| Besoin | Exigence | Scénario / critère | Owner | Statut |
|--------|----------|--------------------|-------|--------|
|        |          |                    |       |        |
```

## Checklist QA interne
- [ ] Chaque exigence est unique, testable, non ambiguë et reliée à une source.
- [ ] Parcours nominal, alternatives, erreurs et états métier importants sont couverts.
- [ ] Les acteurs, déclencheurs, préconditions et résultats sont explicités.
- [ ] Les exigences non fonctionnelles sont séparées et leurs seuils ont un owner.
- [ ] La matrice de traçabilité ne contient pas de liens manquants ou orphelins.

## KPI reliés
- Pourcentage d'exigences traçables vers une source et un scénario de vérification.
- Nombre d'exigences ambiguës ou non testables après revue métier.
- Nombre de changements d'exigence sans décision ou owner documenté.
- Taux de besoins couverts par au moins une exigence validée.

## Definition of done
- [ ] La spécification est reliée aux besoins validés et versionnée.
- [ ] Les scénarios et règles ont été relus ou leurs validations en attente sont marquées.
- [ ] Les exigences ouvertes, hypothèses et dépendances sont explicitement listées.
- [ ] Les liens de traçabilité ont été vérifiés dans les deux sens.

## Exemples d'usage
### Exemple 1 : Recherche de dossier
**Contexte** : Un agent métier doit retrouver un dossier selon plusieurs critères.  
**Action** : Spécifier champs de recherche, règles de combinaison, résultat vide et accès refusé.  
**Résultat** : Exigences testables, chacune reliée à un besoin et à un scénario de vérification.

### Exemple 2 : Règle de validation
**Contexte** : Une demande ne peut être soumise que si des champs obligatoires sont présents.  
**Action** : Décrire les conditions, le comportement en échec et les messages attendus sans dicter la structure du code.  
**Résultat** : Règle métier versionnée et validée par son owner.

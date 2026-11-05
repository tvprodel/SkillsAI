# Requirements Elicitation & Analysis

## Objectif
Recueillir, clarifier et analyser les besoins des parties prenantes afin de produire des exigences fonctionnelles compréhensibles, vérifiables et reliées à un objectif métier.

## Quand l'utiliser (triggers)
- « recueil des besoins », « ateliers métier », « interview utilisateurs », « exigences fonctionnelles ».
- Objectif métier connu mais besoins utilisateurs incomplets, contradictoires ou non vérifiables.
- Besoin d'identifier acteurs, irritants, contraintes, hypothèses et limites d'une évolution logicielle.

## Hors périmètre
- Stratégie produit, vision, priorisation de portefeuille et arbitrage final de valeur → l'agent de stratégie produit.
- Modélisation organisationnelle BPMN, amélioration continue et conception RPA → l'agent d'optimisation des processus métier.
- Architecture logicielle et choix d'implémentation → l'agent d'architecture logicielle.
- Étude UX spécialisée, tests utilisateurs et conception d'interface → l'agent front-end ou l'agent conseiller en sciences humaines.

## Inputs requis
- Problème métier, résultat attendu et contexte du système concerné.
- Parties prenantes et utilisateurs connus, avec leurs rôles et disponibilité.
- Sources existantes : processus, formulaires, règles, documentation, tickets ou exemples.
- Contraintes connues, échéance, périmètre et décisions déjà prises.

## Sorties attendues
- Synthèse du besoin avec objectifs, utilisateurs, contexte et périmètre.
- Registre des exigences, questions ouvertes, hypothèses, contraintes et risques.
- Cartographie simple des parties prenantes et des besoins par rôle.
- Compte rendu des décisions et validation attendue de chaque responsable métier.

## Workflow recommandé
1. Cadrer l'objectif métier, les utilisateurs visés, les limites du système et la décision à éclairer.
2. Préparer les questions ouvertes en séparant faits, opinions, hypothèses et contraintes.
3. Recueillir les éléments auprès des sources disponibles; citer les preuves et l'origine des décisions.
4. Regrouper les besoins, repérer doublons, contradictions, dépendances et scénarios manquants.
5. Reformuler chaque besoin en résultat attendu et confirmer les zones d'incertitude avec le responsable concerné.
6. Produire un registre priorisable, sans décider à la place du l'agent produit.

## Garde-fous
- Ne jamais présenter une hypothèse comme un fait ni inventer une validation de partie prenante.
- Séparer le besoin utilisateur de la solution technique proposée.
- Signaler les besoins contradictoires ou non testables et conserver leur source.
- Ne collecter que les données personnelles nécessaires; faire confirmer les exigences de conformité par l'agent de conformité RGPD.
- Respecter le périmètre validé; toute extension est identifiée comme demande de changement.
- Rédiger en français clair et adapter le vocabulaire au public métier.
- Protéger les informations sensibles et ne pas inclure de secrets dans les artefacts.
- Privilégier les formats ouverts et outils libres; justifier tout outil propriétaire nécessaire.
- Ne pas prescrire de dépendances ni de versions logicielles obsolètes ou EOL.

## Template d'entrée (copier/coller)
```text
[Contexte]
- Objectif métier :
- Système / périmètre :
- Participant et rôle :

[Questions]
- Situation actuelle :
- Résultat attendu :
- Déclencheur et fréquence :
- Exceptions / erreurs :
- Contraintes et dépendances :
- Exemple concret :
```

## Template de sortie (copier/coller)
```text
[Besoin]
- ID :
- Partie prenante / rôle :
- Résultat attendu :
- Justification / source :
- Contrainte :
- Statut de validation : à confirmer / confirmé / rejeté
- Hypothèses :
- Questions ouvertes :
- Décisions et owner :
```

## Checklist QA interne
- [ ] Chaque besoin est relié à un objectif ou à une source identifiable.
- [ ] Les faits, hypothèses, décisions et questions ouvertes sont distingués.
- [ ] Les rôles concernés et les limites de périmètre sont explicites.
- [ ] Les contradictions, exceptions et dépendances visibles sont consignées.
- [ ] Aucune validation n'est supposée sans confirmation du responsable.

## KPI reliés
- Part des besoins confirmés par un responsable métier avant spécification.
- Nombre de contradictions ou questions critiques résolues avant transmission.
- Taux de besoins retournés pour ambiguïté après revue.
- Délai entre cadrage initial et synthèse validée, suivi sans sacrifier la qualité.

## Definition of done
- [ ] Objectif, utilisateurs, périmètre et parties prenantes sont consignés.
- [ ] Les besoins identifiés possèdent une source ou un statut d'hypothèse explicite.
- [ ] Questions ouvertes, contradictions et décisions attendues ont un owner.
- [ ] La synthèse est relue ou sa validation en attente est clairement signalée.

## Exemples d'usage
### Exemple 1 : Demande de suivi de dossier
**Contexte** : Plusieurs équipes demandent un écran de suivi mais décrivent des attentes différentes.  
**Action** : Entretiens par rôle, comparaison des situations et consignation des divergences.  
**Résultat** : Besoins confirmés séparés des options d'interface encore à arbitrer.

### Exemple 2 : Automatisation d'une approbation
**Contexte** : Un processus manuel doit être étudié avant toute décision d'automatisation.  
**Action** : Identifier déclencheurs, acteurs, règles, exceptions et contrôles à partir de cas réels.  
**Résultat** : Registre des besoins et questions remis au responsable métier et au l'agent de processus métier.

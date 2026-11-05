# Audit Cohérence Logique Brief

## Objectif
Vérifier la cohérence logique d'un brief de délégation avant envoi : détecter contradictions internes, critères flous, DoD incomplet, owner ambigu, inférences non fondées.

## Quand l'utiliser (triggers)
- Brief incomplet ou ambigu à valider.
- Critères de succès non mesurables.
- Contradictions internes détectées (ex : Bash sur Windows, urgence critique + délai 3 mois).
- Owner flou ou multiple sur même tâche.
- Inférence sans indice observable récent.

## Hors périmètre
- Choix stratégique produit (→ l'agent produit).
- Validation technique de faisabilité (→ l'agent d'architecture ou agent technique concerné).
- Priorisation multi-projets (→ l'agent de planification).

## Inputs requis
- Brief de délégation à auditer (contexte, objectif, contraintes, DoD).
- Historique des 5 derniers messages si disponible (pour détecter incohérences contextuelles).
- Agent cible pressenti (pour vérifier alignement avec périmètre).

## Sorties attendues
- **Résultat d'audit** : Brief validé OU anomalies détectées avec recommandations.
- **Niveau de confiance** : pourcentage estimé de fiabilité du brief actuel.
- **Recommandations structurées** : actions correctives prioritaires (clarifier, découper, reformuler).
- **Impact si ignoré** : conséquence estimée et probabilité.

## Workflow recommandé

1. **Appliquer checklist de rigueur logique** :
   - [ ] Objectif reformulé sans ambiguïté ?
   - [ ] Critère de succès mesurable et vérifiable ?
   - [ ] Contradiction détectée entre deux éléments du brief ?
   - [ ] Boucle de délégation (A → B → A) identifiée ?
   - [ ] Inférence basée sur indice explicite récent (< 3 messages) ?
   - [ ] Niveau d'urgence cohérent avec l'impact décrit ?
   - [ ] Choix délégation directe vs coordination multi-agents par l'agent de coordination justifié par la complexité ?
   - [ ] Owner unique clairement désigné ?
   - [ ] DoD complet avec preuves attendues ?
   - [ ] Timebox/échéance explicite définie ?

2. **Identifier les anomalies critiques** (bloquantes) :
   - Contradiction logique (incompatibilité technique).
   - DoD absent ou non vérifiable.
   - Owner ambigu ou multiple.

3. **Identifier les anomalies mineures** (améliorations) :
   - Critère de succès flou mais déductible.
   - Timebox absente mais urgence faible.
   - Inférence probable mais non confirmée.

4. **Quantifier niveau de confiance** :
   - **90-100%** : brief clair, cohérent, complet → validation immédiate.
   - **70-89%** : anomalies mineures → recommandations d'amélioration.
   - **50-69%** : anomalies critiques → clarification obligatoire avant envoi.
   - **< 50%** : brief incohérent ou incomplet → refus de validation, reformulation nécessaire.

5. **Formuler recommandations** :
   - Action corrective prioritaire (clarifier X, découper Y, reformuler Z).
   - Alternative si clarification impossible (routage vers agent plus généraliste).

6. **Estimer impact si ignoré** :
   - Conséquence probable (rework, livrable hors cible, blocage agent).
   - Probabilité estimée (sur base historique ou logique).

## Garde-fous

- Ne jamais bloquer un flux par perfectionnisme : distinguer anomalies critiques (bloquantes) et mineures (améliorations).
- Quantifier toujours l'incertitude : éviter "peut-être", préférer "probabilité 60%".
- Tracer les indices observables : chaque recommandation doit citer l'élément du brief incohérent.
- Rester neutre : pas de jugement sur l'intention, uniquement constat factuel.

## Template d'entrée (copier/coller)

```text
[Brief à auditer]
- Contexte : ...
- Objectif : ...
- Contraintes : ...
- DoD : ...
- Agent cible pressenti : ...

[Historique récent (optionnel)]
- Message 1 : ...
- Message 2 : ...
- Message 3 : ...
```

## Template de sortie (copier/coller)

```text
[Constat]
- Élément analysé : ...
- Anomalie(s) détectée(s) : ...
  - Critique (bloquante) : ...
  - Mineure (amélioration) : ...

[Raisonnement]
- Chaîne logique : ...
- Indices observables : ...

[Recommandation]
- Action corrective prioritaire : ...
- Alternative si clarification impossible : ...
- Niveau de confiance (brief actuel) : XX %

[Impact si ignoré]
- Conséquence estimée : ...
- Probabilité : XX %
```

## Checklist QA interne

- [ ] Checklist de rigueur logique appliquée intégralement.
- [ ] Anomalies critiques distinguées des mineures.
- [ ] Niveau de confiance quantifié (pourcentage).
- [ ] Recommandations actionnables (verbe d'action + objet précis).
- [ ] Impact estimé avec probabilité chiffrée.
- [ ] Format de sortie standard respecté.

## KPI reliés

- **Taux de briefs validés sans anomalie** : (briefs validés sans anomalie / briefs totaux audités) x 100
  - Cible : >= 70%
  - Mesure : compter briefs avec confiance >= 90%

- **Taux d'anomalies critiques détectées** : (anomalies critiques / anomalies totales) x 100
  - Cible : <= 20%
  - Mesure : compter anomalies bloquantes vs mineures

- **Temps moyen d'audit** : moyenne du temps entre réception brief et livraison résultat
  - Cible : <= 3 min
  - Mesure : timestamp début - timestamp fin

- **Taux de rework post-audit** : (briefs renvoyés pour correction / briefs audités) x 100
  - Cible : <= 15%
  - Mesure : compter briefs avec recommandations appliquées vs ignorées

## Definition of done

Un audit de cohérence logique de brief est considéré terminé si :

1. **Checklist de rigueur logique appliquée complètement** (10 points minimum vérifiés)
   - Mesure : compter points cochés dans la checklist
   - Preuve : checklist présente dans le résultat avec statut pour chaque point

2. **Niveau de confiance quantifié** (0-100%) avec justification factuelle
   - Mesure : pourcentage présent dans format standard
   - Preuve : échelle 90-100 / 70-89 / 50-69 / <50 appliquée

3. **Anomalies identifiées et classées** (critiques vs mineures)
   - Mesure : liste anomalies avec criticité assignée
   - Preuve : au moins 1 anomalie documentée OU validation "aucune anomalie"

4. **Recommandations formulées avec action corrective prioritaire**
   - Mesure : présence d'au moins 1 recommandation si anomalie détectée
   - Preuve : format "Action corrective : ..." avec owner/alternative si applicable

5. **Impact estimé si recommandations ignorées** (conséquence + probabilité)
   - Mesure : présence de section "Impact si ignoré"
   - Preuve : conséquence (rework/blocage/hors cible) + probabilité (%) documentées

## Exemples types

### Cas 1 : Contradiction technique (Bash sur Windows)
**Input** : "Script Bash pour automatiser déploiement sur serveur Windows Server 2022."

**Output** :
```text
[Constat]
- Élément analysé : Brief script Bash sur Windows
- Anomalie détectée : Contradiction OS/outil (Bash natif sur Linux/Unix, pas Windows)

[Raisonnement]
- Bash non disponible par défaut sur Windows Server.
- Alternatives : PowerShell (natif), WSL (si installé), Git Bash (si installé).
- Aucun indice dans brief précisant environnement d'exécution.

[Recommandation]
- Clarifier : environnement cible (PowerShell / WSL / Git Bash).
- Alternative : router vers l'agent de scripting système avec mention explicite contrainte Windows.
- Niveau de confiance (clarification nécessaire) : 85%

[Impact si ignoré]
- Livrable inexécutable sur cible.
- Rework complet ou confusion utilisateur.
- Probabilité : 90%
```

### Cas 2 : DoD incomplet
**Input** : "Optimiser la performance de l'application."

**Output** :
```text
[Constat]
- Élément analysé : Brief optimisation performance
- Anomalie détectée : DoD absent (aucun critère mesurable)

[Raisonnement]
- "Optimiser performance" = périmètre flou (latence / throughput / CPU / mémoire / requêtes BDD).
- Aucun seuil de réussite défini (ex : "latence < 200ms", "CPU < 50%").

[Recommandation]
- Clarifier : quelle métrique optimiser (latence API / temps de réponse BDD / usage CPU / autre).
- Définir seuil cible mesurable (ex : "réduire latence API de 500ms à 200ms").
- Niveau de confiance (clarification nécessaire) : 90%

[Impact si ignoré]
- Agent technique optimise une métrique non prioritaire.
- Utilisateur insatisfait, rework.
- Probabilité : 75%
```

### Cas 3 : Inférence non fondée
**Input** : "L'utilisateur veut améliorer l'UX, je vais déléguer à l'agent de microcopie."

**Output** :
```text
[Constat]
- Élément analysé : Routage "améliorer UX" → l'agent de microcopie
- Anomalie détectée : Inférence périmètre (UX = large, l'agent de microcopie = microcopie uniquement)

[Raisonnement]
- "Améliorer UX" = spectre large (design visuel / parcours / accessibilité / microcopie / performance).
- L'agent de microcopie = spécialisation microcopie (CTA, messages d'erreur, tooltips).
- Aucun indice dans brief précisant focus microcopie.

[Recommandation]
- Clarifier : quel aspect UX (design visuel / parcours / microcopie / accessibilité).
- Si design visuel → l'agent frontend.
- Si microcopie → l'agent de microcopie (UX writing).
- Si projet complexe multi-facettes → coordination multi-agents par l'agent de coordination.
- Niveau de confiance (clarification nécessaire) : 80%

[Impact si ignoré]
- Agent hors périmètre, livrable partiel.
- Rework ou délégation en cascade.
- Probabilité : 70%
```

## Liens
- Skill complémentaire : [Détection Boucles Délégation](./detectionBouclesDelegation.skill.md)
- Skill complémentaire : [Calibration Confiance Décisionnelle](./calibrationConfianceDecisionnelle.skill.md)

## Exemples d'usage

### Exemple 1 : Détecter des critères contradictoires
**Contexte** : Un brief demande un prototype complet en deux jours, avec intégration en production et sans accès aux systèmes concernés.  
**Input** : Brief, échéance, accès disponibles, livrables attendus, critères de succès et agent pressenti.  
**Output** : Contradiction signalée entre délai, périmètre et accès; questions de clarification prioritaires et version réduite du livrable proposée, sans inventer d'engagement.

### Exemple 2 : Clarifier l'ownership d'une tâche
**Contexte** : Un ticket demande à la fois de définir une politique produit et d'implémenter des tests, sans responsable de décision.  
**Input** : Texte du ticket, rôles impliqués, DoD actuel et contraintes connues.  
**Output** : Décisions métier séparées des tâches QA, owner attendu pour chaque décision, critères de sortie mesurables et recommandation de découpage avant délégation.

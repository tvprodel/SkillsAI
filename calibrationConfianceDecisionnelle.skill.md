# Calibration Confiance Décisionnelle

## Objectif
Fournir un second avis chiffré sur les décisions ambiguës de l'agent de coordination : clarifier vs inférer, routage direct vs coordination multi-agents par l'agent de coordination, urgence critique vs normale, périmètre agent vs multi-agents.

## Quand l'utiliser (triggers)
- Cas limite : clarifier ou inférer ?
- Routage ambigu : agent A ou agent B ?
- Urgence floue : critique ou élevée ?
- Périmètre flou : tâche simple (agent direct) ou complexe (coordination multi-agents par l'agent de coordination) ?
- Demande utilisateur vague sans indice récent.
- L'agent de coordination hésite entre 2+ options et demande calibration.

## Hors périmètre
- Décision stratégique produit (→ l'agent produit).
- Validation technique de faisabilité (→ l'agent d'architecture ou agent technique).
- Priorisation multi-projets (→ l'agent de planification).
- Analyse de risques (→ l'agent de gestion des risques).

## Inputs requis
- Demande utilisateur (texte brut).
- Options considérées par l'agent de coordination (option A, option B, ...).
- Contexte récent (5 derniers messages si disponible).
- Niveau d'urgence perçu par l'agent de coordination (optionnel).

## Sorties attendues
- **Recommandation principale** : option préférée avec justification.
- **Niveau de confiance** : pourcentage estimé de pertinence de la recommandation.
- **Top 2 alternatives classées** : options de repli si recommandation principale échoue.
- **Impact estimé** : conséquence de chaque option (délai, qualité, rework).

## Workflow recommandé

1. **Analyser la demande utilisateur** :
   - Identifier les indices explicites (mots-clés, outils mentionnés, contraintes).
   - Identifier les zones d'ambiguïté (périmètre flou, urgence non précisée).

2. **Évaluer chaque option** :
   - **Probabilité de pertinence** : sur base des indices disponibles.
   - **Coût de l'erreur** : impact si l'option est incorrecte (rework, délai).
   - **Facilité de correction** : peut-on facilement rectifier si erreur ?

3. **Quantifier le niveau de confiance** :
   - **90-100%** : indices clairs, option évidente (ex : "script Bash" → l'agent de scripting système).
   - **70-89%** : indices probables, choix raisonnable mais clarification recommandée.
   - **50-69%** : ambiguïté forte, clarification nécessaire avant routage.
   - **< 50%** : aucun indice fiable, clarification obligatoire.

4. **Classer les alternatives** :
   - **Option 1 (recommandée)** : meilleur équilibre probabilité/coût.
   - **Option 2 (repli)** : si option 1 échoue ou clarification impossible.
   - **Option 3 (sécurité)** : coordination multi-agents par l'agent de coordination (option par défaut en cas de doute fort).

5. **Estimer l'impact de chaque option** :
   - **Délai** : temps de résolution estimé.
   - **Qualité** : risque de livrable hors cible.
   - **Rework** : probabilité de retour en arrière.

6. **Formuler la recommandation** avec format standard.

## Garde-fous

- Toujours quantifier l'incertitude : éviter "probablement", préférer "probabilité 70%".
- Ne jamais recommander une option avec confiance < 50% sans proposer clarification.
- Tracer les indices observables : chaque probabilité doit citer l'élément de contexte.
- Rester neutre : pas de jugement sur l'utilisateur, uniquement analyse factuelle.
- En cas de doute persistant : toujours proposer clarification comme option prioritaire.

## Template d'entrée (copier/coller)

```text
[Demande utilisateur]
- Texte brut : ...

[Options considérées par l'agent de coordination]
- Option A : ...
- Option B : ...
- Option C (optionnel) : ...

[Contexte récent (optionnel)]
- Message 1 : ...
- Message 2 : ...
- Message 3 : ...

[Niveau d'urgence perçu]
- Critique / Élevé / Normal / Non précisé
```

## Template de sortie (copier/coller)

```text
[Constat]
- Demande analysée : ...
- Ambiguïté détectée : ...
- Indices explicites disponibles : ...

[Raisonnement]
- Option A : probabilité XX %, coût erreur : [faible/moyen/élevé], facilité correction : [facile/moyen/difficile]
- Option B : probabilité XX %, coût erreur : [faible/moyen/élevé], facilité correction : [facile/moyen/difficile]
- Option C (si applicable) : ...

[Recommandation]
- **Option recommandée** : [Option X]
- **Justification** : ...
- **Niveau de confiance** : XX %

[Alternatives classées]
1. **Option recommandée** : [X] (confiance XX %, impact : ...)
2. **Option repli** : [Y] (confiance XX %, impact : ...)
3. **Option sécurité** : Clarifier avec utilisateur OU coordonner en multi-agents via l'agent de coordination (confiance 100%, impact : +délai)

[Impact estimé par option]
| Option | Délai estimé | Risque hors cible | Probabilité rework |
|--------|--------------|-------------------|---------------------|
| Option A | ... | ... | ... |
| Option B | ... | ... | ... |
| Clarifier | +1 question | 0% | 0% |
```

## Checklist QA interne

- [ ] Demande utilisateur analysée avec indices explicites identifiés.
- [ ] Chaque option évaluée (probabilité, coût erreur, facilité correction).
- [ ] Niveau de confiance quantifié pour option recommandée.
- [ ] Top 2-3 alternatives classées avec impact estimé.
- [ ] Option "clarifier" proposée si confiance < 70%.
- [ ] Format de sortie standard respecté.

## KPI reliés

- **Taux de décisions correctes post-calibration** : (décisions validées rétrospectivement / décisions totales) x 100
  - Cible : >= 80%
  - Mesure : comparer la recommandation de cette compétence au résultat final effectif (sur 1 mois glissant)

- **Précision des niveaux de confiance** : écart moyen entre confiance annoncée et taux de succès réel
  - Cible : <= 15%
  - Mesure : |confiance annoncée - taux succès| moyenné sur échantillon

- **Temps moyen de calibration** : moyenne du temps entre réception options et livraison recommandation
  - Cible : <= 2 min
  - Mesure : timestamp début - timestamp fin

- **Taux de clarifications évitées** : (recommandations suivies sans clarification supplémentaire / recommandations totales) x 100
  - Cible : >= 70%
  - Mesure : compter les cas où l'agent de coordination a agi directement sur la recommandation de cette compétence

## Definition of done

Une calibration de confiance décisionnelle est considérée terminée si :

1. **Recommandation principale formulée** avec justification factuelle
   - Mesure : présence d'une option désignée comme "recommandée"
   - Preuve : format "Recommandation : Option X (justification ...)"

2. **Niveau de confiance quantifié** (0-100%) avec échelle appliquée
   - Mesure : pourcentage présent avec classification 90-100 / 70-89 / 50-69 / <50
   - Preuve : échelle documentée + mapping vers action (validation immédiate / clarification recommandée / obligatoire)

3. **Top 2 alternatives classées** avec critères de repli
   - Mesure : au moins 2 options présentes avec classement explicite
   - Preuve : format "Option 1 (recommandée) / Option 2 (repli) / Option 3 (sécurité)"

4. **Impact estimé par option** (délai, qualité, rework)
   - Mesure : présence de 3 métriques impact pour chaque option analysée
   - Preuve : tableau ou liste avec Délai / Qualité / Rework documentés

5. **Indices observables tracés** pour chaque probabilité annoncée
   - Mesure : chaque % de confiance cite au moins 1 élément de contexte factuel
   - Preuve : format "Probabilité 70% basée sur [indice X du message Y]"

## Exemples types

### Cas 1 : Clarifier vs Inférer (optimisation BDD)
**Input** :
```text
Demande : "Optimiser la base de données"
Options :
- A : Clarifier (quel aspect ?)
- B : Inférer "requêtes SQL" et router vers l'agent bases de données
Contexte récent : Aucun message sur performance BDD
```

**Output** :
```text
[Constat]
- Demande analysée : "Optimiser la base de données"
- Ambiguïté détectée : Périmètre non précisé (requêtes / schéma / indexation / migration / config serveur)
- Indices explicites : Aucun (pas de mention de métrique, symptôme ou outil)

[Raisonnement]
- Option A (clarifier) : probabilité 100%, coût erreur : nul, facilité correction : nul (aucune action avant réponse)
- Option B (inférer "requêtes SQL") : probabilité 30%, coût erreur : élevé (livrable hors cible), facilité correction : difficile (rework complet)
- "Optimiser BDD" = spectre large (5+ sous-périmètres possibles).
- Inférence "requêtes" = pari sur 1 sous-périmètre sans indice.

[Recommandation]
- **Option recommandée** : Clarifier avec utilisateur
- **Justification** : Coût clarification (+1 question) << coût rework (livrable hors cible).
- **Niveau de confiance** : 95%

[Alternatives classées]
1. **Clarifier** : "Quel aspect optimiser ? (requêtes lentes / schéma / indexation / migration / autre)" (confiance 100%, délai +30s)
2. **Router l'agent bases de données avec brief ouvert** : l'agent déterminera le périmètre (confiance 60%, risque hors cible 65%)
3. **Coordonner en multi-agents (l'agent de coordination)** : Si périmètre multi-facettes (confiance 50%, délai +coordination)

[Impact estimé par option]
| Option | Délai estimé | Risque hors cible | Probabilité rework |
|--------|--------------|-------------------|---------------------|
| Clarifier | +30 secondes | 0% | 0% |
| Router BDD direct | 2-4 heures | 65% | 60% |
| Coordination multi-agents (l'agent de coordination) | 4-6 heures | 20% | 15% |
```

### Cas 2 : Routage ambigu (agent de design d'interface ou agent de microcopie ?)
**Input** :
```text
Demande : "Améliorer l'UX de la page d'inscription"
Options :
- A : Agent de design d'interface (design visuel + parcours)
- B : Agent de microcopie (textes d'interface)
- C : Coordination multi-agents par l'agent de coordination
Contexte récent : Message précédent mentionne "formulaire long et confus"
```

**Output** :
```text
[Constat]
- Demande analysée : "Améliorer l'UX page d'inscription"
- Ambiguïté détectée : "UX" = large (design / parcours / microcopie / accessibilité / performance)
- Indices explicites : "formulaire long et confus" → problème de parcours/structure

[Raisonnement]
- Option A (agent de design d'interface) : probabilité 70%, coût erreur : moyen, facilité correction : moyen
  - "Formulaire long et confus" suggère redesign parcours + simplification champs.
  - L'agent de design d'interface couvre design visuel + parcours utilisateur.
- Option B (agent de microcopie) : probabilité 30%, coût erreur : moyen, facilité correction : moyen
  - L'agent de microcopie traite les labels, messages d'erreur et CTA.
  - "Long et confus" = structure globale, pas seulement texte.
- Option C (coordination multi-agents par l'agent de coordination) : probabilité 50%, coût erreur : faible, facilité correction : facile
  - Si parcours + microcopie nécessaires → multi-agents.

[Recommandation]
- **Option recommandée** : Agent de design d'interface
- **Justification** : Indice "long et confus" = redesign parcours (périmètre design d'interface). L'agent de microcopie peut être sollicité ensuite si nécessaire.
- **Niveau de confiance** : 70%

[Alternatives classées]
1. **Agent de design d'interface** : Redesign parcours + simplification formulaire (confiance 70%, délai 4-6h)
2. **Clarifier** : "Quel aspect UX améliorer ? (parcours formulaire / textes / accessibilité)" (confiance 100%, délai +30s)
3. **Coordination multi-agents (l'agent de coordination)** : Si refonte complète (parcours + microcopie + accessibilité) (confiance 50%, délai 8-12h)

[Impact estimé par option]
| Option | Délai estimé | Risque hors cible | Probabilité rework |
|--------|--------------|-------------------|---------------------|
| Agent de design d'interface | 4-6 heures | 30% | 25% |
| Clarifier | +30 secondes | 0% | 0% |
| Coordination multi-agents (l'agent de coordination) | 8-12 heures | 10% | 5% |
```

### Cas 3 : Urgence floue (critique ou élevée ?)
**Input** :
```text
Demande : "La BDD est lente, il faut corriger ça"
Options :
- A : Urgence critique (P1, incident prod)
- B : Urgence élevée (P2, dégradation)
- C : Clarifier l'impact utilisateur
Contexte récent : Aucun message sur indisponibilité ou SLA
```

**Output** :
```text
[Constat]
- Demande analysée : "BDD lente, corriger"
- Ambiguïté détectée : Urgence non précisée (lenteur perçue vs impact business)
- Indices explicites : Aucun sur indisponibilité, SLA cassé ou impact utilisateur quantifié

[Raisonnement]
- Option A (critique P1) : probabilité 20%, coût erreur : élevé (mobilisation inutile)
  - P1 = incident prod (indisponibilité totale ou SLA cassé).
  - "Lente" ≠ indisponible.
- Option B (élevée P2) : probabilité 60%, coût erreur : moyen
  - P2 = dégradation notable (latence +50%, utilisateurs impactés).
  - "Lente" suggère dégradation, pas panne.
- Option C (clarifier) : probabilité 100%, coût erreur : nul
  - Impact utilisateur non quantifié (combien d'utilisateurs ? quel seuil de latence ?).

[Recommandation]
- **Option recommandée** : Clarifier impact utilisateur
- **Justification** : Distinction P1/P2 dépend de l'impact métier (quantifié). "Lente" est subjectif.
- **Niveau de confiance** : 85%

[Alternatives classées]
1. **Clarifier** : "Quel impact ? (utilisateurs bloqués / latence +X% / SLA cassé)" (confiance 100%, délai +30s)
2. **Urgence élevée (P2)** : Si clarification impossible et production impactée (confiance 60%, risque sur-priorisation 40%)
3. **Urgence critique (P1)** : Si indices de panne totale ou SLA cassé (confiance 20%, risque mobilisation inutile 80%)

[Impact estimé par option]
| Option | Délai estimé | Risque sur/sous-priorisation | Coût mobilisation |
|--------|--------------|------------------------------|-------------------|
| Clarifier | +30 secondes | 0% | Nul |
| P2 (élevée) | Immédiat | 40% | Moyen |
| P1 (critique) | Immédiat | 80% | Élevé |
```

## Liens
- Skill complémentaire : [Audit Cohérence Logique Brief](./auditCoherenceLogiqueBrief.skill.md)
- Skill complémentaire : [Détection Boucles Délégation](./detectionBouclesDelegation.skill.md)
- Guide d'orchestration : [AGENTS.md](../agents.md)

## Exemples d'usage

### Exemple 1 : Choisir entre clarification et hypothèse
**Contexte** : Une demande indique « rends le rapport plus rapide » sans préciser s'il s'agit du temps de chargement ou du délai de livraison.  
**Input** : Formulation exacte, contexte récent, options envisagées et coût d'une interprétation erronée.  
**Output** : Ambiguïté explicitée, indices réellement disponibles, confiance estimée avec justification et recommandation de poser une question avant d'agir si les interprétations changent le résultat.

### Exemple 2 : Arbitrer un routage entre spécialiste et coordination
**Contexte** : Une demande touche une règle métier et une contrainte technique, et l'owner de la décision n'est pas évident.  
**Input** : Besoin, systèmes concernés, décision attendue, agents candidats et impacts d'un mauvais routage.  
**Output** : Options classées, éléments de preuve, coûts possibles d'erreur et recommandation de routage ou de clarification, sans présenter l'estimation comme un fait.

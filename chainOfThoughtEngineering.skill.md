# Chain of Thought Engineering

## Objectif
Concevoir des prompts utilisant des techniques de raisonnement étape par étape (Chain-of-Thought, ReAct, Tree of Thoughts) pour améliorer la qualité des réponses sur tâches complexes nécessitant analyse, décomposition ou résolution multi-étapes.

## Quand l'utiliser (triggers)
- Tâches nécessitant raisonnement multi-étapes (diagnostic, résolution problème, planification).
- Réponses trop directes manquant d'analyse ou de justification.
- Besoin de traçabilité du raisonnement (audit, explicabilité).
- Amélioration de la fiabilité sur tâches arithmétiques, logiques ou de déduction.
- Détection et correction d'erreurs de raisonnement en cours de génération.

## Hors périmètre
- Tâches simples ne nécessitant pas de raisonnement (récupération d'information factuelle directe).
- Optimisation structurelle générale du prompt → **Prompt Structure Optimization**.
- Tests adversariaux → **l'agent d'évaluation IA (red teaming)**.
- Optimisation coûts/latence (CoT augmente tokens) → **l'agent FinOps**.

## Inputs requis
- **Type de tâche** : diagnostic, résolution problème, planification, analyse multi-critères, déduction logique.
- **Complexité** : nombre d'étapes typiques, interdépendances entre étapes, points de décision critiques.
- **Format raisonnement attendu** : séquentiel linéaire (CoT classique), itératif avec actions (ReAct), arborescent avec alternatives (Tree of Thoughts).
- **Critères de qualité** : exactitude finale, traçabilité du raisonnement, détection d'erreurs intermédiaires.

## Sorties attendues
- **Prompt CoT optimisé** avec instructions explicites pour décomposer le raisonnement.
- **Template de raisonnement** : structure type pour guider l'agent (étapes, sous-questions, vérifications).
- **Stratégie de vérification** : mécanismes auto-correctifs (relecture, validation cohérence inter-étapes).
- **Comparatif avant/après** : amélioration exactitude et traçabilité vs prompt direct.

## Workflow recommandé

### 1. Identification du type de raisonnement optimal

- **Chain-of-Thought (CoT) classique** : raisonnement linéaire étape par étape.
  - **Cas d'usage** : arithmétique, logique séquentielle, déduction simple.
  - **Instruction type** : "Raisonne étape par étape avant de donner ta réponse finale."
  
- **ReAct (Reasoning + Acting)** : alternance raisonnement et actions (appel outil, recherche info).
  - **Cas d'usage** : diagnostic nécessitant collecte d'information, résolution problème avec validation empirique.
  - **Instruction type** : "Pour chaque étape : 1) Raisonne sur ce que tu sais, 2) Identifie l'information manquante, 3) Agis pour l'obtenir, 4) Intègre le résultat et passe à l'étape suivante."
  
- **Tree of Thoughts (ToT)** : exploration de plusieurs branches de raisonnement en parallèle.
  - **Cas d'usage** : planification avec alternatives, optimisation multi-critères, résolution créative.
  - **Instruction type** : "Explore 3 approches différentes en parallèle, évalue les avantages/inconvénients de chacune, puis choisis la meilleure."

### 2. Rédaction du prompt CoT

**Structure recommandée** :

```markdown
## Rôle et contexte
[Définir le rôle et le type de tâche nécessitant raisonnement]

## Instructions de raisonnement
Avant de fournir ta réponse finale, décompose ton raisonnement en étapes explicites :

1. **Compréhension** : Reformule le problème dans tes propres mots pour confirmer ta compréhension.

2. **Décomposition** : Identifie les sous-problèmes ou sous-questions à traiter séquentiellement.

3. **Résolution étape par étape** : Pour chaque sous-problème :
   - Analyse : [ce que tu sais]
   - Déduction : [ce que tu en déduis]
   - Validation : [vérification cohérence avec étapes précédentes]

4. **Synthèse** : Intègre les résultats des étapes pour formuler la réponse finale.

5. **Vérification** : Relis ton raisonnement pour détecter contradictions ou erreurs logiques.

## Format de sortie
- **Raisonnement** : [étapes détaillées avec numérotation]
- **Réponse finale** : [conclusion synthétique]
```

### 3. Ajout de mécanismes auto-correctifs

- **Self-consistency** : générer plusieurs chaînes de raisonnement et sélectionner la réponse la plus fréquente.
- **Reflection** : demander à l'agent de critiquer son propre raisonnement avant de finaliser.
- **Verification prompts** : ajouter une étape de vérification explicite ("Relis tes calculs / tes déductions et corrige toute erreur détectée.").

### 4. Test et validation

- Comparer précision réponse finale : prompt direct vs prompt CoT.
- Mesurer traçabilité : pourcentage de réponses avec raisonnement explicite complet.
- Analyser erreurs : détection d'erreurs intermédiaires corrigées vs erreurs non détectées.

### 5. Optimisation itérative

- Ajuster granularité des étapes (trop détaillé = verbosité excessive, trop synthétique = sauts logiques).
- Renforcer instructions de vérification si erreurs récurrentes à certaines étapes.
- Équilibrer exhaustivité du raisonnement vs coût tokens (CoT augmente significativement la longueur).

## Garde-fous
- **Ne pas sur-décomposer** : éviter les micro-étapes triviales qui diluent le raisonnement sans apporter de valeur.
- **Éviter les biais de confirmation** : encourager l'agent à explorer alternatives et contre-arguments, pas seulement confirmer première hypothèse.
- **Gérer l'explosion combinatoire (ToT)** : limiter le nombre de branches explorées pour rester dans des délais/coûts raisonnables.
- **Mesurer le coût** : CoT augmente tokens réponse de 2x à 5x → valider ROI (gain exactitude > surcoût).
- **Ne pas imposer CoT sur tâches simples** : réserver aux tâches réellement complexes (seuil : ≥ 3 étapes de raisonnement).

## Template d'entrée (copier/coller)
```text
[Type de tâche]
- Diagnostic / Résolution problème / Planification / Analyse multi-critères / Déduction logique

[Complexité]
- Nombre d'étapes typiques : [X]
- Interdépendances : [oui/non, détails si oui]
- Points de décision critiques : [liste]

[Format raisonnement attendu]
- CoT classique / ReAct / Tree of Thoughts

[Critères de qualité]
- Exactitude finale : [seuil attendu, ex: ≥ 90%]
- Traçabilité raisonnement : [complète/partielle/optionnelle]
- Détection erreurs intermédiaires : [obligatoire/recommandée]
```

## Template de sortie (copier/coller)
```markdown
# Prompt CoT Optimisé

## Rôle et contexte
[Définition rôle + type de tâche nécessitant raisonnement]

## Instructions de raisonnement
Avant de fournir ta réponse finale, décompose ton raisonnement en étapes explicites :

1. **Compréhension** : [instruction reformulation problème]

2. **Décomposition** : [instruction identification sous-problèmes]

3. **Résolution étape par étape** : [template pour chaque étape]
   - Étape [N] : [analyse → déduction → validation]

4. **Synthèse** : [instruction intégration résultats]

5. **Vérification** : [instruction relecture critique + auto-correction]

## Mécanismes auto-correctifs
- [Self-consistency / Reflection / Verification prompts selon besoin]

## Format de sortie
- **Raisonnement** : [étapes numérotées avec détails]
- **Réponse finale** : [conclusion synthétique]

---

# Comparatif avant/après

| Métrique | Prompt direct | Prompt CoT | Delta |
|----------|---------------|------------|-------|
| Exactitude finale | [X]% | [Y]% | [+Z]% |
| Traçabilité raisonnement | [X]% | [Y]% | [+Z]% |
| Détection erreurs intermédiaires | [X]% | [Y]% | [+Z]% |
| Tokens réponse moyen | [X] | [Y] | [+Z] ([%]) |
| Coût par requête | $[X] | $[Y] | [+$Z] ([%]) |

---

# Recommandation
[Déployer CoT / Affiner / Conserver prompt direct] car [justification basée données]
```

## Checklist QA interne
- [ ] Type de raisonnement (CoT/ReAct/ToT) adapté au type de tâche.
- [ ] Instructions de décomposition explicites et numérotées.
- [ ] Mécanisme de vérification/auto-correction inclus.
- [ ] Template de raisonnement fourni pour guider l'agent.
- [ ] Testé sur jeu de test représentatif (≥ 15 cas complexes).
- [ ] Comparatif avant/après avec métriques exactitude, traçabilité, coût.
- [ ] ROI validé : gain exactitude ≥ surcoût tokens (sauf si traçabilité obligatoire).
- [ ] Documentation complète avec exemples positifs/négatifs.

## KPI reliés
- **Gain exactitude CoT** : (exactitude CoT - exactitude direct) / exactitude direct x 100.
- **Taux traçabilité** : (réponses avec raisonnement explicite complet / réponses totales) x 100.
- **Taux détection erreurs** : (erreurs intermédiaires détectées et corrigées / erreurs totales) x 100.
- **Surcoût tokens CoT** : (tokens moyen CoT / tokens moyen direct) x 100 - 100.
- **ROI CoT** : (gain exactitude % - surcoût tokens %) — positif = rentable.

## Definition of done
- Prompt CoT optimisé avec instructions décomposition et vérification explicites.
- Testé sur minimum 15 cas complexes avec comparatif avant/après.
- Gain exactitude ≥ 10% OU traçabilité obligatoire justifiant le surcoût.
- Documentation complète : template raisonnement, mécanismes auto-correctifs, exemples.
- Validation coût/latence par **l'agent FinOps** si surcoût > 20%.

## Exemples d'usage

### Exemple 1 : CoT pour diagnostic technique
**Contexte** : Agent d'analyse d'erreurs système avec exactitude 68% sur problèmes multi-causes (prompt direct).

**Prompt direct** (extrait) :
```
Analyse cette erreur et propose une solution.
```

**Problème** : réponses trop rapides, pas d'analyse approfondie, causes racines manquées.

**Prompt CoT** (extrait) :
```markdown
## Instructions de diagnostic
Avant de proposer une solution, décompose ton diagnostic en étapes :

1. **Symptômes** : Liste tous les symptômes observés (codes erreur, comportements anormaux, logs pertinents).

2. **Hypothèses** : Formule 2-3 hypothèses de causes racines possibles basées sur les symptômes.

3. **Investigation** : Pour chaque hypothèse, identifie les éléments qui la confirment ou l'infirment.

4. **Cause racine** : Sélectionne la cause la plus probable avec justification.

5. **Solution** : Propose une remédiation ciblée sur la cause racine identifiée.

6. **Vérification** : Relis ton raisonnement pour t'assurer qu'aucune hypothèse plausible n'a été écartée prématurément.

## Format de sortie
- **Raisonnement** : [étapes 1-6 numérotées avec détails]
- **Solution finale** : [remédiation recommandée]
```

**Résultats** :

| Métrique | Prompt direct | Prompt CoT | Delta |
|----------|---------------|------------|-------|
| Exactitude diagnostic | 68% | 89% | +31% ✅ |
| Traçabilité raisonnement | 15% | 97% | +547% ✅ |
| Tokens réponse moyen | 120 | 380 | +217% ⚠️ |
| Coût par requête | $0.012 | $0.035 | +192% ⚠️ |

**Décision** : **Déployer CoT** - gain exactitude +31% justifie surcoût tokens +217% pour tâche critique (diagnostic production).

### Exemple 2 : ReAct pour résolution problème avec collecte d'information
**Contexte** : Agent support technique devant diagnostiquer pannes réseau (nécessite vérifications multiples).

**Prompt ReAct** (extrait) :
```markdown
## Instructions ReAct (Reasoning + Acting)
Pour chaque étape de diagnostic, applique ce cycle :

1. **Raisonne** : Que sais-je actuellement ? Quelle est l'hypothèse la plus probable ?

2. **Identifie l'action** : Quelle information manquante dois-je collecter pour confirmer/infirmer ?

3. **Agis** : [Utilise l'outil approprié : ping, traceroute, vérification config, consultation logs]

4. **Intègre** : Que m'apprend ce résultat ? Ajuste mon hypothèse en conséquence.

5. **Décide** : Ai-je suffisamment d'informations pour conclure, ou dois-je itérer ?

Répète ce cycle jusqu'à identification de la cause racine ou conclusion "diagnostic incomplet".
```

**Résultats** : Taux résolution premier contact 82% (vs 61% sans ReAct), nombre moyen d'itérations 3.2 (collecte d'information ciblée).

### Exemple 3 : Tree of Thoughts pour planification multi-critères
**Contexte** : Agent planification architecture logicielle devant comparer plusieurs approches (monolithe, microservices, serverless).

**Prompt ToT** (extrait) :
```markdown
## Instructions Tree of Thoughts
Explore 3 approches architecturales en parallèle :

### Branche 1 : Architecture monolithique
- **Avantages** : [liste]
- **Inconvénients** : [liste]
- **Score** : [0-10 sur critères : complexité, scalabilité, maintenabilité, coût]

### Branche 2 : Microservices
- **Avantages** : [liste]
- **Inconvénients** : [liste]
- **Score** : [0-10 sur mêmes critères]

### Branche 3 : Serverless
- **Avantages** : [liste]
- **Inconvénients** : [liste]
- **Score** : [0-10 sur mêmes critères]

### Synthèse comparative
| Critère | Monolithe | Microservices | Serverless | Pondération |
|---------|-----------|---------------|------------|-------------|
| Complexité | [score] | [score] | [score] | x2 |
| Scalabilité | [score] | [score] | [score] | x3 |
| Maintenabilité | [score] | [score] | [score] | x2 |
| Coût | [score] | [score] | [score] | x3 |
| **Total pondéré** | [X] | [Y] | [Z] | — |

### Recommandation finale
[Architecture retenue] car [justification basée scores pondérés + contexte projet]
```

**Résultats** : Qualité recommandation architecturale évaluée à 9.2/10 par architecte senior (vs 7.1/10 sans ToT), traçabilité complète des trade-offs.

### Exemple 4 : Optimisation granularité CoT (itération)
**Contexte** : Prompt CoT initial trop détaillé (12 micro-étapes) générant réponses excessivement longues (800 tokens) sans gain qualité vs version 6 étapes (450 tokens).

**Action** : Fusion étapes redondantes 12 → 6, maintien exactitude.

**Résultats** :

| Métrique | CoT 12 étapes | CoT 6 étapes | Delta |
|----------|---------------|--------------|-------|
| Exactitude | 91% | 90% | -1% ✅ |
| Tokens réponse moyen | 800 | 450 | -44% ✅ |
| Coût par requête | $0.072 | $0.041 | -43% ✅ |

**Décision** : **Déployer version 6 étapes** - exactitude quasi-identique (-1% négligeable) avec réduction coût -43%.

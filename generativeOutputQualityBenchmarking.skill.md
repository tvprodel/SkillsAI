# Generative Output Quality Benchmarking

## Objectif
Définir et exécuter un plan d'évaluation qualité des sorties génératives (texte, images, code) pour mesurer hallucination, biais, cohérence, exactitude factuelle, avec métriques automatisées et évaluation humaine.

## Quand l'utiliser (triggers)
- Validation d'un système GenAI avant mise en production.
- Audit qualité d'un système en production (détection dérive qualité).
- Comparaison A/B de modèles ou stratégies (RAG vs fine-tuning, modèle A vs modèle B).
- Investigation d'incidents qualité (plaintes utilisateurs, hallucinations détectées).
- Conformité et auditabilité (preuves qualité pour régulateurs, clients).

## Hors périmètre
- Tests adversariaux et robustesse (prompt injection, jailbreak) → **l'agent d'évaluation IA (red teaming)**.
- Optimisation coûts/latence du système → **l'agent FinOps**.
- Sélection du modèle de base → **l'agent de sélection de modèles génératifs** (skill Generative Model Selection).
- Stratégie RAG vs fine-tuning → **l'agent de sélection de modèles génératifs** (skill RAG & Fine-Tuning Strategy Design).

## Inputs requis
- **Système GenAI à évaluer** : modèle utilisé, architecture (prompting/RAG/fine-tuning), cas d'usage.
- **Exigences qualité** : critères prioritaires (exactitude, cohérence, biais, hallucination), seuils acceptabilité.
- **Jeux de test** : échantillons représentatifs du cas d'usage (volumétrie, diversité, edge cases).
- **Métriques cibles** : KPI qualité à mesurer (BLEU, ROUGE, exactitude, taux hallucination, etc.).
- **Budget évaluation** : temps disponible, budget évaluation humaine (si applicable).

## Sorties attendues
- **Plan d'évaluation** : métriques sélectionnées, méthodes (automatisées/humaines), jeux de test, fréquence.
- **Rapport de benchmark** : résultats mesurés pour chaque métrique, comparaison vs seuils, analyse écarts.
- **Dataset d'évaluation** : jeu de test validé et versionné pour reproductibilité.
- **Recommandations** : actions correctives si qualité insuffisante (amélioration prompt, changement modèle, ajustement RAG).

## Workflow recommandé
1. **Définition des critères qualité** : identifier les dimensions critiques selon le cas d'usage (exactitude factuelle, cohérence, créativité, ton, biais, hallucination).

2. **Sélection des métriques** :
   - **Métriques automatisées** : BLEU, ROUGE, METEOR (texte), FID/IS (images), pass@k (code), perplexité.
   - **LLM-as-judge** : utiliser un LLM (GPT-4, Claude) pour évaluer qualité des sorties selon critères (exactitude, pertinence, cohérence).
   - **Évaluation humaine** : échantillonnage et notation par experts (gold standard).

3. **Construction des jeux de test** :
   - **Baseline** : exemples représentatifs du cas d'usage (diversité, volumétrie).
   - **Edge cases** : cas limites (requêtes ambiguës, données manquantes, langues rares).
   - **Golden set** : jeu validé manuellement avec réponses attendues (ground truth).

4. **Exécution des tests** :
   - Automatisés : scripts de benchmark (BLEU/ROUGE/etc.).
   - LLM-as-judge : prompts d'évaluation standardisés.
   - Humains : protocole d'évaluation (échelles, critères, inter-rater reliability).

5. **Analyse des résultats** :
   - Comparaison vs seuils acceptabilité.
   - Identification patterns d'échec (types de requêtes, edge cases).
   - Calcul métriques agrégées et distribution.

6. **Recommandations** : actions correctives prioritaires selon écarts qualité détectés.

## Garde-fous
- **Ne pas se fier uniquement aux métriques automatisées** : BLEU/ROUGE corrèlent mal avec qualité perçue (cf. recherche NLP) ; combiner avec LLM-as-judge et évaluation humaine.
- **Biais du jeu de test** : s'assurer que le jeu de test est représentatif du trafic réel (diversité, edge cases).
- **LLM-as-judge peut être biaisé** : calibrer avec évaluation humaine ; utiliser plusieurs juges LLM si budget permet.
- **Évaluation humaine coûteuse** : échantillonner intelligemment (stratified sampling) ; calculer inter-rater reliability.
- **Dérive qualité en production** : monitorer en continu (échantillonnage hebdo/mensuel), pas seulement à la mise en production.
- **Hallucination difficile à détecter** : combiner métriques factuelles (fact-checking automatisé) + LLM-as-judge + évaluation humaine.

## Template d'entrée (copier/coller)
```text
[Système GenAI à évaluer]
- Modèle utilisé : ...
- Architecture : [prompting simple / RAG / fine-tuning / hybride]
- Cas d'usage : ...
- Volumétrie production estimée : ... requêtes/jour

[Exigences qualité]
- Critères prioritaires : [exactitude / cohérence / biais / hallucination / créativité / ton / autre]
- Seuils acceptabilité : ...

[Jeux de test]
- Volumétrie disponible : ... exemples
- Diversité : [représentatif / limité / à construire]
- Ground truth disponible : [oui / partiel / non]

[Métriques cibles]
- Automatisées : [BLEU / ROUGE / METEOR / FID / pass@k / autre]
- LLM-as-judge : [oui / non]
- Évaluation humaine : [oui / non]

[Budget évaluation]
- Temps disponible : ... jours/semaines
- Budget évaluation humaine : ... $/heures ou n/a
```

## Template de sortie (copier/coller)
```markdown
# Plan d'évaluation qualité GenAI

## Critères qualité et métriques

| Critère | Métrique | Méthode | Seuil acceptabilité | Poids |
|---------|----------|---------|---------------------|-------|
| Exactitude factuelle | Fact-checking automatisé + LLM-as-judge | Automatisée + LLM | > 95% | Critique |
| Hallucination | Taux hallucination (détection manuelle + LLM) | LLM + Humain | < 2% | Critique |
| Cohérence logique | ROUGE-L + évaluation humaine | Automatisée + Humain | > 0.85 / > 4/5 | Élevé |
| Biais équité | Écart de qualité entre catégories démographiques | Humain | < 5% | Élevé |
| Pertinence | LLM-as-judge (score 1-5) | LLM | > 4.2/5 | Élevé |
| Créativité | Évaluation humaine (échelle 1-5) | Humain | > 3.5/5 | Normal |

## Jeux de test

### Baseline (représentatif)
- Volumétrie : ... exemples
- Source : ...
- Diversité : [catégories, edge cases, langues]

### Golden set (ground truth)
- Volumétrie : ... exemples validés
- Annotation : [manuelle / automatisée / mixte]
- Inter-rater reliability : ... (Kappa / % accord)

### Edge cases
- Types : [requêtes ambiguës / données manquantes / langues rares / autre]
- Volumétrie : ... exemples

## Méthodes d'évaluation

### 1. Métriques automatisées
- **BLEU/ROUGE** : script Python, corpus de référence
- **Fact-checking** : API FactCheckGPT ou similaire
- Fréquence : quotidienne (automatisée)

### 2. LLM-as-judge
- **Modèle juge** : GPT-4 Turbo
- **Prompt d'évaluation** : [voir annexe]
- **Critères** : exactitude, pertinence, cohérence (échelle 1-5)
- Fréquence : hebdomadaire (échantillon 100 requêtes)

### 3. Évaluation humaine
- **Échantillon** : 200 requêtes/mois (stratified sampling)
- **Annotateurs** : 3 experts métier
- **Protocole** : échelle 1-5, critères définis, guidelines
- **Inter-rater reliability** : calculé mensuellement (Kappa > 0.7)

## Planning

| Phase | Durée | Livrables |
|-------|-------|-----------|
| Construction jeu de test | 2 semaines | Golden set validé (500 exemples) |
| Setup automatisation | 1 semaine | Scripts BLEU/ROUGE + LLM-as-judge |
| Évaluation initiale | 1 semaine | Rapport baseline |
| Évaluation humaine | 2 semaines | Rapport évaluation humaine + inter-rater |
| Analyse et recommandations | 1 semaine | Rapport final + actions correctives |

## Seuils de validation

### Go/No-Go production
- Exactitude factuelle > 95% ✅
- Taux hallucination < 2% ✅
- Cohérence ROUGE-L > 0.85 ✅
- Biais équité < 5% écart ✅
- Pertinence LLM-as-judge > 4.2/5 ✅

Si 1+ critère non atteint : actions correctives obligatoires avant mise en production.

## Rapport de benchmark (exemple)

### Résultats mesurés

| Métrique | Résultat | Seuil | Statut |
|----------|----------|-------|--------|
| Exactitude factuelle | 96.8% | > 95% | ✅ PASS |
| Taux hallucination | 1.4% | < 2% | ✅ PASS |
| Cohérence ROUGE-L | 0.87 | > 0.85 | ✅ PASS |
| Biais équité | 3.2% écart | < 5% | ✅ PASS |
| Pertinence (LLM-judge) | 4.3/5 | > 4.2/5 | ✅ PASS |
| Créativité (humain) | 3.8/5 | > 3.5/5 | ✅ PASS |

### Analyse écarts

**Points forts** :
- Exactitude factuelle excellente (96.8%), meilleure que seuil.
- Taux hallucination très faible (1.4%), conforme attentes.

**Points de vigilance** :
- Cohérence ROUGE-L juste au-dessus du seuil (0.87 vs 0.85) : surveiller en production.
- Pertinence LLM-as-judge proche du seuil (4.3 vs 4.2) : échantillonnage humain recommandé.

**Patterns d'échec identifiés** :
- Hallucinations concentrées sur requêtes en langues rares (5% du trafic) : améliorer corpus RAG.
- Biais détecté sur catégorie démographique X (+3.2% écart) : rééquilibrer jeu d'entraînement.

### Recommandations

1. **Mise en production autorisée** : tous les seuils validés.
2. **Actions correctives post-déploiement** :
   - Enrichir corpus RAG langues rares (priorité : allemand, néerlandais).
   - Monitoring hebdomadaire cohérence ROUGE-L (alertes si < 0.85).
   - Rééquilibrage dataset fine-tuning pour réduire biais catégorie X (sprint suivant).
```

## Checklist QA interne
- [ ] Au moins 3 métriques définies (automatisées, LLM-as-judge ou humaines).
- [ ] Seuils acceptabilité définis pour chaque métrique (mesurables, justifiés).
- [ ] Jeu de test construit avec baseline + edge cases + golden set (si applicable).
- [ ] Méthode d'évaluation documentée (scripts, prompts LLM-as-judge, protocole humain).
- [ ] Inter-rater reliability calculé si évaluation humaine (Kappa > 0.7 ou % accord > 80%).
- [ ] Rapport de benchmark produit avec résultats vs seuils + analyse écarts.
- [ ] Patterns d'échec identifiés (types requêtes, edge cases, catégories).
- [ ] Recommandations actions correctives prioritaires (si seuils non atteints).

## KPI reliés
- **Taux de validation qualité** : (systèmes validés / systèmes évalués) x 100.
- **Taux de détection dérive qualité** : (dérives détectées en monitoring / audits effectués) x 100.
- **Inter-rater reliability** : Kappa Cohen > 0.7 (accord substantiel) ou % accord > 80%.
- **Couverture jeux de test** : (volumétrie jeu de test / volumétrie production estimée) x 100.

## Definition of done
- Plan d'évaluation complet avec 3+ métriques, seuils, méthodes, jeux de test (mesure : présence des 4 éléments ; preuve : document Plan d'évaluation).
- Jeu de test construit et versionné (baseline + golden set + edge cases) avec au moins 100 exemples (mesure : volumétrie ; preuve : dataset livré).
- Rapport de benchmark produit avec résultats mesurés, comparaison vs seuils, analyse écarts (mesure : présence de 3+ métriques mesurées ; preuve : tableau résultats).
- Patterns d'échec identifiés (types de requêtes, edge cases, catégories problématiques) (mesure : au moins 2 patterns documentés ; preuve : section Analyse écarts).
- Recommandations actions correctives si seuils non atteints (mesure : au moins 1 action par seuil non atteint ; preuve : section Recommandations).

## Exemples d'usage

### Exemple 1 : Validation chatbot FAQ avant mise en production

**Contexte** : Startup SaaS veut valider la qualité d'un chatbot FAQ support client avant mise en production. Modèle : GPT-4o mini, architecture RAG, corpus 2K articles FAQ.

**Plan d'évaluation** :

| Critère | Métrique | Méthode | Seuil | Poids |
|---------|----------|---------|-------|-------|
| Exactitude factuelle | Fact-checking + LLM-as-judge | Automatisée + LLM | > 95% | Critique |
| Hallucination | Taux hallucination (LLM-as-judge) | LLM | < 2% | Critique |
| Pertinence | LLM-as-judge (score 1-5) | LLM | > 4/5 | Élevé |
| Ton professionnel | Évaluation humaine (échelle 1-5) | Humain | > 4/5 | Élevé |

**Jeu de test** : 500 requêtes FAQ réelles (baseline) + 100 edge cases (requêtes ambiguës, typos) + 200 golden set (réponses validées manuellement).

**Résultats** :

| Métrique | Résultat | Seuil | Statut |
|----------|----------|-------|--------|
| Exactitude factuelle | 97.2% | > 95% | ✅ PASS |
| Taux hallucination | 1.8% | < 2% | ✅ PASS |
| Pertinence | 4.3/5 | > 4/5 | ✅ PASS |
| Ton professionnel | 4.5/5 | > 4/5 | ✅ PASS |

**Décision** : Mise en production autorisée, tous les seuils validés. Monitoring hebdomadaire sur échantillon 100 requêtes. ✅

### Exemple 2 : Audit qualité système en production (dérive détectée)

**Contexte** : Système GenAI en production depuis 6 mois, plaintes utilisateurs en augmentation (+40% mois dernier). Audit qualité demandé.

**Plan audit** :
- Échantillon : 1000 requêtes réelles (mois dernier) stratified sampling
- Métriques : exactitude factuelle, hallucination, pertinence (LLM-as-judge)
- Comparaison : résultats actuels vs baseline mise en production

**Résultats** :

| Métrique | Baseline (T0) | Actuel (T+6m) | Écart | Seuil | Statut |
|----------|---------------|---------------|-------|-------|--------|
| Exactitude factuelle | 96.8% | 89.2% | -7.6 pp | > 95% | ❌ FAIL |
| Taux hallucination | 1.4% | 4.8% | +3.4 pp | < 2% | ❌ FAIL |
| Pertinence | 4.3/5 | 3.9/5 | -0.4 | > 4/5 | ❌ FAIL |

**Analyse** : Dérive qualité significative détectée. Patterns d'échec :
- Hallucinations concentrées sur nouvelles catégories produits (ajoutées mois 3, non présentes dans corpus RAG initial).
- Exactitude factuelle dégradée sur questions prix (catalogue prix modifié mois 4, pas de mise à jour corpus RAG).

**Recommandations** :
1. **Urgent** : Mise à jour corpus RAG avec nouvelles catégories produits + catalogue prix actuel (délai : 3 jours).
2. **Court terme** : Pipeline automatisé de synchronisation corpus RAG avec catalogue produits (quotidien) (délai : 2 semaines).
3. **Moyen terme** : Monitoring qualité automatisé (alertes si dérive > 5%) (délai : 1 mois).

**Résultat post-correction** : Corpus RAG mis à jour, nouvelle évaluation après 1 semaine : exactitude 96.1%, hallucination 1.6%, pertinence 4.2/5. ✅ Dérive corrigée.

### Exemple 3 : Comparaison A/B modèles (GPT-4 vs Claude 3.5 Sonnet)

**Contexte** : Projet GenAI cherche à optimiser coût sans dégradation qualité. Test A/B : GPT-4 Turbo (actuel) vs Claude 3.5 Sonnet (candidat, coût -60%).

**Plan A/B** :
- Échantillon : 500 requêtes réelles (identiques pour les 2 modèles)
- Métriques : exactitude, cohérence (ROUGE-L), pertinence (LLM-as-judge), préférence humaine (blind test)
- Budget : 10 heures évaluation humaine (100 paires blind test)

**Résultats** :

| Métrique | GPT-4 Turbo | Claude 3.5 Sonnet | Écart | Seuil acceptable |
|----------|-------------|-------------------|-------|------------------|
| Exactitude factuelle | 96.8% | 95.2% | -1.6 pp | < 2 pp (toléré) |
| Cohérence ROUGE-L | 0.87 | 0.89 | +0.02 | +/- 0.03 (équivalent) |
| Pertinence (LLM-judge) | 4.3/5 | 4.4/5 | +0.1 | +/- 0.2 (équivalent) |
| Préférence humaine | 48% | 52% | +4 pp | +/- 10 pp (statistiquement équivalent) |

**Décision** : **Migration vers Claude 3.5 Sonnet autorisée** — Qualité équivalente (écarts dans marges tolérées), coût réduit de 60% ($0.015/req → $0.006/req). Économie estimée : $12K/mois. ✅

**Résultat** : Migration effectuée, monitoring qualité post-migration (1 mois) : aucune dérive détectée, satisfaction utilisateurs stable. ✅

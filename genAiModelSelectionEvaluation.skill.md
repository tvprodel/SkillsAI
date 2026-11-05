# Generative Model Selection & Evaluation

## Objectif
Cadrer la comparaison et la sélection motivée d'un modèle génératif (LLM, diffusion, embeddings) selon capacités, coût, licence, contexte, statut de support, avec recommandation finale chiffrée et justifiée.

## Quand l'utiliser (triggers)
- Démarrage d'un projet GenAI nécessitant choix d'un modèle fondation.
- Migration ou remplacement d'un modèle existant (EOL, coût excessif, performances insuffisantes).
- Arbitrage entre plusieurs modèles candidats (open source vs propriétaire).
- Veille technologique : évaluation de nouveaux modèles disponibles.
- Audit de conformité : vérifier statut de support et licence des modèles en production.

## Hors périmètre
- Rédaction/optimisation du texte du prompt → **l'agent de prompt engineering**.
- Implémentation technique du système IA → **l'agent d'intégration et d'automatisation** ou **l'agent de développement back-end**.
- Optimisation fine coûts/latence (tokens, caching, infra) → **l'agent FinOps**.
- Tests adversariaux et robustesse → **l'agent d'évaluation IA (red teaming)**.

## Inputs requis
- **Cas d'usage** : objectif métier, type de tâche (génération texte, embeddings, images, code).
- **Contraintes** : budget max/requête, latence max acceptable (TTFT/TPS), souveraineté/confidentialité données.
- **Volumétrie** : nombre de requêtes/jour estimé, taille moyenne des prompts/réponses.
- **Exigences qualité** : benchmarks prioritaires (MMLU, HumanEval, etc.), critères métier (exactitude, créativité, ton).
- **Liste modèles candidats** (optionnel) : modèles déjà identifiés à comparer.

## Sorties attendues
- **Tableau comparatif chiffré** : modèles comparés sur 7+ critères (capacités, coût, latence, licence, statut support, benchmarks).
- **Shortlist motivée** : 2-3 modèles recommandés avec justification par critère.
- **Recommandation finale** : 1 modèle retenu avec rationale décisionnel (trade-offs, risques, réversibilité).
- **Plan de validation** : tests à effectuer avant mise en production (qualité, coût réel, latence).

## Workflow recommandé
1. **Cadrage du besoin** : clarifier le cas d'usage, les contraintes prioritaires (coût, latence, qualité, souveraineté).

2. **Identification des modèles candidats** : lister les modèles pertinents (open source + propriétaires) selon le type de tâche.
   - LLM génération texte : GPT-4, Claude 3.5, Llama 3.1, Mistral, Gemini
   - Embeddings : text-embedding-3, Voyage AI, sentence-transformers
   - Images : DALL-E 3, Stable Diffusion, Midjourney
   - Code : GPT-4, Claude 3.5, Codex, CodeLlama

3. **Collecte des métriques** : pour chaque modèle candidat, recueillir :
   - Capacités : fenêtre de contexte, multimodalité, langues supportées
   - Coût : prix par 1K tokens input/output ou par image/requête
   - Latence : TTFT (time to first token), TPS (tokens per second)
   - Licence : open source (MIT, Apache, Llama) ou propriétaire
   - Statut support : maintenu activement, EOL prévu, fréquence updates
   - Benchmarks publics : MMLU, HumanEval, MATH, scores qualité

4. **Comparaison multicritères** : construire un tableau comparatif chiffré et scorer chaque modèle selon les priorités métier.

5. **Shortlist et recommandation** : sélectionner 2-3 finalistes, justifier le choix final avec trade-offs explicites.

6. **Plan de validation** : définir les tests à effectuer (qualité sur jeu de test métier, coût réel sur volumétrie cible, latence en conditions réelles).

## Garde-fous
- **Vérifier statut de support** : ne jamais recommander de modèle EOL ou non maintenu sans plan de migration explicite.
- **Comparaison équitable** : utiliser benchmarks publics récents (< 6 mois) sur tâches comparables.
- **Coût total estimé** : inclure coût API + coût fine-tuning éventuel + coût vector store (si RAG).
- **Latence production** : tester latence en conditions réelles (concurrence, pic de charge), pas seulement benchmarks isolés.
- **Licence et souveraineté** : vérifier compatibilité licence (commercial use, data privacy) et contraintes souveraineté (RGPD, Cloud Act).
- **Anti-hallucination sur benchmarks** : ne citer que des scores vérifiés (sources publiques fiables) ; admettre « données non disponibles » si manquantes.

## Template d'entrée (copier/coller)
```text
[Cas d'usage]
- Objectif métier : ...
- Type de tâche : [génération texte / embeddings / images / code / autre]
- Langues : ...
- Multimodalité requise : [oui/non]

[Contraintes]
- Budget max/requête : ...
- Latence max acceptable : TTFT ... ms, TPS ... tokens/s
- Souveraineté/confidentialité : [cloud US/EU, self-hosted, conformité RGPD, etc.]
- Volumétrie estimée : ... requêtes/jour

[Exigences qualité]
- Benchmarks prioritaires : [MMLU, HumanEval, MATH, autre]
- Critères métier : [exactitude, créativité, ton professionnel, multilinguisme, etc.]

[Modèles candidats (optionnel)]
- ...
```

## Template de sortie (copier/coller)
```markdown
# Comparatif de modèles génératifs

## Tableau comparatif

| Modèle | Contexte | Coût/1K tokens (in/out) | Latence TTFT | Licence | Statut support | Score MMLU | Score HumanEval |
|--------|----------|-------------------------|--------------|---------|----------------|------------|-----------------|
| ... | ... | ... | ... | ... | ... | ... | ... |

## Shortlist motivée

### Modèle A : [Nom]
- **Avantages** : ...
- **Inconvénients** : ...
- **Score pondéré** : .../100

### Modèle B : [Nom]
- **Avantages** : ...
- **Inconvénients** : ...
- **Score pondéré** : .../100

## Recommandation finale

**Modèle retenu** : [Nom]

**Justification** :
- Critère 1 : ...
- Critère 2 : ...
- Critère 3 : ...
- Trade-offs acceptés : ...

**Risques identifiés** :
- Risque 1 : ... | Mitigation : ...
- Risque 2 : ... | Mitigation : ...

**Plan de réversibilité** : si échec, fallback vers [Modèle B] avec migration estimée à [durée/coût].

## Plan de validation

### Tests qualité
- Jeu de test : [description, taille]
- Métriques : [exactitude, cohérence, pertinence]
- Seuils acceptabilité : ...

### Tests coût/latence
- Volumétrie test : ... requêtes sur ... jours
- Coût attendu : ... $/jour
- Latence attendue : TTFT ... ms, TPS ... tokens/s

### Critères de succès
- Qualité : score > ...
- Coût : < ... $/requête
- Latence : TTFT < ... ms
```

## Checklist QA interne
- [ ] Au moins 3 modèles comparés (sauf contrainte justifiée).
- [ ] 7 critères minimum dans le tableau comparatif (contexte, coût, latence, licence, support, 2 benchmarks).
- [ ] Statut de support vérifié pour chaque modèle (maintenu/EOL/inconnu).
- [ ] Coût total estimé (API + fine-tuning + vector store si RAG).
- [ ] Latence validée (benchmarks publics + estimation conditions réelles).
- [ ] Licence et souveraineté vérifiées (compatibilité RGPD, commercial use).
- [ ] Benchmarks sources citées (pas de chiffres inventés).
- [ ] Shortlist justifiée avec trade-offs explicites.
- [ ] Recommandation finale avec rationale décisionnel complet.
- [ ] Plan de validation défini (tests qualité + coût/latence + critères de succès).

## KPI reliés
- **Taux de succès sélection** : (modèles retenus validés en production / modèles recommandés) x 100.
- **Écart coût prédit vs réel** : (coût production mesuré - coût estimé) / coût estimé x 100.
- **Écart latence prédite vs réelle** : (latence production mesurée - latence estimée) / latence estimée x 100.
- **Taux d'obsolescence détectée** : (modèles EOL détectés avant production / modèles audités) x 100.

## Definition of done
- Tableau comparatif complet avec 3+ modèles et 7+ critères chiffrés (mesure : nombre de lignes/colonnes ; preuve : tableau livré).
- Shortlist de 2-3 modèles avec justification par critère (mesure : présence de 3+ justifications par modèle ; preuve : section Shortlist).
- Recommandation finale avec rationale décisionnel (contexte, trade-offs, risques, réversibilité) (mesure : présence des 4 rubriques ; preuve : section Recommandation).
- Plan de validation avec tests qualité/coût/latence et critères de succès mesurables (mesure : présence de 3 types de tests + seuils ; preuve : section Plan de validation).
- Aucun modèle EOL recommandé sans plan de migration explicite (mesure : vérification statut support ; preuve : colonne Statut support + plan migration si EOL).

## Exemples d'usage

### Exemple 1 : Sélection LLM pour chatbot support client

**Contexte** : Startup SaaS cherche un LLM pour chatbot support client (français/anglais), volumétrie 10K requêtes/jour, budget serré.

**Inputs** :
- Cas d'usage : chatbot support client FAQ/troubleshooting
- Langues : français, anglais
- Budget max : $0.005/requête
- Latence max : TTFT < 1s
- Volumétrie : 10K requêtes/jour
- Exigences qualité : exactitude > 90%, ton professionnel

**Comparatif** :

| Modèle | Contexte | Coût/1K tokens (in/out) | Latence TTFT | Licence | Statut support | Score MMLU |
|--------|----------|-------------------------|--------------|---------|----------------|------------|
| GPT-4 Turbo | 128k | $0.01 / $0.03 | ~800ms | Propriétaire | Maintenu | 86.4% |
| Claude 3.5 Sonnet | 200k | $0.003 / $0.015 | ~600ms | Propriétaire | Maintenu | 88.7% |
| Llama 3.1 70B | 128k | ~$0 (self-hosted) | ~900ms | Open source | Maintenu | 83.6% |
| Mistral Large 2 | 128k | $0.002 / $0.006 | ~700ms | Propriétaire | Maintenu | 84.0% |

**Recommandation** : **Mistral Large 2** — Meilleur compromis coût/qualité/latence pour le cas d'usage. Coût estimé $0.003/requête (600 tokens moyens in+out), conforme budget. MMLU 84% suffisant pour FAQ. Latence < 1s. Fallback : Claude 3.5 si qualité insuffisante.

**Résultat** : Mistral Large 2 validé en production, coût réel $0.0028/requête, exactitude mesurée 92%, latence TTFT moyenne 720ms. ✅

### Exemple 2 : Sélection embeddings pour RAG documentation technique

**Contexte** : Éditeur logiciel veut implémenter RAG sur documentation technique (100K pages), recherche sémantique précise prioritaire.

**Inputs** :
- Cas d'usage : embeddings pour RAG documentation technique
- Langue : anglais principalement
- Budget : flexible (priorité qualité)
- Volumétrie : 100K pages à embedder initialement, puis 1K requêtes recherche/jour
- Exigences qualité : précision retrieval > 95% (top-5)

**Comparatif** :

| Modèle | Dimension | Coût embed/1M tokens | Latence | Licence | Statut support | Score MTEB |
|--------|-----------|----------------------|---------|---------|----------------|------------|
| text-embedding-3-large | 3072 | $0.13 | ~100ms | Propriétaire | Maintenu | 64.6% |
| Voyage AI voyage-2 | 1024 | $0.12 | ~90ms | Propriétaire | Maintenu | 68.2% |
| sentence-transformers/all-MiniLM-L6-v2 | 384 | ~$0 (self-hosted) | ~50ms | Open source (Apache 2.0) | Maintenu | 58.8% |
| Cohere embed-english-v3.0 | 1024 | $0.10 | ~80ms | Propriétaire | Maintenu | 64.5% |

**Recommandation** : **Voyage AI voyage-2** — Meilleur score MTEB (68.2%), latence < 100ms, coût acceptable pour volumétrie. Dimension 1024 suffisante pour documentation technique. Fallback : text-embedding-3-large si précision insuffisante (score MTEB légèrement inférieur mais dimension 3072 plus riche).

**Résultat** : Voyage-2 validé, précision retrieval top-5 mesurée 96.8% sur jeu de test, coût initial embedding $13 (100M tokens), coût requêtes $0.0001/recherche. ✅

### Exemple 3 : Remplacement modèle EOL (GPT-3.5 Turbo legacy)

**Contexte** : Application en production utilise GPT-3.5 Turbo (version legacy proche EOL), migration urgente requise.

**Inputs** :
- Cas d'usage actuel : génération résumés articles (500 tokens in, 150 tokens out)
- Volumétrie : 50K requêtes/jour
- Budget actuel : $0.0015/requête (GPT-3.5 Turbo legacy $0.0015 / $0.002)
- Latence actuelle : TTFT ~400ms
- Contrainte : migration sans régression qualité ni dépassement budget

**Comparatif modèles de remplacement** :

| Modèle | Contexte | Coût/1K tokens (in/out) | Latence TTFT | Statut support | Score résumé (ROUGE-L) |
|--------|----------|-------------------------|--------------|----------------|------------------------|
| GPT-4o mini | 128k | $0.00015 / $0.0006 | ~350ms | Maintenu (recommandé OpenAI) | 0.42 |
| Claude 3 Haiku | 200k | $0.00025 / $0.00125 | ~300ms | Maintenu | 0.44 |
| Gemini 1.5 Flash | 1M | $0.000075 / $0.0003 | ~400ms | Maintenu | 0.40 |

**Recommandation** : **GPT-4o mini** — Remplaçant officiel GPT-3.5 Turbo recommandé par OpenAI. Coût divisé par 2 ($0.0007/requête vs $0.0015), latence améliorée (350ms vs 400ms), qualité supérieure (ROUGE-L 0.42 vs 0.38 GPT-3.5). Migration API minimale (même endpoint, changement modèle). Fallback : Claude 3 Haiku si problème qualité (score ROUGE-L meilleur 0.44).

**Résultat** : Migration GPT-4o mini effectuée en 48h, coût production réduit de 53%, qualité mesurée +8% ROUGE-L, latence -12%. ✅

# Multi-Agent Orchestration Patterns

**Skill owner** : l'agent d'architecture IA

## Description
Design patterns d'orchestration multi-agents IA : coordination séquentielle/parallèle/conditionnelle, chaînage de prompts, delegation workflows, retry/fallback strategies, human-in-the-loop.

## Déclencheurs
- Système nécessitant coordination de plusieurs agents IA
- Workflows complexes avec branchements conditionnels
- Orchestration multi-LLM (cascade, ensemble, routing)
- Gestion erreurs et résilience agents IA
- Intégration human-in-the-loop dans workflow agents

## Compétences couvertes
1. **Patterns d'orchestration de base** : séquentiel, parallèle, conditionnel (if/else), DAG (directed acyclic graph)
2. **Chaînage de prompts** : output agent N → input agent N+1, transformation contexte, accumulation state
3. **Routing et delegation** : classifier → routing → specialist agents, delegation hiérarchique
4. **Retry et fallback** : retry avec backoff, fallback vers agent secondaire, circuit breaker
5. **Human-in-the-loop** : points de validation humaine, escalation automatique, approval workflows
6. **State management** : gestion état partagé entre agents, persistence conversation, context window management
7. **Monitoring et observabilité** : tracing multi-agents, logging décisions, métriques performance par agent

## Périmètre et frontières
- **Dans le périmètre** : patterns orchestration, coordination agents, gestion erreurs, state management
- **Hors périmètre** :
  - Optimisation prompts individuels → l'agent d'ingénierie de prompts
  - Sélection modèles → l'agent spécialiste en IA générative
  - Implémentation technique → l'agent d'intégration et d'automatisation

## Inputs requis
- Objectif métier, tâches à décomposer et critères de réussite mesurables.
- Agents/outils disponibles, capacités, limites et responsabilités.
- Contraintes de latence, coûts, confidentialité, fiabilité et supervision humaine.
- Cas d'échec attendus, mécanismes de reprise et limites de délégation.

## Workflow recommandé
1. Vérifier si une orchestration multi-agents est nécessaire plutôt qu'un flux simple.
2. Décomposer le travail et attribuer un owner unique à chaque résultat.
3. Choisir un pattern et le justifier selon les dépendances et contraintes.
4. Définir les contrats d'entrée/sortie, erreurs, timeouts, limites et observabilité.
5. Tester les scénarios normaux, limites et échecs avant mise en service.

## Template d'entrée (copier/coller)
```text
[Objectif et tâches] ...
[Agents/outils disponibles et compétences] ...
[Contraintes] Latence, coûts, confidentialité, supervision : ...
[Échecs à gérer] Timeout, réponse invalide, indisponibilité, conflit : ...
```

## Template de sortie (copier/coller)
```text
[Pattern retenu] ...
[Graphe de workflow] Étapes, routage, parallélisme et owners : ...
[Contrats] Entrées, sorties, validations et limites : ...
[Reprise] Erreurs, retries, fallback, escalade humaine et observabilité : ...
```

## Checklist QA interne
- Le nombre d'agents est justifié; aucun rôle ou transfert d'ownership n'est ambigu.
- Les boucles, doublons, timeouts, erreurs et défaillances partielles ont un traitement.
- Les critères d'arrêt, validations humaines et risques de coût/confidentialité sont prévus.

## Definition of done
- Le graphe de coordination, les contrats et owners sont documentés.
- Les scénarios de test couvrent succès, échec et escalade.
- Les limites et critères d'arrêt sont explicités avant implémentation.

## Patterns détaillés

### Pattern 1 : Sequential Chain (Chaîne séquentielle)
**Use case** : processing pipeline avec étapes dépendantes
```
User query → Agent 1 (analysis) → Agent 2 (retrieval) → Agent 3 (synthesis) → Response
```
**Avantages** : simple, prévisible, debuggable  
**Inconvénients** : latence cumulative, pas de parallélisation  
**Quand utiliser** : étapes strictement dépendantes (output N = input N+1)

### Pattern 2 : Parallel Execution (Exécution parallèle)
**Use case** : agrégation de sources multiples indépendantes
```
User query → [Agent 1 (source A) || Agent 2 (source B) || Agent 3 (source C)] → Aggregator → Response
```
**Avantages** : latence réduite (max latence agent le plus lent), throughput élevé  
**Inconvénients** : complexité agrégation, coût si tous agents toujours appelés  
**Quand utiliser** : sources indépendantes, latence critique

### Pattern 3 : Conditional Routing (Routage conditionnel)
**Use case** : dispatch vers agent spécialisé selon intent/contexte
```
User query → Classifier → if (intent=FAQ) → FAQ Agent
                       → elif (intent=Technical) → Tech Agent
                       → elif (intent=Billing) → Billing Agent
                       → else → Escalation Agent
```
**Avantages** : coût optimisé (1 seul specialist agent appelé), qualité supérieure (spécialisation)  
**Inconvénients** : dépend précision classifier, risque misrouting  
**Quand utiliser** : domaines distincts, coût par appel élevé

### Pattern 4 : Cascade (Cascading)
**Use case** : tenter agent performant/cher, fallback vers agent rapide/économique si échec/timeout
```
User query → Primary Agent (GPT-4) → if (success) → Response
                                   → elif (timeout/error) → Secondary Agent (GPT-3.5) → Response
```
**Avantages** : balance qualité/coût, résilience  
**Inconvénients** : latence maximale = primary timeout + secondary latency  
**Quand utiliser** : SLA strict, budget limité, tolérance dégradation qualité

### Pattern 5 : Ensemble (Voting/Averaging)
**Use case** : consensus ou agrégation de plusieurs agents pour robustesse
```
User query → [Agent 1 || Agent 2 || Agent 3] → Voting/Averaging → Response
```
**Avantages** : robustesse (réduction hallucinations, biais), qualité supérieure  
**Inconvénients** : coût 3x, latence = max(agents)  
**Quand utiliser** : décisions critiques (legal, medical, financial), hallucination rate élevé

### Pattern 6 : Human-in-the-Loop (Validation humaine)
**Use case** : approbation humaine avant actions critiques (paiement, suppression, publication)
```
User request → Agent analysis → if (confidence < threshold) → Human approval → Action
                               → elif (confidence >= threshold) → Auto-approve → Action
```
**Avantages** : sécurité, contrôle, apprentissage (feedback humain)  
**Inconvénients** : latence élevée (attente humain), scalabilité limitée  
**Quand utiliser** : actions irréversibles, domaines sensibles, démarrage système (calibration)

### Pattern 7 : Retry with Backoff (Retry avec délai exponentiel)
**Use case** : gestion erreurs transitoires (rate limit, timeout réseau)
```
User query → Agent call → if (error && retries < max) → wait (backoff) → retry
                        → elif (error && retries >= max) → fallback/error
                        → else → Response
```
**Avantages** : résilience face erreurs transitoires  
**Inconvénients** : latence augmentée si erreurs fréquentes  
**Quand utiliser** : API externes instables, rate limits, timeouts réseau

## Livrables types
1. **Diagramme orchestration** : flowchart Mermaid/C4 montrant flux agents, branchements, fallbacks
2. **Spécification patterns** : détail de chaque pattern utilisé (séquentiel, parallèle, conditionnel, retry)
3. **State management design** : schéma état partagé, persistence, context propagation
4. **Plan de monitoring** : métriques par agent, tracing distribué, alertes

## Exemples d'application
### Exemple 1 : Customer support multi-agent (routing + escalation)
- **Pattern** : Conditional Routing + Human-in-the-Loop
- **Flux** : 
  1. User message → Classifier (intent detection)
  2. if (FAQ) → FAQ Agent
  3. elif (Technical && complexity=high) → Human escalation
  4. elif (Technical && complexity=low) → Tech Agent
  5. elif (Billing) → Billing Agent
- **Métriques** : routing accuracy 92%, escalation rate 8%, resolution time P95 <5min

### Exemple 2 : Content generation pipeline (sequential chain)
- **Pattern** : Sequential Chain
- **Flux** :
  1. Topic → Research Agent (gather sources)
  2. Sources → Outline Agent (structure content)
  3. Outline → Writer Agent (draft content)
  4. Draft → Editor Agent (refine, fact-check)
- **Métriques** : latence totale P95 <45s, quality score 4.2/5 (human eval)

### Exemple 3 : High-stakes decision (ensemble voting)
- **Pattern** : Ensemble (Voting)
- **Flux** :
  1. Legal query → [Legal Agent 1 || Legal Agent 2 || Legal Agent 3]
  2. Voting : if (consensus >= 2/3) → Approved response
  3. elif (no consensus) → Human lawyer review
- **Métriques** : consensus rate 78%, hallucination rate <2% (vs 8% single agent)

## Anti-patterns à éviter
- ❌ **Sequential quand parallèle possible** : chaîner agents sans dépendances strictes (latence inutile)
- ❌ **Over-routing** : classifier avec 20+ classes (précision chute, complexité élevée)
- ❌ **Retry sans backoff** : retry immédiat après erreur (rate limit aggravé)
- ❌ **No fallback** : pas de plan B si agent principal échoue (indisponibilité totale)
- ❌ **State management ad-hoc** : passer état entre agents sans schéma clair (bugs, debugging difficile)

## Métriques de succès du skill
- Orchestration implémentée avec résilience (retry, fallback, circuit breaker)
- Latence optimisée (parallélisation quand possible, pas de chaînage inutile)
- Monitoring en place (tracing multi-agents, métriques par agent)
- Pas d'indisponibilité totale si 1 agent échoue (fallback fonctionnel)

## Agents utilisant ce skill
- L'agent d'architecture IA (owner)
- L'agent d'intégration et d'automatisation (implémentation)
- L'agent d'ingénierie de prompts (optimisation prompts agents individuels)

## Ressources et références
- **Frameworks multi-agents** :
  - LangGraph (LangChain) : orchestration graph-based
  - AutoGen (Microsoft) : multi-agent conversations
  - CrewAI : role-based agent orchestration
- **Patterns** :
  - AWS Step Functions (state machines)
  - Temporal (durable workflows)
  - Airflow (DAG orchestration)
- **Monitoring** :
  - LangSmith (LangChain tracing)
  - OpenTelemetry (distributed tracing)
  - Weights & Biases (Weave for LLM apps)

## Exemples d'usage

### Exemple 1 : Router les demandes de support vers un spécialiste
**Contexte** : Un assistant doit traiter les demandes courantes, mais transférer les cas ambigus ou sensibles à une personne.  
**Input** : Catégories de demande, périmètres des spécialistes, seuils de confiance, règles d'escalade, budget/latence et exemples de cas.  
**Output** : Graphe de routage conditionnel, fallback humain, traces de décision et tests de cas limites, avec validation humaine sur les catégories à risque.

### Exemple 2 : Comparer plusieurs sources avant de produire une synthèse
**Contexte** : Une réponse interne doit s'appuyer sur des dépôts documentaires indépendants et signaler les divergences.  
**Input** : Sources/retrievers autorisés, format de citations, règles de confidentialité, délai cible et comportement en cas d'échec d'une source.  
**Output** : Pattern parallèle suivi d'un agrégateur, déduplication des résultats, références par affirmation et tests de panne/latence avec repli explicite.

# AI System Architecture Design

**Skill owner** : l'agent d'architecture IA

## Description
Conception d'architectures de systèmes IA end-to-end : orchestration multi-agents/multi-modèles, pipelines IA complexes, intégration dans SI existant, design patterns agents IA, ADR spécifiques IA.

## Déclencheurs
- Conception d'un nouveau système IA complet
- Architecture RAG avancée (multi-retrieval, hybrid search, reranking)
- Orchestration multi-LLM (cascade, ensemble, fallback)
- Intégration IA dans legacy system
- Architecture agentic workflows (multi-agents autonomes)
- Architecture human-in-the-loop IA

## Compétences couvertes
1. **Analyse de faisabilité IA** : diagnostic cas d'usage, contraintes (coût, latence, données), identification composants IA nécessaires
2. **Design patterns agents IA** : orchestration (séquentiel, parallèle, conditionnel, DAG), chaînage prompts, delegation workflows, retry/fallback
3. **Architecture RAG avancée** : multi-retrieval, hybrid search (dense + sparse), reranking, chunking strategies, metadata filtering
4. **Orchestration multi-modèles** : cascade (GPT-4 → GPT-3.5), ensemble (voting, averaging), fallback (primary → secondary), routing (classifier → specialist)
5. **Intégration SI** : architecture hybride (IA + legacy), API gateways, event-driven IA, augmentation legacy systems
6. **ADR IA** : documentation décisions (choix modèles, RAG vs fine-tuning, trade-offs latence/coût/qualité)
7. **Validation architecture** : critères de succès, métriques cibles (latence, coût, qualité), plan de tests

## Périmètre et frontières
- **Dans le périmètre** : vision globale système IA, composants, flux, orchestration, intégration SI, ADR
- **Hors périmètre** : 
  - Sélection détaillée modèles génératifs → l'agent spécialiste en IA générative
  - Conception pipelines ML classiques → l'agent de machine learning
  - Optimisation prompts → l'agent d'ingénierie de prompts
  - Implémentation technique → l'agent de développement back-end / l'agent d'intégration et d'automatisation

## Inputs requis
- Cas d'usage, utilisateurs, décisions métier et niveau de risque.
- Composants IA/ML/RAG/agents envisagés et systèmes/données concernés.
- Contraintes de qualité, latence, coûts, disponibilité, sécurité et conformité.
- Capacités d'exploitation, dépendances et interfaces avec le SI existant.

## Workflow recommandé
1. Cadrer le cas d'usage, les utilisateurs, les contraintes et les critères de succès.
2. Décomposer le système en composants, flux, interfaces et frontières de responsabilité.
3. Comparer les patterns d'orchestration, d'intégration et de supervision humaine.
4. Documenter les choix et compromis dans des ADR, avec coûts et risques.
5. Définir un plan de validation mesurable et un brief d'implémentation.

## Template d'entrée (copier/coller)
```text
[Cas d'usage et utilisateurs] ...
[Composants/données/systèmes existants] ...
[Contraintes] Qualité, latence, coût, sécurité, conformité, exploitation : ...
[Résultats attendus] Critères d'acceptation et décisions à prendre : ...
```

## Template de sortie (copier/coller)
```text
[Architecture] Composants, flux, interfaces et responsabilités : ...
[Décisions] ADR et alternatives écartées : ...
[Validation] Scénarios, métriques et critères Go/No-Go : ...
[Risques] Sécurité, coûts, dépendances, supervision humaine et rollback : ...
```

## Checklist QA interne
- Chaque composant est justifié par le cas d'usage et les exigences non fonctionnelles.
- Les flux de données, interfaces, owners, coûts et modes de défaillance sont décrits.
- Les garde-fous, la supervision humaine et le plan de validation sont proportionnés au risque.

## Definition of done
- Architecture et ADR sont compréhensibles, vérifiables et reliés aux exigences.
- Les critères de validation et les risques résiduels sont explicités.
- L'équipe d'implémentation dispose d'un brief avec interfaces et dépendances.

## Livrables types
1. **Schéma d'architecture IA** : diagramme C4 ou Mermaid avec composants, flux, orchestration
2. **ADR (Architecture Decision Records)** : justification choix clés avec trade-offs
3. **Plan de validation** : scénarios tests, critères acceptation, métriques cibles
4. **Brief d'implémentation** : instructions pour équipes techniques (composants, interfaces, ordre)

## Exemples d'application
### Exemple 1 : Chatbot interne RAG
- **Contexte** : chatbot interne avec connaissance docs propriétaires (500k pages)
- **Architecture** : 
  - RAG retriever (embeddings + vector DB Pinecone/Weaviate)
  - LLM (GPT-4 Turbo)
  - Orchestration : user query → retrieval → prompt construction → LLM → response
- **ADR** : RAG vs fine-tuning → RAG choisi (coût 10x inférieur, mise à jour temps réel)
- **Métriques cibles** : latence P95 <2s, hallucination rate <5%, retrieval precision >85%

### Exemple 2 : Multi-agent customer support
- **Contexte** : support client automatisé (routing, résolution, escalade)
- **Architecture** :
  - Agent router (classifier intent)
  - Agents spécialisés (FAQ, technical, billing, escalation)
  - Orchestration : user message → router → specialist agent → response (+ human escalation si nécessaire)
- **Design patterns** : routing + delegation + fallback (agent → human)
- **Métriques cibles** : routing accuracy >90%, resolution rate 60%, escalation <10%

### Exemple 3 : Hybrid RAG + fine-tuning
- **Contexte** : assistant juridique (docs légaux + langage juridique spécifique)
- **Architecture** :
  - RAG retriever (docs légaux via vector DB)
  - LLM fine-tuné (langage juridique)
  - Orchestration : query → retrieval → contexte → LLM fine-tuné → legal response
- **ADR** : hybrid choisi (RAG = connaissances actualisées, fine-tuning = ton/style juridique)
- **Trade-offs** : coût +30% vs RAG seul, qualité +40% (évaluations utilisateurs)

## Anti-patterns à éviter
- ❌ **Over-engineering** : ajouter orchestration multi-agents quand un seul LLM suffit
- ❌ **Under-specifying métriques** : valider architecture sans critères mesurables (latence, coût, qualité)
- ❌ **Ignorer coûts** : concevoir sans validation de l'agent FinOps
- ❌ **Négliger sécurité** : oublier guardrails, injection prompts, fuites données
- ❌ **Coupling fort** : coupler architecture IA trop étroitement avec SI legacy (difficile à faire évoluer)

## Métriques de succès du skill
- Architecture IA validée avec ADR complets (contexte, décision, trade-offs, alternatives)
- Plan de validation défini avec métriques cibles (latence, coût, qualité)
- Implémentation réussie (validation post-implémentation des métriques)
- Pas de rework majeur architecture après validation initiale

## Agents utilisant ce skill
- L'agent d'architecture IA (owner)
- L'agent d'architecture logicielle (consultation pour cohérence SI)
- L'agent d'intégration et d'automatisation (implémentation workflows)

## Contraintes et références
- **Architecture patterns IA** : 
  - LangChain design patterns (https://python.langchain.com/docs/modules/)
  - LlamaIndex architectures (https://docs.llamaindex.ai/)
  - OpenAI cookbook (https://github.com/openai/openai-cookbook)
- **ADR templates** : Architecture Decision Records (https://adr.github.io/)
- **RAG patterns** : 
  - Advanced RAG techniques (chunking, reranking, hybrid search)
  - Vector databases comparison (Pinecone, Weaviate, Qdrant, Chroma)
- **Multi-agent frameworks** : 
  - AutoGen (Microsoft)
  - LangGraph (LangChain)
  - CrewAI

## Exemples d'usage

### Exemple 1 : Concevoir un assistant RAG pour les procédures internes
**Contexte** : Des collaborateurs doivent retrouver des réponses à jour dans plusieurs milliers de procédures, avec références vérifiables.  
**Input** : Sources autorisées, profils d'accès, volume documentaire, exigences de fraîcheur, latence/coût cibles et cas de test représentatifs.  
**Output** : Architecture de composants et flux, stratégie d'indexation/récupération, contrôles d'accès, citation des sources, métriques d'évaluation et ADR avec alternatives.

### Exemple 2 : Orchestrer la validation de dossiers sensibles
**Contexte** : Plusieurs contrôles IA peuvent aider à préparer une décision, mais l'approbation finale doit rester humaine.  
**Input** : Étapes métier, agents/modèles candidats, critères d'escalade, actions interdites sans approbation et exigences d'audit.  
**Output** : Diagramme d'orchestration avec contrôles humains, séparation des rôles, gestion des erreurs/fallback, traçabilité des décisions et plan de validation.

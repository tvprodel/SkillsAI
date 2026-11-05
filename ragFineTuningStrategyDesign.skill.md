# RAG & Fine-Tuning Strategy Design

## Objectif
Arbitrer entre prompting simple, RAG (Retrieval-Augmented Generation), fine-tuning ou architecture hybride pour un cas d'usage GenAI donné, avec justification type ADR (trade-offs, risques, réversibilité).

## Quand l'utiliser (triggers)
- Démarrage projet GenAI : choix de la stratégie avant implémentation.
- Système en production avec performances insuffisantes : évaluer migration vers RAG ou fine-tuning.
- Coût ou latence excessive d'un système existant : optimiser l'architecture.
- Données métier spécifiques non couvertes par le modèle de base : arbitrer RAG vs fine-tuning.
- Besoin de fraîcheur des données : RAG vs fine-tuning vs hybride.

## Hors périmètre
- Implémentation technique du système RAG ou fine-tuning → **l'agent d'intégration et d'automatisation** ou **l'agent de développement back-end**.
- Optimisation fine coûts/latence du système implémenté → **l'agent FinOps**.
- Rédaction/optimisation du texte du prompt → **l'agent de prompt engineering**.
- Sélection du modèle de base → **l'agent de sélection de modèles génératifs** (skill Generative Model Selection).

## Inputs requis
- **Cas d'usage** : objectif métier, type de tâche, domaine spécifique.
- **Données disponibles** : volumétrie, structure (structurées/non structurées), fréquence de mise à jour, qualité.
- **Contraintes** : coût max, latence max, fraîcheur requise, confidentialité/souveraineté.
- **Exigences qualité** : exactitude factuelle, spécialisation domaine, adaptation ton/style.
- **Système actuel** (si migration) : architecture existante, performances mesurées, points de douleur.

## Sorties attendues
- **Matrice de décision** : comparatif prompting simple / RAG / fine-tuning / hybride selon 8+ critères.
- **ADR (Architecture Decision Record)** : justification du choix avec contexte, options, décision, conséquences, risques, réversibilité.
- **Architecture cible haut niveau** : schéma du système retenu (composants, flux de données), sans implémentation.
- **Plan de validation** : tests à effectuer pour valider la stratégie (qualité, coût, latence, facilité maintenance).

## Workflow recommandé
1. **Analyse du besoin** : clarifier les drivers de décision (fraîcheur données, spécialisation domaine, coût, latence, facilité maintenance).

2. **Évaluation de chaque stratégie** :
   - **Prompting simple** : contexte fourni dans le prompt, pas de données externes ni fine-tuning.
   - **RAG** : récupération de documents pertinents dans une base de connaissances, augmentation du prompt.
   - **Fine-tuning** : entraînement du modèle sur données métier pour spécialisation.
   - **Hybride** : combinaison RAG + fine-tuning (modèle fine-tuné utilisé avec RAG).

3. **Construction de la matrice de décision** : scorer chaque stratégie selon les critères prioritaires du cas d'usage.

4. **Arbitrage et ADR** : sélectionner la stratégie optimale, documenter la décision avec justification complète.

5. **Design architecture haut niveau** : schématiser le système retenu (composants, flux, dépendances), sans code.

6. **Plan de validation** : définir les tests de validation (POC, pilot, A/B test) avec critères de succès mesurables.

## Garde-fous
- **Ne pas sur-engineer** : commencer par prompting simple si volumétrie faible ou données génériques ; ne pas fine-tuner si RAG suffit.
- **Évaluer coût total** : inclure coût données (collecte, préparation, stockage), coût entraînement (fine-tuning), coût requêtes (RAG indexation + retrieval).
- **Vérifier faisabilité fine-tuning** : données suffisantes (1K+ exemples qualité), budget entraînement, expertise disponible.
- **Anti-lock-in** : préférer RAG pour faciliter changement de modèle de base ; fine-tuning crée dépendance forte au modèle.
- **Risque hallucination** : RAG réduit hallucinations (sources factuelles), fine-tuning peut augmenter si données biaisées.
- **Maintenance long terme** : RAG facilite mises à jour (ajout documents), fine-tuning nécessite ré-entraînement périodique.

## Template d'entrée (copier/coller)
```text
[Cas d'usage]
- Objectif métier : ...
- Type de tâche : [QA/génération/résumé/extraction/autre]
- Domaine spécifique : [médical/juridique/technique/autre]

[Données disponibles]
- Volumétrie : ... documents / ... tokens
- Structure : [structurées/non structurées/mixte]
- Fréquence de mise à jour : [temps réel/quotidienne/hebdomadaire/statique]
- Qualité : [haute/moyenne/faible]

[Contraintes]
- Coût max : ... $/requête ou ... $/mois
- Latence max : TTFT ... ms
- Fraîcheur requise : [temps réel/journalière/hebdomadaire/n/a]
- Confidentialité/souveraineté : [cloud/on-prem/hybride]

[Exigences qualité]
- Exactitude factuelle : [critique/importante/normale]
- Spécialisation domaine : [très spécialisé/spécialisé/générique]
- Adaptation ton/style : [critique/importante/normale]

[Système actuel (si migration)]
- Architecture : ...
- Performances : coût ... $/requête, latence ... ms, exactitude ... %
- Points de douleur : ...
```

## Template de sortie (copier/coller)
```markdown
# ADR : Stratégie GenAI [Prompting Simple / RAG / Fine-Tuning / Hybride]

## Contexte

[Description du cas d'usage, contraintes, objectifs métier]

## Matrice de décision

| Critère | Prompting simple | RAG | Fine-tuning | Hybride | Poids |
|---------|------------------|-----|-------------|---------|-------|
| Fraîcheur données | ⚪ Faible | 🟢 Excellente | 🔴 Nulle (snapshot) | 🟢 Excellente | Élevé |
| Exactitude factuelle | 🟡 Moyenne | 🟢 Haute | 🟡 Dépend données | 🟢 Très haute | Critique |
| Spécialisation domaine | 🔴 Nulle | 🟡 Moyenne | 🟢 Haute | 🟢 Très haute | Élevé |
| Coût initial | 🟢 Nul | 🟡 Moyen | 🔴 Élevé | 🔴 Très élevé | Normal |
| Coût récurrent | 🟢 Tokens prompt | 🟡 Tokens + retrieval | 🟢 Tokens standard | 🔴 Tokens + retrieval | Élevé |
| Latence | 🟢 Basse | 🟡 Moyenne (+retrieval) | 🟢 Basse | 🔴 Haute (retrieval + fine-tuned) | Normal |
| Facilité maintenance | 🟢 Triviale | 🟢 Facile (ajout docs) | 🔴 Complexe (ré-entraînement) | 🔴 Très complexe | Élevé |
| Réversibilité | 🟢 Totale | 🟢 Facile | 🔴 Difficile (lock-in modèle) | 🔴 Très difficile | Normal |

## Options considérées

### Option 1 : Prompting simple
- **Avantages** : ...
- **Inconvénients** : ...
- **Score pondéré** : .../100

### Option 2 : RAG
- **Avantages** : ...
- **Inconvénients** : ...
- **Score pondéré** : .../100

### Option 3 : Fine-tuning
- **Avantages** : ...
- **Inconvénients** : ...
- **Score pondéré** : .../100

### Option 4 : Hybride (RAG + fine-tuning)
- **Avantages** : ...
- **Inconvénients** : ...
- **Score pondéré** : .../100

## Décision

**Stratégie retenue** : [Prompting simple / RAG / Fine-tuning / Hybride]

**Justification** :
- Critère 1 prioritaire : ...
- Critère 2 : ...
- Trade-offs acceptés : ...

## Conséquences

### Positives
- ...

### Négatives
- ...

### Risques identifiés
- Risque 1 : ... | Mitigation : ...
- Risque 2 : ... | Mitigation : ...

## Architecture cible (haut niveau)

[Schéma Mermaid ou description texte des composants et flux]

## Plan de réversibilité

Si échec de la stratégie retenue :
- Fallback vers : [option 2]
- Durée migration estimée : ...
- Coût migration estimé : ...

## Plan de validation

### Phase 1 : POC (X semaines)
- Objectif : ...
- Critères de succès : ...

### Phase 2 : Pilot (X semaines)
- Objectif : ...
- Critères de succès : ...

### Décision go/no-go
- Seuils qualité : ...
- Seuils coût : ...
- Seuils latence : ...
```

## Checklist QA interne
- [ ] Matrice de décision complète avec 8+ critères et 4 stratégies comparées.
- [ ] Poids de chaque critère défini (Critique/Élevé/Normal).
- [ ] Score pondéré calculé pour chaque option (mesurable, justifié).
- [ ] ADR structuré (Contexte, Options, Décision, Conséquences, Risques, Réversibilité).
- [ ] Trade-offs explicites documentés (ce qu'on gagne vs ce qu'on perd).
- [ ] Architecture cible dessinée (composants, flux, dépendances), pas d'implémentation.
- [ ] Plan de réversibilité défini (fallback, durée, coût).
- [ ] Plan de validation avec critères de succès mesurables (qualité, coût, latence).

## KPI reliés
- **Taux de validation stratégie** : (stratégies validées en production / stratégies recommandées) x 100.
- **Écart coût prédit vs réel** : (coût production - coût estimé) / coût estimé x 100.
- **Écart qualité prédite vs réelle** : (exactitude mesurée - exactitude estimée) / exactitude estimée x 100.
- **Taux de réversibilité appliquée** : (stratégies abandonnées avec succès / tentatives abandon) x 100.

## Definition of done
- Matrice de décision complète avec 8+ critères, 4 stratégies, poids et scores (mesure : nombre lignes/colonnes ; preuve : tableau livré).
- ADR structuré avec toutes les sections obligatoires (Contexte, Options, Décision, Conséquences, Risques, Réversibilité) (mesure : présence des 6 sections ; preuve : document ADR).
- Architecture cible haut niveau schématisée (composants, flux) sans implémentation (mesure : diagramme + description texte présents ; preuve : section Architecture).
- Plan de validation avec critères de succès mesurables (qualité, coût, latence) (mesure : présence de 3+ critères ; preuve : section Plan de validation).
- Plan de réversibilité défini (fallback, durée, coût) (mesure : présence des 3 éléments ; preuve : section Réversibilité).

## Exemples d'usage

### Exemple 1 : Chatbot support client e-commerce (décision : RAG)

**Contexte** : Startup e-commerce veut un chatbot support client pour FAQ produits + suivi commandes. Base de connaissances : 5K articles FAQ + catalogue 10K produits, mise à jour quotidienne.

**Matrice décision** :

| Critère | Prompting simple | RAG | Fine-tuning | Hybride | Poids |
|---------|------------------|-----|-------------|---------|-------|
| Fraîcheur données | 🔴 Nulle | 🟢 Quotidienne | 🔴 Nulle | 🟢 Quotidienne | Critique |
| Exactitude factuelle | 🔴 Hallucinations probables | 🟢 Sources fiables | 🟡 Dépend données | 🟢 Excellente | Critique |
| Spécialisation domaine | 🔴 Nulle | 🟡 Moyenne | 🟢 Haute | 🟢 Très haute | Normal |
| Coût initial | 🟢 $0 | 🟡 $5K | 🔴 $50K | 🔴 $80K | Normal |
| Coût récurrent | 🟡 $0.005/req | 🟡 $0.006/req | 🟢 $0.004/req | 🔴 $0.008/req | Élevé |
| Facilité maintenance | 🟢 Triviale | 🟢 Ajout docs | 🔴 Ré-entraînement | 🔴 Complexe | Élevé |

**Décision** : **RAG** — Fraîcheur critique (produits + FAQ changent quotidiennement), coût raisonnable, facilité maintenance. Fine-tuning exclu (données périmées rapidement). Prompting simple exclu (hallucinations inacceptables sur stock produits).

**Architecture** : Vector DB (Pinecone) + embeddings (text-embedding-3) + retrieval top-5 + augmentation prompt GPT-4o mini.

**Résultat** : RAG déployé, exactitude 94%, coût $0.0058/req, temps réponse 1.2s. ✅

### Exemple 2 : Assistant juridique spécialisé (décision : Fine-tuning)

**Contexte** : Cabinet d'avocats veut assistant IA pour rédaction contrats de travail français. Corpus : 10K contrats annotés (5 ans archives), domaine très spécialisé (droit du travail FR), mises à jour législatives trimestrielles.

**Matrice décision** :

| Critère | Prompting simple | RAG | Fine-tuning | Hybride | Poids |
|---------|------------------|-----|-------------|---------|-------|
| Fraîcheur données | 🔴 Nulle | 🟢 Temps réel | 🔴 Snapshot | 🟡 Mixte | Normal |
| Spécialisation domaine | 🔴 Générique | 🟡 Dépend corpus | 🟢 Très spécialisé | 🟢 Excellente | Critique |
| Adaptation ton/style | 🔴 Générique | 🔴 Générique | 🟢 Ton cabinet | 🟢 Ton cabinet | Élevé |
| Coût initial | 🟢 $0 | 🟡 $10K | 🔴 $80K | 🔴 $120K | Élevé |
| Facilité maintenance | 🟢 Triviale | 🟢 Ajout docs | 🟡 Ré-entraînement trimestriel | 🔴 Complexe | Normal |

**Décision** : **Fine-tuning** — Spécialisation critique (terminologie juridique FR très spécifique), adaptation ton/style cabinet prioritaire, volumétrie suffisante (10K contrats), mises à jour trimestrielles gérables. RAG insuffisant pour apprendre le style rédactionnel du cabinet. Hybride exclu (coût trop élevé).

**Architecture** : GPT-4 Turbo fine-tuné sur 10K contrats, ré-entraînement trimestriel (nouvelles lois).

**Résultat** : Modèle fine-tuné déployé, qualité rédactionnelle évaluée 91% (avocats seniors), gain temps rédaction 60%, ré-entraînement trimestriel $5K. ✅

### Exemple 3 : Moteur de recommandation produits (décision : Hybride RAG + fine-tuning)

**Contexte** : Marketplace B2B veut moteur de recommandation produits complexes (machines industrielles). Catalogue 50K produits avec fiches techniques détaillées + historique 100K transactions. Besoin : recommandations très précises (spécifications techniques) + personnalisées (profil acheteur).

**Matrice décision** :

| Critère | Prompting simple | RAG | Fine-tuning | Hybride | Poids |
|---------|------------------|-----|-------------|---------|-------|
| Exactitude factuelle | 🔴 Hallucinations | 🟢 Sources fiables | 🟡 Dépend données | 🟢 Excellente | Critique |
| Spécialisation domaine | 🔴 Générique | 🟡 Corpus technique | 🟢 Très spécialisé | 🟢 Maximale | Critique |
| Personnalisation | 🔴 Nulle | 🔴 Nulle | 🟢 Haute | 🟢 Maximale | Critique |
| Coût initial | 🟢 $0 | 🟡 $20K | 🔴 $150K | 🔴 $200K | Élevé |
| Performance requise | 🔴 Insuffisante | 🟡 Moyenne | 🟡 Moyenne | 🟢 Optimale | Critique |

**Décision** : **Hybride (RAG + fine-tuning)** — Besoin critique de spécialisation (terminologie machines industrielles) + personnalisation (profil acheteur). Fine-tuning seul insuffisant (fiches techniques changent fréquemment). RAG seul insuffisant (pas de personnalisation). Hybride : modèle fine-tuné sur historique transactions (patterns achats) + RAG sur fiches techniques (fraîcheur).

**Architecture** : GPT-4 fine-tuné sur 100K transactions + Vector DB (Weaviate) sur 50K fiches techniques + retrieval top-10 + augmentation prompt.

**Résultat** : Système hybride déployé, précision recommandations 87% (vs 62% baseline), taux de conversion +34%, coût $0.015/recommandation. ✅

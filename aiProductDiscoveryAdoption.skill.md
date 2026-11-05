# AI Product Discovery & Adoption

## Objectif
Valider les hypothèses produit IA (product-market fit), piloter l'adoption des features IA et itérer selon le feedback utilisateur.

**Agents utilisateurs** : l'agent de stratégie produit IA (principal), l'agent de stratégie produit, l'agent data science

## Quand l'utiliser (triggers)
- Valider qu'une opportunité IA a du sens (product-market fit IA)
- Prototyper et tester un MVP IA avec utilisateurs
- Piloter le déploiement progressif d'une feature IA (beta → GA)
- Collecter et analyser le feedback utilisateur sur features IA
- Itérer sur la roadmap IA selon apprentissages

## Hors périmètre
- Discovery produit business (hors IA) → l'agent de stratégie produit
- Analyse exploratoire données → l'agent data science
- User research UX classique → l'agent UX writing

---

## Inputs requis
- Hypothèse produit, public cible, problème utilisateur et résultat attendu.
- Solution IA envisagée et alternatives non-IA à comparer.
- Accès aux utilisateurs, données de feedback et indicateurs de baseline disponibles.
- Contraintes de pilote, déploiement progressif, confidentialité et gouvernance.

## Sorties attendues
- Hypothèses et protocole de validation avec critères de décision.
- Résultats de discovery/pilote et limites de l'échantillon.
- Plan d'adoption ou recommandation d'itération, pivot ou arrêt.
- Métriques d'activation, rétention, satisfaction et qualité IA définies.

## Workflow recommandé
1. Valider le problème et les utilisateurs avant de retenir l'IA comme solution.
2. Comparer l'IA avec des alternatives simples et fixer des critères mesurables.
3. Prototyper/piloter avec un échantillon approprié et un protocole documenté.
4. Collecter feedback, usage, qualité et incidents avec les limites de représentativité.
5. Décider d'itérer, déployer progressivement, pivoter ou arrêter.
6. Suivre l'adoption après déploiement et réviser les hypothèses.

## Garde-fous
- Ne pas confondre intérêt déclaré et adoption ou valeur démontrée.
- Documenter taille, biais et limites de l'échantillon ainsi que les retours négatifs.
- Comparer une option non-IA; ne pas imposer l'IA si elle n'apporte pas de valeur.
- Prévoir supervision, recours et critères d'arrêt proportionnés au risque.

## Template d'entrée (copier/coller)
```text
[Utilisateur/problème] ...
[Hypothèse produit IA et alternative non-IA] ...
[Pilote] Public, durée, accès et contraintes : ...
[Baseline et critères de succès/arrêt] ...
```

## Template de sortie (copier/coller)
```text
[Hypothèse évaluée et protocole] ...
[Résultats] Adoption, feedback, qualité, échantillon et limites : ...
[Décision] Itérer / déployer progressivement / pivoter / arrêter : ...
[Suivi] Actions, owner, garde-fous et prochain point de mesure : ...
```

## KPI reliés
- Taux d'activation et rétention par cohorte.
- Taux de complétion et de recours à une solution alternative/humaine.
- Feedback utilisateur et incidents, ventilés par segment lorsque pertinent.
- Part des hypothèses validées par une preuve utilisateur ou une mesure observée.

## Definition of done
- Hypothèses, population, protocole et critères de décision sont documentés.
- Résultats et limites de l'échantillon sont présentés sans extrapolation injustifiée.
- Décision et actions de suivi sont explicites et attribuées.

## Compétences

### 1. Validation product-market fit IA

**Description** : Valider qu'un produit/feature IA résout un vrai problème utilisateur avec l'IA comme solution optimale.

**Méthodologie** :

**Étape 1 : Problem validation** (le problème existe-t-il ?)
- Interviews utilisateurs (5-10 early adopters) : pain points, workarounds actuels, volonté de payer
- Observation terrain : comment les users résolvent le problème aujourd'hui ?
- Données quantitatives : taux de plainte, support tickets, churn lié au problème
- **Critère de succès** : >70% utilisateurs interrogés confirment le problème comme critique

**Étape 2 : Solution validation** (l'IA est-elle la bonne solution ?)
- Prototypage low-tech (Wizard of Oz) : simuler l'IA manuellement, tester UX
- Benchmark solutions alternatives : règles métier, heuristiques, scripts simples
- Estimation ROI IA vs alternatives : coût/délai/qualité IA vs non-IA
- **Critère de succès** : IA apporte >30% amélioration vs meilleure alternative non-IA

**Étape 3 : Product validation** (les users adoptent-ils le produit IA ?)
- MVP IA (Minimum Viable Product) : modèle simple mais fonctionnel
- Beta fermée (10-50 early adopters) : adoption, feedback, NPS
- Métriques d'adoption : taux d'activation, rétention D7/D30, fréquence usage
- **Critère de succès** : NPS beta >40, rétention D30 >50%, usage hebdomadaire >60%

**Livrables** :
- Rapport de discovery (problème validé ou non, insights utilisateurs)
- Recommandation Go/No-Go/Pivot (avec justification data)
- Plan MVP IA (scope minimal, timeline, métriques de succès)

**Exemple product-market fit chatbot IA** :
```
Discovery : Chatbot IA Support Client Retail

Étape 1 : Problem validation
Interviews : 8 clients (6 grand public, 2 agents support)
Pain points identifiés :
- 75% clients : "Support email trop lent (48h réponse), besoin immédiat"
- 62% clients : "Téléphone souvent saturé, attente >10min"
- 100% agents support : "80% demandes = FAQ répétitives (statut commande, retour produit)"

Données quantitatives :
- Support tickets : 5000/mois, 70% niveau 1 (FAQ)
- Temps réponse moyen : 36h (email), 8min (téléphone)
- NPS support : 42 (insatisfaction temps réponse)

→ Problème validé : latence support critique, volume FAQ élevé

Étape 2 : Solution validation
Alternatives évaluées :
A) FAQ statique améliorée (coût 5k€, délai 1 mois)
   - Limite : pas de personnalisation, recherche manuelle
   - Réduction tickets estimée : -20%

B) Chatbot règles métier (coût 20k€, délai 3 mois)
   - Limite : rigide, maintenance lourde, pas de compréhension naturelle
   - Réduction tickets estimée : -40%

C) Chatbot IA LLM (coût 50k€, délai 4 mois)
   - Avantage : langage naturel, personnalisation, escalade intelligente
   - Réduction tickets estimée : -60%

ROI comparé :
| Solution | Coût | Réduction tickets | Économie/an | ROI |
|----------|------|-------------------|-------------|-----|
| FAQ statique | 5k€ | -20% (1000) | 30k€ | +500% |
| Chatbot règles | 20k€ | -40% (2000) | 60k€ | +200% |
| Chatbot IA LLM | 50k€ | -60% (3000) | 90k€ | +80% |

→ IA apporte +50% réduction tickets vs chatbot règles (+20% économie)
→ Solution validée : IA justifiée si adoption >50% (sinon FAQ statique suffit)

Étape 3 : Product validation (MVP)
MVP scope :
- Chatbot FR/EN uniquement
- FAQ 20 questions top (statut commande, retour, livraison)
- Escalade agent humain si incompréhension
- Modèle : GPT-4 Turbo API (MVP rapide, pas de fine-tuning)

Beta fermée : 50 clients early adopters (2 semaines)
Résultats :
- Taux d'activation : 68% (34/50 ont ouvert chatbot)
- Rétention D7 : 58% (29/50 ont réutilisé après 7 jours)
- Usage hebdomadaire : 72% (36/50 utilisent >1x/semaine)
- NPS beta : 52 (vs NPS support actuel 42)
- Feedback qualitatif : "Rapide, pratique, mais parfois répond à côté"

→ Product validé : adoption >50%, NPS >50, usage >60%

**Recommandation : GO développement v1.0 (beta externe 1000 clients)**
Justification :
- Problème critique validé (75% clients insatisfaits latence support)
- IA apporte valeur vs alternatives (+50% réduction tickets vs chatbot règles)
- Adoption MVP positive (NPS 52, rétention D7 58%, usage 72%)
- ROI positif attendu (+80% après 1 an)

Risques :
- Qualité réponses variable (mitigation : fine-tuning Q2)
- Adoption <50% si UX non optimisée (mitigation : tests UX beta externe)
```

**Pièges à éviter** :
- Sauter la problem validation (solution en quête de problème)
- MVP surdimensionné (trop de features, délai long, learnings tardifs)
- Ignorer les alternatives non-IA (IA pas toujours la meilleure solution)

---

### 2. Prototypage et MVP IA

**Description** : Créer des prototypes/MVP IA rapidement pour tester avec utilisateurs.

**Niveaux de fidélité** :

**Low-fi : Wizard of Oz (simulation manuelle)** :
- Principe : simuler l'IA manuellement (humain joue le rôle du modèle ML)
- Avantage : très rapide (1-2 jours), pas de dev, focus UX
- Limite : pas scalable, coût humain élevé
- Usage : valider UX/flows avant développement IA

**Mid-fi : Modèle pré-entraîné générique (API)** :
- Principe : utiliser GPT-4, Claude, modèles Hugging Face via API
- Avantage : rapide (1-2 semaines), qualité correcte, pas d'entraînement
- Limite : coût API, pas de personnalisation, dépendance externe
- Usage : MVP rapide, validation product-market fit

**High-fi : Modèle fine-tuné/custom** :
- Principe : fine-tuning modèle sur données spécifiques
- Avantage : qualité optimale, contrôle, coûts long terme
- Limite : délai long (2-4 mois), effort ML élevé
- Usage : production, après validation MVP

**Livrables** :
- Prototype fonctionnel (selon niveau de fidélité)
- Plan de tests utilisateurs (scénarios, métriques)
- Rapport de tests (insights, taux de succès, feedback)
- Recommandation next steps (itérer, pivoter, scaler)

**Exemple prototypage chatbot IA** :
```
Prototypage : Chatbot IA Support Client (3 itérations)

Itération 1 : Wizard of Oz (1 semaine)
- Setup : interface chat basique (frontend), humain répond côté backend
- Tests : 5 utilisateurs, 3 scénarios (statut commande, retour produit, livraison)
- Résultats :
  - Taux de succès : 80% (4/5 utilisateurs ont résolu leur problème)
  - Temps moyen résolution : 2 minutes
  - Feedback : "Rapide, bien guidé, j'aurais aimé plus de détails sur la livraison"
- Insight : UX validée, besoin enrichir base de connaissances livraison
- Décision : GO itération 2 (API GPT-4)

Itération 2 : MVP GPT-4 API (2 semaines)
- Setup : GPT-4 Turbo API + prompt engineering + base FAQ 20 questions
- Tests : 20 utilisateurs beta interne, 2 semaines usage réel
- Résultats :
  - Taux de succès : 70% (14/20 problèmes résolus sans escalade)
  - Taux d'activation : 75% (15/20 ont ouvert chatbot)
  - NPS : 48
  - Feedback : "Parfois répond à côté", "Manque support NL/DE"
- Insight : qualité correcte mais hallucinations occasionnelles, demande multilingue
- Décision : GO itération 3 (fine-tuning + NL/DE)

Itération 3 : Fine-tuning Llama 3 + NL/DE (3 mois)
- Setup : fine-tuning Llama 3 70B sur 10k conversations historiques, ajout NL/DE
- Tests : 100 utilisateurs beta externe, 1 mois usage réel
- Résultats :
  - Taux de succès : 82% (82/100 problèmes résolus sans escalade)
  - Taux d'activation : 68%
  - NPS : 58
  - Feedback : "Meilleure qualité réponses", "Support NL/DE apprécié"
- Insight : fine-tuning améliore qualité +12%, NL/DE élargit adoption
- Décision : GO déploiement GA (tous clients)
```

**Pièges à éviter** :
- High-fi d'emblée (over-engineering, délai long, learnings tardifs)
- Pas de tests utilisateurs (build in the dark)
- Itérations trop longues (cycle >4 semaines = trop lent)

---

### 3. Déploiement progressif (beta → GA)

**Description** : Déployer des features IA progressivement pour mitiger les risques et itérer selon feedback.

**Stratégie de rollout** :

**Phase 1 : Beta interne (early team, 1-2 semaines)** :
- Public : équipe interne (PM, devs, support)
- Objectif : détecter bugs critiques, valider UX basique
- Critères de passage Phase 2 : 0 bugs bloquants, taux de succès >60%

**Phase 2 : Beta fermée (early adopters, 2-4 semaines)** :
- Public : 10-50 utilisateurs pilotes (champions, beta testers)
- Objectif : valider adoption, collecter feedback qualité
- Critères de passage Phase 3 : NPS >40, taux d'activation >50%, bugs critiques <3

**Phase 3 : Beta ouverte / Early access (opt-in, 4-8 semaines)** :
- Public : utilisateurs volontaires (opt-in via toggle)
- Objectif : valider scalabilité, monitoring production
- Critères de passage GA : NPS >50, uptime >99.5%, coûts <budget

**Phase 4 : GA (General Availability, progressif)** :
- Public : tous utilisateurs (rollout 25% → 50% → 75% → 100% sur 2-4 semaines)
- Objectif : déploiement final, monitoring continu
- Critères de succès : métriques roadmap atteintes (adoption, NPS, ROI)

**Livrables** :
- Plan de rollout (phases, publics, timelines, critères)
- Playbook incidents (monitoring, alertes, rollback)
- Communication utilisateurs (annonces, guides, support)
- Rapport post-mortem (adoption, feedback, lessons learned)

**Exemple déploiement chatbot IA** :
```
Déploiement : Chatbot IA v1.5 (Fine-tuning + NL/DE)

Phase 1 : Beta interne (1 semaine, 5-15 juin)
Public : 10 personnes (PM, devs, support)
Critères :
✅ 0 bugs bloquants
✅ Taux de succès 72% (8/10 scénarios réussis)
⚠️ 1 bug mineur (latence >5s si question longue) → fixé

→ GO Phase 2

Phase 2 : Beta fermée (4 semaines, 20 juin - 20 juillet)
Public : 50 clients early adopters (invités par email)
Communication : email invitation + guide prise en main (délégation l'agent de rédaction technique)
Monitoring : dashboard quotidien (NPS, bugs, latence)
Critères :
✅ NPS 52 (cible >40)
✅ Taux d'activation 68% (cible >50%)
✅ Bugs critiques 1 (cible <3) → fixé
⚠️ Latence NL 2.3s (cible <2s) → optimisation prompts → 1.8s

→ GO Phase 3

Phase 3 : Early access opt-in (8 semaines, 1 août - 30 septembre)
Public : utilisateurs volontaires (toggle dans paramètres), ~1000 utilisateurs
Communication : annonce in-app + blog post + email newsletter
Monitoring : dashboard quotidien + alertes (uptime <99%, NPS <45)
Critères :
✅ NPS 58 (cible >50)
✅ Uptime 99.8% (cible >99.5%)
✅ Coût/conversation 0.33€ (budget <0.40€)
✅ Adoption 42% (cible >30%)
⚠️ Spike latence 1 jour (pic trafic) → auto-scaling ajusté

→ GO Phase 4 (GA)

Phase 4 : GA rollout progressif (4 semaines, 1-31 octobre)
Public : tous clients (100k)
Rollout :
- Semaine 1 : 25% (25k clients)
- Semaine 2 : 50% (50k clients) si 0 incident critique
- Semaine 3 : 75% (75k clients) si NPS stable
- Semaine 4 : 100% (100k clients)

Monitoring : dashboard temps réel, alertes critiques (latence >3s, uptime <99%, bugs critiques)
Rollback plan : si >5 bugs critiques OU NPS <40 OU uptime <99% → rollback v1.0 immédiat

Résultats (fin octobre) :
✅ Déploiement 100% réussi (0 rollback)
✅ NPS 61 (vs cible 60)
✅ Adoption 48% (vs cible 40%)
✅ Résolution autonome 82% (vs cible 80%)
✅ Économie coûts support 22k€/mois (vs cible 20k€)
```

**Pièges à éviter** :
- Big bang deployment (100% d'emblée = risque élevé)
- Pas de critères Go/No-Go (décisions au feeling)
- Pas de rollback plan (incident critique = panique)

---

### 4. Collecte et analyse du feedback utilisateur IA

**Description** : Collecter et analyser le feedback utilisateur pour itérer sur les produits IA.

**Canaux de feedback** :

**Quantitatifs** :
- **NPS (Net Promoter Score)** : sondage 1-10 post-interaction
- **CSAT (Customer Satisfaction)** : sondage 1-5 étoiles
- **Usage analytics** : taux d'activation, rétention, fréquence, features utilisées
- **A/B tests** : comparer versions IA, features

**Qualitatifs** :
- **Sondages ouverts** : "Que pensez-vous de cette feature IA ?"
- **Interviews utilisateurs** : sessions 30min (5-10 users/mois)
- **Support tickets** : bugs, frustrations, suggestions
- **Session recordings** : observer usage réel (Hotjar, FullStory)

**Livrables** :
- Rapport feedback mensuel (insights, tendances, actions)
- Top pain points utilisateurs (priorisés par fréquence/impact)
- Roadmap mise à jour (ajout features demandées, déprioritisation features non utilisées)
- Plan d'actions correctives (bugs, UX, performance)

**Exemple analyse feedback chatbot IA** :
```
Feedback Chatbot IA : Juillet 2026 (1 mois post-GA)

Quantitatifs :
- NPS : 58 (vs cible 60, -2pts)
  Détracteurs (0-6) : 18% (vs 15% attendu)
  Passifs (7-8) : 24%
  Promoteurs (9-10) : 58%

- CSAT : 4.1/5 (vs cible 4.0, +0.1)

- Usage analytics :
  Taux d'activation : 45% (vs cible 40%, +5%)
  Rétention D30 : 62% (vs cible 50%, +12%)
  Fréquence : 3.2x/semaine (vs cible 2x, +60%)

Qualitatifs (100 réponses sondage ouvert) :
Top 5 pain points :
1. "Parfois ne comprend pas ma question" (32 mentions)
2. "Manque d'infos sur délais de livraison" (18 mentions)
3. "Pas de support vocal, que du texte" (12 mentions)
4. "Répétitif si je pose 2 fois la même question" (9 mentions)
5. "Pas de suivi historique conversations" (8 mentions)

Top 5 features appréciées :
1. "Rapide, réponse <2s" (45 mentions)
2. "Disponible 24/7" (38 mentions)
3. "Support NL/DE très utile" (22 mentions)
4. "Escalade vers agent humain seamless" (15 mentions)
5. "Personnalisation (me reconnaît)" (12 mentions)

Insights :
1. **Qualité compréhension** : 32% feedback négatif sur compréhension → priorité haute
   Action : fine-tuning supplémentaire sur 5k nouvelles conversations (délégation l'agent de machine learning)

2. **Infos livraison** : 18% demande enrichissement base de connaissances
   Action : ajout 10 nouvelles FAQ livraison (délégation l'agent de rédaction technique)

3. **Voice support** : 12% demande fonctionnalité vocale
   Action : roadmap Q4 (Voice-to-Text + Text-to-Voice)

4. **Mémoire conversations** : 9% demande suivi historique
   Action : roadmap Q3 (session memory)

Impact roadmap :
- Ajout Q3 : Session memory + enrichissement FAQ livraison
- Ajout Q4 : Voice support (speech-to-text)
- Déprioritisation : Intégration CRM (peu demandé) → Q4→Q1 2027
```

**Pièges à éviter** :
- Feedback non analysé (collecté mais jamais actionné)
- Biais de sélection (n'écouter que les détracteurs ou que les fans)
- Pas de priorisation (traiter tous feedbacks = dilution focus)

---

### 5. Itération continue et pivots produit IA

**Description** : Itérer rapidement sur les produits IA selon apprentissages, savoir pivoter si hypothèses invalidées.

**Framework d'itération** :

**Build → Measure → Learn (Lean Startup)** :
- **Build** : développer MVP/feature (sprint 2-4 semaines)
- **Measure** : déployer, mesurer métriques (adoption, NPS, usage)
- **Learn** : analyser résultats, valider/invalider hypothèses
- **Decide** : itérer (amélioration) / persévérer (scaling) / pivoter (changement stratégie)

**Types de pivots IA** :
- **Pivot technologique** : changer modèle ML (GPT-4 → Llama 3 fine-tuné)
- **Pivot use case** : changer cas d'usage (chatbot support → chatbot vente)
- **Pivot public** : changer cible utilisateurs (B2C → B2B)
- **Pivot business model** : changer monétisation (gratuit → freemium → payant)

**Livrables** :
- Bilan sprint (résultats vs hypothèses)
- Décision (itérer / persévérer / pivoter) avec justification
- Plan d'actions (next sprint, pivots, abandons)
- Mise à jour roadmap

**Exemple itération chatbot IA** :
```
Itération : Chatbot IA Support Client (Sprint 5, août 2026)

Hypothèses Sprint 5 :
H1 : Session memory améliore NPS de +5 points (58 → 63)
H2 : Enrichissement FAQ livraison réduit escalades de -10%

Build (2 semaines) :
- Feature 1 : Session memory (historique 7 derniers jours)
- Feature 2 : 10 nouvelles FAQ livraison (tracking colis, délais, retours)

Measure (2 semaines beta 500 users) :
- NPS : 60 (vs baseline 58, +2pts, cible +5pts)
- Taux escalade : 16% (vs baseline 18%, -2%, cible -10%)
- Adoption session memory : 42% (utilisateurs consultant historique)
- Adoption FAQ livraison : 68% (questions livraison résolues sans escalade)

Learn :
- H1 (session memory) : PARTIELLEMENT VALIDÉE
  Impact NPS +2pts (vs +5pts attendu), adoption 42% correcte
  Insight : session memory apprécié mais impact NPS limité (pas le pain point #1)

- H2 (FAQ livraison) : PARTIELLEMENT VALIDÉE
  Réduction escalades -2% (vs -10% attendu), adoption 68% bonne
  Insight : FAQ livraison utile mais pas suffisant (besoin aussi API temps réel tracking colis)

Decide :
- **Itérer session memory** : améliorer UX (affichage historique plus visible) → Sprint 6
- **Itérer FAQ livraison** : ajouter API tracking colis temps réel → Sprint 7
- **Persévérer** : features adoptées (42%, 68%), impact positif même si <cible
- **Pivoter ?** : Non (hypothèses partiellement validées, pas de signaux faibles adoption)

Actions Sprint 6 :
1. Amélioration UX session memory (affichage historique en sidebar) (1 semaine)
2. Prototypage API tracking colis (POC avec 2 transporteurs) (1 semaine)
3. A/B test session memory amélioré vs actuel (2 semaines)
4. Validation faisabilité API tracking (délégation l'agent d'intégration et d'automatisation)
```

**Exemple pivot** :
```
Pivot : Chatbot IA Vente (initialement Support)

Contexte :
- Chatbot support déployé avec succès (NPS 61, adoption 48%)
- Feedback sales team : "Clients posent beaucoup de questions pré-achat sur le chat"
- Opportunité : réutiliser chatbot IA pour support pré-vente (recommandation produits, devis)

Hypothèse pivot :
H : Chatbot IA peut améliorer conversion pré-vente de +15% (baseline 25% → cible 40%)

Validation pivot :
- Analyse conversations : 30% conversations chat = questions pré-vente (volume suffisant)
- Interviews sales team : "Si chatbot qualifie leads, économie temps énorme"
- Benchmark concurrents : chatbots IA vente courants (Drift, Intercom)

Décision : GO Pivot partiel (chatbot support + vente)
Justification :
- Volume conversations pré-vente suffisant (30%)
- Impact métier potentiel élevé (conversion +15% = +500k€ revenus/an)
- Réutilisation technologie existante (même modèle LLM, prompts adaptés)

Plan :
- Sprint 6-7 : Développement module vente (recommandation produits, devis automatique)
- Sprint 8 : Beta vente (100 conversations pré-vente)
- Sprint 9 : GA vente si NPS >50 et conversion >35%
```

**Pièges à éviter** :
- Itérations trop lentes (sprints >4 semaines = inertie)
- Pivoter trop vite (1 sprint négatif ≠ échec, persévérer 2-3 sprints)
- Ne jamais pivoter (attachment biais, ignorer signaux d'échec)

---

## Exemples d'utilisation

### Exemple 1 : Validation product-market fit recommandation produits IA

**Contexte** : E-commerce, hypothèse "moteur de recommandation IA améliore conversion +30%".

**Discovery** :
- Problem validation : interviews 10 clients, 70% disent "trop de choix, besoin recommandations"
- Solution validation : benchmark alternatives (règles métier vs IA), IA apporte +40% précision
- Product validation : MVP IA (collaborative filtering), beta 50 users, NPS 55, rétention D30 62%

**Résultat** : GO développement v1.0 (ROI +200% attendu).

### Exemple 2 : Déploiement progressif détection fraude IA

**Contexte** : Fintech, nouveau modèle ML détection fraude paiement, besoin rollout sécurisé.

**Phases** :
1. Beta interne (1 semaine, 10 transactions test) : 0 bugs
2. Beta fermée (2 semaines, 1000 transactions pilotes) : precision 96%, 2 faux positifs
3. Early access (4 semaines, 10k transactions opt-in) : precision 95%, uptime 99.8%
4. GA rollout (4 semaines, 25%→50%→75%→100%) : precision 94%, économie fraude 50k€/mois

**Résultat** : déploiement réussi, 0 rollback.

### Exemple 3 : Pivot chatbot support → vente

**Contexte** : Chatbot support adopté (NPS 61), opportunité vente détectée (30% conversations pré-vente).

**Pivot** :
- Hypothèse : chatbot IA vente améliore conversion pré-vente +15%
- Validation : 30% volume conversations = pré-vente, sales team enthousiaste, benchmark concurrents positif
- Plan : développement module vente (recommandation produits, devis), beta 100 conversations
- Résultat : conversion +18%, NPS vente 58, GO GA module vente

**Impact** : +500k€ revenus/an, expansion produit IA support→vente.

---

## Outils et méthodologies

**Discovery** :
- **User research** : interviews (Calendly, Zoom), sondages (Typeform, Google Forms)
- **Product-market fit** : frameworks Sean Ellis (40% règle), Rahul Vohra (superhuman PMF)
- **Prototyping** : Figma (UX), Wizard of Oz (simulation manuelle)

**Déploiement progressif** :
- **Feature flags** : LaunchDarkly, Unleash, Flagsmith
- **A/B testing** : Optimizely, VWO, Google Optimize
- **Monitoring** : Datadog, New Relic, Grafana

**Feedback** :
- **NPS/CSAT** : Delighted, SurveyMonkey, Typeform
- **Analytics** : Google Analytics, Mixpanel, Amplitude
- **Session replay** : Hotjar, FullStory, LogRocket

**Itération** :
- **Lean Startup** : Build-Measure-Learn, MVP, pivots
- **Agile** : sprints 2-4 semaines, retrospectives, backlogs

---

## Checklist qualité discovery/adoption

Avant de valider une discovery ou un déploiement :
- [ ] Problem validation réalisée (interviews >5 users, données quantitatives)
- [ ] Solution validation (benchmark IA vs alternatives, ROI estimé)
- [ ] Product validation (MVP testé, NPS >40, rétention D30 >50%)
- [ ] Plan de rollout progressif (beta interne → fermée → ouverte → GA)
- [ ] Critères Go/No-Go définis (métriques, seuils, timeline)
- [ ] Playbook incidents (monitoring, alertes, rollback)
- [ ] Communication utilisateurs (annonces, guides, support)
- [ ] Collecte feedback multi-canal (NPS, CSAT, analytics, interviews)
- [ ] Analyse feedback mensuelle (insights, pain points, actions)
- [ ] Itération rapide (sprints 2-4 semaines, Build-Measure-Learn)
- [ ] Décision pivot/persévérer basée sur data (pas au feeling)
- [ ] Mise à jour roadmap selon learnings (features ajoutées/déprioritisées)

## Exemples d'usage

### Exemple 1 : Valider un assistant de réponse aux questions internes
**Contexte** : Une organisation envisage un assistant IA pour retrouver des réponses dans ses procédures, mais l'utilité du cas n'est pas confirmée.  
**Input** : Profils d'utilisateurs, demandes récurrentes, sources documentaires autorisées, solutions actuelles et critères de succès proposés.  
**Output** : Plan de discovery avec entretiens et prototype limité, hypothèses à tester, comparaison à une recherche classique et critères Go/No-Go soumis aux owners.

### Exemple 2 : Piloter l'adoption d'une aide IA à la rédaction
**Contexte** : Une fonctionnalité est déployée à un petit groupe; l'activation est correcte, mais l'usage récurrent et la qualité restent inconnus.  
**Input** : Cohorte pilote, parcours, retours utilisateurs, données d'usage agrégées et incidents/erreurs signalés.  
**Output** : Analyse des frictions, plan d'itération et métriques d'adoption/qualité, avec recommandations de poursuivre, ajuster ou suspendre selon les seuils convenus.

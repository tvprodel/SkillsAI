# AI Feature Prioritization & Metrics

## Objectif
Prioriser les features IA selon la valeur métier, définir et suivre les métriques de succès des produits IA/ML.

**Agents utilisateurs** : l'agent de stratégie produit IA (principal), l'agent de stratégie produit, l'agent data science

## Quand l'utiliser (triggers)
- Prioriser un backlog de features IA (MoSCoW, RICE, ICE)
- Définir les métriques de succès d'un produit/feature IA
- Arbitrer Go/No-Go sur un développement IA
- Suivre et analyser les métriques IA/ML en production

## Hors périmètre
- Priorisation features business (hors IA) → l'agent de stratégie produit
- Métriques techniques ML uniquement → l'agent data science
- Architecture de tracking → l'agent d'architecture logicielle

---

## Inputs requis
- Backlog de features et objectifs métier/produit concernés.
- Estimations Reach, Impact, Confidence, Effort et sources justifiant ces estimations.
- Dépendances techniques, contraintes de capacité et hypothèses de faisabilité fournies par les équipes.
- Résultats actuels et besoins de mesure métier, technique, éthique et coût.

## Sorties attendues
- Backlog priorisé avec méthode, scores, hypothèses et niveau de confiance.
- Recommandations de séquencement, dépendances et éléments reportés.
- Catalogue de métriques avec définition, baseline, cible, source et fréquence.
- Décision Go/No-Go argumentée lorsque demandée.

## Workflow recommandé
1. Cadrer l'objectif et les décisions à prendre.
2. Vérifier les données et la confiance des estimations de chaque feature.
3. Appliquer RICE, MoSCoW ou ICE en explicitant la méthode et ses limites.
4. Revoir dépendances, capacité technique, risques éthiques et coût avec les owners concernés.
5. Définir les métriques, baselines, cibles et modalités de suivi.
6. Publier l'arbitrage, les hypothèses et les éléments à réévaluer.

## Garde-fous
- Ne pas présenter un score comme une mesure objective si les entrées sont des estimations incertaines.
- Ne pas prioriser sans validation de la faisabilité et des dépendances techniques.
- Inclure qualité, fairness, coûts et risques réglementaires selon le cas d'usage.
- Distinguer les KPI métier des métriques techniques et d'éthique.

## Template d'entrée (copier/coller)
```text
[Objectif produit IA] ...
[Features candidates et valeur attendue] ...
[Reach / Impact / Confidence / Effort et sources] ...
[Contraintes techniques, capacité, risques et dépendances] ...
[Baselines et décisions à éclairer] ...
```

## Template de sortie (copier/coller)
```text
[Backlog priorisé] Feature, méthode, score, confiance et dépendances : ...
[Arbitrage] Séquencement, report, Go/No-Go et justification : ...
[Métriques] Définition, baseline, cible, source, owner et fréquence : ...
[Hypothèses et risques] ...
```

## KPI reliés
- Part des features priorisées avec estimations sourcées et niveau de confiance explicite.
- Part des métriques retenues avec définition, baseline, cible, source et owner.
- Écart entre effort estimé et réel, suivi par période comparable.

## Definition of done
- Le backlog est priorisé avec méthode et hypothèses explicites.
- Faisabilité, dépendances, risques et capacité ont été examinés.
- Chaque métrique proposée est mesurable et a une définition exploitable.
- Les décisions et incertitudes restantes sont consignées.

## Compétences

### 1. Frameworks de priorisation IA (RICE, MoSCoW, ICE)

**Description** : Appliquer des frameworks structurés pour prioriser les features IA selon critères métier/technique.

**Frameworks** :

**RICE (Reach, Impact, Confidence, Effort)** :
- **Reach** : Combien d'utilisateurs impactés par trimestre ? (ex: 10k users/Q)
- **Impact** : Quel impact par utilisateur ? (Massive=3, High=2, Medium=1, Low=0.5)
- **Confidence** : Quelle confiance dans les estimations ? (High=100%, Medium=80%, Low=50%)
- **Effort** : Combien de person-months ? (ex: 2 devs × 1 mois = 2 PM)
- **Score RICE** = (Reach × Impact × Confidence) / Effort

**MoSCoW** :
- **Must Have** : critique pour la release (MVP non viable sans)
- **Should Have** : important mais contournable temporairement
- **Could Have** : nice to have, valeur ajoutée faible
- **Won't Have** : hors scope cette release (peut-être plus tard)

**ICE (Impact, Confidence, Ease)** :
- **Impact** : Quel impact métier ? (1-10)
- **Confidence** : Quelle confiance ? (1-10)
- **Ease** : Facilité d'implémentation ? (1-10, 10=très facile)
- **Score ICE** = (Impact + Confidence + Ease) / 3

**Livrables** :
- Backlog priorisé avec scores RICE/ICE ou catégories MoSCoW
- Matrice effort/valeur (2×2 : quick wins, long terme, remplissage, à éviter)
- Recommandations séquencement features

**Exemple RICE** :
```
Backlog Chatbot IA Support Client

| Feature | Reach | Impact | Confidence | Effort | RICE | Priorité |
|---------|-------|--------|------------|--------|------|----------|
| Support NL/DE | 20k | 2 (High) | 80% | 1.5 PM | 21.3 | Must Have |
| Fine-tuning historique | 50k | 3 (Massive) | 50% | 3 PM | 25.0 | Must Have |
| Dashboard analytics | 5k | 1 (Medium) | 100% | 0.5 PM | 10.0 | Should Have |
| Personnalisation réponses | 30k | 2 (High) | 80% | 2 PM | 24.0 | Must Have |
| Intégration CRM | 10k | 2 (High) | 50% | 4 PM | 2.5 | Could Have |
| Voice support | 5k | 3 (Massive) | 30% | 6 PM | 0.75 | Won't Have |

Priorisation Q2 :
1. Fine-tuning historique (RICE 25.0)
2. Personnalisation réponses (RICE 24.0)
3. Support NL/DE (RICE 21.3)
4. Dashboard analytics (RICE 10.0)
5. Intégration CRM (RICE 2.5) → reporté Q3
6. Voice support (RICE 0.75) → reporté Q4+
```

**Pièges à éviter** :
- Scores fantaisistes (Reach/Impact/Effort non validés avec équipe technique)
- Prioriser uniquement sur RICE sans considérer dépendances techniques
- Ignorer l'effort technique (consulter **l'agent de machine learning** obligatoire)

---

### 2. Définition de métriques IA/ML (métier + technique + éthique + coûts)

**Description** : Définir des métriques complètes pour mesurer le succès des produits IA/ML.

**4 dimensions de métriques IA** :

**1. Métriques métier** :
- **Adoption** : % utilisateurs actifs, taux d'activation, rétention
- **Satisfaction** : NPS, CSAT, taux de feedback positif
- **Impact business** : revenus générés, coûts économisés, temps gagné
- **Engagement** : fréquence d'utilisation, durée sessions, features utilisées

**2. Métriques techniques ML** :
- **Performance modèle** : accuracy, precision, recall, F1-score, AUC
- **Qualité prédictions** : calibration, confiance, taux d'erreur
- **Latence** : temps de réponse (p50, p95, p99)
- **Disponibilité** : uptime, taux d'erreur API

**3. Métriques éthique** :
- **Fairness** : parité démographique, égalité des chances (par genre/âge/origine)
- **Explicabilité** : % prédictions avec explication (SHAP, LIME)
- **Conformité** : conformité RGPD, AI Act (supervision humaine, transparence)
- **Impact sociétal** : biais détectés, réclamations discrimination

**4. Métriques coûts** :
- **Coût inférence** : coût par prédiction, coût par utilisateur actif
- **Coût entraînement** : coût réentraînement modèle, fréquence
- **Coût infra** : compute, stockage, réseau
- **ROI** : (valeur métier - coûts IA) / coûts IA

**Livrables** :
- Document de métriques de succès (4 dimensions)
- Dashboards de suivi (délégation **l'agent data science**)
- Seuils d'alerte (ex: accuracy < 80% → alerte)
- Critères Go/No-Go déploiement

**Exemple métriques chatbot IA** :
```
Métriques de succès : Chatbot IA Support Client

Métriques métier :
- Adoption : % clients ayant utilisé chatbot IA au moins 1 fois
  Baseline : 15% (fin Q1)
  Cible Q2 : 40%
  Tracking : Google Analytics, événement "chatbot_opened"

- Satisfaction : NPS chatbot IA (sondage post-conversation)
  Baseline : 45 (fin Q1)
  Cible Q2 : 60
  Tracking : Sondage 1-10 après conversation, calcul NPS

- Impact business : Économie coûts support (€/mois)
  Baseline : 0€ (fin Q1, pas de chatbot)
  Cible Q2 : 20k€/mois économisés (vs agents humains niveau 1)
  Tracking : (nb conversations résolues autonomes × coût agent humain)

Métriques techniques ML :
- Taux de résolution autonome (sans escalade humaine)
  Baseline : 70% (fin Q1)
  Cible Q2 : 80%
  Tracking : tag "resolved_without_escalation" / total conversations

- Latence (p95)
  Baseline : 2.5s (fin Q1)
  Cible Q2 : 1.5s
  Tracking : API monitoring, percentile 95

- Uptime API chatbot
  Baseline : 99.5% (fin Q1)
  Cible Q2 : 99.9%
  Tracking : monitoring infra, SLA

Métriques éthique :
- Parité démographique résolution (genre)
  Baseline : Non mesuré (fin Q1)
  Cible Q2 : >95% (écart max 5% résolution hommes vs femmes)
  Tracking : audit **l'agent d'éthique des données** mensuel

- Taux d'explicabilité prédictions
  Baseline : 0% (fin Q1, pas d'explications)
  Cible Q2 : 100% (affichage confiance modèle + sources)
  Tracking : % conversations avec affichage confiance

Métriques coûts :
- Coût moyen par conversation résolue
  Baseline : 0.50€ (fin Q1, API GPT-4)
  Cible Q2 : 0.30€ (optimisation prompts + caching)
  Tracking : dashboard **FinOps**, coût API / nb conversations

- ROI chatbot IA
  Baseline : -100% (fin Q1, investissement MVP)
  Cible Q2 : +50% ((20k€ économisés - 10k€ coûts IA) / 10k€)
  Tracking : (valeur métier - coûts IA) / coûts IA
```

**Pièges à éviter** :
- Métriques techniques ML uniquement (accuracy 95% mais adoption 5% = échec produit)
- Métriques métier floues (pas de baseline, pas de cible, pas de tracking)
- Ignorer éthique/fairness (biais discriminatoires en prod)

---

### 3. Arbitrage Go/No-Go modèle ML

**Description** : Décider si un modèle ML est prêt pour le déploiement (beta, GA, production).

**Critères Go/No-Go** :

**Performance technique** :
- Accuracy/F1/AUC > seuil défini (ex: accuracy > 80%)
- Latence < seuil (ex: p95 < 2s)
- Pas de régression vs version précédente (A/B test favorable)

**Qualité données** :
- Pas de data drift significatif (distribution entrée stable)
- Couverture données représentative (pas de biais échantillonnage)
- Qualité données validation (pas de leakage, pas de contamination)

**Éthique/Fairness** :
- Audit **l'agent d'éthique des données** validé (pas de biais discriminatoires)
- Conformité RGPD/AI Act (supervision humaine, explicabilité)
- Impact sociétal acceptable (pas de risque réputation)

**Coûts** :
- Coût inférence < budget (ex: coût/requête < 0.05€)
- ROI positif (valeur métier > coûts IA)
- Scalabilité validée (coûts linéaires ou sub-linéaires)

**Adoption/UX** :
- Tests utilisateurs positifs (NPS beta > seuil, ex: NPS > 50)
- Pas de frictions UX majeures (taux d'abandon < 30%)
- Documentation utilisateur complète (guides, troubleshooting)

**Livrables** :
- Checklist Go/No-Go (critères + statut + validation)
- Rapport de validation (résumé tests, benchmarks, audit)
- Recommandation (Go / No-Go / Itérer) avec justification
- Plan de contingence si Go (monitoring, rollback, support)

**Exemple Go/No-Go** :
```
Go/No-Go : Chatbot IA v1.5 (Fine-tuning + NL/DE) - Beta externe

Critères techniques :
✅ Accuracy FR/EN : 82% (cible 80%, +2%)
✅ Accuracy NL/DE : 78% (cible 75%, +3%)
✅ Latence p95 : 1.8s (cible <2s)
✅ Uptime staging : 99.8% (cible 99.5%)
✅ Pas de régression vs v1.0 (A/B test : +5% résolution autonome)

Critères données :
✅ Data drift < 5% (distribution stable vs historique)
✅ Couverture NL/DE : 10k conversations validées (cible 5k)
⚠️ Biais échantillonnage NL : sur-représentation Amsterdam (70% vs 40% pop)
   → Mitigation : réentraînement Q3 avec données régions manquantes

Critères éthique :
✅ Audit l'agent d'éthique des données validé (pas de biais genre/âge)
⚠️ Conformité AI Act : explicabilité partielle (affichage confiance, pas de SHAP)
   → Mitigation : ajout SHAP Q3, OK pour beta

Critères coûts :
✅ Coût/conversation : 0.35€ (cible <0.40€)
✅ ROI projeté : +60% (15k€ économisés - 6k€ coûts)
✅ Scalabilité : coûts linéaires validés (stress test 10k conv/jour)

Critères adoption :
✅ NPS beta interne : 58 (cible >50)
✅ Taux d'abandon : 18% (cible <30%)
⚠️ Documentation NL/DE incomplète (manque troubleshooting)
   → Mitigation : rédaction guide NL/DE avant beta externe (1 semaine)

**Décision : GO Beta externe (avec 2 mitigations)**
Justification :
- Tous critères critiques validés (performance, éthique, coûts)
- 3 points d'attention (biais NL, explicabilité, doc) = non-bloquants pour beta
- Mitigations planifiées Q3 avant GA

Plan :
- Beta externe : 1000 clients pilotes (20 juin - 20 août)
- Monitoring renforcé (dashboards quotidiens, alertes)
- Hotline support dédiée beta (réponse <4h)
- Go/No-Go GA : revue 31 août (critères : NPS >55, résolution >78%, bugs critiques <5)
```

**Pièges à éviter** :
- Go sans audit éthique (risque biais discriminatoires)
- No-Go sur critère mineur (perfectionnisme, paralysie décision)
- Ignorer feedback beta avant GA (déploiement aveugle)

---

### 4. A/B testing et expérimentation produits IA

**Description** : Tester et comparer des features IA via A/B tests pour décisions data-driven.

**Techniques** :
- **Design A/B test** : groupe contrôle (A) vs groupe traitement (B), randomisation utilisateurs
- **Hypothèses** : H0 (pas de différence) vs H1 (B meilleur que A)
- **Métriques primaires** : 1-2 métriques clés (ex: taux de résolution autonome)
- **Métriques secondaires** : métriques complémentaires (latence, satisfaction, coûts)
- **Taille échantillon** : power analysis (consulter **l'agent data science**)
- **Durée test** : suffisamment longue pour significativité statistique (ex: 2-4 semaines)
- **Analyse** : tests statistiques (t-test, chi², bootstrap), intervalles de confiance
- **Decision** : déployer B si amélioration significative (p<0.05) et impact métier positif

**Livrables** :
- Protocole A/B test (hypothèses, métriques, taille échantillon, durée)
- Rapport A/B test (résultats, significativité, recommandation)
- Décision (déployer B / garder A / itérer) avec justification

**Exemple A/B test** :
```
A/B Test : Chatbot v1.5 fine-tuné vs v1.0 API GPT-4

Hypothèse :
H0 : Taux de résolution autonome v1.5 = v1.0
H1 : Taux de résolution autonome v1.5 > v1.0 (amélioration attendue +10%)

Design :
- Groupe A (contrôle) : 50% utilisateurs → v1.0 API GPT-4
- Groupe B (traitement) : 50% utilisateurs → v1.5 fine-tuné
- Randomisation : par user_id (stable, pas de contamination)
- Durée : 4 semaines (1er-30 juin)

Métriques primaires :
- Taux de résolution autonome (% conversations sans escalade humaine)
  A (baseline) : 70%
  B (attendu) : 80%

Métriques secondaires :
- NPS chatbot (sondage post-conversation)
- Latence p95 (secondes)
- Coût moyen par conversation (€)

Taille échantillon :
- Power analysis (α=0.05, β=0.20, effet attendu 10%) : 1000 conversations/groupe
- Total : 2000 conversations sur 4 semaines (OK, volume 5000 conv/mois)

Résultats (après 4 semaines) :
| Métrique | Groupe A (v1.0) | Groupe B (v1.5) | Différence | p-value | Significatif |
|----------|-----------------|-----------------|------------|---------|--------------|
| Résolution autonome | 71% | 82% | +11% | p=0.002 | ✅ Oui |
| NPS | 48 | 61 | +13 pts | p=0.01 | ✅ Oui |
| Latence p95 | 2.1s | 1.7s | -0.4s | p=0.03 | ✅ Oui |
| Coût/conv | 0.48€ | 0.33€ | -0.15€ | p=0.001 | ✅ Oui |

Analyse :
- Hypothèse H1 validée : v1.5 améliore résolution autonome (+11%, p=0.002)
- Toutes métriques secondaires favorables (NPS +13, latence -0.4s, coût -31%)
- Pas d'effet négatif détecté (taux d'erreur stable, satisfaction stable)
- ROI positif : économie 0.15€/conv × 5000 conv/mois = 750€/mois

**Décision : Déployer v1.5 à 100% utilisateurs**
Justification :
- Amélioration significative résolution autonome (+11%, p<0.01)
- Pas de trade-off négatif (toutes métriques améliorées)
- ROI positif (économie 9k€/an)

Plan déploiement :
- Rollout progressif : 25% → 50% → 75% → 100% sur 2 semaines
- Monitoring renforcé (alertes si régression)
- Dépréciation v1.0 : 31 décembre 2026
```

**Pièges à éviter** :
- Échantillon trop petit (pas de significativité statistique)
- Durée test trop courte (effet Novelty, saisonnalité)
- Cherry-picking métriques (p-hacking : tester 20 métriques, garder la seule significative)

---

### 5. Suivi et dashboarding métriques IA

**Description** : Mettre en place des dashboards pour suivre les métriques IA/ML en temps réel ou quasi-réel.

**Techniques** :
- **Outils dashboarding** : Tableau, Looker, Metabase, Streamlit, Plotly Dash
- **Métriques temps réel** : adoption, latence, taux d'erreur, coûts (mise à jour horaire/quotidienne)
- **Métriques batch** : accuracy, fairness, drift (mise à jour hebdomadaire/mensuelle)
- **Alertes** : seuils d'alerte (ex: accuracy < 80% → email équipe ML)
- **Segmentation** : métriques par segment utilisateur (pays, âge, usage...)
- **Tendances** : évolution temporelle (courbes, comparaison périodes)

**Livrables** :
- Dashboard interactif métriques IA (délégation **l'agent data science** pour implémentation)
- Documentation dashboard (guide utilisateur, définition métriques)
- Plan de maintenance dashboard (mise à jour données, évolution métriques)

**Exemple dashboard chatbot IA** :
```
Dashboard Chatbot IA Support Client

Section 1 : Métriques métier (mise à jour quotidienne)
- KPI : Adoption (% clients actifs chatbot) : 38% (cible 40%)
  Tendance : +5% vs mois dernier
  Alerte : aucune

- KPI : NPS chatbot : 59 (cible 60)
  Tendance : +8 pts vs mois dernier
  Alerte : aucune

- KPI : Économie coûts support : 18k€/mois (cible 20k€)
  Tendance : +10k€ vs mois dernier
  Alerte : aucune

Section 2 : Métriques techniques ML (mise à jour quotidienne)
- KPI : Taux résolution autonome : 81% (cible 80%)
  Tendance : +1% vs mois dernier
  Alerte : aucune

- KPI : Latence p95 : 1.6s (cible <2s)
  Tendance : -0.3s vs mois dernier
  Alerte : aucune

- KPI : Uptime API : 99.9% (cible 99.9%)
  Tendance : stable
  Alerte : aucune

Section 3 : Métriques éthique (mise à jour mensuelle)
- KPI : Parité démographique résolution (genre) : 97% (cible >95%)
  Tendance : +2% vs mois dernier
  Alerte : aucune

- KPI : Taux explicabilité : 100% (cible 100%)
  Tendance : stable
  Alerte : aucune

Section 4 : Métriques coûts (mise à jour quotidienne)
- KPI : Coût moyen/conversation : 0.32€ (cible <0.40€)
  Tendance : -0.05€ vs mois dernier
  Alerte : aucune

- KPI : ROI chatbot : +65% (cible >50%)
  Tendance : +15% vs mois dernier
  Alerte : aucune

Section 5 : Segmentation (mise à jour hebdomadaire)
- Adoption par pays : FR 45%, NL 38%, DE 32%, EN 40%
- NPS par pays : FR 62, NL 58, DE 55, EN 61
- Résolution autonome par langue : FR 85%, NL 80%, DE 76%, EN 82%
  ⚠️ Alerte : DE sous-performant (-4% vs cible) → investigation requise

Section 6 : Monitoring dérive (mise à jour hebdomadaire)
- Data drift (distribution entrée) : 3% (cible <5%)
- Model drift (accuracy test set) : -1% vs baseline (cible <-5%)
  Statut : stable, pas de réentraînement requis
```

**Pièges à éviter** :
- Dashboard surchargé (trop de métriques = dilution focus)
- Pas d'alertes (métriques visualisées mais jamais actionnées)
- Données obsolètes (mise à jour manuelle oubliée)

---

## Exemples d'utilisation

### Exemple 1 : Priorisation backlog chatbot IA (RICE)

**Contexte** : Backlog de 8 features IA, budget limité Q2 (2 devs × 2 mois), besoin prioriser.

**Features candidates** :
1. Support NL/DE
2. Fine-tuning historique conversations
3. Dashboard analytics
4. Personnalisation réponses selon profil client
5. Intégration CRM
6. Voice support
7. Proactive suggestions
8. Multi-channel (email, SMS)

**Priorisation RICE** :
- Consultation **l'agent de machine learning** pour estimation effort
- Consultation **l'agent de stratégie produit** pour estimation impact métier
- Calcul scores RICE
- **Top 3** : Fine-tuning (25.0), Personnalisation (24.0), NL/DE (21.3)

**Résultat** : Q2 focus sur 3 features Must Have, report intégration CRM/voice support Q3-Q4.

### Exemple 2 : Définition métriques de succès recommandation produits IA

**Contexte** : E-commerce, nouveau moteur de recommandation produits IA (ML collaborative filtering).

**Métriques définies** :
- **Métier** : CTR recommandations (+30% vs baseline), revenus générés (+100k€/trimestre), taux d'ajout panier (+15%)
- **Technique ML** : precision@10 (>40%), recall@10 (>30%), latence p95 (<500ms)
- **Éthique** : pas de biais de popularité (diversity >0.5), pas de filterbubble (serendipity >0.3)
- **Coûts** : coût/recommandation (<0.001€), ROI (+200%)

**Dashboard Streamlit** créé (délégation **l'agent data science**), alertes configurées.

### Exemple 3 : A/B test chatbot v1.5 fine-tuné vs v1.0 API

**Contexte** : Chatbot en prod v1.0 (GPT-4 API), v1.5 fine-tuné prête, besoin valider amélioration avant GA.

**A/B test** :
- 50% utilisateurs v1.0, 50% v1.5
- Métrique primaire : taux résolution autonome
- Durée : 4 semaines, 2000 conversations
- **Résultat** : v1.5 améliore résolution +11% (p=0.002), NPS +13, coût -31%

**Décision** : Déployer v1.5 à 100%, déprécier v1.0 fin année.

---

## Outils et frameworks

**Priorisation** :
- **RICE calculator** : templates Google Sheets, Notion
- **MoSCoW** : Jira, Trello, Asana
- **ICE scoring** : ProductPlan, Aha!

**Métriques et dashboarding** :
- **BI tools** : Tableau, Looker, Metabase, PowerBI
- **Custom dashboards** : Streamlit, Plotly Dash, Grafana
- **ML monitoring** : Evidently AI, Arize, Fiddler

**A/B testing** :
- **Experimentation platforms** : Optimizely, VWO, Google Optimize
- **Statistical analysis** : Python (SciPy, Statsmodels), R
- **ML experiment tracking** : MLflow, Weights & Biases

---

## Checklist qualité priorisation/métriques

Avant de finaliser une priorisation ou définition de métriques :
- [ ] Framework de priorisation appliqué (RICE/MoSCoW/ICE)
- [ ] Estimation effort validée avec équipe technique (l'agent de machine learning/l'agent de sélection de modèles génératifs)
- [ ] Métriques 4 dimensions définies (métier + technique + éthique + coûts)
- [ ] Baselines et cibles quantifiées (pas de flou)
- [ ] Plan de tracking défini (outils, fréquence, responsables)
- [ ] Critères Go/No-Go formalisés (checklist complète)
- [ ] A/B tests avec power analysis (taille échantillon suffisante)
- [ ] Dashboard opérationnel (mise à jour automatique, alertes)
- [ ] Documentation métriques (définitions claires, sources données)
- [ ] Revue mensuelle métriques planifiée (itération continue)

## Exemples d'usage

### Exemple 1 : Prioriser des améliorations d'un assistant de support
**Contexte** : Une équipe produit doit choisir les améliorations IA du prochain trimestre sans confondre impact attendu et facilité technique.  
**Input** : Backlog des fonctions candidates, utilisateurs concernés, estimations de portée/impact/confiance/effort et dépendances confirmées par l'équipe technique.  
**Output** : Tableau RICE ou MoSCoW avec hypothèses et incertitudes visibles, ordre proposé et décisions de priorité laissées au l'agent produit.

### Exemple 2 : Définir les métriques de succès d'un résumé automatique
**Contexte** : Une fonction de résumé de tickets est en pilote et son taux d'utilisation seul ne permet pas d'évaluer sa valeur.  
**Input** : Objectif métier, parcours pilote, données de référence et contraintes de qualité, coût, délai et supervision humaine.  
**Output** : Fiche de métriques séparant adoption, qualité des résumés, temps économisé, coût par usage et indicateurs de risque, avec source, fréquence et seuils à valider.

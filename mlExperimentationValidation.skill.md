# ML Experimentation & Validation

## Objectif
Concevoir des expériences ML rigoureuses, comparer des modèles et interpréter les résultats avec une validation statistique adaptée.

**Agents utilisateurs** : l'agent data science (principal), l'agent de machine learning, l'agent de stratégie produit

## Quand l'utiliser (triggers)
- Comparaison performance de plusieurs modèles ML (A/B testing, benchmarks)
- Validation statistique d'améliorations performance (nouveau modèle vs baseline)
- Design protocole expérimental ML robuste (métriques, taille échantillon, protocole test)
- Interprétation résultats ML pour audiences non-techniques

## Hors périmètre
- Construction pipelines ML de production → [ML Pipeline Design & Evaluation]
- Tests robustesse adversariaux (prompt injection) → [Adversarial Testing & Robustness]
- Optimisation hyperparamètres automatisée → [ML Pipeline Design & Evaluation]

---

## Inputs requis
- Hypothèse, baseline et effet minimal pertinent pour le métier.
- Modèles, dataset d'évaluation, protocole de split et métriques candidates.
- Taille d'échantillon, contexte temporel et risques de fuite ou de contamination.
- Seuils de décision et contraintes de déploiement ou de coût.

## Sorties attendues
- Protocole expérimental avec hypothèses, métriques, échantillon et tests.
- Comparaison des modèles avec intervalles d'incertitude et limites.
- Recommandation Go/No-Go/itération reliée aux critères convenus.
- Rapport reproductible indiquant données, méthode et version des modèles.

## Workflow recommandé
1. Définir H0/H1, baseline, effet minimal détectable et décision attendue.
2. Choisir métriques cohérentes avec le coût des erreurs et le cas d'usage.
3. Vérifier l'indépendance des jeux, les fuites, le biais de sélection et la puissance.
4. Pré-enregistrer le protocole et appliquer les tests statistiques appropriés.
5. Présenter les résultats avec intervalles, limites et analyse par segment pertinente.
6. Relier la conclusion aux critères Go/No-Go sans extrapolation.

## Garde-fous
- Ne pas choisir les métriques après observation des résultats sans le signaler.
- Ne pas conclure sur la seule significativité statistique; évaluer l'effet pratique.
- Contrôler leakage, sélection, tests multiples, représentativité et comparabilité.
- Ne pas généraliser les résultats hors du protocole et de la population évalués.

## Template d'entrée (copier/coller)
```text
[Hypothèse et baseline] ...
[Modèles/données] Versions, split, période et population : ...
[Métriques et effet minimal attendu] ...
[Taille/contraintes] Puissance, coût, seuil de décision : ...
```

## Template de sortie (copier/coller)
```text
[Protocole] H0/H1, population, split, métriques et tests : ...
[Résultats] Estimations, intervalles et significativité : ...
[Limites] Puissance, biais, leakage, tests multiples : ...
[Décision] Go/No-Go/itérer selon critères convenus : ...
```

## KPI reliés
- Part des expériences avec hypothèse, baseline et protocole définis avant analyse.
- Taux de reproductibilité des résultats sur les données et versions spécifiées.
- Écart entre amélioration statistique observée et effet métier minimal attendu.

## Definition of done
- Le protocole et les critères de décision sont documentés.
- Les tests respectent leurs hypothèses et les limites sont explicites.
- La recommandation est reproductible et proportionnée aux résultats observés.

## Compétences

### 1. Design d'expériences ML et protocole de test

**Description** : Concevoir protocoles expérimentaux rigoureux pour tester hypothèses ML, définir métriques appropriées, calculer taille échantillon nécessaire.

**Techniques** :
- **Formulation hypothèses** : H0 (baseline performance), H1 (amélioration attendue), seuil significativité (alpha)
- **Choix métriques** : alignement métier (accuracy vs precision/recall vs F1 vs AUC vs custom), single metric vs multi-objective
- **Power analysis** : calcul taille échantillon nécessaire pour détecter effet attendu (effect size, puissance 0.8, alpha 0.05)
- **Protocole randomisation** : train/val/test splits stratifiés, cross-validation k-fold, time-based splits (séries temporelles)
- **Contrôle biais** : randomisation stricte, blinding (si humain dans boucle), correction multiple testing (Bonferroni)

**Livrables** :
- Document design expérimental avec hypothèses H0/H1, métriques, protocole, taille échantillon
- Justification choix métriques (lien avec objectif métier, trade-offs)
- Plan randomisation et splits (stratification si déséquilibre classes)
- Power analysis avec calcul taille échantillon minimum
- Protocole validation statistique (tests appliqués, seuils significativité)

**Exemple** :
```python
from statsmodels.stats.power import tt_ind_solve_power

# Power analysis (comparaison 2 modèles, t-test indépendant)
# Objectif : détecter amélioration +3% accuracy (effect size 0.3)
effect_size = 0.3
alpha = 0.05
power = 0.8

sample_size = tt_ind_solve_power(effect_size=effect_size, alpha=alpha, power=power, alternative='larger')
print(f"Taille échantillon nécessaire par groupe : {int(sample_size)}")

# Stratified split (préserver distribution classes)
from sklearn.model_selection import train_test_split
X_train, X_test, y_train, y_test = train_test_split(
    X, y, test_size=0.2, stratify=y, random_state=42
)

# Cross-validation k-fold
from sklearn.model_selection import StratifiedKFold
skf = StratifiedKFold(n_splits=5, shuffle=True, random_state=42)
for train_idx, val_idx in skf.split(X, y):
    X_train_fold, X_val_fold = X[train_idx], X[val_idx]
    y_train_fold, y_val_fold = y[train_idx], y[val_idx]
    # Train et valide modèle sur ce fold
```

**Pièges à éviter** :
- Sous-dimensionner échantillon test (manque puissance pour détecter effets réels)
- Tester multiples modèles sans correction p-value (risque faux positifs)
- Choisir métriques déconnectées de l'objectif métier (accuracy élevée mais recall faible sur classe rare critique)


### 2. A/B testing et comparaison de modèles ML

**Description** : Comparer performance de 2+ modèles ML statistiquement, valider amélioration vs baseline.

**Techniques** :
- **Bootstrap comparaison** : rééchantillonner prédictions test, calculer métrique chaque bootstrap, comparer distributions
- **Tests paramétriques** : t-test apparié (si paires prédictions), t-test indépendant (si échantillons distincts)
- **Tests non-paramétriques** : Mann-Whitney U, Wilcoxon signed-rank (si distribution métriques non-normale)
- **Intervalles confiance** : différence métriques avec IC 95% (ex: accuracy_B - accuracy_A = +3% [1.2%, 4.8%])
- **Correction multiple testing** : Bonferroni, Benjamini-Hochberg (si comparaison 3+ modèles)

**Livrables** :
- Résultats A/B test avec métriques par modèle (mean, std, IC 95%)
- Test statistique comparaison (t-test, Mann-Whitney) avec p-value, conclusion
- Effect size (différence absolue et relative) avec interprétation pratique
- Visualisation distributions métriques (boxplots, violin plots) par modèle
- Recommandation déploiement basée sur significativité statistique + pratique

**Exemple** :
```python
from scipy import stats
import numpy as np

# Prédictions 2 modèles sur même test set
y_true = [...]  # Labels réels
y_pred_A = [...]  # Prédictions modèle A
y_pred_B = [...]  # Prédictions modèle B

# Calcul métriques
from sklearn.metrics import accuracy_score
acc_A = accuracy_score(y_true, y_pred_A)
acc_B = accuracy_score(y_true, y_pred_B)
print(f"Accuracy A: {acc_A:.4f}, Accuracy B: {acc_B:.4f}")
print(f"Différence absolue: {acc_B - acc_A:.4f}")

# Bootstrap pour IC différence
n_bootstraps = 1000
rng = np.random.default_rng(42)
bootstrap_diffs = []

for _ in range(n_bootstraps):
    indices = rng.choice(len(y_true), size=len(y_true), replace=True)
    y_true_boot = [y_true[i] for i in indices]
    y_pred_A_boot = [y_pred_A[i] for i in indices]
    y_pred_B_boot = [y_pred_B[i] for i in indices]
    
    acc_A_boot = accuracy_score(y_true_boot, y_pred_A_boot)
    acc_B_boot = accuracy_score(y_true_boot, y_pred_B_boot)
    bootstrap_diffs.append(acc_B_boot - acc_A_boot)

# IC 95% différence
ci_low, ci_high = np.percentile(bootstrap_diffs, [2.5, 97.5])
print(f"IC 95% différence: [{ci_low:.4f}, {ci_high:.4f}]")

# Test permutation (H0: pas de différence)
observed_diff = acc_B - acc_A
permutation_diffs = []
for _ in range(1000):
    combined_preds = y_pred_A + y_pred_B
    rng.shuffle(combined_preds)
    perm_A = combined_preds[:len(y_pred_A)]
    perm_B = combined_preds[len(y_pred_A):]
    perm_diff = accuracy_score(y_true, perm_B) - accuracy_score(y_true, perm_A)
    permutation_diffs.append(perm_diff)

p_value = np.mean(np.abs(permutation_diffs) >= abs(observed_diff))
print(f"P-value (test permutation): {p_value:.4f}")
if p_value < 0.05:
    print("Différence significative (p < 0.05)")
```

**Pièges à éviter** :
- Comparer modèles sur échantillons différents (biais sélection, utiliser même test set)
- Ignorer variance aléatoire (run unique, préférer k-fold CV + moyenne)
- Considérer seulement significativité statistique sans effect size (différence significative mais négligeable en pratique)


### 3. Interprétation métriques ML et choix contextuels

**Description** : Comprendre trade-offs métriques ML, choisir métriques appropriées au contexte métier, interpréter résultats.

**Techniques** :
- **Classification binaire** : accuracy, precision, recall, F1, AUC-ROC, AUC-PR, seuil optimal
- **Classification multi-classe** : macro/micro/weighted averaging, confusion matrix, per-class metrics
- **Régression** : MSE, RMSE, MAE, MAPE, R², adjusted R²
- **Ranking** : NDCG, MAP, MRR, precision@k, recall@k
- **Contexte business** : cost-sensitive metrics (false positive cost vs false negative cost), custom metrics métier

**Livrables** :
- Justification choix métrique principale alignée avec objectif métier
- Calcul et interprétation métrique(s) (valeur, signification business)
- Analyse trade-offs (precision vs recall, bias vs variance)
- Seuil de décision optimal si classification binaire (ROC curve, precision-recall curve)
- Rapport performance avec contexte métier (ex: recall 0.85 = détecte 85% fraudes, manque 15%)

**Exemple** :
```python
from sklearn.metrics import classification_report, confusion_matrix, roc_auc_score, roc_curve
import matplotlib.pyplot as plt

# Rapport complet classification
print(classification_report(y_true, y_pred, target_names=['Classe 0', 'Classe 1']))

# Matrice confusion
cm = confusion_matrix(y_true, y_pred)
print("Confusion matrix:\n", cm)
# cm[0,0] = TN, cm[0,1] = FP, cm[1,0] = FN, cm[1,1] = TP

# AUC-ROC
y_proba = model.predict_proba(X_test)[:, 1]  # Probabilités classe positive
auc = roc_auc_score(y_true, y_proba)
print(f"AUC-ROC: {auc:.4f}")

# Courbe ROC + seuil optimal
fpr, tpr, thresholds = roc_curve(y_true, y_proba)
plt.plot(fpr, tpr, label=f'ROC curve (AUC = {auc:.2f})')
plt.plot([0, 1], [0, 1], 'k--', label='Random')
plt.xlabel('False Positive Rate')
plt.ylabel('True Positive Rate')
plt.title('ROC Curve')
plt.legend()
plt.show()

# Seuil optimal (Youden's J statistic = TPR - FPR max)
optimal_idx = np.argmax(tpr - fpr)
optimal_threshold = thresholds[optimal_idx]
print(f"Seuil optimal: {optimal_threshold:.4f}")
```

**Contextes métier** :
- **Détection fraude** : priorité recall élevé (minimiser faux négatifs = fraudes manquées), acceptable FP modéré
- **Diagnostic médical** : priorité recall élevé (minimiser faux négatifs = maladies non détectées), precision importante aussi
- **Spam filtering** : balance precision/recall (trop FP = emails légitimes en spam), F1 approprié
- **Recommandation produits** : NDCG, MAP (ranking quality), precision@k (top k résultats pertinents)

**Pièges à éviter** :
- Utiliser accuracy sur classes déséquilibrées (99% accuracy avec 1% classe positive si prédire toujours négatif)
- Ignorer coûts business différents FP vs FN (optimiser métrique sans lien objectif métier)
- Comparer modèles sur métriques différentes (choisir métrique principale commune)


### 4. Validation croisée et robustesse des résultats

**Description** : Valider généralisation modèle, mesurer variance performance, détecter overfitting.

**Techniques** :
- **K-fold CV** : k splits, moyenne performance k folds, std (mesure variance)
- **Stratified k-fold** : préserve distribution classes dans chaque fold
- **Time-series CV** : splits chronologiques (train sur passé, test sur futur)
- **Leave-one-out CV** : k = n (exhaustif mais coûteux)
- **Nested CV** : CV externe (évaluation) + CV interne (tuning hyperparamètres)
- **Learning curves** : performance vs taille dataset train (détecte overfitting/underfitting)

**Livrables** :
- Résultats k-fold CV avec mean ± std par métrique (ex: accuracy 0.85 ± 0.03)
- Learning curves (train/validation loss ou métrique vs epochs/taille dataset)
- Analyse variance inter-folds (std faible = robuste, std élevé = instable)
- Diagnostic overfitting/underfitting avec recommandations (régularisation, plus de données, etc.)
- Validation protocole CV approprié au contexte (stratified si classes déséquilibrées, time-series si temporel)

**Exemple** :
```python
from sklearn.model_selection import cross_val_score, cross_validate, learning_curve

# K-fold CV simple
from sklearn.ensemble import RandomForestClassifier
model = RandomForestClassifier(random_state=42)

scores = cross_val_score(model, X, y, cv=5, scoring='accuracy')
print(f"Accuracy 5-fold CV: {scores.mean():.4f} ± {scores.std():.4f}")
print(f"Scores par fold: {scores}")

# Cross-validate avec multiples métriques
scoring = ['accuracy', 'precision', 'recall', 'f1', 'roc_auc']
cv_results = cross_validate(model, X, y, cv=5, scoring=scoring, return_train_score=True)

for metric in scoring:
    test_score = cv_results[f'test_{metric}'].mean()
    test_std = cv_results[f'test_{metric}'].std()
    print(f"{metric}: {test_score:.4f} ± {test_std:.4f}")

# Learning curve (détection overfitting)
train_sizes, train_scores, val_scores = learning_curve(
    model, X, y, cv=5, train_sizes=np.linspace(0.1, 1.0, 10), scoring='accuracy'
)

plt.plot(train_sizes, train_scores.mean(axis=1), label='Train')
plt.plot(train_sizes, val_scores.mean(axis=1), label='Validation')
plt.xlabel('Training set size')
plt.ylabel('Accuracy')
plt.title('Learning Curves')
plt.legend()
plt.show()
```

**Diagnostic learning curves** :
- **Overfitting** : gap large train >> validation, augmenter données ou régularisation
- **Underfitting** : train et validation faibles, modèle trop simple ou features insuffisantes
- **Bon fit** : train et validation convergent vers même niveau élevé

**Pièges à éviter** :
- Utiliser k-fold standard sur données temporelles (fuite information future vers passé)
- Tuner hyperparamètres sur test set (overfitting paramètres, utiliser validation set ou nested CV)
- Ignorer variance inter-folds (std élevé = modèle instable, résultats peu fiables)


### 5. Communication résultats ML aux non-techniques

**Description** : Traduire métriques ML en langage métier, créer narratif clair, recommander actions.

**Techniques** :
- **Storytelling data** : structure Problem-Insight-Action, focus sur impact métier
- **Analogies métier** : traduire métriques (recall 0.85 = "détecte 85 fraudes sur 100", pas "TPR 0.85")
- **Visualisations business** : courbes ROC annotées, confusion matrix avec coûts, feature importance avec exemples concrets
- **Recommandations actionnables** : lier résultats ML à décisions métier (déployer/ne pas déployer, collecter plus de données, ajuster seuil)
- **Limites et risques** : expliciter incertitudes, biais potentiels, cas d'échec modèle

**Livrables** :
- Résumé exécutif 1 page (problème, solution ML, résultats clés, recommandation)
- Traduction métriques en impact métier (ex: AUC 0.90 → "détecte 90% clients à risque avec 10% fausses alarmes")
- Visualisations annotées avec insights métier (pas seulement graphiques bruts)
- Recommandations priorisées avec justification (data-driven)
- Section risques et limites (transparence sur incertitudes)

**Exemple de traduction métriques** :
- **Accuracy 0.85** → "Le modèle prédit correctement 85% des cas, soit 8500 sur 10000"
- **Recall 0.90** → "Le modèle détecte 90% des fraudes réelles, en manque 10%"
- **Precision 0.75** → "Parmi les alertes fraude, 75% sont vraies fraudes, 25% fausses alarmes"
- **AUC-ROC 0.92** → "Le modèle distingue très bien les fraudes (92% de capacité discriminante)"

**Structure recommandée présentation exécutive** :
1. **Problème** : Quel problème métier résout-on ? (ex: réduire fraudes de 30%)
2. **Approche** : Quelle solution ML ? (ex: modèle classification prédictif, 50k transactions historiques)
3. **Résultats** : Performance atteinte ? (ex: détecte 90% fraudes avec 5% fausses alarmes)
4. **Impact métier** : Gain estimé ? (ex: économie 2M€/an si déployé, réduction temps investigation 40%)
5. **Recommandation** : Déployer ? (ex: OUI, pilote 3 mois puis déploiement complet)
6. **Risques** : Limites ? (ex: performance peut baisser si nouveaux types fraude, monitoring requis)

**Pièges à éviter** :
- Jargon technique sans traduction (p-value, AUC, F1 sans explication)
- Métriques sans contexte métier (accuracy 0.85 sans dire impact business)
- Présentation résultats sans recommandation actionnable
- Omettre limites et risques (sur-confiance dans modèle)

---

## Exemples d'utilisation

### Exemple 1 : A/B test nouveau modèle de recommandation

**Contexte** : E-commerce, modèle A (collaborative filtering, CTR 3.2%) vs modèle B (deep learning, CTR 3.8% observé sur 10k users).

**Objectif** : Valider statistiquement que modèle B > A avant déploiement complet.

**Démarche** :
1. **Hypothèses** : H0 = CTR_A = CTR_B ; H1 = CTR_B > CTR_A
2. **Power analysis** : effect size 0.6% (différence observée), alpha 0.05, power 0.8 → besoin 8000 users/groupe
3. **Randomisation** : split 50/50 users (stratifié par segment), durée 2 semaines
4. **Résultats** : CTR_A 3.18%, CTR_B 3.82%, différence +0.64% [0.32%, 0.96%] IC 95%
5. **Test** : z-test proportions, p-value 0.001 < 0.05 → significatif
6. **Impact métier** : +0.64% CTR = +20% revenus (estimation 500k€/an)
7. **Recommandation** : Déployer modèle B en production

**Livrable** : Rapport A/B test avec p-value, IC, impact métier, recommandation déploiement


### Exemple 2 : Validation cross-validation modèle churn

**Contexte** : Télécoms, prédiction churn (désabonnement), dataset 100k clients, 20% churn rate.

**Objectif** : Valider généralisation modèle avant déploiement.

**Démarche** :
1. **Protocole** : Stratified 5-fold CV (préserver 20% churn dans chaque fold)
2. **Métriques** : recall (priorité), precision, F1, AUC-ROC
3. **Résultats** : recall 0.78 ± 0.04, precision 0.65 ± 0.05, AUC 0.85 ± 0.03
4. **Analyse variance** : std faible (< 0.05) → modèle robuste
5. **Learning curves** : convergence train/validation, pas d'overfitting visible
6. **Traduction métier** : "Détecte 78% clients à risque churn, 35% fausses alarmes"
7. **Impact** : intervention ciblée sur 22% clients prédits à risque → rétention 40% → économie 3M€/an

**Livrable** : Rapport validation avec CV scores, learning curves, impact métier estimé


### Exemple 3 : Comparaison 5 modèles classification

**Contexte** : Diagnostic médical, 5 modèles candidats (Logistic Regression, Random Forest, XGBoost, SVM, Neural Network).

**Objectif** : Choisir meilleur modèle statistiquement pour déploiement.

**Démarche** :
1. **Métrique principale** : recall (minimiser faux négatifs = maladies non détectées)
2. **Protocole** : Stratified 10-fold CV sur même dataset
3. **Résultats recall** : LR 0.82, RF 0.87, XGB 0.89, SVM 0.84, NN 0.88
4. **Tests statistiques** : Friedman test (équivalent ANOVA pour modèles appariés), p-value 0.003 → différences significatives
5. **Post-hoc** : Nemenyi test pairwise → XGB significativement > LR et SVM, pas de différence XGB vs NN/RF
6. **Correction Bonferroni** : alpha ajusté 0.05/10 = 0.005 (10 comparaisons pairwise)
7. **Choix** : XGBoost (recall 0.89, interprétabilité feature importance, déjà en prod ailleurs)

**Livrable** : Rapport benchmarking avec tests statistiques, recommandation XGBoost justifiée

---

## Outils et librairies

**Python** :
- **Scikit-learn** : cross_val_score, cross_validate, learning_curve, métriques classification/régression
- **SciPy** : tests statistiques (stats module)
- **Statsmodels** : power analysis, tests avancés
- **MLflow** : tracking expériences, logging métriques/paramètres, comparaison runs
- **Weights & Biases (wandb)** : tracking expériences ML, visualisations
- **TensorBoard** : visualisation training (loss curves, métriques)

**R** (si contexte R) :
- **caret** : cross-validation, tuning, comparaison modèles
- **mlr3** : framework ML moderne R
- **pwr** : power analysis

---

## Checklist qualité expérimentation ML

Avant de finaliser une expérience ML, vérifier :
- [ ] Hypothèses H0/H1 formulées clairement
- [ ] Métriques principales choisies et justifiées (lien objectif métier)
- [ ] Power analysis effectuée (taille échantillon suffisante)
- [ ] Protocole randomisation défini (stratification si nécessaire)
- [ ] Cross-validation appropriée au contexte (k-fold, stratified, time-series)
- [ ] Tests statistiques appliqués (p-value, IC 95%)
- [ ] Effect size calculé et interprété (significativité pratique)
- [ ] Variance inter-folds analysée (robustesse résultats)
- [ ] Learning curves générées (diagnostic overfitting/underfitting)
- [ ] Résultats traduits en langage métier (impact business)
- [ ] Recommandations actionnables formulées
- [ ] Limites et risques explicités (transparence)

## Exemples d'usage

### Exemple 1 : Comparer un nouveau modèle de classification à la baseline
**Contexte** : Une équipe observe une hausse de précision sur un échantillon, mais doit déterminer si le gain est robuste et utile au métier.  
**Input** : Prédictions appariées sur un jeu de test indépendant, métrique métier principale, hypothèse d'amélioration, seuil de décision et protocole d'évaluation.  
**Output** : Comparaison avec intervalle d'incertitude et test approprié, taille/limites de l'échantillon, effet pratique et recommandation conditionnelle plutôt qu'une conclusion fondée sur un seul score.

### Exemple 2 : Évaluer une nouvelle détection sur une classe rare
**Contexte** : Un modèle de détection d'incidents améliore l'accuracy globale, mais les incidents manqués sont coûteux.  
**Input** : Labels validés, prédictions des modèles, coût relatif des faux positifs/faux négatifs, segments temporels et budget de test.  
**Output** : Protocole stratifié ou temporel adapté, précision/rappel et incertitude sur la classe rare, comparaison à la baseline et seuils de décision à faire approuver.

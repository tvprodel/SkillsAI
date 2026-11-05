# EDA & Statistical Analysis for ML

## Objectif
Réaliser une analyse exploratoire et statistique des données pour caractériser un dataset, repérer ses limites et éclairer une décision de modélisation ou d'investigation.

**Agents utilisateurs** : l'agent data science (principal), l'agent de machine learning, l'agent d'éthique des données

## Quand l'utiliser (triggers)
- Phase initiale d'un projet ML : comprendre les données avant modélisation
- Diagnostic problème ML en production : analyse statistique des erreurs/résidus
- Validation qualité dataset : détection anomalies, valeurs manquantes, outliers
- Détection biais statistiques : déséquilibres, under-representation, sampling bias

## Hors périmètre
- Construction de modèles ML → [ML Pipeline Design & Evaluation]
- Optimisation requêtes BDD → [Data Governance & Quality]
- Audit fairness algorithmique → [Fairness & Bias Detection]

---

## Inputs requis
- Dataset ou description du processus de collecte, schéma et dictionnaire disponible.
- Question d'analyse, cible éventuelle et décision à éclairer.
- Période, population, règles d'accès et contraintes de confidentialité.
- Contexte métier, critères de qualité et hypothèses statistiques connues.

## Sorties attendues
- Profil descriptif des variables, valeurs manquantes et distributions.
- Analyse des relations, anomalies, biais d'échantillonnage et limites.
- Tests statistiques avec hypothèses, paramètres et interprétation.
- Recommandations de préparation ou de collecte, sans dépasser les preuves.

## Workflow recommandé
1. Vérifier provenance, schéma, unités, population et qualité du dataset.
2. Profiler les variables et quantifier valeurs manquantes, doublons et anomalies.
3. Explorer distributions et relations avec des méthodes adaptées aux données.
4. Formuler les tests statistiques et leurs hypothèses avant interprétation.
5. Rapporter les résultats, limites, biais possibles et prochaines vérifications.

## Garde-fous
- Ne pas inférer causalité depuis une corrélation ni généraliser hors population observée.
- Documenter hypothèses, taille d'échantillon, tests multiples et incertitudes.
- Ne pas supprimer ou transformer des données sans justifier l'impact.
- Traiter les données personnelles selon les accès et règles approuvés.

## Template d'entrée (copier/coller)
```text
[Question d'analyse] ...
[Dataset] Source, période, taille, schéma et cible éventuelle : ...
[Population/collecte] ...
[Contraintes et hypothèses] ...
```

## Template de sortie (copier/coller)
```text
[Profil] Variables, distributions, valeurs manquantes et anomalies : ...
[Analyses/tests] Méthodes, hypothèses et résultats : ...
[Limites] Échantillon, biais, incertitudes et tests multiples : ...
[Suite] Préparation recommandée et questions ouvertes : ...
```

## KPI reliés
- Couverture des variables profilées et des contrôles qualité convenus.
- Part des analyses avec source, population, période et limites documentées.
- Taux d'anomalies confirmées et temps de résolution, si suivis.

## Definition of done
- Résultats descriptifs et analyses répondent à la question de départ.
- Les méthodes, hypothèses, population et limites sont traçables.
- Les recommandations distinguent faits observés et pistes à vérifier.

## Compétences

### 1. Statistiques descriptives et profiling datasets

**Description** : Calculer et interpréter statistiques univariées/bivariées, profiler datasets pour identifier caractéristiques clés.

**Techniques** :
- **Mesures centralité** : mean, median, mode (choix selon distribution)
- **Mesures dispersion** : std, variance, IQR, range, coefficient variation
- **Mesures forme** : skewness (asymétrie), kurtosis (aplatissement)
- **Quantiles** : percentiles, quartiles, déciles
- **Profiling automatique** : pandas-profiling/ydata-profiling, sweetviz

**Livrables** :
- Tableau statistiques descriptives par feature (mean/median/std/min/max/quartiles)
- Rapport profiling automatique avec distributions, corrélations, warnings
- Identification features numériques vs catégorielles, types inférés
- Détection valeurs manquantes (% par colonne), stratégies imputation suggérées

**Exemple** :
```python
import pandas as pd
import numpy as np
from ydata_profiling import ProfileReport

# Statistiques descriptives
df.describe(include='all')  # Toutes colonnes
df.select_dtypes(include=np.number).describe()  # Numériques seules

# Profiling automatique
profile = ProfileReport(df, title="EDA Report", explorative=True)
profile.to_file("eda_report.html")

# Statistiques custom
print(f"Skewness: {df['feature'].skew()}")
print(f"Kurtosis: {df['feature'].kurtosis()}")
print(f"Missing: {df.isnull().sum() / len(df) * 100}%")
```

**Pièges à éviter** :
- Utiliser mean sur distributions fortement asymétriques (préférer median)
- Ignorer l'échelle des features (normaliser avant comparaisons)
- Ne pas différencier valeurs manquantes (NaN) vs valeurs nulles sémantiques (0 légitime)


### 2. Analyse distributions et tests de normalité

**Description** : Analyser distributions univariées, tester normalité, détecter outliers et asymétries.

**Techniques** :
- **Tests normalité** : Shapiro-Wilk (n < 5000), Kolmogorov-Smirnov, Anderson-Darling, Q-Q plots
- **Visualisations** : histogrammes, boxplots, violin plots, density plots (KDE)
- **Détection outliers** : IQR method (Q1 - 1.5*IQR, Q3 + 1.5*IQR), z-scores (> 3), Isolation Forest (algorithmic)
- **Transformations** : log-transform (réduire asymétrie), Box-Cox, Yeo-Johnson

**Livrables** :
- Tests normalité par feature numérique (p-value, conclusion)
- Visualisations distributions (histogrammes + KDE overlay)
- Liste outliers détectés par feature (indices lignes, % dataset impacté)
- Recommandations transformations pour normaliser distributions si nécessaire

**Exemple** :
```python
from scipy import stats
import matplotlib.pyplot as plt
import seaborn as sns

# Test normalité Shapiro-Wilk
stat, p_value = stats.shapiro(df['feature'])
print(f"Shapiro-Wilk: stat={stat:.4f}, p-value={p_value:.4f}")
if p_value > 0.05:
    print("Distribution probablement normale (p > 0.05)")
else:
    print("Distribution non normale (p <= 0.05)")

# Q-Q plot
stats.probplot(df['feature'], dist="norm", plot=plt)
plt.title("Q-Q plot")
plt.show()

# Détection outliers IQR
Q1 = df['feature'].quantile(0.25)
Q3 = df['feature'].quantile(0.75)
IQR = Q3 - Q1
outliers = df[(df['feature'] < Q1 - 1.5*IQR) | (df['feature'] > Q3 + 1.5*IQR)]
print(f"Outliers détectés : {len(outliers)} ({len(outliers)/len(df)*100:.2f}%)")

# Log-transform pour réduire asymétrie
df['feature_log'] = np.log1p(df['feature'])  # log1p = log(1+x) pour gérer zéros
```

**Pièges à éviter** :
- Appliquer Shapiro-Wilk sur datasets > 5000 lignes (perd puissance, préférer KS test)
- Supprimer tous les outliers sans analyser leur origine (peuvent être légitimes)
- Transformer données sans comprendre impact sur modèle ML (certains modèles robustes aux distributions)


### 3. Analyse corrélations et relations bivariées

**Description** : Mesurer relations linéaires/monotones entre features, détecter multicolinéarité.

**Techniques** :
- **Corrélations linéaires** : Pearson (relation linéaire, assume normalité)
- **Corrélations monotones** : Spearman (relations monotones, robuste outliers), Kendall's Tau
- **Visualisations** : heatmap corrélations, scatter plots, pairplots
- **Multicolinéarité** : VIF (Variance Inflation Factor), condition number matrice corrélation
- **Features catégorielles** : Chi² test (indépendance), Cramér's V (force association)

**Livrables** :
- Matrice corrélations avec heatmap annotée (top corrélations positives/négatives)
- Liste paires features fortement corrélées (|r| > 0.7) avec risque multicolinéarité
- Scatter plots features clés vs target (si régression)
- VIF par feature si multicolinéarité suspectée (VIF > 10 = problématique)

**Exemple** :
```python
# Corrélations Pearson
corr_matrix = df.corr(method='pearson')
sns.heatmap(corr_matrix, annot=True, cmap='coolwarm', center=0)
plt.title("Heatmap corrélations Pearson")
plt.show()

# Top 10 corrélations (hors diagonale)
corr_pairs = corr_matrix.unstack()
corr_pairs = corr_pairs[corr_pairs != 1.0]  # Exclure autocorrélations
top_corr = corr_pairs.abs().sort_values(ascending=False).head(10)
print("Top 10 corrélations :\n", top_corr)

# Multicolinéarité VIF
from statsmodels.stats.outliers_influence import variance_inflation_factor
X = df[['feature1', 'feature2', 'feature3']]
vif_data = pd.DataFrame()
vif_data["Feature"] = X.columns
vif_data["VIF"] = [variance_inflation_factor(X.values, i) for i in range(X.shape[1])]
print(vif_data)  # VIF > 10 = multicolinéarité problématique

# Spearman (robuste outliers)
corr_spearman = df.corr(method='spearman')
```

**Pièges à éviter** :
- Utiliser Pearson sur relations non-linéaires (préférer Spearman ou analyse visuelle)
- Ignorer multicolinéarité dans modèles linéaires (régression linéaire, logistique sensibles)
- Confondre corrélation et causalité (corrélation ≠ causalité)


### 4. Tests statistiques inférentiels

**Description** : Tester hypothèses statistiques, valider différences entre groupes, mesurer significativité.

**Techniques** :
- **Comparaison 2 groupes** : t-test indépendant (moyennes, assume normalité), Mann-Whitney U (médians, non-paramétrique)
- **Comparaison 3+ groupes** : ANOVA (moyennes plusieurs groupes, assume normalité), Kruskal-Wallis (médians, non-paramétrique)
- **Tests proportion** : z-test, chi² test d'indépendance
- **Tests normalité** : Shapiro-Wilk, Kolmogorov-Smirnov, Anderson-Darling
- **Intervalles confiance** : bootstrap, t-distribution (petits échantillons), z-distribution (grands échantillons)

**Livrables** :
- Formulation hypothèses H0/H1 claires
- Résultats tests avec statistique, p-value, conclusion (rejet/non-rejet H0)
- Intervalles de confiance à 95% pour estimations (moyennes, proportions, différences)
- Interprétation significativité statistique vs significativité pratique (effect size)

**Exemple** :
```python
from scipy import stats

# T-test indépendant (comparaison 2 moyennes)
group1 = df[df['category'] == 'A']['metric']
group2 = df[df['category'] == 'B']['metric']
stat, p_value = stats.ttest_ind(group1, group2)
print(f"T-test: t={stat:.4f}, p-value={p_value:.4f}")
if p_value < 0.05:
    print("Différence significative entre groupes (p < 0.05)")
else:
    print("Pas de différence significative (p >= 0.05)")

# ANOVA (comparaison 3+ groupes)
groups = [df[df['category'] == cat]['metric'].values for cat in df['category'].unique()]
stat, p_value = stats.f_oneway(*groups)
print(f"ANOVA: F={stat:.4f}, p-value={p_value:.4f}")

# Intervalle de confiance (bootstrap)
from scipy.stats import bootstrap
rng = np.random.default_rng()
data = (df['metric'].values,)
res = bootstrap(data, np.mean, confidence_level=0.95, random_state=rng)
print(f"IC 95% moyenne : [{res.confidence_interval.low:.2f}, {res.confidence_interval.high:.2f}]")

# Chi² test (indépendance 2 variables catégorielles)
contingency_table = pd.crosstab(df['cat1'], df['cat2'])
chi2, p_value, dof, expected = stats.chi2_contingency(contingency_table)
print(f"Chi²: χ²={chi2:.4f}, p-value={p_value:.4f}, dof={dof}")
```

**Pièges à éviter** :
- Utiliser t-test sans vérifier normalité (préférer Mann-Whitney si non-normal)
- Tester multiple hypothèses sans correction p-value (Bonferroni, Benjamini-Hochberg)
- Confondre significativité statistique (p < 0.05) et importance pratique (effect size faible peut être significatif avec grand n)


### 5. Détection et quantification biais statistiques

**Description** : Identifier biais dans échantillonnage, mesure et sélection ; quantifier déséquilibres.

**Techniques** :
- **Selection bias** : comparer distribution échantillon vs population (KS test)
- **Sampling bias** : analyser représentativité groupes démographiques (chi² goodness of fit)
- **Measurement bias** : analyser patterns valeurs manquantes (MCAR/MAR/MNAR), erreurs systématiques
- **Class imbalance** : calculer ratios classes, métriques déséquilibre (imbalance ratio, Gini coefficient)
- **Survivorship bias** : analyser données manquantes non-aléatoires (attrition, dropout)

**Livrables** :
- Rapport biais détectés avec type (selection/sampling/measurement) et quantification
- Comparaison distributions échantillon vs population attendue (si référence disponible)
- Analyse valeurs manquantes : pattern (MCAR/MAR/MNAR), % par groupe démographique
- Métriques déséquilibre classes (si classification) avec imbalance ratio
- Recommandations mitigation (resampling, reweighting, data augmentation)

**Exemple** :
```python
# Class imbalance
class_counts = df['target'].value_counts()
imbalance_ratio = class_counts.max() / class_counts.min()
print(f"Imbalance ratio: {imbalance_ratio:.2f} (> 3 = déséquilibré)")

# Sampling bias (test Chi² goodness of fit vs référence)
observed = df['demographic'].value_counts()
expected = pd.Series([0.6, 0.3, 0.1], index=observed.index) * len(df)  # Distribution attendue
chi2, p_value = stats.chisquare(observed, expected)
print(f"Chi² goodness of fit: χ²={chi2:.4f}, p-value={p_value:.4f}")
if p_value < 0.05:
    print("Distribution significativement différente de la référence (sampling bias)")

# Analyse valeurs manquantes par groupe
missing_by_group = df.groupby('demographic')['feature'].apply(lambda x: x.isnull().mean())
print("% valeurs manquantes par groupe :\n", missing_by_group)

# KS test (comparaison distribution échantillon vs population)
sample_dist = df['metric'].values
population_dist = np.random.normal(loc=50, scale=10, size=10000)  # Population référence
stat, p_value = stats.ks_2samp(sample_dist, population_dist)
print(f"KS test: D={stat:.4f}, p-value={p_value:.4f}")
```

**Pièges à éviter** :
- Ignorer patterns valeurs manquantes (MCAR/MAR/MNAR ont mitigation différentes)
- Ne pas documenter biais détectés dans données sensibles (risque fairness modèle)
- Appliquer mitigation biais sans validation impact (resampling peut introduire overfitting)

---

## Exemples d'utilisation

### Exemple 1 : EDA initiale dataset crédit

**Contexte** : Dataset 10 000 demandes crédit (approuvé/refusé), 20 features (age, revenu, dette, historique crédit, etc.).

**Objectif** : Identifier features prometteuses pour modèle classification, détecter problèmes données.

**Démarche** :
1. **Profiling** : ydata-profiling pour vue d'ensemble (distributions, corrélations, warnings)
2. **Statistiques descriptives** : mean/median/std par feature, identification outliers revenu (> 500k€)
3. **Distributions** : test normalité sur features numériques (revenu log-normal, age normale)
4. **Corrélations** : heatmap révèle forte corrélation dette/revenu (r=0.82, risque multicolinéarité)
5. **Biais** : class imbalance 70% approuvé / 30% refusé (imbalance ratio 2.3), acceptable
6. **Recommandations** : log-transform revenu, considérer ratio dette/revenu plutôt que 2 features séparées, surveiller fairness (age peut être proxy genre)

**Livrable** : Notebook EDA avec insights clés, recommandations features engineering, alertes biais


### Exemple 2 : A/B test comparaison 2 modèles ML

**Contexte** : Modèle A (baseline, accuracy 0.82) vs Modèle B (nouveau, accuracy 0.85) sur 5000 prédictions test.

**Objectif** : Valider statistiquement que Modèle B > Modèle A (pas juste variance aléatoire).

**Démarche** :
1. **Hypothèses** : H0 = accuracy A = accuracy B ; H1 = accuracy B > accuracy A
2. **Protocole** : 1000 bootstraps (rééchantillonnage avec remise), calcul accuracy chaque bootstrap
3. **Test** : comparaison distributions bootstrap (A vs B) avec test permutation
4. **Résultat** : p-value = 0.003 < 0.05 → différence significative
5. **Effect size** : différence absolue 3%, IC 95% [1.2%, 4.8%] → amélioration réelle
6. **Conclusion** : Modèle B significativement meilleur, déploiement recommandé

**Livrable** : Rapport A/B test avec p-value, effect size, IC, recommandation déploiement


### Exemple 3 : Diagnostic biais dataset recrutement

**Contexte** : Dataset 50 000 candidatures (embauché/rejeté), features incluent genre, âge, origine ethnique.

**Objectif** : Détecter biais statistiques avant entraînement modèle ML de screening.

**Démarche** :
1. **Class imbalance** : 20% embauchés / 80% rejetés (imbalance ratio 4.0, élevé)
2. **Sampling bias genre** : Chi² test vs population active (60% H / 40% F attendu) → p-value 0.001, sous-représentation femmes dans dataset
3. **Valeurs manquantes** : 15% CVs sans mention diplôme, concentration dans candidatures origine ethnique minoritaire (measurement bias)
4. **Corrélations** : âge corrélé négativement avec embauche (r=-0.3), proxy potentiel discrimination
5. **Recommandation** : augmenter collecte candidatures femmes, imputer diplômes avec soin, déléguer audit fairness à l'agent d'éthique des données avant modélisation

**Livrable** : Rapport biais détaillé avec quantification, recommandations mitigation, alerte risque discrimination

---

## Outils et librairies

**Python** :
- **Pandas** : manipulation données, statistiques descriptives
- **NumPy** : calculs numériques, statistiques
- **SciPy** : tests statistiques (stats module)
- **Statsmodels** : tests avancés, VIF, time series
- **ydata-profiling** (ex pandas-profiling) : profiling automatique datasets
- **Sweetviz** : EDA automatisé avec comparaison datasets
- **Matplotlib/Seaborn** : visualisations statistiques
- **Plotly** : visualisations interactives

**R** (si contexte R) :
- **dplyr** : manipulation données
- **ggplot2** : visualisations
- **car** : VIF, tests diagnostics
- **psych** : statistiques descriptives

---

## Checklist qualité EDA

Avant de finaliser une analyse exploratoire, vérifier :
- [ ] Profiling dataset réalisé (ydata-profiling ou équivalent)
- [ ] Statistiques descriptives calculées pour toutes features numériques
- [ ] Tests normalité effectués sur features clés
- [ ] Outliers détectés et analysés (origine, légitimité)
- [ ] Matrice corrélations générée avec heatmap
- [ ] Multicolinéarité vérifiée si modèle linéaire envisagé (VIF)
- [ ] Valeurs manquantes quantifiées (% par colonne, pattern MCAR/MAR/MNAR)
- [ ] Class imbalance quantifié si classification (imbalance ratio)
- [ ] Biais statistiques détectés et documentés (sampling, selection, measurement)
- [ ] Visualisations annotées avec insights clés
- [ ] Recommandations features engineering formulées
- [ ] Délégations nécessaires identifiées (l'agent de machine learning, l'agent d'éthique des données, etc.)

## Exemples d'usage

### Exemple 1 : Profiler un jeu de données de résiliation
**Contexte** : Avant d'entraîner un modèle de churn, l'équipe veut comprendre les données disponibles et éviter les fuites temporelles.  
**Input** : Extrait anonymisé avec date d'observation, cible, dictionnaire des variables et période de collecte.  
**Output** : Profil des distributions et valeurs manquantes, déséquilibre de classes, corrélations/valeurs aberrantes, risques de fuite et questions à valider avant le split temporel.

### Exemple 2 : Comprendre l'augmentation des erreurs sur une période
**Contexte** : Un modèle de prévision fonctionne moins bien sur les semaines récentes et l'équipe doit séparer dérive des données et variation aléatoire.  
**Input** : Résidus/prédictions, dates, valeurs observées, segments métier et version du modèle.  
**Output** : Comparaisons descriptives par période/segment, intervalles ou tests adaptés si justifiés, visualisations et limites d'interprétation, sans conclure à une causalité non testée.

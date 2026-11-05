# Data Visualization & ML Insights

## Objectif
Visualiser et interpréter les données et résultats de modèles ML, créer des dashboards analytiques et communiquer les constats avec leur contexte et leurs limites.

**Agents utilisateurs** : l'agent data science (principal), l'agent de stratégie produit, l'agent de machine learning

## Quand l'utiliser (triggers)
- Exploration visuelle datasets ML (distributions, relations, patterns)
- Interprétation résultats modèles ML (feature importance, SHAP, erreurs)
- Communication insights data à audiences techniques ou métier
- Création dashboards ML interactifs (monitoring modèles, analyses ad-hoc)

## Hors périmètre
- Design UI/UX applicatif → l'agent front-end
- Direction artistique/identité visuelle → l'agent de direction artistique
- Visualisation temps réel haute performance → Observability Engineer

---

## Inputs requis
- Question d'analyse, public cible et décision ou interprétation attendue.
- Dataset ou résultats de modèle, schéma, période et définitions des mesures.
- Type de modèle, métriques disponibles et segments d'intérêt.
- Outils autorisés et contraintes de confidentialité ou de performance.

## Sorties attendues
- Graphiques annotés avec unités, population, période et source.
- Analyse des tendances, erreurs ou contributions avec limites d'interprétation.
- Dashboard ou rapport adapté à l'audience si demandé.
- Recommandations de validation ou investigation complémentaire.

## Workflow recommandé
1. Clarifier la question et vérifier la qualité, la représentativité et les limites des données.
2. Choisir une visualisation adaptée au type de variable, de comparaison et d'audience.
3. Calculer les indicateurs et contrôler les agrégations avant visualisation.
4. Annoter les constats, incertitudes et limites; vérifier l'interprétation.
5. Livrer le visuel et la méthode de reproduction.

## Garde-fous
- Ne pas suggérer causalité ou importance causale à partir d'une simple association.
- Rendre visibles axes, unités, population, périodes et limites de l'échantillon.
- Protéger les données sensibles et éviter les visualisations trompeuses.
- Distinguer importance prédictive, explication locale et causalité.

## Template d'entrée (copier/coller)
```text
[Question/public] ...
[Données/résultats modèle] Source, schéma, période, volume : ...
[Métrique/segments à examiner] ...
[Outils et contraintes] ...
```

## Template de sortie (copier/coller)
```text
[Visualisation] Type, variables, unités, population et période : ...
[Constats] Résultats observés et incertitudes : ...
[Limites] Biais, représentativité et portée d'interprétation : ...
[Reproduction] Données, méthode et outil : ...
```

## KPI reliés
- Part des visualisations avec source, période, unités et population documentées.
- Nombre d'erreurs d'interprétation ou d'agrégation détectées avant diffusion.
- Délai de production et taux de réutilisation des dashboards, si mesurés.

## Definition of done
- Chaque visualisation répond à une question explicite et comporte le contexte nécessaire.
- Les calculs sont contrôlés et les limites d'interprétation sont documentées.
- Le résultat est lisible pour l'audience et reproductible avec les sources indiquées.

## Compétences

### 1. Visualisations exploratoires de datasets

**Description** : Créer visualisations pour comprendre distributions, relations, patterns dans données ML.

**Techniques** :
- **Distributions univariées** : histogrammes, boxplots, violin plots, density plots (KDE)
- **Relations bivariées** : scatter plots, hexbin plots, 2D density plots, regression plots
- **Relations multivariées** : pairplots (grilles scatter), parallel coordinates, heatmaps corrélations
- **Données catégorielles** : bar charts, count plots, stacked bars, mosaic plots
- **Séries temporelles** : line plots, area charts, rolling averages, seasonal decomposition

**Livrables** :
- Visualisations annotées distributions features clés (avec interprétation)
- Heatmap corrélations avec annotations paires fortement corrélées
- Pairplot features prometteuses vs target
- Visualisations outliers (boxplots avec seuils IQR marqués)
- Dashboard exploratoire interactif (Plotly/Streamlit) si demandé

**Exemple** :
```python
import matplotlib.pyplot as plt
import seaborn as sns
import plotly.express as px
import plotly.graph_objects as go

# Histogramme + KDE
plt.figure(figsize=(10, 6))
sns.histplot(df['feature'], kde=True, bins=30)
plt.title('Distribution de [Feature]')
plt.xlabel('[Feature]')
plt.ylabel('Fréquence')
plt.axvline(df['feature'].mean(), color='red', linestyle='--', label=f'Moyenne: {df["feature"].mean():.2f}')
plt.axvline(df['feature'].median(), color='green', linestyle='--', label=f'Médiane: {df["feature"].median():.2f}')
plt.legend()
plt.show()

# Boxplot par catégorie
plt.figure(figsize=(12, 6))
sns.boxplot(x='category', y='metric', data=df)
plt.title('Distribution [Metric] par catégorie')
plt.xticks(rotation=45)
plt.show()

# Heatmap corrélations annotée
corr = df.corr()
mask = np.triu(np.ones_like(corr, dtype=bool))  # Masque triangle supérieur
plt.figure(figsize=(12, 10))
sns.heatmap(corr, mask=mask, annot=True, fmt='.2f', cmap='coolwarm', center=0, 
            square=True, linewidths=1, cbar_kws={"shrink": 0.8})
plt.title('Matrice de corrélations')
plt.tight_layout()
plt.show()

# Pairplot features vs target (Seaborn)
sns.pairplot(df[['feature1', 'feature2', 'feature3', 'target']], hue='target', diag_kind='kde')
plt.suptitle('Pairplot features vs target', y=1.02)
plt.show()

# Scatter interactif (Plotly)
fig = px.scatter(df, x='feature1', y='feature2', color='target', 
                 hover_data=['feature3', 'feature4'],
                 title='Relation feature1 vs feature2')
fig.show()
```

**Pièges à éviter** :
- Trop de variables dans un pairplot (> 8 features = illisible)
- Échelles non normalisées masquant patterns (standardiser si nécessaire)
- Palette couleurs inappropriée (divergente pour données centrées, séquentielle pour positives)


### 2. Visualisations performance modèles ML

**Description** : Créer visualisations spécifiques ML (courbes ROC, PR, learning curves, confusion matrices).

**Techniques** :
- **Courbe ROC** : TPR vs FPR, AUC, seuil optimal marqué
- **Courbe Precision-Recall** : precision vs recall, area under curve, F1 optimal
- **Confusion matrix** : heatmap TP/TN/FP/FN, annotations pourcentages
- **Learning curves** : train/validation loss ou métrique vs epochs ou taille dataset
- **Calibration curves** : probabilités prédites vs fréquences observées (bien calibré = diagonale)
- **Residual plots** (régression) : erreurs vs valeurs prédites, Q-Q plot normalité résidus

**Livrables** :
- Courbe ROC avec AUC et seuil optimal marqué
- Confusion matrix annotée avec précision/recall par classe
- Learning curves diagnostiquant overfitting/underfitting
- Calibration curve (si probabilités utilisées)
- Residual plots (si régression) avec diagnostic

**Exemple** :
```python
from sklearn.metrics import roc_curve, auc, precision_recall_curve, confusion_matrix, ConfusionMatrixDisplay
import matplotlib.pyplot as plt
import seaborn as sns

# Courbe ROC
y_proba = model.predict_proba(X_test)[:, 1]
fpr, tpr, thresholds = roc_curve(y_true, y_proba)
roc_auc = auc(fpr, tpr)

plt.figure(figsize=(8, 6))
plt.plot(fpr, tpr, label=f'ROC curve (AUC = {roc_auc:.3f})', linewidth=2)
plt.plot([0, 1], [0, 1], 'k--', label='Random (AUC = 0.5)')
plt.xlabel('False Positive Rate', fontsize=12)
plt.ylabel('True Positive Rate', fontsize=12)
plt.title('Receiver Operating Characteristic (ROC) Curve', fontsize=14)
plt.legend(fontsize=11)
plt.grid(alpha=0.3)

# Marquer seuil optimal (Youden's J)
optimal_idx = np.argmax(tpr - fpr)
optimal_threshold = thresholds[optimal_idx]
plt.scatter(fpr[optimal_idx], tpr[optimal_idx], marker='o', color='red', s=100, 
            label=f'Optimal threshold = {optimal_threshold:.3f}')
plt.legend()
plt.show()

# Courbe Precision-Recall
precision, recall, thresholds_pr = precision_recall_curve(y_true, y_proba)
plt.figure(figsize=(8, 6))
plt.plot(recall, precision, linewidth=2)
plt.xlabel('Recall', fontsize=12)
plt.ylabel('Precision', fontsize=12)
plt.title('Precision-Recall Curve', fontsize=14)
plt.grid(alpha=0.3)
plt.show()

# Confusion matrix heatmap
cm = confusion_matrix(y_true, y_pred)
plt.figure(figsize=(8, 6))
sns.heatmap(cm, annot=True, fmt='d', cmap='Blues', cbar=True,
            xticklabels=['Classe 0', 'Classe 1'],
            yticklabels=['Classe 0', 'Classe 1'])
plt.ylabel('True label', fontsize=12)
plt.xlabel('Predicted label', fontsize=12)
plt.title('Confusion Matrix', fontsize=14)
plt.tight_layout()
plt.show()

# Learning curves
from sklearn.model_selection import learning_curve
train_sizes, train_scores, val_scores = learning_curve(
    model, X, y, cv=5, train_sizes=np.linspace(0.1, 1.0, 10), scoring='accuracy'
)

plt.figure(figsize=(10, 6))
plt.plot(train_sizes, train_scores.mean(axis=1), label='Training score', linewidth=2)
plt.fill_between(train_sizes, train_scores.mean(axis=1) - train_scores.std(axis=1),
                 train_scores.mean(axis=1) + train_scores.std(axis=1), alpha=0.2)
plt.plot(train_sizes, val_scores.mean(axis=1), label='Validation score', linewidth=2)
plt.fill_between(train_sizes, val_scores.mean(axis=1) - val_scores.std(axis=1),
                 val_scores.mean(axis=1) + val_scores.std(axis=1), alpha=0.2)
plt.xlabel('Training set size', fontsize=12)
plt.ylabel('Accuracy', fontsize=12)
plt.title('Learning Curves', fontsize=14)
plt.legend(fontsize=11)
plt.grid(alpha=0.3)
plt.show()
```

**Pièges à éviter** :
- Confusion matrix sans normalisation (chiffres bruts peu informatifs si classes déséquilibrées)
- Learning curves sur 1 seul fold (variance non visible, utiliser CV)
- Courbe ROC sans marquer seuil optimal (difficile de choisir seuil ensuite)


### 3. Interprétabilité modèles : feature importance et SHAP

**Description** : Visualiser contribution features aux prédictions ML, interpréter modèles boîtes noires.

**Techniques** :
- **Feature importance** : importances intrinsèques (tree-based models), permutation importance (model-agnostic)
- **SHAP (SHapley Additive exPlanations)** : valeurs SHAP par feature/prédiction, summary plots, dependence plots, force plots
- **LIME (Local Interpretable Model-agnostic Explanations)** : explications locales (1 prédiction)
- **Partial Dependence Plots (PDP)** : effet marginal d'une feature sur prédictions
- **Individual Conditional Expectation (ICE)** : PDP par instance

**Livrables** :
- Bar chart feature importance (top 10-20 features)
- SHAP summary plot (impact global features + distributions valeurs SHAP)
- SHAP dependence plot features clés (relation feature-prédiction)
- SHAP force plot prédiction individuelle (explication locale)
- Partial dependence plots features critiques

**Exemple** :
```python
import shap
import matplotlib.pyplot as plt

# Feature importance (Random Forest/XGBoost)
feature_importance = model.feature_importances_
feature_names = X_train.columns
indices = np.argsort(feature_importance)[::-1][:20]  # Top 20

plt.figure(figsize=(10, 8))
plt.barh(range(len(indices)), feature_importance[indices], align='center')
plt.yticks(range(len(indices)), [feature_names[i] for i in indices])
plt.xlabel('Feature Importance', fontsize=12)
plt.title('Top 20 Feature Importances', fontsize=14)
plt.gca().invert_yaxis()
plt.tight_layout()
plt.show()

# SHAP values (explainer adapté au modèle)
explainer = shap.TreeExplainer(model)  # Pour tree-based (XGBoost, RF, etc.)
shap_values = explainer.shap_values(X_test)

# SHAP summary plot (impact global + distributions)
shap.summary_plot(shap_values, X_test, feature_names=feature_names, show=False)
plt.title('SHAP Summary Plot', fontsize=14)
plt.tight_layout()
plt.show()

# SHAP dependence plot (relation feature-prédiction)
shap.dependence_plot("feature_name", shap_values, X_test, feature_names=feature_names, show=False)
plt.title('SHAP Dependence Plot - [Feature Name]', fontsize=14)
plt.tight_layout()
plt.show()

# SHAP force plot (explication 1 prédiction)
i = 0  # Index prédiction à expliquer
shap.force_plot(explainer.expected_value, shap_values[i], X_test.iloc[i], 
                feature_names=feature_names, matplotlib=True, show=False)
plt.title(f'SHAP Force Plot - Prédiction {i}', fontsize=14)
plt.tight_layout()
plt.show()

# Permutation importance (model-agnostic)
from sklearn.inspection import permutation_importance
perm_importance = permutation_importance(model, X_test, y_test, n_repeats=10, random_state=42)
sorted_idx = perm_importance.importances_mean.argsort()[::-1][:20]

plt.figure(figsize=(10, 8))
plt.barh(range(len(sorted_idx)), perm_importance.importances_mean[sorted_idx])
plt.yticks(range(len(sorted_idx)), X_test.columns[sorted_idx])
plt.xlabel('Permutation Importance', fontsize=12)
plt.title('Top 20 Permutation Importances', fontsize=14)
plt.gca().invert_yaxis()
plt.tight_layout()
plt.show()
```

**Pièges à éviter** :
- Confondre feature importance intrinsèque (biaisée vers features haute cardinalité) et permutation (plus robuste)
- SHAP sur gros datasets sans échantillonnage (très lent, échantillonner 1000-5000 lignes)
- Interpréter SHAP values sans contexte métier (valeur SHAP élevée ≠ toujours actionnable)


### 4. Dashboards interactifs ML (Streamlit, Plotly Dash)

**Description** : Créer applications web interactives pour exploration données ML, monitoring modèles, analyses ad-hoc.

**Techniques** :
- **Streamlit** : framework Python simple, widgets interactifs, mise en page rapide
- **Plotly Dash** : framework Python/React, dashboards production-ready, callbacks
- **Widgets** : sliders, dropdowns, checkboxes, date pickers, file uploaders
- **Graphiques interactifs** : Plotly (zoom, pan, hover, click events)
- **Déploiement** : Streamlit Cloud, Heroku, Docker, cloud providers

**Livrables** :
- Application Streamlit/Dash déployée avec URL accessible
- Code source dashboard (reproductible, commenté)
- Documentation utilisation dashboard (guide utilisateur)
- Widgets interactifs pertinents (filtres, sélection features, seuil décision)
- Graphiques actualisés dynamiquement selon inputs utilisateur

**Exemple Streamlit** :
```python
# app.py
import streamlit as st
import pandas as pd
import plotly.express as px
from sklearn.ensemble import RandomForestClassifier
import joblib

st.set_page_config(page_title="ML Dashboard", layout="wide")
st.title("🤖 Machine Learning Dashboard")

# Sidebar - Paramètres
st.sidebar.header("Paramètres")
uploaded_file = st.sidebar.file_uploader("Upload dataset CSV", type=['csv'])
threshold = st.sidebar.slider("Seuil de décision", 0.0, 1.0, 0.5, 0.01)

# Load dataset
if uploaded_file is not None:
    df = pd.read_csv(uploaded_file)
    
    # Aperçu données
    st.header("📊 Aperçu dataset")
    col1, col2, col3 = st.columns(3)
    with col1:
        st.metric("Lignes", df.shape[0])
    with col2:
        st.metric("Colonnes", df.shape[1])
    with col3:
        st.metric("Valeurs manquantes", df.isnull().sum().sum())
    
    st.dataframe(df.head(10))
    
    # Sélection features à visualiser
    st.header("🔍 Exploration visuelle")
    numeric_cols = df.select_dtypes(include='number').columns.tolist()
    x_col = st.selectbox("Feature X", numeric_cols, index=0)
    y_col = st.selectbox("Feature Y", numeric_cols, index=1)
    color_col = st.selectbox("Couleur par", df.columns.tolist(), index=len(df.columns)-1)
    
    # Scatter plot interactif
    fig = px.scatter(df, x=x_col, y=y_col, color=color_col, 
                     hover_data=numeric_cols[:5],
                     title=f"{x_col} vs {y_col}")
    st.plotly_chart(fig, use_container_width=True)
    
    # Distributions
    st.header("📈 Distributions")
    selected_feature = st.selectbox("Feature à analyser", numeric_cols)
    fig_hist = px.histogram(df, x=selected_feature, nbins=30, 
                            title=f"Distribution {selected_feature}")
    st.plotly_chart(fig_hist, use_container_width=True)
    
    # Prédictions (si modèle uploadé)
    st.header("🎯 Prédictions")
    if st.sidebar.button("Charger modèle"):
        model = joblib.load('model.pkl')  # Pré-entrainé
        X = df[numeric_cols[:-1]]
        y_proba = model.predict_proba(X)[:, 1]
        y_pred = (y_proba >= threshold).astype(int)
        
        df['Probabilité'] = y_proba
        df['Prédiction'] = y_pred
        
        st.metric("Prédictions positives", (y_pred == 1).sum())
        st.dataframe(df[['Probabilité', 'Prédiction']].head(20))

# Run: streamlit run app.py
```

**Exemple Plotly Dash** :
```python
# app_dash.py
import dash
from dash import dcc, html, Input, Output
import plotly.express as px
import pandas as pd

app = dash.Dash(__name__)

df = pd.read_csv('data.csv')

app.layout = html.Div([
    html.H1("ML Dashboard", style={'textAlign': 'center'}),
    
    dcc.Dropdown(
        id='feature-dropdown',
        options=[{'label': col, 'value': col} for col in df.columns],
        value=df.columns[0],
        style={'width': '50%'}
    ),
    
    dcc.Graph(id='distribution-graph'),
    
    dcc.Slider(
        id='threshold-slider',
        min=0, max=1, step=0.01, value=0.5,
        marks={i/10: str(i/10) for i in range(11)}
    ),
    
    html.Div(id='metrics-output')
])

@app.callback(
    Output('distribution-graph', 'figure'),
    Input('feature-dropdown', 'value')
)
def update_graph(selected_feature):
    fig = px.histogram(df, x=selected_feature, nbins=30)
    return fig

@app.callback(
    Output('metrics-output', 'children'),
    Input('threshold-slider', 'value')
)
def update_metrics(threshold):
    # Calculs basés sur threshold
    return f"Seuil: {threshold}"

if __name__ == '__main__':
    app.run_server(debug=True)
```

**Pièges à éviter** :
- Dashboard trop complexe (trop de widgets/graphiques = confusion utilisateur)
- Pas de caching données (rechargement à chaque interaction = lent, utiliser @st.cache)
- Déploiement sans authentification (données sensibles exposées publiquement)


### 5. Storytelling data et communication visuelle

**Description** : Créer narratifs visuels convaincants, annoter graphiques pour guider interprétation, adapter style au public.

**Techniques** :
- **Structure narratif** : Problem-Data-Insight-Action (PDIA), progression logique
- **Annotations** : titres clairs, légendes explicites, highlights insights clés, callout boxes
- **Principes design** : couleurs intentionnelles (divergent vs séquentiel), ratio signal/bruit élevé, hiérarchie visuelle
- **Adaptation public** : technique (détails méthodologiques) vs métier (insights seuls) vs exécutif (1 slide 1 message)
- **Format** : notebooks (analyse technique), slides (présentation métier), dashboards (exploration interactive)

**Livrables** :
- Visualisations annotées avec insights clés mis en évidence
- Narrative clair liant visualisations (progression logique Problem→Insight→Action)
- Style visuel adapté au public cible (densité info, jargon, couleurs)
- Slides/rapport avec 1 message clé par visualisation
- Dashboard exploratoire si analyses ad-hoc fréquentes

**Principes de design** :
- **Couleurs** :
  - Divergent (bleu-rouge) : données centrées (corrélations, différences)
  - Séquentiel (dégradé unique) : données positives (probabilités, counts)
  - Qualitatif (distinct) : catégories (classes, groupes)
  - Accessibilité : éviter rouge-vert seul (daltonisme), utiliser textures/shapes complémentaires

- **Signal/bruit** :
  - Maximiser data-ink ratio (Tufte) : enlever grilles superflues, bordures, décorations
  - Highlights intentionnels : couleur/gras sur insights clés uniquement
  - Whitespace : ne pas saturer, laisser respirer

- **Annotations** :
  - Titres informatifs : "Revenu corrélé positivement avec approbation crédit (r=0.65)" vs "Scatter plot"
  - Axes clairs : unités, échelle, transformations (log)
  - Légende auto-suffisante : graphique compréhensible sans texte externe

**Exemple annotations** :
```python
import matplotlib.pyplot as plt
import numpy as np

# Graphique sans annotations (mauvais)
plt.plot(x, y)
plt.show()

# Graphique avec annotations (bon)
fig, ax = plt.subplots(figsize=(10, 6))
ax.plot(x, y, linewidth=2, color='steelblue', label='Série observée')

# Titre informatif
ax.set_title('Chiffre d\'affaires mensuel : tendance haussière (+15% YoY)', 
             fontsize=14, fontweight='bold')

# Axes clairs
ax.set_xlabel('Mois', fontsize=12)
ax.set_ylabel('Chiffre d\'affaires (M€)', fontsize=12)

# Highlight insight clé
peak_idx = np.argmax(y)
ax.scatter(x[peak_idx], y[peak_idx], s=200, color='red', zorder=5)
ax.annotate(f'Pic: {y[peak_idx]:.1f}M€\n(Décembre)', 
            xy=(x[peak_idx], y[peak_idx]), xytext=(x[peak_idx]-2, y[peak_idx]+1),
            arrowprops=dict(arrowstyle='->', color='red', lw=2),
            fontsize=11, fontweight='bold', color='red')

# Ligne moyenne
mean_val = np.mean(y)
ax.axhline(mean_val, color='gray', linestyle='--', linewidth=1, alpha=0.7, 
           label=f'Moyenne: {mean_val:.1f}M€')

ax.legend(fontsize=10)
ax.grid(alpha=0.3)
plt.tight_layout()
plt.show()
```

**Pièges à éviter** :
- Graphiques bruts sans titre/annotations (utilisateur doit deviner le message)
- Trop d'informations sur 1 graphique (split en plusieurs graphiques ciblés)
- Couleurs non intentionnelles (arc-en-ciel sans signification)
- Échelles trompeuses (y-axis ne commençant pas à 0 pour bar charts)

---

## Exemples d'utilisation

### Exemple 1 : Dashboard monitoring modèle crédit

**Contexte** : Modèle crédit en production, besoin monitoring performance hebdomadaire (drift, fairness, métriques).

**Objectif** : Dashboard Streamlit interactif pour analyser performance et détecter dégradations.

**Composants** :
1. **KPIs** : accuracy, precision, recall, AUC (évolution 12 dernières semaines)
2. **Drift détection** : distributions features clés (semaine courante vs baseline)
3. **Fairness** : approval rate par groupe démographique (genre, âge)
4. **Confusion matrix** : heatmap TP/TN/FP/FN hebdomadaire
5. **Filters** : sélection période, segment clients, seuil décision

**Livrable** : App Streamlit déployée, mise à jour automatique chaque lundi

### Exemple 2 : Rapport exécutif avec storytelling

**Contexte** : Présentation résultats modèle churn à C-level, 10 slides max.

**Objectif** : Convaincre de déployer modèle avec ROI clair.

**Structure** :
1. **Problème** : 25% churn annuel = 5M€ pertes (1 slide, bar chart tendance churn)
2. **Solution** : Modèle ML prédictif, 100k clients historique (1 slide, schéma simple)
3. **Performance** : Recall 78%, détecte 78% clients à risque (1 slide, confusion matrix annotée)
4. **Impact** : Intervention ciblée 22% clients → rétention 40% → économie 2M€/an (1 slide, cascade chart ROI)
5. **Recommandation** : Pilote 3 mois → déploiement complet (1 slide, timeline)

**Chaque slide** : 1 graphique + 1 message clé en gras + 2-3 bullets max

### Exemple 3 : Notebook EDA technique pour data team

**Contexte** : Dataset NLP 50k documents, préparer rapport EDA complet pour équipe data.

**Objectif** : Analyse approfondie avec méthodologie statistique, code reproductible.

**Sections notebook** :
1. **Overview** : shape, types, valeurs manquantes, profiling automatique (ydata-profiling)
2. **Distributions** : histogrammes longueurs textes, distributions langues, top mots
3. **Statistiques** : mean/median/std longueurs, tests normalité, outliers détectés
4. **Visualisations** : word clouds top features, heatmap corrélations features numériques, pairplot
5. **Insights** : 7 insights clés avec métriques, recommandations features engineering
6. **Code** : tout reproductible, commenté, requirements.txt fourni

**Livrable** : Notebook Jupyter (.ipynb) + rapport HTML exporté

---

## Outils et librairies

**Python** :
- **Matplotlib** : visualisations statiques publication-ready
- **Seaborn** : visualisations statistiques haut niveau (heatmaps, pairplots)
- **Plotly** : graphiques interactifs (hover, zoom, pan)
- **Altair** : visualisations déclaratives (grammar of graphics)
- **Bokeh** : visualisations interactives serveur (dashboards)
- **Streamlit** : applications ML interactives rapides
- **Dash (Plotly)** : dashboards production-ready
- **SHAP** : interprétabilité modèles (SHAP values)
- **Yellowbrick** : visualisations ML spécialisées (learning curves, feature importance)

**Notebooks** :
- **Jupyter** : notebooks interactifs Python/R
- **Google Colab** : notebooks cloud gratuits (GPU)
- **Deepnote** : notebooks collaboratifs

---

## Checklist qualité visualisation

Avant de finaliser une visualisation, vérifier :
- [ ] Titre informatif (message clé, pas juste "Graph")
- [ ] Axes clairs (labels, unités, échelle explicite)
- [ ] Légende auto-suffisante (graphique compréhensible seul)
- [ ] Couleurs intentionnelles (sémantique, accessibilité)
- [ ] Annotations insights clés (highlights, callouts)
- [ ] Ratio signal/bruit élevé (pas de grilles/bordures superflues)
- [ ] Échelles non trompeuses (y-axis à 0 pour bar charts)
- [ ] Adaptation public cible (densité info, jargon)
- [ ] Code reproductible si technique (commenté, dépendances claires)
- [ ] Format exportable approprié (PNG/PDF/HTML/dashboard)

## Exemples d'usage

### Exemple 1 : Examiner les faux négatifs d'un modèle de détection
**Contexte** : Une équipe cherche à comprendre pourquoi des cas positifs ne sont pas détectés avant d'ajuster le seuil du modèle.  
**Input** : Prédictions et vérités terrain sur un jeu de test documenté, classes et segments pertinents, métriques métier et contraintes de confidentialité.  
**Output** : Matrice de confusion annotée, rappel/précision par segment, visualisation des seuils et interprétation des erreurs avec limites d'échantillon.

### Exemple 2 : Détecter un changement de distribution après déploiement
**Contexte** : Les performances d'un modèle diminuent après une modification du processus de saisie.  
**Input** : Distributions de référence et récentes, dates de déploiement, variables autorisées, résultats étiquetés disponibles et audience.  
**Output** : Visualisations comparatives des distributions et métriques, segments affectés, hypothèses de dérive à vérifier et recommandations de surveillance.

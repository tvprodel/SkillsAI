# Skill: AI Explainability & Transparency

## Objectif
Rendre les systèmes d'intelligence artificielle transparents et explicables au moyen d'audits d'opacité, de techniques XAI, de documentation des décisions algorithmiques et de communication adaptée aux non-experts.

## Agents principaux
- L'agent d'éthique des données
- L'agent spécialiste en IA générative
- L'agent de machine learning
- L'agent de documentation de code

## Quand l'utiliser (triggers)
- Évaluer l'opacité ou l'explicabilité d'un système IA.
- Choisir ou interpréter des méthodes XAI (SHAP, LIME, contrefactuels).
- Documenter des décisions algorithmiques ou expliquer des résultats à des personnes concernées.

## Hors périmètre
- L'analyse XAI ne constitue pas à elle seule une preuve de causalité, d'équité ou de conformité.
- La conception ou l'entraînement du modèle relève de l'agent de machine learning.
- Les avis juridiques individualisés relèvent de professionnels compétents; coordonner les exigences réglementaires avec l'agent de conformité RGPD.

## Inputs requis
- Description du système, cas d'usage, utilisateurs et décision concernée.
- Modèle, données, variables, métriques et versions disponibles.
- Explication recherchée (globale, locale, contrefactuelle) et audience cible.
- Contraintes de confidentialité, de performance et d'accès.

## Sorties attendues
- Évaluation du niveau d'opacité et des limites de transparence.
- Méthode d'explicabilité choisie avec justification et limites.
- Rapport d'explications lisible par l'audience, incluant exemples et incertitudes.
- Recommandations de documentation, supervision ou amélioration.

## Workflow recommandé
1. Cadrer la décision à expliquer, l'audience et le niveau de risque.
2. Documenter le modèle, les données et le contexte d'inférence.
3. Choisir une méthode adaptée et vérifier sa fidélité et sa stabilité.
4. Tester les explications sur des cas représentatifs et des segments pertinents.
5. Communiquer résultats, limites, risques de mauvaise interprétation et actions.

## Garde-fous
- Ne pas assimiler contribution d'une feature ou poids d'attention à une cause.
- Vérifier fidélité, stabilité et représentativité des explications produites.
- Signaler les limites des approximations post-hoc et éviter toute garantie d'explicabilité absolue.
- Protéger les données sensibles dans les explications locales et exemples publiés.

## Template d'entrée (copier/coller)
```text
[Système et décision à expliquer] ...
[Modèle/données/version] ...
[Audience et type d'explication attendu] Globale / locale / contrefactuelle : ...
[Contraintes] Confidentialité, latence, format : ...
```

## Template de sortie (copier/coller)
```text
[Niveau d'opacité et justification] ...
[Méthode XAI] Choix, fidélité, stabilité et limites : ...
[Explications] Constats adaptés à l'audience : ...
[Actions et risques de mauvaise interprétation] ...
```

## Checklist QA interne
- La méthode correspond-elle à la question, au modèle et à l'audience?
- Les explications sont-elles évaluées pour fidélité et stabilité?
- Les limites et incertitudes sont-elles visibles?
- Les exemples préservent-ils la confidentialité?

## KPI reliés
- Part des systèmes concernés disposant d'une documentation d'explicabilité à jour.
- Fidélité et stabilité observées des explications sur le protocole retenu.
- Taux de compréhension ou d'utilisation des explications, si évalué auprès des audiences.

## Definition of done
- La décision, le modèle, les données et l'audience sont explicités.
- La méthode retenue est justifiée, testée et accompagnée de limites.
- Les résultats et recommandations sont documentés de manière compréhensible.

## Compétences détaillées

### 1. Audit de niveau d'opacité
**Objectif** : Évaluer le degré de transparence d'un système IA selon une taxonomie standardisée.

**Niveaux d'opacité** :

#### Niveau 1 : Transparent (Glass Box)
- **Caractéristiques** : modèle intrinsèquement interprétable (régression linéaire, arbre de décision peu profond, règles if-then)
- **Explicabilité** : directe, lecture coefficients/règles suffit
- **Exemples** : Régression logistique, Decision tree (max_depth ≤ 5), Rule-based system
- **Exigences doc** : équation modèle + coefficients + intervalles confiance

#### Niveau 2 : Semi-transparent (Grey Box)
- **Caractéristiques** : modèle complexe mais avec mécanismes d'attention/interprétabilité intégrés
- **Explicabilité** : partielle, nécessite outils XAI pour détails
- **Exemples** : Random Forest + feature importance, Neural network + attention weights, GAM (Generalized Additive Models)
- **Exigences doc** : architecture modèle + feature importance + exemples prédictions annotées

#### Niveau 3 : Opaque (Black Box)
- **Caractéristiques** : modèle complexe sans mécanisme d'interprétabilité natif
- **Explicabilité** : nécessite techniques post-hoc (LIME, SHAP, counterfactuals)
- **Exemples** : Deep Neural Networks, Gradient Boosting (XGBoost, LightGBM), Ensembles complexes
- **Exigences doc** : architecture + métriques globales + explications locales échantillon représentatif

**Livrables** :
- Classification niveau opacité du système
- Recommandations amélioration transparence
- Roadmap migration vers modèle plus interprétable (si applicable)

**Exemple** :
```markdown
## Audit Opacité : Système Détection Fraude Bancaire

### Classification
- **Niveau opacité** : Niveau 3 - Opaque (Black Box)
- **Modèle** : Ensemble de 5 XGBoost + 3 Neural Networks
- **Justification** : 
  - Complexité élevée (150+ features, interactions non-linéaires)
  - Pas d'attention mechanism natif
  - Prédictions non traçables sans outils externes

### Recommandations
1. **Court terme** : Implémenter SHAP pour explications locales
2. **Moyen terme** : Ajouter modèle de substitution (surrogate) linéaire pour validation
3. **Long terme** : Explorer migration vers Explainable Boosting Machine (EBM) si performance acceptable
```


### 2. Techniques XAI (Explainable AI)
**Objectif** : Appliquer méthodes d'explicabilité post-hoc pour auditer boîtes noires.

#### LIME (Local Interpretable Model-agnostic Explanations)
**Principe** : Approximer localement modèle complexe par modèle linéaire interprétable.

**Quand utiliser** :
- Expliquer prédiction individuelle spécifique
- Modèle tabular, texte ou image
- Besoin d'explication compréhensible par humain

**Implémentation** :
```python
import lime
import lime.lime_tabular

# Créer explainer LIME
explainer = lime.lime_tabular.LimeTabularExplainer(
    X_train.values,
    feature_names=feature_names,
    class_names=['Refus', 'Approbation'],
    mode='classification'
)

# Expliquer prédiction individuelle
exp = explainer.explain_instance(
    X_test.values[0],
    model.predict_proba,
    num_features=10
)
exp.show_in_notebook()
```

**Sortie** :
```
Prédiction : Approbation (probabilité = 0.87)

Features importantes :
  Revenu annuel = 75000 EUR  →  +0.35 (favorise approbation)
  Historique crédit = Bon     →  +0.28
  Taux endettement = 25%      →  -0.12 (défavorise)
  Ancienneté emploi = 5 ans   →  +0.08
```

**Limites** :
- Instabilité explications si modèle très non-linéaire
- Difficile de définir "voisinage" pertinent pour données hétérogènes


#### SHAP (SHapley Additive exPlanations)
**Principe** : Utiliser valeurs de Shapley (théorie des jeux) pour attribuer contribution de chaque feature.

**Quand utiliser** :
- Expliquer globalement ou localement
- Garanties théoriques de cohérence (axiomes Shapley)
- Besoin de feature importance robuste

**Implémentation** :
```python
import shap

# TreeExplainer pour tree-based models (rapide)
explainer = shap.TreeExplainer(model)
shap_values = explainer.shap_values(X_test)

# Visualiser feature importance globale
shap.summary_plot(shap_values, X_test, feature_names=feature_names)

# Visualiser explication locale (waterfall plot)
shap.waterfall_plot(shap.Explanation(
    values=shap_values[0],
    base_values=explainer.expected_value,
    data=X_test.iloc[0],
    feature_names=feature_names
))
```

**Sortie** :
```
Base value (prédiction moyenne) : 0.52
Feature contributions :
  Revenu annuel                 +0.18
  Historique crédit             +0.12
  Taux endettement              -0.09
  Ancienneté emploi             +0.04
  ...
  = Prédiction finale            0.87
```

**Limites** :
- Coûteux computationnellement pour gros datasets
- Suppose indépendance features (problématique si multicolinéarité forte)


#### Counterfactual Explanations
**Principe** : "Quelle modification minimale des features changerait la prédiction ?"

**Quand utiliser** :
- Expliquer décision négative (refus crédit, rejet candidature)
- Guider utilisateur vers actions correctrices
- Contexte réglementaire (droit à explication RGPD)

**Implémentation** :
```python
from dice_ml import Data, Model, Dice

# Préparer DiCE (Diverse Counterfactual Explanations)
d = Data(dataframe=df, continuous_features=cont_features, outcome_name='decision')
m = Model(model=model, backend='sklearn')
dice = Dice(d, m)

# Générer counterfactuals
cf = dice.generate_counterfactuals(
    query_instance=X_test.iloc[0],
    total_CFs=3,
    desired_class='opposite'
)
cf.visualize_as_dataframe()
```

**Sortie** :
```
Instance actuelle : Refus crédit
  Revenu = 35000 EUR, Historique = Moyen, Endettement = 45%

Counterfactuals (3 scénarios pour obtenir approbation) :
  CF1 : Revenu = 45000 EUR (↑10k), Endettement = 35% (↓10%)
  CF2 : Historique = Bon, Endettement = 30% (↓15%)
  CF3 : Revenu = 50000 EUR (↑15k)
```

**Limites** :
- Peut suggérer changements irréalistes (ex: changer âge)
- Suppose features modifiables par utilisateur (pas toujours vrai)


### 3. Explications pour LLMs
**Objectif** : Techniques spécifiques pour expliquer comportement de grands modèles de langage.

#### Attention Visualization
**Principe** : Visualiser poids d'attention pour comprendre quels tokens influencent génération.

**Outils** :
- [BertViz](https://github.com/jessevig/bertviz) : visualisation attention Transformers
- [Ecco](https://github.com/jalammar/ecco) : exploration interne LLMs

**Exemple** :
```python
from bertviz import head_view

# Visualiser attention heads
head_view(attention, tokens)
```

#### Prompt Probing
**Principe** : Tester sensibilité LLM à variations de prompt pour déduire logique interne.

**Techniques** :
- **Ablation prompts** : retirer parties du prompt et mesurer impact
- **Contrast sets** : paires minimales (changement 1 mot) pour isoler effet
- **Chain-of-thought elicitation** : forcer LLM à expliciter raisonnement

**Exemple** :
```markdown
Prompt original : "Résume cet article en 3 phrases."
  → Sortie : [Résumé A]

Prompt sans contexte : "Résume en 3 phrases."
  → Sortie : [Résumé B]
  → Impact contexte : Δ = 40% différence sémantique

Prompt avec CoT : "Résume cet article en 3 phrases. Explique d'abord les points clés."
  → Sortie : [Raisonnement explicite] + [Résumé C]
  → Explicabilité améliorée
```

#### Model Behavior Analysis
**Principe** : Analyser patterns de comportement LLM sur datasets de test.

**Métriques** :
- **Toxicity score** : fréquence générations toxiques par catégorie prompt
- **Bias probing** : disparité réponses selon attributs sensibles dans prompt
- **Consistency testing** : variance réponses sur prompts sémantiquement équivalents

**Livrables** :
- Rapport audit LLM avec scores toxicité/biais
- Exemples générations problématiques annotées
- Recommandations guardrails


### 4. Documentation transparence (Model Cards & Datasheets)
**Objectif** : Standardiser documentation pour assurer transparence système IA.

#### Model Card (template complet)
```markdown
# Model Card : [Nom Modèle]

## Détails du modèle
- **Nom** : [Nom/Version]
- **Développeur** : [Organisation]
- **Date** : [YYYY-MM-DD]
- **Type** : [Classification/Régression/Génératif/...]
- **Informations contact** : [Email/URL]

## Usage prévu
- **Cas d'usage primaire** : [Description]
- **Cas d'usage hors périmètre** : [Usages déconseillés]
- **Utilisateurs cibles** : [Profils]

## Facteurs
- **Groupes** : [Démographiques/géographiques évalués]
- **Instrumentation** : [Capteurs/données collectées]
- **Environnement** : [Conditions déploiement]

## Métriques
- **Métriques performance** : Accuracy=0.92, F1=0.89, AUC=0.95
- **Seuils décision** : Seuil=0.5 (optimisé recall)
- **Approches variation** : [Métriques par sous-groupe]

## Données d'entraînement
- **Datasets** : [Nom(s), version(s), lien(s)]
- **Prétraitement** : [Nettoyage, normalisation, augmentation]
- **Biais connus** : [Limitations représentativité]

## Données d'évaluation
- **Datasets** : [Nom(s), version(s)]
- **Différences avec entraînement** : [Temporelles, géographiques...]
- **Prétraitement** : [Idem entraînement ou adapté]

## Considérations éthiques
- **Données sensibles** : [Données personnelles, consentement]
- **Impact humain** : [Risques, populations vulnérables]
- **Cas limites** : [Scénarios défaillance connue]

## Avertissements et recommandations
- **Supervision humaine** : [Obligatoire/recommandée/optionnelle]
- **Fréquence revalidation** : [Mensuelle/trimestrielle/annuelle]
- **Limitations techniques** : [Performance dégradée si...]
```

#### Datasheet for Datasets (template)
```markdown
# Datasheet : [Nom Dataset]

## Motivation
- **Pourquoi créé** : [Objectif]
- **Créateur** : [Organisation/individu]
- **Financement** : [Source]

## Composition
- **Instances** : [Type données : images/texte/tabular/...]
- **Nombre** : [Total instances]
- **Données manquantes** : [% et raison]
- **Données confidentielles** : [Oui/Non, type]

## Collecte
- **Processus** : [Scraping/enquêtes/capteurs/...]
- **Période** : [Dates début-fin]
- **Source** : [URLs, APIs, partenaires]
- **Consentement** : [RGPD-compliant, opt-in/opt-out]

## Prétraitement
- **Nettoyage** : [Déduplication, outliers, ...]
- **Labellisation** : [Manuelle/automatique, QC]
- **Transformations** : [Normalisation, encoding, ...]

## Usages
- **Tâches** : [Déjà utilisé pour quoi]
- **Repository** : [Lien public si applicable]
- **Impact connu** : [Biais, limitations documentées]

## Distribution
- **Licence** : [CC-BY/MIT/propriétaire/...]
- **Restrictions** : [Géographiques, d'usage]
- **Redistribution** : [Autorisée sous conditions]

## Maintenance
- **Responsable** : [Nom/Email]
- **Mises à jour** : [Fréquence, procédure]
- **Deprecated** : [Date fin de vie prévue]
```

**Livrables** :
- Model card complétée et validée
- Datasheet for datasets associés
- Checklist complétude documentation


### 5. Communication explications aux non-experts
**Objectif** : Traduire explications techniques XAI en langage accessible.

**Principes** :
1. **Analogies simples** : comparer modèle à processus connu
2. **Visualisations** : graphiques > équations
3. **Exemples concrets** : cas réels annotés
4. **Langage naturel** : éviter jargon technique

**Template explication utilisateur** :
```markdown
## Pourquoi votre demande de crédit a été refusée

### Raison principale
Votre taux d'endettement actuel (45%) dépasse notre seuil recommandé (35%).

### Facteurs secondaires
- Historique de crédit récent (< 2 ans)
- Revenus variables (freelance)

### Comment améliorer votre profil
Pour augmenter vos chances d'approbation future :
1. **Réduire endettement** : Remboursez 10% dette actuelle (≈ 5000 EUR)
2. **Stabiliser revenus** : Fournir preuves revenus réguliers sur 6 mois
3. **Renforcer historique** : Maintenir paiements à jour pendant 12 mois supplémentaires

### Questions ?
Contactez un conseiller pour analyse personnalisée.
```

**Anti-patterns** :
- ❌ "Le modèle XGBoost avec 150 features a prédit probabilité 0.32 < seuil 0.5"
- ❌ Graphiques SHAP bruts sans annotation
- ❌ Équations mathématiques dans communication client

**Livrables** :
- Templates explications utilisateurs validés juridiquement
- FAQ explications
- Formation équipes customer-facing


## Cas d'usage typiques

### Refus crédit (RGPD droit à explication)
- **Technique** : Counterfactual explanations
- **Sortie** : "Si votre revenu était 10% supérieur OU endettement 15% inférieur, décision serait positive"
- **Réglementaire** : Conforme RGPD Article 22

### Diagnostic médical IA
- **Technique** : LIME + attention visualization (si image médicale)
- **Sortie** : Heatmap zones image influençant diagnostic + feature importance symptômes
- **Réglementaire** : Supervision humaine obligatoire, traçabilité décision

### Système recommandation contenu
- **Technique** : SHAP + documentation Model Card
- **Sortie** : "Recommandé car vous avez aimé [item X, Y], genre [Z], et acteurs [W]"
- **Réglementaire** : Transparence algorithme (DSA européen)


## Outils recommandés
- **LIME** : https://github.com/marcotcr/lime
- **SHAP** : https://github.com/slundberg/shap
- **DiCE** : https://github.com/interpretml/DiCE
- **InterpretML** : https://github.com/interpretml/interpret
- **Captum** (PyTorch) : https://captum.ai/
- **AI Explainability 360** (IBM) : https://github.com/Trusted-AI/AIX360


## Contraintes et références
- [Model Cards for Model Reporting (Google)](https://arxiv.org/abs/1810.03993)
- [Datasheets for Datasets (Microsoft)](https://arxiv.org/abs/1803.09010)
- [LIME paper](https://arxiv.org/abs/1602.04938)
- [SHAP paper](https://arxiv.org/abs/1705.07874)
- [GDPR Right to Explanation](https://gdpr-info.eu/art-22-gdpr/)

## Exemples d'usage

### Exemple 1 : Expliquer un refus de crédit
**Contexte** : Une équipe conformité doit comprendre les facteurs d'une décision de crédit automatisée avant de préparer une explication destinée au demandeur.  
**Input** : Version du modèle, dossier de test pseudonymisé, décision produite, variables utilisées et méthode d'explication validée.  
**Output** : Explication locale des facteurs ayant contribué à la décision, limites de l'explication et proposition de revue humaine; aucune causalité n'est affirmée à partir d'une importance de variable seule.

### Exemple 2 : Documenter un modèle de détection de fraude
**Contexte** : Les analystes fraude contestent des alertes et ont besoin de comprendre le comportement d'un modèle opaque.  
**Input** : Modèle en production, échantillon représentatif de transactions anonymisées, résultats de validation et exigences internes de traçabilité.  
**Output** : Niveau d'opacité justifié, explications locales/globales à évaluer, exemples de décisions annotées et plan de contrôle des limites et dérives.

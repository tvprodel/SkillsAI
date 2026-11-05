# Feature Engineering & Data Preparation

## Objectif
Cadrer la préparation des données et la construction de features pour un pipeline de machine learning classique/prédictif, en prévenant les risques de fuite de données et de biais.

## Quand l'utiliser (triggers)
- Préparation d'un nouveau jeu de données avant entraînement d'un modèle ML.
- Gestion de valeurs manquantes, d'outliers ou de déséquilibre de classes.
- Conception ou revue d'un feature store.
- Diagnostic d'un modèle sous-performant suspecté de souffrir d'un feature engineering insuffisant.

## Hors périmètre
- Choix de l'algorithme et protocole d'évaluation → **ML Pipeline Design & Evaluation** (l'agent de machine learning).
- Stockage/indexation définitif des données transformées → **l'agent bases de données**.
- Implémentation finale du code de transformation → **l'agent de développement back-end**.
- Conformité RGPD sur les données personnelles utilisées → **l'agent de conformité RGPD**.

## Inputs requis
- **Schéma des données brutes** : colonnes disponibles, types, sources, fraîcheur.
- **Objectif du modèle** : variable cible, type de tâche ML.
- **Qualité connue** : taux de valeurs manquantes, doublons, incohérences connues.
- **Contraintes** : volumétrie, fréquence de rafraîchissement, contraintes de confidentialité.

## Sorties attendues
- **Plan de nettoyage** : traitement des valeurs manquantes, doublons, outliers.
- **Plan de feature engineering** : encodage des variables catégorielles, normalisation/standardisation, création de features dérivées.
- **Stratégie anti-fuite de données** : ordre des opérations garantissant l'absence de contamination train/test.
- **Stratégie de gestion du déséquilibre** (si applicable) : rééchantillonnage, pondération de classes.

## Workflow recommandé
1. **Audit des données brutes** : analyser la qualité (valeurs manquantes, doublons, outliers, incohérences de types), la distribution de la variable cible.

2. **Plan de nettoyage** : définir le traitement de chaque anomalie détectée (imputation, suppression, correction), en documentant les choix et leur impact potentiel.

3. **Encodage et transformation** : définir l'encodage des variables catégorielles (one-hot, ordinal, target encoding selon cardinalité), la normalisation/standardisation des variables numériques.

4. **Création de features dérivées** : proposer des features métier pertinentes (ratios, agrégations temporelles, interactions) en lien avec l'objectif du modèle.

5. **Vérification anti-fuite** : s'assurer que toute statistique utilisée pour transformer les données (moyenne, médiane, encodage) est calculée UNIQUEMENT sur le jeu d'entraînement, puis appliquée au jeu de test/validation.

6. **Gestion du déséquilibre de classes** (si applicable) : proposer une stratégie adaptée (sur-échantillonnage, sous-échantillonnage, pondération de classes, métriques adaptées) sans jamais rééquilibrer avant le split train/test.

7. **Documentation** : produire un plan reproductible transmis pour implémentation.

## Garde-fous
- **Anti-fuite de données stricte** : split train/test AVANT tout calcul de statistiques (moyenne, encodage, normalisation) ; jamais l'inverse.
- **Cohérence temporelle** : pour les données chronologiques, ne jamais utiliser d'informations futures pour construire des features passées.
- **Traçabilité des transformations** : chaque transformation appliquée doit être documentée et reproductible sur de nouvelles données en production.
- **Vigilance biais** : vérifier que les features ne encodent pas indirectement des variables sensibles (proxy discrimination) si le modèle impacte des personnes.
- **Qualité avant volume** : privilégier la correction des anomalies de qualité plutôt que l'ajout de features superflues.
- **Pas de données personnelles non nécessaires** : appliquer le principe de minimisation ; signaler à **l'agent de conformité RGPD** si des données sensibles sont impliquées.

## Template d'entrée (copier/coller)
```text
[Données brutes]
- Colonnes disponibles : ...
- Variable cible : ...
- Type de tâche : [classification / régression / clustering / série temporelle]

[Qualité connue]
- Taux de valeurs manquantes : ...
- Doublons connus : [oui/non]
- Outliers suspectés : ...

[Contraintes]
- Volumétrie : ...
- Fraîcheur/fréquence de mise à jour : ...
- Données sensibles impliquées : [oui/non]
```

## Template de sortie (copier/coller)
```markdown
# Plan de préparation des données — [Nom du cas d'usage]

## Audit qualité
- Valeurs manquantes : ... (traitement : ...)
- Doublons : ... (traitement : ...)
- Outliers : ... (traitement : ...)

## Encodage et transformation
- Variables catégorielles : ... (méthode : ...)
- Variables numériques : ... (méthode : ...)

## Features dérivées proposées
- Feature 1 : ... (justification métier : ...)
- Feature 2 : ... (justification métier : ...)

## Stratégie anti-fuite
- Ordre des opérations : split → statistiques calculées sur train → application sur test/validation

## Gestion du déséquilibre (si applicable)
- Stratégie retenue : ...
```

## Checklist QA interne
- [ ] Audit qualité des données brutes réalisé (valeurs manquantes, doublons, outliers).
- [ ] Toutes les statistiques de transformation calculées uniquement sur le jeu d'entraînement.
- [ ] Cohérence temporelle vérifiée pour les données chronologiques.
- [ ] Features dérivées justifiées par une logique métier explicite.
- [ ] Déséquilibre de classes traité après le split train/test (pas avant).
- [ ] Vigilance biais/proxy discrimination vérifiée si données sensibles.
- [ ] Plan documenté de façon reproductible.

## KPI reliés
- **Taux de fuite de données détectée en revue** : (pipelines revus avec fuite détectée / pipelines revus) x 100.
- **Réduction du taux de valeurs manquantes** : (taux avant - taux après traitement) / taux avant x 100.
- **Gain de performance attribuable au feature engineering** : (métrique modèle avec nouvelles features - métrique modèle sans) / métrique sans x 100.

## Definition of done
- Audit qualité complet documenté (mesure : 3 catégories d'anomalies couvertes ; preuve : section Audit qualité complétée).
- Plan de transformation anti-fuite validé (mesure : ordre des opérations explicite ; preuve : section Stratégie anti-fuite complétée).
- Features dérivées justifiées par une logique métier (mesure : justification présente pour chaque feature ; preuve : section Features dérivées complétée).

## Exemples d'usage
- "Prépare les données clients pour un modèle de prédiction de churn (gestion valeurs manquantes et encodage)."
- "Vérifie s'il y a un risque de fuite de données dans ce pipeline de scoring crédit."
- "Propose des features dérivées pour un modèle de prévision de ventes hebdomadaires."

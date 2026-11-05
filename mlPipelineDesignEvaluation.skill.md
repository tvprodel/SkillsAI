# ML Pipeline Design & Evaluation

## Objectif
Cadrer la conception d'un pipeline de machine learning classique/prédictif (classification, régression, clustering, séries temporelles, recommandation) et son protocole d'évaluation, avec sélection d'algorithmes et de métriques justifiées.

## Quand l'utiliser (triggers)
- Démarrage d'un nouveau cas d'usage ML prédictif (score de risque, prévision de demande, segmentation clients, système de recommandation).
- Comparaison de plusieurs algorithmes candidats pour un même problème.
- Revue d'un pipeline existant sous-performant (métriques insuffisantes, sur-apprentissage suspecté).
- Définition du protocole de validation avant tout entraînement en production.

## Hors périmètre
- Sélection de modèles génératifs (LLM, diffusion, embeddings) → **l'agent de sélection de modèles génératifs**.
- Rédaction/optimisation du texte des prompts → **l'agent de prompt engineering**.
- Implémentation complète du code de production → **l'agent de développement back-end**.
- Optimisation coût/latence infrastructure → **l'agent FinOps**.
- Stockage/indexation des données → **l'agent bases de données**.

## Inputs requis
- **Cas d'usage** : objectif métier, type de tâche (classification/régression/clustering/série temporelle/recommandation).
- **Données disponibles** : volumétrie, fraîcheur, qualité connue, présence de labels, déséquilibre de classes éventuel.
- **Contraintes** : latence d'inférence acceptable, criticité de la décision, contraintes d'explicabilité.
- **Historique** (si applicable) : pipeline existant, métriques actuelles, problèmes observés.

## Sorties attendues
- **Cadrage du problème** : type de tâche ML confirmé, métriques cibles alignées sur l'objectif métier.
- **Protocole d'évaluation** : stratégie de split (train/val/test ou validation croisée), métriques retenues et justifiées.
- **Tableau comparatif d'algorithmes** : au moins 2-3 candidats avec avantages/inconvénients et complexité.
- **Modèle recommandé** : choix final justifié avec trade-offs explicites.

## Workflow recommandé
1. **Cadrage du problème** : clarifier l'objectif métier et le traduire en tâche ML (classification binaire/multi-classe, régression, clustering, prévision temporelle, recommandation).

2. **Analyse des données disponibles** : évaluer la qualité, la volumétrie, la présence de labels, le déséquilibre de classes et les risques de biais.

3. **Sélection des métriques** : choisir les métriques alignées sur l'impact métier des erreurs.
   - Classification : précision, rappel, F1, AUC-ROC, matrice de confusion (privilégier rappel si faux négatifs coûteux, précision si faux positifs coûteux).
   - Régression : RMSE, MAE, R², MAPE.
   - Clustering : silhouette score, indice de Davies-Bouldin, cohérence métier des clusters.
   - Séries temporelles : MAPE, RMSE sur horizon de prévision, respect de la causalité temporelle.

4. **Sélection des algorithmes candidats** : proposer 2-3 approches allant du simple (baseline interprétable) au complexe (ensembles/boosting), en tenant compte des contraintes d'explicabilité.

5. **Définition du protocole de validation** : split temporel pour séries chronologiques, split stratifié pour classes déséquilibrées, validation croisée k-fold pour petits jeux de données.

6. **Comparaison et recommandation** : établir un tableau comparatif chiffré, recommander un modèle avec justification et plan de repli (fallback) si non concluant.

## Garde-fous
- **Anti-fuite de données (data leakage)** : le split train/test doit précéder tout feature engineering dépendant des statistiques globales (normalisation, imputation).
- **Split temporel obligatoire** pour les séries chronologiques : jamais de validation croisée aléatoire classique qui violerait la causalité.
- **Baseline systématique** : toujours comparer à une baseline simple (modèle naïf, règle métier) pour contextualiser le gain des modèles complexes.
- **Vérification du déséquilibre de classes** : signaler et traiter explicitement (rééchantillonnage, pondération de classes, métriques adaptées) avant d'entraîner.
- **Explicabilité** : si la décision impacte des personnes, privilégier des modèles interprétables ou prévoir une méthode d'explication (SHAP, feature importance).
- **Reproductibilité** : fixer les seeds aléatoires et documenter versions des données/librairies.

## Template d'entrée (copier/coller)
```text
[Cas d'usage]
- Objectif métier : ...
- Type de tâche : [classification / régression / clustering / série temporelle / recommandation]
- Impact métier des erreurs : [faux positifs coûteux / faux négatifs coûteux / équilibré]

[Données]
- Volumétrie : ...
- Labels disponibles : [oui/non, qualité]
- Déséquilibre de classes : [oui/non, ratio]
- Fraîcheur/fréquence de mise à jour : ...

[Contraintes]
- Latence d'inférence max : ...
- Explicabilité requise : [oui/non]
- Criticité de la décision : [faible/moyenne/élevée]
```

## Template de sortie (copier/coller)
```markdown
# Pipeline ML — [Nom du cas d'usage]

## Cadrage
- Type de tâche : ...
- Métrique(s) cible(s) : ...

## Protocole d'évaluation
- Stratégie de split : ...
- Métriques retenues et justification : ...

## Comparatif d'algorithmes

| Algorithme | Métrique 1 | Métrique 2 | Complexité | Explicabilité |
|-----------|-----------|-----------|------------|---------------|
| Baseline | ... | ... | Faible | Élevée |
| ... | ... | ... | ... | ... |

## Recommandation finale
**Modèle retenu** : ...
**Justification** : ...
**Risques identifiés** : ...
**Plan de repli** : ...
```

## Checklist QA interne
- [ ] Type de tâche ML clairement identifié et confirmé avec le métier.
- [ ] Métriques choisies alignées sur le coût réel des erreurs (pas de métrique par défaut non justifiée).
- [ ] Split respectant l'anti-fuite de données et la causalité temporelle si applicable.
- [ ] Déséquilibre de classes vérifié et traité si présent.
- [ ] Baseline simple incluse dans la comparaison.
- [ ] Au moins 2 algorithmes candidats comparés avec trade-offs explicites.
- [ ] Reproductibilité garantie (seeds, versions documentées).

## KPI reliés
- **Gain vs baseline** : (métrique modèle retenu - métrique baseline) / métrique baseline x 100.
- **Écart validation/production** : (métrique mesurée en production - métrique validée) / métrique validée x 100.
- **Taux de fuite de données détectée** : (pipelines audités avec fuite détectée / pipelines audités) x 100.

## Definition of done
- Cadrage du problème documenté et validé (mesure : type de tâche + métrique cible ; preuve : section Cadrage complétée).
- Protocole d'évaluation anti-fuite défini (mesure : stratégie de split documentée ; preuve : section Protocole complétée).
- Au moins 2 algorithmes comparés avec un tableau chiffré (mesure : nombre de lignes du tableau ; preuve : tableau livré).
- Recommandation finale justifiée avec risques et plan de repli (mesure : présence des 3 sous-sections ; preuve : section Recommandation complète).

## Exemples d'usage
- "Conçois un pipeline de classification pour détecter le churn client à partir de l'historique d'usage."
- "Compare Random Forest et Gradient Boosting pour prédire le montant d'une transaction frauduleuse."
- "Définis le protocole de validation pour un modèle de prévision de la demande sur 12 semaines."

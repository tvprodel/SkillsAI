# MLOps & Model Lifecycle Management

## Objectif
Cadrer la mise en production, le versioning, le monitoring et le réentraînement des modèles de machine learning classiques/prédictifs, afin de garantir un cycle de vie fiable, traçable et détectant la dérive.

## Quand l'utiliser (triggers)
- Mise en production d'un premier modèle ML (besoin de stratégie de versioning/registry).
- Définition d'un pipeline CI/CD dédié au ML (retraining automatisé, tests de non-régression modèle).
- Détection ou suspicion de dérive de données (data drift) ou de dérive de concept (concept drift).
- Revue périodique de la performance d'un modèle en production.
- Définition de la cadence et des déclencheurs de réentraînement.

## Hors périmètre
- Conception initiale du pipeline et choix d'algorithme → **ML Pipeline Design & Evaluation** (l'agent de machine learning).
- Optimisation coût/latence de l'infrastructure d'entraînement/inférence → **l'agent FinOps**.
- Implémentation du pipeline CI/CD générique (hors ML) → **l'agent d'intégration et d'automatisation** ou **l'agent de développement back-end**.
- Tests adversariaux/robustesse (empoisonnement, biais) → **l'agent d'évaluation IA (red teaming)**.

## Inputs requis
- **Modèle validé** : algorithme retenu, métriques de validation, dataset d'entraînement de référence.
- **Contraintes d'exploitation** : fréquence de prédiction (batch/temps réel), criticité métier, SLA de disponibilité.
- **Infrastructure cible** : registry disponible (MLflow, DVC, ou équivalent libre), environnement de déploiement.
- **Historique** (si réentraînement) : dérive observée, dernière date d'entraînement, incidents précédents.

## Sorties attendues
- **Stratégie de versioning** : convention de nommage, registry retenu, métadonnées tracées (données, hyperparamètres, métriques).
- **Pipeline CI/CD ML** : étapes automatisées (validation données, entraînement, tests de non-régression, déploiement).
- **Plan de monitoring** : métriques de dérive suivies, seuils d'alerte, fréquence de contrôle.
- **Politique de réentraînement** : déclencheurs (dérive détectée, cadence calendaire, dégradation métier), procédure de validation avant remplacement du modèle en production.

## Workflow recommandé
1. **Définition de la stratégie de versioning** : choisir un registry de modèles (MLflow, DVC ou équivalent open source), définir les métadonnées obligatoires (version des données, hyperparamètres, métriques, date, auteur).

2. **Conception du pipeline CI/CD ML** : automatiser la validation des données d'entrée, l'entraînement, les tests de non-régression (comparaison au modèle en production) et le déploiement conditionnel.

3. **Définition du monitoring de dérive** : sélectionner les métriques de data drift (distribution des features) et de concept drift (dégradation de la performance réelle), définir les seuils d'alerte.

4. **Politique de réentraînement** : définir les déclencheurs (dérive au-delà du seuil, cadence calendaire fixe, dégradation métier observée) et la procédure de validation avant bascule en production (A/B test, shadow deployment, validation humaine).

5. **Plan de rollback** : définir la procédure de retour au modèle précédent en cas de dégradation post-déploiement.

6. **Documentation et transmission** : synthétiser le plan MLOps complet, transmettre pour implémentation (l'agent de développement back-end) et documentation (l'agent de documentation de code).

## Garde-fous
- **Jamais de déploiement sans registry** : tout modèle en production doit être versionné et traçable (rollback possible).
- **Tests de non-régression obligatoires** : un nouveau modèle ne remplace l'ancien que s'il est démontré au moins équivalent sur le jeu de validation de référence.
- **Distinction data drift vs concept drift** : traiter différemment (data drift = distribution des entrées change ; concept drift = la relation entrée-sortie change).
- **Shadow deployment recommandé** pour les modèles critiques : faire tourner le nouveau modèle en parallèle sans impacter la production avant bascule complète.
- **Plan de rollback documenté** avant toute mise en production.
- **Pas de secrets en dur** : accès au registry/infra via variables d'environnement, jamais de clé en dur.
- **Priorité logiciel libre / open source** : privilégier MLflow, DVC, Evidently ou équivalents libres avant solutions propriétaires.

## Template d'entrée (copier/coller)
```text
[Modèle]
- Algorithme retenu : ...
- Métriques de validation : ...
- Dataset de référence : ...

[Exploitation]
- Fréquence de prédiction : [batch / temps réel]
- Criticité métier : [faible / moyenne / élevée]
- SLA disponibilité : ...

[Infrastructure]
- Registry disponible : [MLflow / DVC / autre / à définir]
- Environnement de déploiement : ...
```

## Template de sortie (copier/coller)
```markdown
# Plan MLOps — [Nom du modèle]

## Versioning
- Registry retenu : ...
- Métadonnées tracées : données, hyperparamètres, métriques, date, auteur

## Pipeline CI/CD
1. Validation des données d'entrée
2. Entraînement automatisé
3. Tests de non-régression (seuil : ...)
4. Déploiement conditionnel

## Monitoring de dérive
- Métriques data drift suivies : ...
- Métriques concept drift suivies : ...
- Seuils d'alerte : ...
- Fréquence de contrôle : ...

## Politique de réentraînement
- Déclencheurs : [dérive > seuil / cadence calendaire / dégradation métier]
- Procédure de validation avant bascule : [A/B test / shadow deployment / validation humaine]

## Plan de rollback
- Condition de rollback : ...
- Procédure : ...
```

## Checklist QA interne
- [ ] Registry de versioning défini avec métadonnées obligatoires tracées.
- [ ] Pipeline CI/CD inclut des tests de non-régression avant déploiement.
- [ ] Métriques de data drift ET concept drift distinctement définies.
- [ ] Seuils d'alerte de dérive chiffrés (pas de seuil vague).
- [ ] Politique de réentraînement avec déclencheurs explicites.
- [ ] Plan de rollback documenté et testé conceptuellement.
- [ ] Aucun secret/clé en dur dans la configuration proposée.

## KPI reliés
- **Taux de dérive détectée avant impact métier** : (dérives détectées par monitoring / dérives totales observées) x 100.
- **Délai moyen de réentraînement** : moyenne du temps entre déclenchement et modèle réentraîné validé.
- **Taux de rollback** : (déploiements annulés / déploiements totaux) x 100.
- **Taux de tests de non-régression réussis** : (déploiements validés sans dégradation / déploiements totaux) x 100.

## Definition of done
- Stratégie de versioning documentée avec registry et métadonnées (mesure : liste des métadonnées ; preuve : section Versioning complétée).
- Pipeline CI/CD ML avec tests de non-régression défini (mesure : présence des 4 étapes ; preuve : section Pipeline CI/CD complète).
- Plan de monitoring avec seuils chiffrés (mesure : seuils numériques présents ; preuve : section Monitoring complétée).
- Politique de réentraînement et plan de rollback documentés (mesure : présence des 2 sections ; preuve : livrable complet).

## Exemples d'usage
- "Définis la stratégie MLOps pour un modèle de scoring crédit en production."
- "Quels seuils de data drift surveiller pour un modèle de détection de fraude ?"
- "Conçois le pipeline CI/CD pour réentraîner automatiquement un modèle de prévision de demande chaque semaine."

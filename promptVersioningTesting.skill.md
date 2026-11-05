# Prompt Versioning & Testing

## Objectif
Gérer les versions de prompts IA, documenter les changements, et réaliser des tests A/B pour mesurer l'impact des modifications sur la qualité, le coût et la performance.

## Quand l'utiliser (triggers)
- Modification substantielle d'un prompt existant (restructuration, ajout guardrails, changement format).
- Besoin de comparer plusieurs variantes de prompt pour choisir la plus performante.
- Documentation de l'évolution d'un prompt critique au fil du temps.
- Audit de l'historique des modifications pour comprendre les dégradations/améliorations.
- Rollback nécessaire suite à régression détectée après modification.

## Hors périmètre
- Optimisation structurelle initiale du prompt → **Prompt Structure Optimization**.
- Tests adversariaux et red teaming → **l'agent d'évaluation IA (red teaming)**.
- Analyse coûts/latence détaillée → **l'agent FinOps**.

## Inputs requis
- **Prompt actuel** (baseline ou version précédente).
- **Prompt candidat** (nouvelle version à tester).
- **Jeu de test représentatif** : minimum 20-30 requêtes couvrant cas normaux + edge cases + cas adversariaux.
- **Métriques cibles** : qualité (exactitude, respect périmètre, stabilité format), coût (tokens), latence (TTFT, TPS).
- **Critères de succès** : seuils acceptables pour chaque métrique (ex: taux conformité ≥ 95%, coût ≤ +10% vs baseline).

## Sorties attendues
- **Schéma de versioning** : convention de numérotation (sémantique recommandée : MAJOR.MINOR.PATCH).
  - MAJOR : refonte structurelle majeure (changement de rôle, périmètre, processus).
  - MINOR : ajout de fonctionnalité ou amélioration substantielle (nouveaux guardrails, format enrichi).
  - PATCH : correction bug, clarification mineure, optimisation verbosité.

- **Changelog détaillé** : pour chaque version, documenter :
  - Date et auteur de la modification.
  - Nature du changement (restructuration, guardrails, format, optimisation).
  - Raison de la modification (problème observé, nouveau besoin, optimisation).
  - Gains mesurés (si applicable).

- **Rapport de test A/B** : comparaison quantitative entre versions avec tableau de métriques.

- **Recommandation** : version à déployer avec justification basée données.

## Workflow recommandé
1. **Définir baseline** : identifier la version actuelle (v1.X.X) comme référence pour comparaison.

2. **Créer version candidate** : appliquer les modifications et incrémenter numéro de version selon convention.

3. **Préparer jeu de test** : sélectionner 20-30 requêtes représentatives (70% cas normaux, 20% edge cases, 10% adversariaux).

4. **Exécuter tests parallèles** : soumettre le même jeu de test aux deux versions (baseline vs candidate).

5. **Collecter métriques** : pour chaque version, mesurer :
   - **Qualité** : taux de conformité périmètre, taux de respect format, taux de refus corrects, exactitude factuelle.
   - **Coût** : tokens prompt moyen, tokens réponse moyen, coût par requête.
   - **Latence** : TTFT moyen, TPS moyen, temps total réponse.

6. **Analyser écarts** : calculer les deltas (%) entre baseline et candidate pour chaque métrique.

7. **Décision** : 
   - Si candidate ≥ critères de succès → **Déployer** (promouvoir en version stable).
   - Si candidate < critères mais améliorations partielles → **Itérer** (ajuster et re-tester).
   - Si candidate régression significative → **Rollback** (conserver baseline, archiver candidate avec leçons apprises).

8. **Documenter** : mettre à jour changelog et archiver rapport de test A/B.

## Garde-fous
- **Ne jamais déployer sans test** : toute modification de prompt doit passer par phase de test A/B avant production.
- **Jeu de test représentatif** : éviter les biais de sélection (trop de cas simples, manque de variété).
- **Baseline stable** : ne pas modifier la baseline pendant la période de test (pollue la comparaison).
- **Métriques multiples** : ne pas optimiser une seule métrique au détriment des autres (ex: réduire coût en sacrifiant qualité).
- **Archivage versions** : conserver toutes les versions avec changelog pour audit et rollback potentiel.
- **Seuils de régression** : définir seuils d'alerte (ex: si coût +20% ou qualité -5%, bloquer le déploiement).

## Template d'entrée (copier/coller)
```text
[Version baseline]
- Numéro : v1.X.X
- Prompt : [texte complet ou lien fichier]

[Version candidate]
- Numéro : v1.Y.Y
- Prompt : [texte complet ou lien fichier]
- Modifications apportées : [liste changements]

[Jeu de test]
- Nombre de requêtes : [20-30 recommandé]
- Répartition : [70% normaux, 20% edge, 10% adversariaux]
- Requêtes : [liste ou lien fichier]

[Métriques cibles]
- Qualité : [taux conformité ≥ X%, taux format stable ≥ Y%]
- Coût : [tokens/requête ≤ Z, coût ≤ $W]
- Latence : [TTFT ≤ Xs, temps total ≤ Ys]

[Critères de succès]
- [Métrique 1] : [seuil acceptable]
- [Métrique 2] : [seuil acceptable]
- [...]
```

## Template de sortie (copier/coller)
```markdown
# Rapport Test A/B : v[X.X.X] vs v[Y.Y.Y]

## Résumé exécutif
- **Version baseline** : v[X.X.X]
- **Version candidate** : v[Y.Y.Y]
- **Date test** : [YYYY-MM-DD]
- **Jeu de test** : [N] requêtes ([X]% normaux, [Y]% edge, [Z]% adversariaux)
- **Recommandation** : [Déployer / Itérer / Rollback]

## Comparatif métriques

| Métrique | Baseline v[X.X.X] | Candidate v[Y.Y.Y] | Delta | Statut |
|----------|-------------------|---------------------|-------|--------|
| Taux conformité périmètre | [X]% | [Y]% | [+/-Z]% | ✅/⚠️/❌ |
| Taux respect format | [X]% | [Y]% | [+/-Z]% | ✅/⚠️/❌ |
| Taux refus corrects | [X]% | [Y]% | [+/-Z]% | ✅/⚠️/❌ |
| Tokens prompt moyen | [X] | [Y] | [+/-Z] ([%]) | ✅/⚠️/❌ |
| Tokens réponse moyen | [X] | [Y] | [+/-Z] ([%]) | ✅/⚠️/❌ |
| Coût par requête | $[X] | $[Y] | [+/-$Z] ([%]) | ✅/⚠️/❌ |
| TTFT moyen | [X]s | [Y]s | [+/-Z]s ([%]) | ✅/⚠️/❌ |
| Temps total moyen | [X]s | [Y]s | [+/-Z]s ([%]) | ✅/⚠️/❌ |

**Légende statut** : ✅ Amélioration ou neutre acceptable | ⚠️ Dégradation mineure | ❌ Régression critique

## Changelog v[Y.Y.Y]
- **Type** : [MAJOR / MINOR / PATCH]
- **Date** : [YYYY-MM-DD]
- **Auteur** : [Nom ou agent]
- **Modifications** :
  - [Changement 1] : [description détaillée]
  - [Changement 2] : [description détaillée]
  - [...]
- **Raison** : [problème observé ou objectif d'amélioration]

## Analyse détaillée

### Points forts
- [Amélioration 1 avec chiffres]
- [Amélioration 2 avec chiffres]
- [...]

### Points faibles
- [Dégradation 1 avec chiffres]
- [Dégradation 2 avec chiffres]
- [...]

### Cas edge notables
- [Cas 1] : [comportement baseline vs candidate]
- [Cas 2] : [comportement baseline vs candidate]

## Recommandation finale
[Déployer / Itérer / Rollback] car [justification basée données].

**Si Itérer** : ajustements recommandés pour prochaine version :
- [Ajustement 1]
- [Ajustement 2]
- [...]

**Si Rollback** : leçons apprises :
- [Leçon 1]
- [Leçon 2]
- [...]
```

## Checklist QA interne
- [ ] Schéma de versioning sémantique appliqué (MAJOR.MINOR.PATCH).
- [ ] Changelog complet pour la version candidate (date, auteur, modifications, raison).
- [ ] Jeu de test ≥ 20 requêtes avec répartition équilibrée (normaux/edge/adversariaux).
- [ ] Tests exécutés en parallèle (même jeu de test, même conditions).
- [ ] Métriques collectées pour les 3 dimensions (qualité, coût, latence).
- [ ] Deltas calculés avec précision (valeur absolue + pourcentage).
- [ ] Seuils de régression définis et respectés (pas de déploiement si régression critique).
- [ ] Rapport de test A/B complet et archivé.
- [ ] Recommandation justifiée par les données (pas d'intuition subjective).

## KPI reliés
- **Taux de déploiement réussi** : (versions déployées sans rollback / versions testées) x 100.
- **Amplitude amélioration moyenne** : moyenne des deltas positifs sur métriques qualité.
- **Réduction coût cumulée** : somme des gains coût sur toutes les versions déployées.
- **Temps moyen cycle version** : durée moyenne entre création candidate et déploiement/rollback.

## Definition of done
- Version candidate testée sur jeu de test représentatif (≥ 20 requêtes).
- Rapport de test A/B complet avec comparatif métriques (qualité, coût, latence).
- Décision documentée (Déployer/Itérer/Rollback) avec justification basée données.
- Changelog mis à jour avec détails modifications et raison.
- Version archivée (baseline et candidate) pour audit et rollback potentiel.
- Si déploiement : version candidate promue en stable, baseline archivée.

## Exemples d'usage

### Exemple 1 : Test A/B ajout guardrails anti-hallucination
**Contexte** : Agent technique avec taux hallucination estimé à 12% (réponses inventées quand données insuffisantes).

**Modifications** (v1.2.0 → v1.3.0 - MINOR) :
- Ajout instruction explicite : "Si tu ne sais pas, réponds 'Je ne dispose pas de données suffisantes pour répondre'."
- Ajout exemples positifs (admission de limite) et négatifs (invention de faits).

**Jeu de test** : 25 requêtes (15 réponses possibles, 10 réponses impossibles faute de données).

**Résultats** :

| Métrique | v1.2.0 | v1.3.0 | Delta |
|----------|--------|--------|-------|
| Taux hallucination | 12% | 2% | -83% ✅ |
| Taux admission limite | 65% | 98% | +51% ✅ |
| Tokens réponse moyen | 180 | 175 | -3% ✅ |
| Coût par requête | $0.018 | $0.017 | -6% ✅ |

**Décision** : **Déployer v1.3.0** - amélioration significative hallucination sans dégradation autres métriques.

### Exemple 2 : Test A/B optimisation verbosité
**Contexte** : Prompt agent de 2200 tokens jugé trop verbeux, objectif réduction -30% sans perte qualité.

**Modifications** (v2.1.0 → v2.2.0 - PATCH) :
- Fusion sections redondantes.
- Simplification exemples.
- Suppression instructions obsolètes.

**Jeu de test** : 30 requêtes (20 normaux, 7 edge, 3 adversariaux).

**Résultats** :

| Métrique | v2.1.0 | v2.2.0 | Delta |
|----------|--------|--------|-------|
| Tokens prompt | 2200 | 1500 | -32% ✅ |
| Taux conformité périmètre | 94% | 91% | -3% ⚠️ |
| Taux respect format | 97% | 96% | -1% ✅ |
| Coût par requête | $0.022 | $0.015 | -32% ✅ |
| TTFT moyen | 3.8s | 2.9s | -24% ✅ |

**Décision** : **Itérer** - réduction verbosité réussie mais conformité périmètre en baisse (94% → 91%). Ajustement nécessaire : renforcer ONLY/DO NOT sans rallonger excessivement.

**v2.2.1** (PATCH) : ajout 2 phrases clés dans périmètre ONLY (50 tokens).

**Re-test** : conformité périmètre 94% restaurée, coût toujours -28% vs v2.1.0 → **Déployer v2.2.1**.

### Exemple 3 : Rollback après régression format
**Contexte** : Modification format de sortie de 4 rubriques obligatoires (Résultat/Hypothèses/Risques/Prochaines actions) à 2 rubriques simplifiées (Résultat/Recommandations).

**Modifications** (v3.0.0 → v3.1.0 - MINOR) :
- Simplification format sortie pour gain concision.

**Jeu de test** : 28 requêtes.

**Résultats** :

| Métrique | v3.0.0 | v3.1.0 | Delta |
|----------|--------|--------|-------|
| Taux respect format | 98% | 72% | -27% ❌ |
| Tokens réponse moyen | 220 | 180 | -18% ✅ |
| Taux omission risques | 2% | 31% | +1450% ❌ |
| Coût par requête | $0.020 | $0.016 | -20% ✅ |

**Décision** : **Rollback v3.1.0** - régression critique sur stabilité format (-27%) et omission fréquente des risques (+31% des réponses). Le gain coût (-20%) ne compense pas la perte de fiabilité.

**Leçons apprises** :
- Format 4 rubriques est critique pour traçabilité complète (Hypothèses et Risques non optionnels).
- Simplification format = risque d'omissions structurelles.
- Ne pas prioriser concision au détriment de la complétude.

**Version archivée** : v3.1.0 conservée comme contre-exemple documenté.

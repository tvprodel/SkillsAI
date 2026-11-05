# Operations Transformation Portfolio & Benefits Governance

## Objectif

Structurer le portefeuille d'initiatives de transformation des opérations, relier chaque initiative à un résultat métier et définir une gouvernance des bénéfices, dépendances et capacités. Le skill aide la direction à arbitrer le portefeuille sans remplacer le l'agent produit ni le l'agent de planification.

## Quand l'utiliser (triggers)

- Prioriser plusieurs initiatives d'amélioration ou de transformation opérationnelle.
- Évaluer la cohérence entre une initiative et les résultats stratégiques attendus.
- Établir des critères de décision et rendre les dépendances visibles.
- Suivre les bénéfices prévus et observés après lancement d'une initiative.
- Préparer une revue de portefeuille ou décider de poursuivre, adapter ou arrêter une initiative.

**Déclencheurs** :
- « Priorise notre portefeuille de transformation opérationnelle »
- « Comment vérifier que ce programme réalise ses bénéfices ? »
- « Prépare une revue de portefeuille des opérations »

## Hors périmètre

- La stratégie produit, le portefeuille de fonctionnalités et la roadmap produit relèvent de l'agent de stratégie produit.
- Le WBS détaillé, les estimations de tâches et le planning projet relèvent de l'agent de gestion de projet.
- L'analyse détaillée et la refonte d'un processus individuel relèvent de l'agent d'optimisation des processus métier.
- Le modèle capacitaire multi-sprints des équipes agents relève du skill Portfolio / Capacity Planner.
- Les prévisions financières certifiées, contrats et avis réglementaires doivent être confirmés par les experts concernés.

## Inputs requis

- Objectifs stratégiques et critères de succès approuvés.
- Liste d'initiatives avec périmètre, sponsor, état, coûts ou efforts connus.
- Bénéfices attendus, preuves disponibles et horizon de réalisation.
- Dépendances, contraintes de capacité et risques connus.
- Règles de gouvernance et seuils d'arbitrage déjà approuvés.

## Sorties attendues

- Vue portefeuille reliant objectifs, initiatives, sponsors et résultats.
- Grille de priorisation avec critères pondérés uniquement si approuvés.
- Carte des dépendances, risques et contraintes de capacité à escalader.
- Registre de bénéfices avec baseline, owner, échéance et méthode de mesure à confirmer.
- Décisions de portefeuille proposées avec options de poursuivre, adapter, séquencer ou arrêter.

## Workflow recommandé

1. **Cadrer le portefeuille** : définir les objectifs, horizons, décideurs et critères d'inclusion.
2. **Normaliser les initiatives** : comparer leur périmètre, sponsor, état, effort, risques et bénéfices sans combler les données manquantes.
3. **Évaluer l'alignement** : relier chaque initiative à un objectif et distinguer les bénéfices mesurables des hypothèses.
4. **Analyser le portefeuille** : examiner les dépendances, concentration de risques, capacités et conflits de calendrier.
5. **Préparer les arbitrages** : formuler les options et conséquences, sans présenter un score indicatif comme une décision automatique.
6. **Suivre les bénéfices** : établir owner, baseline, mesure, fréquence et décision de réexamen après l'approbation.

## Garde-fous

- Ne jamais attribuer de gains chiffrés sans source, baseline et méthode de mesure.
- Rendre explicites les données manquantes et les biais de comparaison.
- Ne pas confondre valeur stratégique, urgence, faisabilité et retour financier.
- Tout poids ou score de priorisation doit être accepté par les décideurs et rester explicable.
- Signaler dépendances humaines, sociales, réglementaires et de continuité de service.
- Ne pas décider seul de l'arrêt d'une initiative ou de l'allocation de budgets.

## Template d'entrée (copier/coller)

```text
[Portefeuille]
- Objectifs stratégiques :
- Horizon / règles de décision :

[Initiatives]
- Nom / sponsor / état :
- Bénéfices attendus et preuves :
- Effort, dépendances et risques :

[Contraintes]
- Capacité / budget approuvés :
- Arbitrages attendus et décideurs :
```

## Template de sortie (copier/coller)

```text
[Vue portefeuille]
| Initiative | Objectif lié | Sponsor | Bénéfice / preuve | Dépendances / risques | Décision à préparer |
|---|---|---|---|---|---|

[Arbitrages]
- Option :
- Conséquences / incertitudes :
- Validation requise :

[Suivi des bénéfices]
- Indicateur / baseline / owner / date de revue :
```

## Checklist QA interne

- [ ] Chaque initiative est liée à un objectif explicite et à un sponsor.
- [ ] Les bénéfices sont identifiés comme mesurés, estimés ou hypothétiques.
- [ ] Dépendances, capacités et risques de portefeuille sont visibles.
- [ ] Les critères et éventuels poids de priorisation sont approuvés et explicables.
- [ ] Les décisions proposées sont clairement réservées aux décideurs.

## KPI reliés

- Part des initiatives avec sponsor, objectif et bénéfice défini.
- Taux de bénéfices vérifiés à l'échéance : bénéfices vérifiés / bénéfices arrivés à échéance.
- Part des initiatives en cours avec dépendances critiques et owner identifiés.
- Écart entre effort prévu et effort observé, si les données sont disponibles et comparables.

## Definition of done

- [ ] Le périmètre du portefeuille et les critères de décision sont documentés.
- [ ] Les initiatives et informations manquantes sont présentées de façon comparable.
- [ ] Les arbitrages incluent conséquences, dépendances et incertitudes.
- [ ] Un mécanisme de suivi des bénéfices est défini avec owners et échéances.

## Exemples d'usage

### Exemple 1 : Réduction des délais de service
**Contexte** : Une direction dispose de quatre initiatives visant à réduire les délais de traitement.
**Input** : Elle fournit les sponsors, estimations d'effort et bénéfices espérés, mais seules deux initiatives ont une baseline vérifiée.
**Output** : Comparer l'alignement et les dépendances, distinguer bénéfices mesurés et hypothétiques et demander aux sponsors de compléter les baselines avant l'arbitrage.

### Exemple 2 : Revue trimestrielle d'un programme
**Contexte** : Un programme de transformation a plusieurs chantiers et doit faire l'objet d'une décision de poursuite.
**Input** : Le sponsor fournit l'état des chantiers, les risques, la capacité engagée et les bénéfices observés.
**Output** : Produire une synthèse des écarts et options (poursuivre, adapter, séquencer), avec décisions et owners à confirmer par le comité.

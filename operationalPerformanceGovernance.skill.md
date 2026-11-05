# Operational Performance System & Governance

## Objectif

Concevoir un système de pilotage opérationnel reliant objectifs, indicateurs, owners, seuils d'attention et instances de décision. Le skill formalise la gouvernance et les actions attendues; il ne construit pas de pipeline de données ni de dashboard technique.

## Quand l'utiliser (triggers)

- Définir les résultats et indicateurs suivis par une direction opérationnelle.
- Mettre en place une revue de performance périodique et ses règles d'escalade.
- Clarifier qui est responsable d'un KPI, d'une décision ou d'une action corrective.
- Réduire les indicateurs redondants ou sans décision associée.
- Harmoniser les indicateurs entre plusieurs unités ou sites.

**Déclencheurs** :
- « Mets en place notre gouvernance de performance opérationnelle »
- « Quels indicateurs doit suivre le comité des opérations ? »
- « Clarifie les owners et le rythme de revue des KPI »

## Hors périmètre

- L'analyse statistique, les requêtes SQL, la qualité des données et la construction de dashboards relèvent de l'agent d'analyse de données.
- Les KPI détaillés d'un processus et sa cartographie relèvent de l'agent d'optimisation des processus métier.
- La gouvernance des métadonnées, la classification ou le lineage relèvent de l'agent de gouvernance des données.
- Le reporting comptable ou fiscal relève de l'agent d'information comptable et du professionnel qualifié.
- L'agent ne certifie pas la qualité des données et ne fixe pas seul les objectifs de performance.

## Inputs requis

- Objectifs opérationnels et décisions que les instances doivent prendre.
- Indicateurs actuels, définitions, sources connues et limites de qualité.
- Owners, fréquence de mise à jour et instances existantes.
- Seuils, engagements de service ou objectifs approuvés, s'ils existent.
- Contraintes de confidentialité et d'accès aux données.

## Sorties attendues

- Arbre de résultats et catalogue d'indicateurs avec définition et owner.
- Proposition de cadence, participants, ordre du jour et règles d'escalade.
- Matrice des droits de décision et des actions de suivi.
- Liste des définitions et sources à valider avec l'agent d'analyse de données ou les owners.
- Plan de revue pour retirer les indicateurs inutiles ou réviser les seuils.

## Workflow recommandé

1. **Partir des décisions** : préciser les décisions de gestion que le pilotage doit rendre possibles.
2. **Relier les résultats** : organiser les résultats de haut niveau et les mesures opérationnelles contributrices.
3. **Spécifier chaque indicateur** : nom, définition, formule à valider, unité, owner, source, fréquence et limites.
4. **Définir la gouvernance** : participants, cadence, seuils approuvés, escalades et suivi des actions.
5. **Vérifier la faisabilité** : signaler les données manquantes et demander l'avis de l'agent d'analyse de données si nécessaire.
6. **Installer l'amélioration continue** : revoir périodiquement la pertinence des indicateurs et décisions associées.

## Garde-fous

- Ne jamais fabriquer une baseline, une cible, un seuil ou une formule métier.
- Séparer les indicateurs avancés, résultats observés et simples activités.
- Associer chaque KPI à une décision ou préciser pourquoi il est informatif.
- Indiquer les risques de comparaison si les définitions ou périodes diffèrent.
- Limiter les données personnelles et opérationnelles au strict nécessaire.
- Ne pas présenter une corrélation comme une causalité.

## Template d'entrée (copier/coller)

```text
[Objectifs et décisions]
- Résultats à piloter :
- Décisions attendues :

[Indicateurs existants]
- Nom / définition / source / fréquence :
- Owner / cible / seuil approuvé :

[Gouvernance]
- Instances et participants :
- Contraintes ou problèmes constatés :
```

## Template de sortie (copier/coller)

```text
[Arbre de résultats]
- Objectif :
- Résultats / mesures contributrices :

[Catalogue de pilotage]
| KPI | Définition à valider | Owner | Source / fréquence | Décision liée |
|---|---|---|---|---|

[Cadence et escalade]
- Instance / participants :
- Revue / décisions :
- Règle d'escalade :
- Données à valider avec Data :
```

## Checklist QA interne

- [ ] Chaque indicateur est relié à une décision ou à un résultat explicite.
- [ ] Owner, définition, source et fréquence sont identifiés ou marqués à confirmer.
- [ ] Cibles et seuils ne sont pas inventés.
- [ ] La cadence de gouvernance comprend une gestion des actions et des escalades.
- [ ] Les limites de comparabilité et de qualité des données sont visibles.

## KPI reliés

- Part des KPI avec owner et définition validée : KPI complets / KPI retenus.
- Taux d'actions de revue clôturées à la date convenue.
- Part des instances de performance ayant produit une décision ou action documentée.

## Definition of done

- [ ] Les objectifs et décisions du système de pilotage sont définis.
- [ ] Un catalogue initial d'indicateurs et leurs owners est fourni.
- [ ] La cadence, les responsabilités et escalades sont documentées.
- [ ] Les validations Data et métier restantes sont listées explicitement.

## Exemples d'usage

### Exemple 1 : Revue mensuelle des opérations
**Contexte** : Une direction examine chaque mois une vingtaine d'indicateurs, mais les réunions ne débouchent pas sur des décisions claires.
**Input** : L'équipe fournit les indicateurs, leurs owners, les instances et les décisions attendues.
**Output** : Regrouper les mesures autour des décisions, proposer owners et ordre du jour, et marquer comme « à valider » les définitions et seuils absents.

### Exemple 2 : Indicateurs entre sites
**Contexte** : Deux sites veulent comparer leurs délais de traitement.
**Input** : Les sites ont des définitions et périodes de mesure qui peuvent différer.
**Output** : Construire une grille de comparabilité, signaler les définitions à harmoniser avec l'agent d'analyse de données et suspendre toute conclusion de classement jusqu'à validation.

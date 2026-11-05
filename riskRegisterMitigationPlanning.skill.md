# Risk Register & Mitigation Planning

## Objectif
Construire et maintenir un registre des risques structuré (identification, catégorisation, cotation probabilité x impact, priorisation), définir des plans de mitigation et de contingence, applicable à tout type de projet (informatique, BTP, événementiel, marketing, R&D, industriel, associatif).

## Quand l'utiliser (triggers)
- « registre des risques », « risk register », « coter un risque », « matrice probabilité impact ».
- « plan de mitigation », « plan de contingence », « criticité », « aléas », « points de vigilance ».
- Lancement d'un nouveau projet nécessitant une cartographie des risques initiale.
- Revue périodique de risques (comité de pilotage, jalon projet).

## Hors périmètre
- Analyse de coûts détaillée (budget, ROI, arbitrages financiers) → l'agent FinOps.
- Conformité légale/RGPD (traitement de données personnelles, obligations réglementaires) → l'agent de conformité RGPD.
- Planification de projet/jalons (planning, chemin critique, allocation ressources) → l'agent de planification.

## Inputs requis
- Périmètre du projet (objectifs, livrables, contraintes majeures).
- Retours d'expérience projets similaires (leçons apprises, incidents passés).
- Liste des parties prenantes et acteurs impliqués.
- Contraintes connues (délais, budget, ressources, dépendances externes).
- Échelle de cotation retenue (1-5 ou 1-3) et seuils de criticité de l'organisation.

## Sorties attendues
- Registre des risques structuré (tableau ID, description, catégorie, probabilité, impact, criticité, plan de mitigation, owner, statut).
- Matrice probabilité/impact visuelle (zones critique/élevé/normal).
- Plans de mitigation et de contingence documentés pour les risques prioritaires.
- Rapport de synthèse (top risques, tendances, recommandations).

## Workflow recommandé
1. Identification des risques (brainstorming avec parties prenantes, retours d'expérience, checklist par domaine : technique, business, légal, opérationnel, financier).
2. Catégorisation de chaque risque identifié (technique/business/légal/opérationnel/financier).
3. Cotation probabilité x impact pour chaque risque sur une échelle définie (1-5 ou 1-3), en s'appuyant sur les données historiques disponibles ou l'avis d'experts.
4. Priorisation via matrice probabilité/impact, classement en zones critique/élevé/normal.
5. Définition d'un plan de mitigation pour chaque risque prioritaire (actions préventives concrètes, responsable désigné, échéance).
6. Définition d'un plan de contingence pour les risques critiques (actions curatives à déclencher si le risque se matérialise, seuils de déclenchement).
7. Suivi et mise à jour périodique du registre (revue de risques lors des comités, réévaluation de la cotation, clôture des risques éteints).

## Garde-fous
- Chaque risque doit avoir un owner nommé (pas de risque orphelin).
- La cotation doit être justifiée (pas de cotation arbitraire sans argumentation minimale).
- Les risques critiques doivent systématiquement disposer d'un plan de contingence, pas uniquement d'un plan de mitigation.
- Le registre doit être revu à une fréquence définie (au minimum à chaque jalon majeur du projet).
- Ne pas confondre risque (événement incertain futur) et problème (déjà survenu) : un problème avéré relève du suivi d'incidents, pas du registre de risques.

## Template d'entrée (copier/coller)
```text
[Projet]
- Nom : ...
- Objectif : ...
- Périmètre : ...
- Contraintes connues : ...

[Contexte risques]
- Retours d'expérience projets similaires : ...
- Parties prenantes impliquées : ...
- Échelle de cotation retenue : ...
```

## Template de sortie (copier/coller)
```text
[Registre des risques]
| ID | Description | Catégorie | Probabilité | Impact | Criticité | Plan de mitigation | Owner | Statut |
|----|--------------|-----------|-------------|--------|-----------|---------------------|-------|--------|
| R1 | ... | ... | ... | ... | ... | ... | ... | ... |

[Plans de contingence (risques critiques)]
- Risque R1 : action curative, déclencheur, responsable.

[Synthèse]
- Nb risques critiques : ...
- Nb risques mitigés : ...
- Recommandations : ...
```

## Checklist QA interne
- Chaque risque a un ID unique, une description claire et une catégorie.
- Chaque risque a une cotation probabilité/impact justifiée.
- Chaque risque prioritaire a un plan de mitigation avec responsable et échéance.
- Chaque risque critique a un plan de contingence associé.
- Le registre est daté et versionné (traçabilité des mises à jour).

## KPI reliés
- Nombre de risques critiques non mitigés.
- Taux de risques matérialisés (risques survenus / risques identifiés).
- Délai moyen de mitigation (temps entre identification et clôture/réduction du risque).
- Fréquence de revue du registre (respect du cycle défini).

## Definition of done
- Registre des risques créé et partagé avec les parties prenantes.
- Matrice probabilité/impact produite et validée.
- Plans de mitigation et de contingence définis pour tous les risques critiques/élevés.
- Première revue de suivi planifiée.

## Exemples d'usage

### Exemple 1 : Lancement d'un projet de migration ERP
**Contexte** : Une PME industrielle lance un projet de migration de son ERP legacy vers une solution cloud, avec un budget serré et une équipe IT réduite.
**Action** : L'agent l'agent d'analyse des risques anime un atelier d'identification avec les équipes IT, finance et opérations, catégorise 18 risques identifiés (dont dépendance à un prestataire unique, perte de données lors de la migration, résistance au changement des utilisateurs), les cote sur une échelle 1-5, et priorise 4 risques critiques nécessitant un plan de contingence (dont un plan de rollback vers l'ancien système en cas d'échec de bascule).
**Résultat** : Un registre de 18 risques est livré avec 4 plans de mitigation actifs et 4 plans de contingence documentés ; lors du go-live, le risque de perte de données s'est partiellement matérialisé mais le plan de contingence (sauvegarde complète pré-bascule) a permis une restauration en moins de 2 heures sans impact business majeur.

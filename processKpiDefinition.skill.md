# Process KPI Definition

## Objectif
Définir KPI processus métier SMART (Specific, Measurable, Achievable, Relevant, Time-bound) pour pilotage amélioration continue.

## Quand l'utiliser (triggers)
- « KPI processus », « indicateurs performance », « mesure processus », « dashboard métier », « SMART KPI ».
- Pilotage processus post-amélioration.
- Monitoring processus critiques.

## Hors périmètre
- KPI techniques (infra, app) → agents techniques.
- Dashboards implémentation (Power BI, Tableau) → outils BI externes.
- Analyse financière ROI → l'agent produit.

## Inputs requis
- Processus à mesurer (nom, objectifs).
- Dimensions mesure (temps, qualité, coût, satisfaction).
- Baseline actuelle (si disponible).
- Cibles (objectifs quantifiés).

## Sorties attendues
- Liste KPI SMART (nom, formule, baseline, target, fréquence collecte).
- Dashboard mockup (structure, visualisations recommandées).
- Plan collecte données (sources, responsables).

## Workflow recommandé
1. Identifier dimensions clés :
   - Temps : cycle time, lead time, takt time, waiting time.
   - Qualité : taux défauts, rework rate, First Pass Yield (FPY).
   - Coût : cost per transaction, coût processus total.
   - Satisfaction : NPS, CSAT clients/utilisateurs.
2. Définir KPI SMART :
   - Exemple : « Réduire cycle time onboarding employé de 12j (baseline) à 5j (target) d’ici 6 mois. Mesure : date demande → date accès complet IT. Collecte : mensuelle, responsable RH. »
3. Dashboard structure :
   - KPI temps : line charts (évolution cycle time).
   - KPI qualité : gauges (taux défauts vs target).
   - KPI coût : bar charts (coût par département).
4. Plan collecte données (extraction logs systèmes, saisie manuelle si nécessaire).

## Garde-fous
- KPI SMART obligatoire (pas vagues « améliorer qualité »).
- Baseline documentée (pas target sans baseline).
- Fréquence collecte réaliste (mensuelle, pas quotidienne si trop lourd).
- Responsable KPI désigné (ownership).

## Template d'entrée (copier/coller)
```text
[Processus]
- Nom : ...
- Objectifs : ...

[Dimensions]
- Temps/qualité/coût/satisfaction : ...

[Baseline]
- Valeurs actuelles : ...
```

## Template de sortie (copier/coller)
```text
[KPI SMART]
- KPI 1 : nom, formule, baseline, target, fréquence
- KPI 2 : ...

[Dashboard mockup]
- Structure : ...
- Visualisations : ...

[Plan collecte]
- Sources : ...
- Responsables : ...
```

## Checklist QA interne
- KPI SMART (tous critères).
- Baseline documentée.
- Target quantifiée.
- Fréquence collecte définie.
- Responsable désigné.

## KPI reliés
- Nb KPI processus (complexité).
- Taux KPI atteignant target (%).
- Fréquence revue KPI (mensuelle).

## Definition of done
- KPI définis (SMART).
- Dashboard mockup publié.
- Plan collecte documenté.

## Exemples d'usage

### Exemple 1 : [Titre du cas d'usage]
**Contexte** : [Description de la situation]
**Action** : [Ce qui a été fait]
**Résultat** : [Résultat obtenu]
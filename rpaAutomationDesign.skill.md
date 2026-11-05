# RPA Automation Design

## Objectif
Concevoir automatisations RPA (UiPath, Power Automate) pour tâches répétitives métier UI/documents (hors intégrations techniques API).

## Quand l'utiliser (triggers)
- « RPA », « UiPath », « Power Automate », « automatise tâches manuelles », « data entry », « scraping UI ».
- Automatisation tâches UI (saisie formulaires, extraction données écrans).
- Automatisation documents (OCR, extraction PDF, Excel).

## Hors périmètre
- Automatisation technique (API, webhooks, ETL) → l'agent d'intégration et d'automatisation.
- Processus métier modélisation → skill BPMN Process Modeling.
- Développement code custom → agents dev.

## Inputs requis
- Tâches à automatiser (description, fréquence, volumes).
- Systèmes UI (applications legacy, web apps, Excel).
- Objectif ROI (réduction temps, élimination erreurs).

## Sorties attendues
- Workflow RPA (UiPath .xaml, Power Automate flow JSON export).
- Spécifications automation (steps, inputs/outputs, error handling).
- ROI estimé (heures économisées, coût bot vs humain).

## Workflow recommandé
1. Identifier tâches candidates RPA (règles claires, UI stable, volumes élevés).
2. Concevoir workflow :
   - UiPath : Sequences, Flowcharts, Activities (Click, Type Into, Get Text, Data Scraping).
   - Power Automate : Cloud flows (trigger, actions, conditions), Desktop flows (UI automation).
3. Error handling (Try-Catch, retries, screenshots on failure).
4. Logging (logs transactions, succès/échecs, durée).
5. Tester (environnement dev, données test).
6. Déployer (UiPath Orchestrator, Power Automate unattended).

## Garde-fous
- UI stable (éviter RPA si UI change fréquemment, fragile).
- Error handling robuste (Try-Catch, retries max 3, fallback humain).
- Logging détaillé (audit trail, troubleshooting).
- ROI justifié (coût bot license vs économies humaines).

## Template d'entrée (copier/coller)
```text
[Tâche]
- Description : ...
- Fréquence : ...
- Volumes : ...

[Systèmes]
- UI/apps : ...

[Objectif ROI]
- Heures économisées : ...
```

## Template de sortie (copier/coller)
```text
[Workflow RPA]
- Outil : UiPath/Power Automate
- Steps : ...

[Error handling]
- Try-Catch : ...
- Retries : ...

[ROI]
- Heures économisées : ...
- Coût bot vs humain : ...
```

## Checklist QA interne
- Workflow testé (dev env).
- Error handling (Try-Catch).
- Logging détaillé.
- ROI justifié (> 0).
- UI stable (pas changes fréquents).

## KPI reliés
- Heures économisées/mois.
- Taux succès bot (%).
- Nb erreurs/jour (cible < 5%).

## Definition of done
- Workflow RPA créé et testé.
- Error handling validé.
- ROI publié.

## Exemples d'usage

### Exemple 1 : [Titre du cas d'usage]
**Contexte** : [Description de la situation]
**Action** : [Ce qui a été fait]
**Résultat** : [Résultat obtenu]
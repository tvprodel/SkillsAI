# BPMN Process Modeling

## Objectif
Modéliser processus métier en BPMN 2.0 (Business Process Model and Notation) pour analyse, optimisation et communication stakeholders.

## Quand l'utiliser (triggers)
- « modélise processus », « BPMN », « cartographie processus », « process mapping », « workflow métier ».
- Analyse processus as-is.
- Conception processus to-be.
- Communication processus stakeholders non techniques.

## Hors périmètre
- Automatisation technique (API, webhooks) → l'agent d'intégration et d'automatisation.
- RPA implémentation détaillée → skill RPA Automation Design.
- Process mining (extraction logs) → outils externes (Celonis, ProM).

## Inputs requis
- Processus à modéliser (description textuelle, interviews stakeholders).
- Acteurs (pools/lanes).
- Activités, décisions (gateways), événements.
- Objectif (as-is analysis, to-be design).

## Sorties attendues
- Diagramme BPMN 2.0 (.bpmn XML, SVG/PNG export).
- Documentation annotations (waste, goulots, temps).
- Rapport analyse (lead time, nb handoffs, opportunités amélioration).

## Workflow recommandé
1. Interviews stakeholders (identifier activités, décisions, acteurs).
2. Modéliser BPMN (Camunda Modeler, Bizagi, Lucidchart) :
   - Pools : organisations/départements.
   - Lanes : rôles acteurs (manager, employee, système).
   - Activités : tâches (rectangles).
   - Gateways : décisions (diamants XOR, AND, OR).
   - Events : start/intermediate/end (circles).
   - Flux : séquence (flèches).
3. Annoter waste (waiting time, rework loops, handoffs excessifs).
4. Calculer lead time (somme durées activités + waiting).
5. Identifier opportunités (éliminer handoffs, automatiser tâches manuelles, paralléliser).

## Garde-fous
- BPMN 2.0 syntax valide (Camunda Modeler validation).
- Pools/lanes bien définis (acteurs clairs).
- Gateways logique correcte (XOR exclusive, AND parallel, OR inclusive).
- Annotations explicites (temps, volumes, pain points).

## Template d'entrée (copier/coller)
```text
[Processus]
- Nom : ...
- Objectif : as-is/to-be

[Acteurs]
- Pools/lanes : ...

[Activités]
- Liste : ...
```

## Template de sortie (copier/coller)
```text
[Diagramme BPMN]
- Fichier .bpmn : ...
- Export SVG : ...

[Analyse]
- Lead time : ...
- Nb handoffs : ...
- Waste identifié : ...

[Opportunités]
- Amélioration 1 : ...
- Amélioration 2 : ...
```

## Checklist QA interne
- BPMN 2.0 valide.
- Pools/lanes définis.
- Gateways logique correcte.
- Lead time calculé.
- Waste annoté.

## KPI reliés
- Lead time processus (jours).
- Nb handoffs (complexité).
- Nb activités (granularité).

## Definition of done
- Diagramme BPMN créé.
- Analyse lead time publiée.
- Opportunités identifiées.

## Exemples d'usage

### Exemple 1 : [Titre du cas d'usage]
**Contexte** : [Description de la situation]
**Action** : [Ce qui a été fait]
**Résultat** : [Résultat obtenu]
# Knowledge Curator (RAG / Docs Ops)

## Objectif
Assurer une base de connaissance fiable, a jour et exploitable par les agents.

## Quand l'utiliser (triggers)
- Reponses obsoletes/hallucinees.
- Sources contradictoires.
- Documentation eparpillee.

## Hors périmètre
- Redaction marketing pure.
- Refactor applicatif sans enjeu documentaire.

## Inputs requis
- Corpus docs existant.
- Regles de priorite des sources.
- Frequences de mise a jour.

## Sorties attendues
- Cartographie des sources de verite.
- Politique de freshness.
- Regles de curation et archivage.
- Plan d'indexation.

## Workflow recommandé
1. Inventorier sources.
2. Classer fiabilite.
3. Definir governance de mise a jour.
4. Auditer periodiquement la qualite.

## Garde-fous
- Une source primaire par domaine critique.
- Historiser les changements majeurs.
- Eviter la duplication non maitrisee.

## Template d'entrée (copier/coller)
```text
[Corpus]
- Sources : ...
- Volumetrie : ...

[Problemes]
- Obsolescence : ...
- Contradictions : ...
```

## Template de sortie (copier/coller)
```text
[Sources de verite]
- Domaine A : ...

[Regles]
- Freshness : ...
- Archivage : ...

[Plan d'action]
1) ...
2) ...
```

## Checklist QA interne
- Sources owner-assignees.
- Regles de mise a jour publiees.
- Contradictions resolues.

## KPI reliés
- Taux d'information obsolete.
- Taux de correction documentaire.
- Temps de resolution incoherences.

## Definition of done
- Base de connaissance gouvernee et auditable.
- Reduction mesurable des erreurs de contexte.

## Exemples d'usage

### Exemple 1 : [Titre du cas d'usage]
**Contexte** : [Description de la situation]
**Action** : [Ce qui a été fait]
**Résultat** : [Résultat obtenu]
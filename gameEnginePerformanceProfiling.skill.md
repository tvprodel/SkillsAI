# Game Engine Performance & Profiling

## Objectif
Optimiser les performances runtime d'un projet jeu (CPU, GPU, memoire, frame pacing) via profiling structure.

## Quand l'utiliser (triggers)
- Chutes de FPS, stutters, freeze intermittents.
- Scenes lourdes ou consommation memoire anormale.
- Preparation d'une build cible plateforme.

## Hors périmètre
- Design gameplay sans enjeu perf.
- Marketing ou contenu non technique.

## Inputs requis
- Version moteur (ex: Godot 4.x).
- Plateformes cibles.
- Scene/script a probleme et symptomes observes.

## Sorties attendues
- Diagnostic perf priorise.
- Plan d'optimisation incremental.
- Checklist de validation post-correctif.

## Workflow recommandé
1. Baseline de performance (FPS, frametime, memoire).
2. Profiling CPU/GPU pour isoler les hotspots.
3. Optimisations ciblees (draw calls, allocations, physics, streaming).
4. Re-mesure et comparaison avant/apres.

## Garde-fous
- Ne pas optimiser sans mesure.
- Eviter les micro-optimisations hors hotspots.
- Conserver la lisibilite du code.

## Template d'entrée (copier/coller)
```text
[Contexte]
- Moteur/version : ...
- Plateforme : ...
- Symptomatologie : ...

[Objectif]
- Cible FPS/frametime : ...
```

## Template de sortie (copier/coller)
```text
[Hotspots]
1) ...
2) ...

[Optimisations]
1) ...
2) ...

[Avant/Apres]
- FPS : ... -> ...
- Frametime : ... -> ...
```

## Checklist QA interne
- Baseline mesuree avant optimisation.
- Gains verifies apres correctifs.
- Risques de regression identifies.

## KPI reliés
- FPS moyen.
- Frametime P95.
- Utilisation memoire.

## Definition of done
- Hotspots critiques reduits.
- Gain mesurable documente.
- Build stable sur plateforme cible.

## Exemples d'usage

### Exemple 1 : [Titre du cas d'usage]
**Contexte** : [Description de la situation]
**Action** : [Ce qui a été fait]
**Résultat** : [Résultat obtenu]
# Cognitive Load Assessment

## Objectif
Évaluer la charge cognitive des interfaces et workflows pour identifier les points de surcharge mentale et proposer des simplifications basées sur la théorie de la charge cognitive (Sweller) et l'ergonomie cognitive.

## Quand l'utiliser (triggers)
- « charge cognitive élevée », « interface complexe », « trop d'informations », « utilisateurs perdus », « surcharge mentale »
- Audit UX d'interface dense (dashboards, formulaires complexes, workflows multi-étapes)
- Analyse parcours utilisateur avec taux abandon élevé
- Optimisation temps d'apprentissage (onboarding, nouveaux utilisateurs)
- Réduction erreurs utilisateurs (erreurs de saisie, clics erronés, confusion navigation)

## Hors périmètre
- Implémentation technique simplifications UI → l'agent frontend
- Rédaction micro-copie simplifiée → l'agent de microcopie (UX writing)
- Tests A/B quantitatifs charge cognitive → l'agent qualité
- Design visuel réduction bruit visuel → l'agent de direction artistique

## Inputs requis
- Interface/parcours à analyser (captures écran, maquettes, prototypes, URL prod)
- Contexte utilisateur (profil, expertise domaine, objectif tâche)
- Données comportementales si disponibles (heatmaps, session recordings, temps tâche, taux erreurs)
- Contraintes business (information obligatoire, workflow imposé)

## Sorties attendues
- Audit charge cognitive (score par écran/étape)
- Analyse détaillée (charge intrinsèque/extrinsèque/essentielle par zone)
- Carte chaleur cognitive (zones surcharge mentale)
- Recommandations simplification priorisées (impact élevé/moyen/faible)
- Plan d'action réduction charge cognitive

## Workflow recommandé

### 1. Décomposition tâche cognitive
- Identifier tâche principale utilisateur (objectif final)
- Décomposer en sous-tâches cognitives (étapes mentales nécessaires)
- Cartographier ressources attentionnelles requises (mémoire de travail, attention visuelle, prise de décision)
- **Output** : arbre tâches cognitives, ressources attentionnelles par étape

### 2. Mesure charge cognitive par type

**Charge intrinsèque** (complexité inhérente tâche) :
- Nombre éléments information nouveaux (concepts, termes techniques)
- Interactivité éléments (dépendances, relations entre informations)
- **Mesure** : nombre éléments interagissants, score complexité domaine (1-10)

**Charge extrinsèque** (complexité présentation) :
- Bruit visuel (éléments non essentiels, distractions)
- Organisation information (structure, hiérarchie, regroupement)
- Navigation cognitive (chemins mentaux pour trouver information)
- **Mesure** : nombre éléments visuels, profondeur navigation, score désorganisation (1-10)

**Charge essentielle** (effort construction schémas mentaux) :
- Apprentissage requis (nouveaux patterns, nouveaux comportements)
- Automatisation possible (tâche répétitive vs unique)
- **Mesure** : nombre patterns nouveaux, répétabilité tâche

### 3. Application lois ergonomie cognitive

**Loi de Hick** (temps décision = f(nombre choix)) :
- Mesurer nombre options par écran/étape
- Identifier décisions complexes (> 7 options = surcharge)
- **Recommandation** : réduire choix, chunking, organisation hiérarchique

**Loi de Fitts** (temps acquisition cible = f(distance, taille)) :
- Mesurer distance clics successifs (pixels)
- Mesurer taille cibles cliquables (boutons, liens)
- **Recommandation** : rapprocher actions fréquentes, agrandir cibles critiques

**Règle 7±2 (Miller)** (capacité mémoire de travail) :
- Compter éléments simultanés à mémoriser
- Identifier rétention information entre écrans
- **Recommandation** : chunking (regrouper 3-4 items), répétition information critique

### 4. Scoring charge cognitive

**Formule composite** :
```
Score Charge Cognitive = (Intrinsèque × 0.3) + (Extrinsèque × 0.5) + (Essentielle × 0.2)
```

**Grille notation** (0-100) :
- **0-30** : Charge faible (interface intuitive, workflow fluide)
- **31-60** : Charge modérée (améliorations possibles, points friction localisés)
- **61-80** : Charge élevée (surcharge mentale, risque abandon/erreurs élevé)
- **81-100** : Charge critique (interface inutilisable sans formation, refonte nécessaire)

### 5. Identification points de surcharge

**Carte chaleur cognitive** :
- Rouge : zones surcharge critique (> 80)
- Orange : zones charge élevée (61-80)
- Jaune : zones charge modérée (31-60)
- Vert : zones charge acceptable (< 30)

**Patterns surcharge fréquents** :
- Formulaires longs (> 10 champs visibles)
- Dashboards surchargés (> 15 widgets)
- Workflows multi-étapes (> 5 étapes sans progression visible)
- Terminologie technique dense (jargon métier non explicité)
- Navigation profonde (> 3 niveaux hiérarchie)

### 6. Recommandations simplification

**Réduction charge intrinsèque** :
- Glossaire termes techniques (tooltips, aide contextuelle)
- Exemples concrets (avant/après, cas d'usage)
- Formation intégrée (tutoriels, vidéos courtes)

**Réduction charge extrinsèque** :
- Progressive disclosure (masquer détails avancés par défaut)
- Chunking visuel (regrouper informations liées, espacements)
- Réduction bruit visuel (supprimer éléments non essentiels)
- Navigation simplifiée (breadcrumb, raccourcis, menu contextuel)

**Optimisation charge essentielle** :
- Patterns familiers (conventions UI standard, métaphores connues)
- Cohérence interface (même pattern = même fonction)
- Affordances claires (boutons ressemblent à des boutons)

### 7. Validation empirique

**Méthodes recommandées** :
- Tests utilisateurs avec think-aloud (verbatims charge mentale)
- Mesure temps tâche (baseline vs après simplification)
- Questionnaire NASA-TLX (charge de travail perçue)
- Eye-tracking si disponible (fixations, saccades = charge attentionnelle)

## Garde-fous
- **Toujours contextualiser** : charge cognitive acceptable dépend de l'expertise utilisateur (novice vs expert)
- **Éviter simplification excessive** : ne pas infantiliser utilisateurs experts
- **Mesurer impact réel** : post-simplification, valider réduction erreurs/temps tâche
- **Prioriser réductions extrinsèques** : plus faciles à implémenter, impact immédiat
- **Respecter contraintes métier** : information obligatoire légale/réglementaire ne peut être cachée
- **Références scientifiques** : citer Sweller (charge cognitive), Miller (7±2), Hick (temps décision), Fitts (acquisition cible)

## Template d'entrée (copier/coller)
```text
[Interface à analyser]
- Type : écran / parcours / workflow
- Objectif utilisateur : ...
- Profil utilisateur : novice / intermédiaire / expert
- Captures/URL : ...

[Données comportementales disponibles]
- Temps moyen tâche : ...
- Taux erreurs : ...
- Taux abandon : ...
- Heatmaps/recordings : oui / non

[Contraintes]
- Information obligatoire : ...
- Workflow imposé : ...
```

## Template de sortie (copier/coller)
```text
[Score Charge Cognitive]
- Score global : X/100
- Charge intrinsèque : X/100
- Charge extrinsèque : X/100
- Charge essentielle : X/100

[Carte chaleur cognitive]
Zone 1 : [nom zone] | Score : X | Couleur : rouge/orange/jaune/vert
Zone 2 : ...

[Recommandations simplification]
1) [Action] | Impact : élevé/moyen/faible | Justification : [théorie cognitive] | Références : [Sweller 1988, etc.]
2) ...

[Plan d'action priorisé]
- Court terme (< 1 semaine) : ...
- Moyen terme (1-4 semaines) : ...
- Long terme (> 1 mois) : ...

[Validation empirique suggérée]
- Méthode : ...
- Critères succès : ...
```

## Checklist QA interne
- [ ] Tâche cognitive principale identifiée et décomposée
- [ ] Charge intrinsèque/extrinsèque/essentielle mesurée séparément
- [ ] Lois ergonomie cognitive appliquées (Hick, Fitts, Miller)
- [ ] Score charge cognitive calculé (0-100)
- [ ] Carte chaleur cognitive produite (zones critique/élevée/modérée/acceptable)
- [ ] Recommandations simplification liées à théories scientifiques
- [ ] Références scientifiques citées (APA style)
- [ ] Priorisation recommandations (impact élevé/moyen/faible)
- [ ] Validation empirique suggérée (méthode + critères succès)
- [ ] Contraintes métier respectées

## KPI reliés
- **Score charge cognitive** : 0-100 (cible < 60)
- **Temps moyen tâche** : secondes (cible : réduction 20-30% post-simplification)
- **Taux erreurs utilisateurs** : % (cible : réduction 50% post-simplification)
- **Taux abandon parcours** : % (cible : réduction 30% post-simplification)
- **Score NASA-TLX** : 0-100 (charge de travail perçue, cible < 50)
- **Nombre étapes workflow** : étapes (cible : < 5 étapes)
- **Nombre options par décision** : choix (cible : < 7 options, idéal 3-5)

## Definition of done
- Audit charge cognitive complet (score global + détail intrinsèque/extrinsèque/essentielle)
- Carte chaleur cognitive produite (visualisation zones surcharge)
- Recommandations simplification priorisées (impact + justification scientifique + références)
- Plan d'action détaillé (court/moyen/long terme)
- Validation empirique suggérée (méthode + critères succès)
- Rapport stocké dans `/docs/rapports/HumanSpecialist/cognitiveLoad_[nomProjet]_[date].md`

## Exemples d'usage

### Exemple 1 : [Titre du cas d'usage]
**Contexte** : [Description de la situation]
**Action** : [Ce qui a été fait]
**Résultat** : [Résultat obtenu]
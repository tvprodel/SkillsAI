# Behavioral Pattern Analysis (Analyse Patterns Comportementaux)

## Objectif
Analyser les patterns comportementaux utilisateurs en mobilisant la psychologie comportementale et les neurosciences pour identifier motivations, freins, biais cognitifs et proposer des nudges (incitations comportementales douces) afin d'améliorer adoption, engagement et complétion des parcours.

## Quand l'utiliser (triggers)
- « utilisateurs n'adoptent pas la feature », « taux abandon élevé », « engagement faible », « comportement inattendu »
- Lancement nouvelle fonctionnalité (prédire adoption)
- Optimisation parcours conversion (inscription, achat, complétion tâche)
- Analyse comportements déviants (contournements, erreurs récurrentes, non-utilisation features)
- Design nudges comportementaux (inciter bons comportements sans contraindre)

## Hors périmètre
- Implémentation technique nudges (boutons, notifications, gamification) → l'agent frontend
- Rédaction messages persuasifs (CTA, emails, notifications) → l'agent de copywriting
- Tests A/B quantitatifs comportements → l'agent qualité
- Analytics quantitatifs (funnel, rétention, cohortes) → l'agent FinOps

## Inputs requis
- Comportement observé (description factuelle : utilisateurs font X au lieu de Y)
- Données comportementales (taux adoption, taux abandon, session recordings, heatmaps, verbatims)
- Contexte utilisateur (profil, motivations présumées, contraintes environnement)
- Objectif comportemental (comportement souhaité, KPI cible)

## Sorties attendues
- Analyse pattern comportemental (description, fréquence, contexte)
- Hypothèses psychologiques (motivations, freins, biais cognitifs en jeu)
- Modèle COM-B (Capability-Opportunity-Motivation-Behavior mapping)
- Recommandations nudges (incitations comportementales douces)
- Plan d'expérimentation comportementale (validation hypothèses)

## Workflow recommandé

### 1. Observation et documentation comportement

**Collecte données comportementales** :
- Données quantitatives : taux adoption, taux abandon, temps tâche, fréquence utilisation
- Données qualitatives : session recordings (observation comportement), verbatims (interviews, support), heatmaps (zones cliquées/ignorées)
- **Output** : description factuelle comportement observé, fréquence, contexte

**Identification patterns récurrents** :
- Comportements majoritaires (> 70% utilisateurs)
- Comportements minoritaires mais significatifs (10-30%)
- Comportements déviants/contournements (< 10% mais signaux faibles importants)
- **Output** : typologie comportements (dominant/alternatif/déviant)

### 2. Analyse psychologique comportement

**Modèle COM-B (Michie et al.)** :
```
Behavior = f(Capability, Opportunity, Motivation)
```

**Capability (Capacité)** :
- Physique : utilisateur peut-il physiquement faire l'action ? (accessibilité motrice, visuelle)
- Psychologique : utilisateur a-t-il les connaissances/compétences ? (compréhension, expertise)
- **Diagnostic** : barrières capacité (manque formation, interface non accessible, terminologie incompréhensible)

**Opportunity (Opportunité)** :
- Physique : environnement permet-il l'action ? (temps disponible, équipement, connectivité)
- Sociale : normes sociales favorisent-elles l'action ? (pratiques collègues, culture org)
- **Diagnostic** : barrières opportunité (pas de temps, pas d'accès, normes défavorables)

**Motivation (Motivation)** :
- Réflexive : intentions conscientes, croyances, objectifs personnels
- Automatique : émotions, habitudes, impulsions
- **Diagnostic** : barrières motivation (pas d'intérêt perçu, émotions négatives, habitudes concurrentes)

**Output** : matrice COM-B (barrières identifiées par dimension)

### 3. Identification biais cognitifs

**Biais décisionnels (Kahneman & Tversky)** :
- **Biais de statu quo** : préférence pour situation actuelle, résistance changement
- **Aversion à la perte** : peur perte > espoir gain équivalent
- **Effect de cadrage** : formulation influence décision (verre à moitié plein vs vide)
- **Ancrage** : première information influence jugements suivants
- **Disponibilité heuristique** : surestimation événements récents/mémorables
- **Preuve sociale** : comportement influencé par comportement d'autrui
- **Biais de confirmation** : recherche informations confirmant croyances existantes

**Application à l'UX** :
- Identifier quels biais expliquent comportement observé
- Formuler hypothèses psychologiques testables
- **Output** : liste biais cognitifs actifs, hypothèses psychologiques

### 4. Design nudges comportementaux

**Nudge** = Incitation douce modifiant architecture de choix sans interdire options ni changer incitations économiques (Thaler & Sunstein).

**Types de nudges UX** :

**Nudges informationnels** :
- Feedback en temps réel (progression, impact actions)
- Comparaison sociale (« 80% utilisateurs ont complété cette étape »)
- Simplification information (mise en avant option recommandée)

**Nudges structurels** :
- Choix par défaut (option pré-sélectionnée)
- Ordre de présentation (option souhaitée en premier)
- Friction sélective (ajouter étapes pour comportements indésirables)

**Nudges temporels** :
- Rappels (notifications opportunes)
- Deadlines (urgence limitée dans le temps)
- Timing optimal (sollicitation au bon moment parcours)

**Nudges sociaux** :
- Preuve sociale (« utilisateurs comme vous ont choisi X »)
- Normes descriptives (« comportement majoritaire »)
- Témoignages (pairs, experts)

**Nudges émotionnels** :
- Gamification (points, badges, progression)
- Renforcement positif (célébrations micro-succès)
- Réduction anxiété (messages rassurants, reversibilité actions)

**Output** : catalogue nudges recommandés (type, mécanisme psychologique, implémentation suggérée)

### 5. Priorisation nudges (critères)

**Critères évaluation** :
- **Impact comportemental prédit** : élevé (changement > 30%) / moyen (10-30%) / faible (< 10%)
- **Facilité implémentation** : facile (< 1 semaine) / moyenne (1-4 semaines) / difficile (> 1 mois)
- **Éthique** : nudge transparent, réversible, dans intérêt utilisateur (pas de dark patterns)
- **Robustesse scientifique** : nudge validé empiriquement dans littérature

**Matrice priorisation** :
```
        | Impact Élevé      | Impact Moyen      | Impact Faible
--------|-------------------|-------------------|------------------
Facile  | PRIORITÉ 1 (GO)   | PRIORITÉ 2 (GO)   | PRIORITÉ 3 (Maybe)
Moyen   | PRIORITÉ 2 (GO)   | PRIORITÉ 3 (Maybe)| PRIORITÉ 4 (No)
Difficile| PRIORITÉ 3 (Maybe)| PRIORITÉ 4 (No)   | PRIORITÉ 5 (No)
```

**Output** : nudges priorisés (P1 > P2 > P3)

### 6. Plan d'expérimentation comportementale

**Hypothèses à tester** :
- H0 (hypothèse nulle) : nudge n'a pas d'effet
- H1 (hypothèse alternative) : nudge augmente comportement souhaité de X%

**Méthode expérimentale** :
- Design : A/B test (groupe contrôle vs groupe nudge)
- Échantillon : taille minimale (calcul puissance statistique)
- Durée : 2-4 semaines minimum (capturer variabilité temporelle)
- Métriques : KPI primaire (taux adoption, taux complétion), KPI secondaires (satisfaction, temps tâche)

**Critères succès** :
- Augmentation KPI primaire > X% (seuil prédéfini)
- Significativité statistique (p < 0.05)
- Pas d'effet négatif secondaire (satisfaction maintenue)

**Output** : protocole expérimentation (design, échantillon, durée, métriques, critères succès)

### 7. Rapport analyse comportementale

**Structure rapport** :
1. Comportement observé (description factuelle, fréquence)
2. Analyse COM-B (barrières capacité/opportunité/motivation)
3. Biais cognitifs identifiés (hypothèses psychologiques)
4. Recommandations nudges (priorisés P1/P2/P3)
5. Plan expérimentation (protocole validation)
6. Références scientifiques (COM-B, nudges, biais cognitifs)

**Stockage** : `/docs/rapports/HumanSpecialist/behavioral_[nomProjet]_[date].md`

## Garde-fous
- **Éthique nudges** : transparence (utilisateur conscient), réversibilité (peut opt-out), bénéfice utilisateur (pas dark patterns manipulation)
- **Pas de dark patterns** : interdire shame tactics, fausse urgence, culpabilisation, friction excessive opt-out
- **Validation empirique obligatoire** : tout nudge doit être testé (A/B test) avant généralisation
- **Respect autonomie** : nudge incite, ne contraint jamais ; liberté choix préservée
- **Contextualiser** : nudge efficace dans contexte A peut échouer dans contexte B (tester)
- **Références scientifiques** : citer Thaler & Sunstein (Nudge), Kahneman (biais cognitifs), Michie (COM-B), Cialdini (influence sociale)

## Template d'entrée (copier/coller)
```text
[Comportement observé]
- Description : utilisateurs font X au lieu de Y
- Fréquence : ...
- Données quantitatives : taux adoption X%, taux abandon Y%
- Données qualitatives : verbatims, session recordings

[Contexte utilisateur]
- Profil : ...
- Motivations présumées : ...
- Contraintes environnement : ...

[Objectif comportemental]
- Comportement souhaité : ...
- KPI cible : augmenter X de ...% / réduire Y de ...%
```

## Template de sortie (copier/coller)
```text
[Analyse COM-B]
Capability : barrières ...
Opportunity : barrières ...
Motivation : barrières ...

[Biais cognitifs identifiés]
1) [Nom biais] : manifestation ..., impact comportement ...
2) ...

[Hypothèses psychologiques]
H1 : Si [condition], alors [comportement prédit], car [mécanisme psychologique]
H2 : ...

[Recommandations nudges]
Nudge 1 : [Type] | Mécanisme : ... | Implémentation : ... | Impact prédit : élevé/moyen/faible | Priorité : P1/P2/P3 | Références : [Thaler 2008, etc.]
Nudge 2 : ...

[Plan expérimentation]
- Design : A/B test (contrôle vs nudge)
- Échantillon : ...
- Durée : ...
- Métriques : KPI primaire ..., KPI secondaires ...
- Critères succès : ...
```

## Checklist QA interne
- [ ] Comportement observé documenté (description factuelle, fréquence, données quanti/quali)
- [ ] Analyse COM-B complète (barrières capacité/opportunité/motivation identifiées)
- [ ] Biais cognitifs identifiés (minimum 2 biais pertinents)
- [ ] Hypothèses psychologiques formulées (testables)
- [ ] Nudges recommandés (minimum 3 nudges)
- [ ] Nudges éthiques (transparence, réversibilité, bénéfice utilisateur vérifiés)
- [ ] Priorisation nudges (matrice impact/facilité)
- [ ] Plan expérimentation défini (design, échantillon, durée, métriques, critères succès)
- [ ] Références scientifiques citées (APA style)
- [ ] Pas de dark patterns (vérification explicite)

## KPI reliés
- **Taux adoption comportement souhaité** : % (cible : augmentation 30-50% post-nudge)
- **Taux abandon parcours** : % (cible : réduction 30-50% post-nudge)
- **Engagement utilisateurs** : fréquence utilisation, durée session (cible : +20%)
- **Taux complétion tâche** : % (cible : +30% post-nudge)
- **Satisfaction utilisateurs** : score NPS, CSAT (cible : maintien ou amélioration)
- **Temps moyen tâche** : secondes (cible : neutre ou réduction, pas augmentation)

## Definition of done
- Analyse COM-B complète (barrières capacité/opportunité/motivation documentées)
- Biais cognitifs identifiés (minimum 2 biais pertinents au comportement)
- Hypothèses psychologiques formulées (testables empiriquement)
- Recommandations nudges priorisées (P1/P2/P3, minimum 3 nudges)
- Vérification éthique (pas de dark patterns, transparence/réversibilité/bénéfice confirmés)
- Plan expérimentation détaillé (design A/B test, échantillon, métriques, critères succès)
- Rapport stocké dans `/docs/rapports/HumanSpecialist/behavioral_[nomProjet]_[date].md`

## Exemples d'usage

### Exemple 1 : [Titre du cas d'usage]
**Contexte** : [Description de la situation]
**Action** : [Ce qui a été fait]
**Résultat** : [Résultat obtenu]
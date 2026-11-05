# Inclusive Design Psychology (Psychologie Design Inclusif)

## Objectif
Garantir l'accessibilité cognitive et le design inclusif en prenant en compte la neurodiversité (TDAH, autisme, dyslexie, troubles apprentissage) et les handicaps cognitifs, pour créer des expériences utilisables par le plus grand nombre sans stigmatisation.

## Quand l'utiliser (triggers)
- « accessibilité cognitive », « design inclusif », « neurodiversité », « TDAH », « autisme », « dyslexie », « handicap cognitif »
- Audit accessibilité pré-lancement produit
- Conception features pour public neurodivers
- Réduction barrières cognitives (langage complexe, navigation confuse, surcharge sensorielle)
- Validation WCAG cognitive (Web Content Accessibility Guidelines critères cognitifs)
- Amélioration inclusion utilisateurs marginalisés

## Hors périmètre
- Accessibilité technique WCAG (contraste, taille texte, navigation clavier) → l'agent frontend
- Accessibilité visuelle/auditive pure (lecteurs écran, sous-titres) → l'agent frontend
- Rédaction langage simplifié (FALC - Facile À Lire et à Comprendre) → l'agent de microcopie (UX writing)
- Tests accessibilité automatisés (outils Axe, Lighthouse) → l'agent qualité

## Inputs requis
- Interface/parcours à auditer (captures écran, maquettes, prototypes, URL prod)
- Public cible (profils neurodiversité concernés : TDAH, autisme, dyslexie, autres)
- Contraintes légales/réglementaires (WCAG 2.1/2.2 niveau AA/AAA, AI Act accessibilité)
- Données utilisateurs neurodivers si disponibles (verbatims, retours support, tests utilisateurs)

## Sorties attendues
- Audit accessibilité cognitive (grille évaluation WCAG cognitive + neurodiversité)
- Score accessibilité cognitive (0-100)
- Barrières cognitives identifiées (par profil neurodivers)
- Recommandations adaptation priorisées (impact élevé/moyen/faible)
- Plan validation inclusive (tests utilisateurs neurodivers)

## Workflow recommandé

### 1. Compréhension profils neurodivers cibles

**TDAH (Trouble Déficit Attention / Hyperactivité)** :
- **Caractéristiques cognitives** : attention labile, distractibilité, impulsivité, difficulté organisation/planification, hyperfocus sur intérêt
- **Besoins UX** : réduction distractions visuelles, feedback immédiat actions, aide organisation (todo lists, rappels), gamification modérée, navigation simple

**Autisme (TSA - Trouble Spectre Autistique)** :
- **Caractéristiques cognitives** : traitement littéral langage, difficulté implicite/métaphores, surcharge sensorielle (visuel/auditif), besoin prévisibilité/routine, attention détails
- **Besoins UX** : langage explicite (pas métaphores), consignes précises, réduction stimuli sensoriels (animations, sons auto), prévisibilité navigation, patterns cohérents

**Dyslexie** :
- **Caractéristiques cognitives** : difficulté décodage lecture, confusion lettres similaires (b/d, p/q), fatigue cognitive lecture dense, mémoire de travail faible
- **Besoins UX** : police lisible (sans-serif, OpenDyslexic), espacement lignes/mots augmenté, paragraphes courts, support audio, pas de justification texte

**Autres troubles apprentissage** :
- **Dyspraxie** : difficulté coordination motrice fine, clics précis difficiles
- **Dyscalculie** : difficulté manipulation nombres, graphiques complexes
- **Troubles mémoire** : difficulté rétention information, besoin répétition

**Output** : personas neurodivers (profils, caractéristiques cognitives, besoins UX)

### 2. Audit accessibilité cognitive (WCAG 2.1/2.2)

**Principe 1 : Perceptible**
- **1.4.8 Présentation visuelle (AAA)** : espacement lignes 1.5×, paragraphes 2×, largeur max 80 caractères, pas de justification, couleur fond personnalisable
- **1.4.12 Espacement du texte (AA)** : permettre espacement personnalisé sans perte contenu

**Principe 2 : Utilisable**
- **2.4.6 En-têtes et étiquettes (AA)** : titres descriptifs, labels explicites
- **2.5.8 Taille de la cible (AAA)** : cibles cliquables min 44×44 pixels, espacement 8px

**Principe 3 : Compréhensible**
- **3.1.5 Niveau de lecture (AAA)** : niveau lecture secondaire (~ 12 ans) sauf contenu technique
- **3.2.3 Navigation cohérente (AA)** : navigation identique sur toutes pages
- **3.2.4 Identification cohérente (AA)** : même fonction = même label
- **3.3.2 Étiquettes ou instructions (A)** : consignes claires pour saisies
- **3.3.5 Aide contextuelle (AAA)** : aide disponible pour formulaires complexes

**Principe 4 : Robuste**
- **4.1.3 Messages d'état (AA)** : notifications changements contexte sans focus

**Output** : grille audit WCAG cognitive (conforme/partiel/non-conforme par critère)

### 3. Évaluation neurodiversité-spécifique

**Grille évaluation TDAH** :
| Critère | Conforme | Partiel | Non conforme | Recommandations |
|---------|----------|---------|--------------|-----------------|
| Réduction distractions (animations auto, pop-ups) | ... | ... | ... | ... |
| Feedback immédiat actions (confirmation visuelle) | ... | ... | ... | ... |
| Aide organisation (progression, étapes restantes) | ... | ... | ... | ... |
| Navigation simple (< 3 clics objectif) | ... | ... | ... | ... |
| Gamification modérée (pas over-stimulation) | ... | ... | ... | ... |

**Grille évaluation Autisme** :
| Critère | Conforme | Partiel | Non conforme | Recommandations |
|---------|----------|---------|--------------|-----------------|
| Langage explicite (pas métaphores/implicite) | ... | ... | ... | ... |
| Consignes précises (action attendue claire) | ... | ... | ... | ... |
| Réduction stimuli sensoriels (animations, sons) | ... | ... | ... | ... |
| Prévisibilité navigation (patterns cohérents) | ... | ... | ... | ... |
| Cohérence interface (même pattern = même fonction) | ... | ... | ... | ... |

**Grille évaluation Dyslexie** :
| Critère | Conforme | Partiel | Non conforme | Recommandations |
|---------|----------|---------|--------------|-----------------|
| Police lisible (sans-serif, taille ≥ 14px) | ... | ... | ... | ... |
| Espacement lignes 1.5×, paragraphes 2× | ... | ... | ... | ... |
| Paragraphes courts (< 5 lignes) | ... | ... | ... | ... |
| Support audio (text-to-speech) | ... | ... | ... | ... |
| Pas de justification texte (alignement gauche) | ... | ... | ... | ... |

**Output** : grilles évaluation par profil neurodivers

### 4. Scoring accessibilité cognitive

**Formule composite** :
```
Score Accessibilité Cognitive = (WCAG cognitive × 0.5) + (TDAH × 0.2) + (Autisme × 0.15) + (Dyslexie × 0.15)
```

**Pondération ajustable** selon public cible (si produit spécifique TDAH, augmenter poids TDAH).

**Grille notation** (0-100) :
- **90-100** : Accessibilité exemplaire (design universel, aucune barrière significative)
- **70-89** : Accessibilité bonne (conformité WCAG AA+, adaptation neurodiversité partielle)
- **50-69** : Accessibilité moyenne (conformité WCAG A, barrières neurodiversité identifiées)
- **< 50** : Accessibilité faible (non-conformité WCAG, barrières cognitives critiques)

**Output** : score accessibilité cognitive global + détail par dimension

### 5. Identification barrières cognitives

**Barrières TDAH fréquentes** :
- Distractions visuelles (animations auto, carrousels, pop-ups intrusifs)
- Manque feedback immédiat (action sans confirmation visuelle)
- Navigation complexe (> 3 clics pour atteindre objectif)
- Absence aide organisation (pas de progression visible, pas de to-do)

**Barrières Autisme fréquentes** :
- Langage implicite (métaphores, sarcasme, expressions idiomatiques)
- Consignes vagues (« remplir ce formulaire » sans détails)
- Surcharge sensorielle (sons auto, animations vives, contrastes extrêmes)
- Imprédictibilité navigation (patterns incohérents)

**Barrières Dyslexie fréquentes** :
- Police à empattements (serif), taille < 14px
- Espacement lignes/mots insuffisant (< 1.5×)
- Paragraphes longs (> 5 lignes), justification texte
- Absence support audio (pas de text-to-speech)

**Output** : matrice barrières par profil neurodivers (critique/élevée/moyenne)

### 6. Recommandations adaptation

**Principes design universel** :
1. **Utilisation équitable** : utilisable par tous sans adaptation
2. **Flexibilité d'utilisation** : s'adapte aux préférences individuelles
3. **Utilisation simple et intuitive** : facile comprendre
4. **Information perceptible** : communique efficacement information
5. **Tolérance à l'erreur** : minimise conséquences erreurs
6. **Effort physique faible** : utilisable confortablement
7. **Taille et espace appropriés** : adapté morphologies diverses

**Adaptations TDAH** :
- Réduction distractions : désactiver animations auto (ou option désactivation), pop-ups modals minimaux
- Feedback immédiat : confirmation visuelle actions (checkmarks, toasts), micro-animations validation
- Aide organisation : barre progression visible, étapes restantes, to-do lists intégrées
- Gamification modérée : points/badges sans over-stimulation, célébrations discrètes

**Adaptations Autisme** :
- Langage explicite : éviter métaphores, remplacer « cliquer sur la loupe » par « cliquer sur Rechercher »
- Consignes précises : « Entrez votre email au format nom@domaine.fr » vs « Email »
- Réduction stimuli : sons auto désactivés par défaut, animations subtiles, mode sensoriel réduit
- Prévisibilité : navigation cohérente (menu toujours même position), patterns répétés

**Adaptations Dyslexie** :
- Police lisible : sans-serif (Arial, Verdana, OpenDyslexic), taille ≥ 14px, graisse medium
- Espacement : lignes 1.5-2×, mots/lettres légèrement augmentés, paragraphes courts (< 5 lignes)
- Alignement : gauche strict (jamais justifié), largeur max 80 caractères
- Support audio : bouton text-to-speech, lecture automatique optionnelle

**Output** : catalogue adaptations priorisées (P1/P2/P3)

### 7. Plan validation inclusive

**Tests utilisateurs neurodivers** :
- Recrutement : 5-8 utilisateurs par profil neurodivers (TDAH, autisme, dyslexie)
- Protocole : think-aloud, observation comportement, questionnaire satisfaction
- Tâches : parcours critiques produit (inscription, action principale, support)
- Métriques : taux succès tâche, temps tâche, nombre erreurs, satisfaction (SUS, CSAT)

**Critères succès** :
- Taux succès tâche > 80% (par profil neurodivers)
- Satisfaction ≥ 4/5 (échelle Likert)
- Pas de barrière bloquante identifiée
- Score accessibilité cognitive > 70

**Output** : protocole validation inclusive (recrutement, tâches, métriques, critères succès)

## Garde-fous
- **Pas de stigmatisation** : éviter design « pour handicapés », viser design universel bénéficiant à tous
- **Validation avec utilisateurs neurodivers réels** : ne pas supposer, tester avec personnes concernées
- **Flexibilité/personnalisation** : permettre ajustements individuels (taille texte, espacement, mode sensoriel réduit)
- **Conformité légale minimale** : WCAG 2.1 niveau AA obligatoire (EU, US), AAA recommandé
- **Intersectionnalité** : considérer combinaisons (ex: TDAH + dyslexie), pas profils isolés
- **Références scientifiques** : citer WCAG 2.1/2.2, principes design universel, recherche neurodiversité

## Template d'entrée (copier/coller)
```text
[Interface à auditer]
- Type : écran / parcours / produit complet
- URL/captures : ...

[Public cible]
- Profils neurodiversité : TDAH / autisme / dyslexie / autres
- Contraintes légales : WCAG 2.1 AA / WCAG 2.2 AAA / AI Act

[Données existantes]
- Retours utilisateurs neurodivers : ...
- Tests accessibilité antérieurs : ...
```

## Template de sortie (copier/coller)
```text
[Score Accessibilité Cognitive]
- Score global : X/100
- WCAG cognitive : X/100
- TDAH : X/100
- Autisme : X/100
- Dyslexie : X/100

[Barrières identifiées]
Critique (bloquantes) :
1) [Barrière] | Profil impacté : ... | Recommandation : ...
Élevées :
2) ...
Moyennes :
3) ...

[Recommandations adaptation]
Priorité 1 (court terme, < 1 semaine) :
1) [Adaptation] | Profil bénéficiaire : ... | Impact : élevé | Effort : faible | Références : [WCAG 2.1, etc.]
Priorité 2 (moyen terme, 1-4 semaines) :
2) ...
Priorité 3 (long terme, > 1 mois) :
3) ...

[Plan validation inclusive]
- Profils à recruter : ...
- Tâches à tester : ...
- Métriques : ...
- Critères succès : ...
```

## Checklist QA interne
- [ ] Personas neurodivers documentés (TDAH, autisme, dyslexie, autres)
- [ ] Audit WCAG cognitive complet (principes 1-4, critères AA minimum)
- [ ] Grilles évaluation neurodiversité-spécifique complétées (TDAH, autisme, dyslexie)
- [ ] Score accessibilité cognitive calculé (0-100)
- [ ] Barrières identifiées et priorisées (critique/élevée/moyenne)
- [ ] Recommandations adaptation liées à principes design universel
- [ ] Pas de stigmatisation (design universel, pas « pour handicapés »)
- [ ] Plan validation inclusive défini (recrutement utilisateurs neurodivers, protocole, métriques)
- [ ] Conformité légale vérifiée (WCAG 2.1 AA minimum)
- [ ] Références scientifiques citées (APA style)

## KPI reliés
- **Score accessibilité cognitive** : 0-100 (cible > 70)
- **Taux succès tâche utilisateurs neurodivers** : % (cible > 80%)
- **Satisfaction utilisateurs neurodivers** : score SUS, CSAT (cible ≥ 4/5)
- **Nombre barrières bloquantes** : nombre (cible = 0)
- **Conformité WCAG** : % critères conformes (cible AA = 100%, AAA = 80%+)
- **Couverture profils neurodivers** : profils testés (cible : TDAH + autisme + dyslexie minimum)

## Definition of done
- Audit accessibilité cognitive complet (WCAG cognitive + neurodiversité)
- Score accessibilité cognitive calculé (global + détail par dimension)
- Barrières cognitives identifiées et priorisées (critique/élevée/moyenne)
- Recommandations adaptation priorisées (P1/P2/P3, liées principes design universel)
- Plan validation inclusive défini (recrutement, protocole, métriques, critères succès)
- Conformité légale vérifiée (WCAG 2.1 AA minimum)
- Rapport stocké dans `/docs/rapports/HumanSpecialist/inclusive_[nomProjet]_[date].md`

## Exemples d'usage

### Exemple 1 : [Titre du cas d'usage]
**Contexte** : [Description de la situation]
**Action** : [Ce qui a été fait]
**Résultat** : [Résultat obtenu]
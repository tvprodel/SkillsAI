# Web Accessibility Audit (Audit Accessibilité Web)

## Objectif
Évaluer la conformité accessibilité web des interfaces selon les référentiels OPQUAST v4 (226 critères), WCAG 2.1/2.2 (niveaux A/AA/AAA) et RGAA 4.1, en combinant audits automatisés et tests manuels avec technologies assistives (lecteurs d'écran, tablettes braille, navigation clavier).

## Quand l'utiliser (triggers)
- « OPQUAST », « WCAG », « RGAA », « Section 508 », « accessibilité web », « conformité accessibilité »
- « lecteur d'écran », « NVDA », « JAWS », « VoiceOver », « TalkBack », « screen reader »
- « tablette braille », « afficheur braille », « braille 40 caractères », « braille 80 caractères »
- « mal voyant », « aveugle », « cécité », « daltonisme », « handicap visuel »
- « contraste texte », « ratio contraste », « lisibilité », « typographie accessible »
- « navigation clavier », « accessibilité clavier », « ARIA », « semantic HTML »
- Audit conformité site web/application avant mise en production
- Évaluation accessibilité après refonte UI majeure
- Diagnostic utilisabilité pour handicaps visuels (cécité, mal-voyance, daltonisme)
- Validation accessibilité technologies assistives (lecteurs écran, tablettes braille)

## Hors périmètre
- Implémentation technique ARIA/semantic HTML → l'agent frontend
- Rédaction micro-copie accessible → l'agent de microcopie (UX writing)
- Tests automatisés accessibilité (intégration CI/CD) → l'agent qualité
- Design visuel couleurs/typographie → l'agent de direction artistique

## Inputs requis
- Code source HTML/CSS/JavaScript (ou URL prod/staging)
- Maquettes UI/wireframes (pour validation en amont)
- Parcours utilisateurs critiques (pour tests scénarisés)
- Contraintes techniques (frameworks, composants tiers, legacy)
- Référentiel cible (OPQUAST/WCAG 2.1/WCAG 2.2/RGAA 4.1/Section 508)

## Sorties attendues
- Rapport conformité accessibilité web (scoring OPQUAST /226, WCAG A/AA/AAA, RGAA)
- Inventaire violations critiques (bloquants, majeurs, mineurs)
- Résultats tests technologies assistives (lecteurs écran, tablettes braille, navigation clavier)
- Plan de remédiation priorisé (impact utilisateurs × effort correction)
- Recommandations accessibilité (ARIA, semantic HTML, contraste, lisibilité)

## Workflow recommandé

### 1. Analyse code HTML/CSS/ARIA
**Objectif** : Identifier problèmes accessibilité dans le code source avant tests manuels

**Actions** :
- Validation sémantique HTML5 (headings H1-H6, landmarks, structure)
- Audit ARIA (rôles, états, propriétés : role, aria-label, aria-describedby, aria-expanded, aria-hidden, aria-live)
- Vérification attributs accessibilité (alt sur images, label sur formulaires, title, lang)
- Analyse contraste texte/arrière-plan (ratio WCAG : 4.5:1 normal, 3:1 gros texte, 7:1 AAA)
- Inspection CSS accessibilité (focus visible, outline, skip links, responsive)

**Outils** :
- Inspecteur navigateur (DevTools, Accessibility tree)
- Extensions navigateur : Accessibility Insights, axe DevTools
- Validateurs W3C : HTML Validator, CSS Validator

**Output** : Liste problèmes code source (semantic HTML manquant, ARIA incorrect, contraste insuffisant)

### 2. Audit automatisé (axe-core, Lighthouse, WAVE)
**Objectif** : Détecter violations accessibilité automatiquement sur l'ensemble du site

**Actions** :
- **axe-core** : Audit WCAG complet (A/AA/AAA), scoring violations par gravité (critical/serious/moderate/minor)
- **Lighthouse** : Score accessibilité /100 (Google Chrome DevTools), audit ARIA, contraste, semantic HTML
- **WAVE** : Visualisation problèmes accessibilité (WebAIM), identification erreurs/alertes/features
- **Pa11y** : Tests CLI automatisés, intégration CI/CD possible (hors périmètre implémentation)

**Référentiels testés** :
- WCAG 2.1 niveau A/AA/AAA (Web Content Accessibility Guidelines)
- WCAG 2.2 (nouvelles règles 2023 : focus visible amélioré, drag-and-drop accessible, authentification accessible)
- Section 508 (US) si applicable

**Output** : Rapport automatisé (score Lighthouse /100, violations axe-core par gravité, erreurs WAVE)

### 3. Tests lecteurs d'écran (NVDA, JAWS, VoiceOver, TalkBack)
**Objectif** : Valider utilisabilité réelle pour utilisateurs aveugles/mal-voyants avec lecteurs d'écran

**Scénarios tests** :
- Navigation par landmarks (header, nav, main, aside, footer)
- Navigation par headings (H1-H6 structure hiérarchique)
- Navigation formulaires (labels, fieldsets, erreurs explicites)
- Lecture tableaux (th, scope, caption, summary)
- Lecture listes (ul, ol, dl structurées)
- Feedback dynamique (aria-live regions, messages temporaires)
- Boutons/liens (label explicite, role clair)

**Technologies testées** :
- **NVDA** (Windows, gratuit open source) — PRIORITAIRE
- **JAWS** (Windows, commercial) — si budget disponible
- **VoiceOver** (macOS/iOS, natif Apple)
- **TalkBack** (Android, natif Google)

**Critères validation** :
- Contenu annoncé correctement (texte, labels, rôles)
- Navigation fluide (pas de piège clavier, ordre logique)
- Formulaires utilisables (erreurs compréhensibles, soumission possible)
- Contenu dynamique notifié (aria-live updates)

**Output** : Rapport tests lecteurs d'écran (taux réussite navigation %, problèmes bloquants, expérience utilisateur)

### 4. Tests tablettes braille (afficheurs braille 40/80 caractères)
**Objectif** : Valider utilisabilité pour utilisateurs aveugles avec tablettes braille

**Équipement requis** :
- Tablette braille 40 caractères (ex: Focus 40 Blue, Brailliant BI 40X)
- Tablette braille 80 caractères (ex: Focus 80 Blue, Brailliant BI 80)
- Connexion lecteur d'écran (NVDA/JAWS + tablette braille via Bluetooth/USB)

**Scénarios tests** :
- Lecture navigation (menus, liens, boutons)
- Lecture formulaires (labels, champs, erreurs)
- Lecture tableaux (navigation cellules)
- Navigation par zones (landmarks, headings)
- Feedback dynamique (aria-live en braille)

**Critères validation** :
- Contenu affiché correctement en braille (caractères, symboles)
- Navigation possible (combinaisons touches tablette)
- Pas de perte d'information vs audio (équivalence braille/audio)

**Output** : Rapport tests tablettes braille (compatibilité 40/80 car, problèmes affichage, navigation)

### 5. Tests navigation clavier seul
**Objectif** : Valider utilisabilité sans souris (handicaps moteurs, experts clavier, lecteurs d'écran)

**Scénarios tests** :
- Navigation Tab/Shift+Tab (ordre logique, tous éléments focusables)
- Activation Enter/Space (boutons, liens, formulaires)
- Navigation flèches (menus déroulants, sliders, tableurs)
- Fermeture Escape (modales, menus, tooltips)
- Skip links (sauter navigation répétitive)
- Pas de piège clavier (focus sort des composants)

**Critères validation** :
- Focus visible en permanence (outline CSS, :focus-visible)
- Ordre tabulation logique (correspond ordre visuel)
- Tous éléments interactifs accessibles (pas d'éléments "souris uniquement")
- Pas de piège clavier (focus bloqué dans composant)
- Raccourcis clavier documentés (si complexes)

**Output** : Rapport navigation clavier (taux réussite parcours %, pièges clavier, focus invisible)

### 6. Scoring WCAG (A/AA/AAA) + OPQUAST (/226)
**Objectif** : Calculer scores conformité selon référentiels officiels

**WCAG 2.1/2.2 scoring** :
- **Niveau A** (basique) : 30 critères de succès obligatoires
- **Niveau AA** (recommandé web) : +20 critères (total 50 critères)
- **Niveau AAA** (optimal) : +28 critères (total 78 critères)

Formule conformité :
```
Conformité WCAG AA = (critères A+AA réussis / 50) × 100
```

**OPQUAST v4 scoring** :
- 226 critères qualité web (dont accessibilité)
- Grille notation : 0-40 % (insuffisant), 41-60 % (moyen), 61-80 % (bon), 81-100 % (excellent)

Formule conformité :
```
Score OPQUAST = (critères réussis / 226) × 100
```

**Output** : Scores conformité (WCAG A/AA/AAA, OPQUAST /226), niveau atteint, écart vs cible

### 7. Rapport conformité + recommandations priorisées
**Objectif** : Produire rapport actionnable avec plan de remédiation

**Structure rapport** :
1. **Executive summary** : scores globaux (WCAG, OPQUAST), niveau conformité atteint, points bloquants
2. **Résultats audits automatisés** : axe-core, Lighthouse, WAVE (violations par gravité)
3. **Résultats tests manuels** : lecteurs d'écran (NVDA/JAWS/VoiceOver/TalkBack), tablettes braille, navigation clavier
4. **Inventaire violations** : tableau violations (critère WCAG, gravité, page/composant impacté, impact utilisateurs)
5. **Plan de remédiation priorisé** : matrice impact utilisateurs × effort correction (Quick wins, Chantiers majeurs, Optimisations)
6. **Recommandations techniques** : ARIA (rôles/états/propriétés), semantic HTML (headings/landmarks), contraste (ratios), lisibilité (typographie/espacement)
7. **Annexes** : captures écran problèmes, références WCAG/OPQUAST, ressources accessibilité

**Priorisation recommandations** :
- **P1 Critique** : bloque utilisateurs handicapés (ex: formulaire inutilisable, piège clavier, contraste insuffisant texte critique)
- **P2 Majeur** : dégrade expérience (ex: headings manquants, labels imprécis, focus invisible)
- **P3 Mineur** : amélioration confort (ex: skip links manquants, ARIA redondant, ordre tabulation sous-optimal)

**Output** : Rapport PDF/Markdown complet (20-50 pages selon taille site), plan remédiation Excel/CSV, slides exécutives

## Garde-fous

- Ne jamais se limiter aux tests automatisés : 30-40% des problèmes accessibilité nécessitent tests manuels (lecteurs écran, clavier).
- Toujours tester avec NVDA (gratuit, standard) en priorité avant autres lecteurs.
- Différencier niveau A (base légale) vs AA (cible recommandée) vs AAA (excellence) selon contexte.
- Prioriser violations selon impact utilisateurs réels, pas seulement gravité technique.
- Ne jamais publier rapport sans validation manuelle tablette braille sur au moins 1 parcours critique.

## Template d'entrée (copier/coller)

```text
[Contexte]
- Type site/application : ...
- URL (prod/staging) : ...
- Frameworks utilisés : ...

[Objectif]
- Référentiel cible : WCAG 2.1/2.2 niveau AA | OPQUAST | RGAA 4.1 | Section 508
- Parcours critiques : ...
- Contraintes techniques : ...

[Livrable attendu]
- Rapport conformité complet : Oui/Non
- Plan remédiation priorisé : Oui/Non
- Slides exécutives : Oui/Non
```

## Template de sortie (copier/coller)

```text
[Résultats conformité]
- Score WCAG : niveau X atteint (A/AA/AAA), XX critères réussis/50
- Score OPQUAST : XX/226 (XX%)
- Violations critiques : XX (P1), XX (P2), XX (P3)

[Tests technologies assistives]
- Lecteurs d'écran : NVDA (XX% réussite), JAWS/VoiceOver/TalkBack (XX% réussite)
- Tablettes braille : XX% parcours réussis
- Navigation clavier : XX% interactions réussies

[Plan remédiation]
- Quick wins (P1) : [liste actions immédiates]
- Chantiers majeurs (P2) : [liste refonte nécessaire]
- Optimisations (P3) : [liste améliorations futures]

[Recommandations prioritaires]
1. ...
2. ...
3. ...

[Livrables]
- Rapport PDF/Markdown : [lien]
- Plan remédiation Excel/CSV : [lien]
- Slides exécutives : [lien]
```

## Checklist QA interne

- [ ] Audits automatisés exécutés sur 100% pages critiques (axe-core, Lighthouse, WAVE).
- [ ] Tests manuels NVDA réalisés sur tous parcours critiques.
- [ ] Tests tablette braille réalisés sur au moins 1 parcours critique.
- [ ] Tests navigation clavier réalisés sur 100% interactions (Tab/Enter/Escape).
- [ ] Scoring WCAG calculé avec détail critères A/AA/AAA.
- [ ] Scoring OPQUAST calculé avec liste critères échoués.
- [ ] Violations classées par gravité (P1/P2/P3) et impact utilisateurs.
- [ ] Plan remédiation priorisé avec effort/impact pour chaque action.
- [ ] Rapport structure complète (summary, audits, violations, remédiation, recommandations, annexes).
- [ ] Livrables validés (PDF, Excel, slides) avant diffusion.

## KPI reliés

### 1. Score WCAG (A/AA/AAA)
**Formule** :
```
Score WCAG AA = (critères A+AA réussis / 50) × 100
```
**Cibles** :
- < 80 % : Non conforme (blocages critiques)
- 80-95 % : Partiellement conforme (améliorations nécessaires)
- > 95 % : Conforme WCAG AA (cible recommandée)
- 100 % : Conforme strict

### 2. Score OPQUAST (/226)
**Formule** :
```
Score OPQUAST = (critères réussis / 226) × 100
```
**Cibles** :
- < 60 % : Insuffisant
- 60-80 % : Bon (acceptable)
- 80-90 % : Très bon (cible recommandée)
- > 90 % : Excellent

### 3. Nombre violations critiques
**Définition** : Nombre de violations WCAG niveau A (bloquantes) détectées par audits automatisés (axe-core/Lighthouse/WAVE)

**Cibles** :
- 0 violations critiques (cible stricte)
- < 5 violations critiques (acceptable pré-production)
- > 10 violations critiques (refus mise en production)

### 4. Taux compatibilité lecteurs d'écran (%)
**Formule** :
```
Compatibilité lecteurs écran = (parcours réussis sans blocage / parcours testés) × 100
```
**Parcours testés** : Navigation principale, formulaires critiques, tableaux, contenu dynamique

**Cibles** :
- < 80 % : Non utilisable (blocages majeurs)
- 80-95 % : Utilisable avec difficultés
- > 95 % : Pleinement utilisable (cible recommandée)

### 5. Taux navigation clavier réussie (%)
**Formule** :
```
Navigation clavier réussie = (parcours clavier réussis sans piège / parcours testés) × 100
```
**Parcours testés** : Navigation Tab complète, activation formulaires, fermeture modales, skip links

**Cibles** :
- < 90 % : Non conforme (pièges clavier)
- 90-98 % : Partiellement conforme
- > 98 % : Conforme (cible recommandée)

### 6. Ratio contraste texte minimum
**Définition** : Ratio contraste le plus faible détecté sur textes essentiels (corps de texte, labels formulaires, boutons)

**Référence WCAG** :
- **AA (normal)** : 4.5:1 minimum (texte < 18pt ou < 14pt gras)
- **AA (gros texte)** : 3:1 minimum (texte ≥ 18pt ou ≥ 14pt gras)
- **AAA (normal)** : 7:1 minimum (optimal)
- **AAA (gros texte)** : 4.5:1 minimum (optimal)

**Cibles** :
- < 4.5:1 sur texte normal : Non conforme AA (correction urgente)
- 4.5:1 - 7:1 : Conforme AA (cible minimale)
- ≥ 7:1 : Conforme AAA (optimal)

## Definition of done

- [ ] Audit code HTML/CSS/ARIA réalisé (semantic HTML, ARIA, contraste)
- [ ] Audits automatisés exécutés (axe-core, Lighthouse, WAVE) sur 100 % pages critiques
- [ ] Tests lecteurs d'écran réalisés (NVDA prioritaire + 1 autre : JAWS/VoiceOver/TalkBack) sur parcours critiques
- [ ] Tests tablettes braille réalisés (40 ou 80 caractères) sur au moins 1 parcours critique
- [ ] Tests navigation clavier réalisés (Tab/Enter/Escape) sur 100 % parcours critiques
- [ ] Scoring WCAG calculé (niveau A/AA/AAA atteint)
- [ ] Scoring OPQUAST calculé (/226)
- [ ] Rapport conformité produit (structure complète : summary, audits, violations, remédiation, recommandations, annexes)
- [ ] Plan de remédiation priorisé (P1/P2/P3 avec impact × effort)
- [ ] Violations critiques P1 identifiées et documentées (bloquants utilisateurs handicapés)

## Exemples d'usage

### Exemple 1 : Audit OPQUAST site e-commerce
**Contexte** : Site e-commerce avant refonte UI, cible OPQUAST 80 %

**Input** : URL production, parcours critiques (catalogue, panier, tunnel achat)

**Actions** :
1. Analyse code : semantic HTML, ARIA formulaires, contraste boutons CTA
2. Audits automatisés : Lighthouse, axe-core, WAVE sur 20 pages clés
3. Tests NVDA : navigation catalogue, ajout panier, formulaire livraison
4. Tests clavier : parcours complet Tab/Enter
5. Scoring OPQUAST : 172/226 critères réussis = 76 %

**Output** :
- Score OPQUAST : 76 % (cible 80 % non atteinte, écart -4 %)
- Violations critiques : 8 (formulaire livraison inaccessible NVDA, piège clavier modale)
- Plan remédiation : 12 corrections P1 (2 jours), 25 corrections P2 (5 jours)

### Exemple 2 : Test compatibilité NVDA interface dashboard
**Contexte** : Dashboard analytics interne, utilisateurs mal-voyants signalent difficultés

**Input** : URL dashboard, parcours critiques (login, navigation widgets, export CSV)

**Actions** :
1. Tests NVDA : navigation widgets (aria-live updates), graphiques (tableaux alternatifs), filtres (labels explicites)
2. Tests clavier : navigation flèches widgets, activation filtres Enter
3. Audit ARIA : aria-live regions, aria-label boutons, role widgets

**Output** :
- Compatibilité NVDA : 65 % (widgets dynamiques mal annoncés)
- Violations critiques : Graphiques sans alternative textuelle, aria-live manquants, labels boutons génériques ("Cliquer ici")
- Recommandations : Ajouter aria-live sur widgets temps réel, tableaux alternatifs graphiques, labels boutons explicites ("Exporter CSV analytics")

### Exemple 3 : Évaluer contraste texte boutons
**Contexte** : Refonte design system, nouveaux boutons CTA, validation contraste WCAG AA

**Input** : Maquettes Figma, code CSS boutons (couleurs hex)

**Actions** :
1. Analyse contraste : bouton primaire (#3498db fond, #ffffff texte), bouton secondaire (#95a5a6 fond, #2c3e50 texte)
2. Calcul ratios : bouton primaire 4.52:1 (WCAG AA OK), bouton secondaire 2.85:1 (WCAG AA KO)
3. Recommandations : Assombrir bouton secondaire (#7f8c8d fond → ratio 4.51:1 OK)

**Output** :
- Bouton primaire : Conforme WCAG AA (4.52:1)
- Bouton secondaire : Non conforme (2.85:1), correction requise (#7f8c8d recommandé)

### Exemple 4 : Valider navigation clavier formulaire
**Contexte** : Formulaire inscription multi-étapes, validation accessibilité clavier avant production

**Input** : URL formulaire staging, parcours complet (4 étapes)

**Actions** :
1. Tests clavier : Tab (ordre logique), Enter (soumission), Escape (fermeture erreurs)
2. Détection pièges : Étape 3 modale date (focus bloqué, Escape ne ferme pas)
3. Vérification focus visible : Étape 2 checkbox (outline invisible)

**Output** :
- Navigation clavier : 75 % réussie (piège étape 3, focus invisible étape 2)
- Violations critiques : Modale date (piège clavier), checkbox (focus invisible)
- Recommandations : Ajouter fermeture Escape modale, ajouter :focus-visible CSS checkbox

### Exemple 5 : Tester tablette braille 40 caractères
**Contexte** : Application gouvernementale, exigence conformité RGAA AAA, validation tablette braille

**Input** : URL application staging, tablette braille Focus 40 Blue + NVDA

**Actions** :
1. Tests braille : Navigation menu (landmarks), formulaires (labels), tableaux (th/td)
2. Vérification symboles : Listes (puces affichées ?), liens (symbole lien ?), headings (niveau H1-H6 ?)
3. Feedback dynamique : aria-live (notifications affichées braille ?)

**Output** :
- Compatibilité braille 40 car : 90 % (puces listes manquantes, aria-live non affiché)
- Violations : Listes (puces non retranscrites braille), notifications (aria-live ignoré tablette)
- Recommandations : Vérifier compatibilité NVDA + Focus 40 (mise à jour drivers ?), tester aria-live alternatifs

## Contraintes et références
- [WCAG 2.1](https://www.w3.org/TR/WCAG21/) (W3C Recommendation)
- [WCAG 2.2](https://www.w3.org/TR/WCAG22/) (W3C Recommendation 2023)
- [OPQUAST v4](https://checklists.opquast.com/fr/assurance-qualite-web/) (226 critères qualité web)
- [RGAA 4.1](https://www.numerique.gouv.fr/publications/rgaa-accessibilite/) (Référentiel Général d'Amélioration de l'Accessibilité, France)
- [Section 508](https://www.section508.gov/) (US Federal Accessibility Standards)
- [axe-core](https://github.com/dequelabs/axe-core) (Accessibility testing engine)
- [Lighthouse](https://developers.google.com/web/tools/lighthouse) (Google Chrome DevTools)
- [WAVE](https://wave.webaim.org/) (WebAIM accessibility evaluation tool)
- [NVDA](https://www.nvaccess.org/) (NonVisual Desktop Access, gratuit open source)
- [WebAIM Contrast Checker](https://webaim.org/resources/contrastchecker/) (Vérification contraste WCAG)

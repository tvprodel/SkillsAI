# Data Storytelling & Insights Communication

## Objectif

Transformer des analyses de données complexes en récits clairs, convaincants et actionnables pour des audiences non-techniques (direction, métier, clients). Communiquer des insights data de manière visuelle et narrative pour faciliter la prise de décision et l'adoption de recommandations basées sur les données.

---

## Quand l'utiliser (triggers)

- Présentation de résultats d'analyse à la direction ou aux stakeholders métier
- Transformation de dashboards complexes en executive summary (1 page)
- Communication d'insights data pour justifier une décision stratégique
- Vulgarisation de concepts data/statistiques pour un public non-technique
- Rapport d'analyse avec recommandations actionnables
- Storytelling visuel (infographies, slides, vidéos explicatives)
- Facilitation d'ateliers data-driven (workshop décisionnel basé sur les données)

**Déclencheurs** :
- "Présente ces résultats à la direction en 10 minutes"
- "Transforme ce dashboard en synthèse 1 page pour le comex"
- "Explique pourquoi on doit investir dans [X] avec les données"
- "Rends cette analyse compréhensible pour le métier"
- "Crée une infographie pour communiquer ces KPI"

---

## Hors périmètre

- ❌ **Analyse statistique approfondie** → l'agent data science
- ❌ **Conception de dashboards interactifs** → Skill précédent (Business KPI Analysis & Dashboard Design)
- ❌ **Requêtes SQL complexes** → Skill précédent (SQL Analytics & Data Quality)
- ❌ **Copy marketing orienté conversion** → l'agent de copywriting
- ❌ **Design graphique avancé (charte, identité visuelle)** → l'agent de direction artistique
- ❌ **Rédaction documentation technique utilisateur** → l'agent de rédaction technique

**Frontière l'agent de copywriting** :
- l'agent d'analyse de données (ce skill) : Communication insights data pour décision métier/stratégique, neutralité factuelle
- Copywriter : Persuasion marketing, conversion, vente, tonalité émotionnelle

---

## Inputs requis

### Contexte décisionnel
- **Audience** : Direction (C-level), managers opérationnels, équipes métier, clients externes
- **Objectif** : Informer, convaincre, former, aligner, décider
- **Contraintes de temps** : Présentation 5 min, 15 min, 30 min, rapport écrit 1 page, 5 pages

### Données d'analyse
- **Résultats bruts** : Fichier CSV, export SQL, dashboard existant
- **Insights clés** : 3-5 insights principaux à communiquer
- **Recommandations** : Actions métier proposées basées sur les données

### Format de livraison
- **Support** : Slides PowerPoint/Google Slides, rapport PDF, infographie PNG/SVG, vidéo explicative
- **Style visuel** : Minimaliste (slides texte), visuel (graphiques + icônes), immersif (storytelling narratif)

---

## Sorties attendues

### Livrables standards
1. **Executive summary (1 page)** : Synthèse des insights clés + recommandations + impact chiffré
2. **Présentation slides** : 5-15 slides avec structure narrative (problème → données → insights → recommandations)
3. **Infographie** : Visualisation standalone des KPI principaux (format A4/A3, exportable PNG/PDF)
4. **Script de présentation** : Texte de prise de parole oral (~150 mots/min) pour accompagner les slides
5. **FAQ anticipées** : 5-10 questions/objections probables avec réponses préparées

### Structure narrative recommandée (méthode SCR)
**S**ituation → **C**omplication → **R**ésolution

1. **Situation (contexte)** : Quel est le contexte business ? Pourquoi cette analyse ?
2. **Complication (problème)** : Quel problème/question les données révèlent-elles ?
3. **Résolution (recommandations)** : Que faire concrètement ? Impact attendu ?

---

## Workflow recommandé

### Phase 1 : Distillation des insights (1-2h)
1. **Identifier les 3-5 insights clés** : Parmi tous les résultats, quels sont les plus actionnables ?
2. **Formuler en langage métier** : Éviter jargon data (« distribution bimodale » → « deux groupes distincts de clients »)
3. **Chiffrer l'impact** : Pour chaque insight, quantifier l'impact potentiel (€, %, temps gagné)
4. **Prioriser par importance** : Quel insight a le plus d'impact business ? Commencer par celui-là

**Critères d'un bon insight** :
- ✅ **Surprenant** : Révèle quelque chose de non-évident
- ✅ **Actionnable** : Permet de décider ou d'agir concrètement
- ✅ **Chiffré** : Quantifie l'opportunité ou le risque
- ✅ **Contextuel** : Relié à un enjeu business clair

### Phase 2 : Construction de la structure narrative (30 min - 1h)
1. **Choisir l'arc narratif** : SCR (Situation-Complication-Résolution) ou autre (ex: STAR pour retour d'expérience)
2. **Définir les sections** :
   - Introduction (contexte + objectif de l'analyse)
   - Méthodologie rapide (sources, période, filtres) [optionnel si audience non-technique]
   - Insights clés (1 slide par insight principal)
   - Recommandations (actions concrètes + impact attendu)
   - Conclusion (récap + prochaines étapes)

3. **Storyboard visuel** : Esquisser chaque slide en mode wireframe (titre + 1 graphique + 1 message clé)

### Phase 3 : Design visuel des supports (2-4h)
**Principes de design data storytelling** :

1. **Clarté avant esthétique** : Graphique simple compréhensible > graphique sophistiqué illisible
2. **Règle du 1-5-25** : 
   - 1 message clé par slide
   - Max 5 bullets ou éléments visuels par slide
   - Max 25 mots par slide (hors graphiques)
3. **Hiérarchie visuelle** : Titre > Graphique > Texte explicatif
4. **Contraste fort** : Texte noir sur fond blanc (ou inverse), éviter gris sur gris
5. **Annotations directes** : Annoter directement les graphiques (flèches, étiquettes) plutôt que légende externe

**Choix du bon type de graphique** :

| Objectif | Type de graphique | Exemple |
|----------|-------------------|---------|
| Comparaison catégories | Bar chart horizontal | Comparer CA par région |
| Évolution temporelle | Line chart | Tendance ventes sur 12 mois |
| Proportion d'un tout | Pie chart (max 5 catégories) ou Treemap | Parts de marché |
| Distribution | Histogram ou Box plot | Distribution âges clients |
| Corrélation 2 variables | Scatter plot | Corrélation prix vs ventes |
| Classement/ranking | Bar chart vertical trié | Top 10 produits |
| Évolution cumulée | Area chart empilé | Progression CA cumulé YTD |

4. **Créer les slides** :
   - Slide de titre (contexte + objectif en 1 phrase)
   - 1 slide méthodologie (si audience technique ou réglementation)
   - 3-5 slides insights (1 graphique + 1 titre-message + annotations)
   - 1-2 slides recommandations (bullets actionnables + impact chiffré)
   - Slide de conclusion (synthèse + next steps)

5. **Appliquer la charte visuelle** : Couleurs entreprise, logo, polices (si charte fournie)

### Phase 4 : Préparation de la présentation orale (1-2h)
1. **Rédiger le script** : Texte oral pour accompagner chaque slide (~150-200 mots/min)
2. **Répéter la présentation** : Chronométrer (10 min annoncées = 8-9 min réelles pour laisser marge questions)
3. **Préparer les transitions** : Phrases de liaison entre slides ("Maintenant que nous avons vu X, regardons Y")
4. **Anticiper les questions** : Lister 5-10 questions probables + réponses préparées
5. **Backup slides** : Préparer 2-3 slides supplémentaires avec détails (si questions approfondies)

### Phase 5 : Livraison et feedback (1h + présentation)
1. **Tester le matériel** : Vérifier vidéoprojecteur, son, animations slides, export PDF
2. **Présenter** : Suivre le script, adapter au rythme de l'audience, gérer le temps
3. **Session Q&A** : Répondre aux questions, noter celles nécessitant analyse complémentaire
4. **Collecter le feedback** : Sondage rapide post-présentation (clarté, utilité, actions)
5. **Itérer** : Améliorer les slides/script basé sur le feedback pour prochaine présentation

---

## Garde-fous

### GF1 - Règle du "So What?" (Et alors ?)
**Règle** : Chaque slide d'insight doit répondre à la question "Et alors ?" = Pourquoi c'est important ? Quelle action ?

**Justification** : Une donnée sans implication business n'a aucune valeur décisionnelle.

**Mesure** : Pour chaque slide d'insight, vérifier présence d'une phrase "Cela signifie que..." ou "Action recommandée : ..."

**Preuve** : Audit des slides finales (checklist "So What?" par slide).

**Exemple** :
- ❌ Mauvais : "Le taux de conversion est de 2,3%"
- ✅ Bon : "Le taux de conversion est de 2,3%, soit 40% inférieur à la moyenne du secteur (3,8%). **Action** : Optimiser le funnel de checkout pour gagner +1,5 points = +€120k CA annuel"

### GF2 - Limite de charge cognitive (7±2 éléments)
**Règle** : Maximum 5-9 éléments visuels ou textuels par slide (règle de Miller).

**Justification** : Au-delà de 9 éléments, le cerveau humain sature et ne retient plus l'information.

**Mesure** : Compter le nombre d'éléments par slide (bullets, graphiques, images, étiquettes).

**Preuve** : Aucune slide ne doit dépasser 9 éléments. Si >9, scinder en 2 slides.

### GF3 - Test de compréhension naïve (5 secondes)
**Règle** : Toute personne hors contexte doit comprendre le message principal d'un graphique en <5 secondes.

**Justification** : En présentation, l'audience découvre le graphique en même temps que vous parlez. Si incompréhensible en 5s, l'attention est perdue.

**Mesure** : Test utilisateur : montrer le graphique 5s à quelqu'un hors projet, lui demander le message clé.

**Preuve** : Si la personne ne peut pas reformuler le message en 1 phrase, simplifier le graphique.

**Actions correctives** :
- Retirer les éléments non-essentiels (gridlines inutiles, légende complexe)
- Annoter directement les valeurs importantes sur le graphique
- Utiliser un titre-message ("Les ventes augmentent de 15% en Q2") plutôt qu'un titre descriptif ("Évolution des ventes")

### GF4 - Honnêteté des visualisations (pas de manipulation visuelle)
**Règle** : Les axes Y doivent commencer à 0 pour les bar charts. Les échelles doivent être linéaires sauf justification explicite.

**Justification** : Les visualisations trompeuses (axes tronqués, échelles non-linéaires) faussent la perception et érodent la confiance.

**Mesure** : Audit des graphiques (checklist : axe Y à 0 ? échelle linéaire ? proportions respectées ?).

**Preuve** : Capture d'écran des graphiques avec axes visibles.

**Exceptions autorisées** :
- Line charts (tendances) : Axe Y peut ne pas commencer à 0 si plage étroite
- Échelle logarithmique : Si justifiée explicitement (données sur plusieurs ordres de grandeur)
- Axes tronqués : UNIQUEMENT si annotation visible "⚠️ Axe tronqué à [valeur]"

### GF5 - Citations de sources obligatoires
**Règle** : Toute donnée présentée doit avoir sa source citée (en bas de slide ou dans notes).

**Justification** : Garantir la traçabilité et la vérifiabilité des données présentées.

**Mesure** : Chaque slide avec données doit avoir une note de bas de page "Source : [BDD interne / Étude X / API Y]".

**Preuve** : Audit des slides finales (checklist source par slide).

---

## Template d'entrée (copier/coller)
```text
[Brief de communication data]
- Décision à éclairer et audience : ...
- Question métier, période et périmètre : ...
- Données, sources et limites connues : ...
- Format, durée et niveau de détail attendu : ...
```

## Template de sortie (copier/coller)
```text
[Récit décisionnel]
- Message principal et décision sollicitée : ...
- Insights clés reliés aux données/sources : ...
- Visualisations et limites/interprétation : ...
- Recommandations, actions, owners et questions ouvertes : ...
```

## Templates copier/coller

### Template 1 : Executive Summary (1 page)

```markdown
# Executive Summary : [Titre de l'analyse]

**Date** : YYYY-MM-DD  
**Destinataire** : [Nom Stakeholder / Comité de direction]  
**Analyste** : l'agent d'analyse de données

---

## Contexte

[1-2 phrases : Pourquoi cette analyse ? Quel problème business ?]

Exemple : Face à une baisse de 12% des ventes en Q2 2024, nous avons analysé les données clients pour identifier les segments impactés et les actions correctives prioritaires.

---

## Insights clés

### 🔍 Insight 1 : [Titre-message]
**Constat** : [Donnée chiffrée]  
**Impact** : [Conséquence business]  
**Recommandation** : [Action concrète] → **Gain estimé** : [€ ou % ou temps]

### 🔍 Insight 2 : [Titre-message]
**Constat** : [Donnée chiffrée]  
**Impact** : [Conséquence business]  
**Recommandation** : [Action concrète] → **Gain estimé** : [€ ou % ou temps]

### 🔍 Insight 3 : [Titre-message]
**Constat** : [Donnée chiffrée]  
**Impact** : [Conséquence business]  
**Recommandation** : [Action concrète] → **Gain estimé** : [€ ou % ou temps]

---

## Recommandations prioritaires

| Priorité | Action | Owner | Échéance | Impact estimé |
|----------|--------|-------|----------|---------------|
| 🔴 Critique | [Action 1] | [Nom] | [Date] | +€[X]k |
| 🟠 Élevée | [Action 2] | [Nom] | [Date] | +€[Y]k |
| 🟡 Normale | [Action 3] | [Nom] | [Date] | +€[Z]k |

**Impact total estimé** : +€[X+Y+Z]k sur [période]

---

## Prochaines étapes

1. **[Action immédiate]** : [Description] - **Deadline** : [Date]
2. **[Suivi mensuel]** : KPI à tracker - **Responsable** : [Nom]
3. **[Revue trimestrielle]** : Point d'étape - **Date** : [Date]

---

**Contact** : l'agent d'analyse de données - [email]
```

### Template 2 : Structure slides présentation (PowerPoint/Google Slides)

**Slide 1 - Titre**
```
[Titre de l'analyse en 1 phrase]

[Sous-titre : Contexte ou période]

[Nom analyste] - [Date]
```

**Slide 2 - Agenda**
```
Agenda

1. Contexte et objectif
2. Méthodologie [optionnel]
3. Insights clés (3-5 insights)
4. Recommandations
5. Prochaines étapes
```

**Slide 3 - Contexte**
```
Contexte : Pourquoi cette analyse ?

[1 paragraphe court : problème business, enjeu, question]

[Image ou icône illustrative]
```

**Slide 4-8 - Insights (1 slide par insight)**
```
Titre-message : [Le message clé en 1 phrase]

[Graphique principal avec annotations]

📊 Constat : [Donnée chiffrée]
💡 Implication : [Pourquoi c'est important]
✅ Action : [Recommandation concrète]
```

**Slide 9 - Recommandations**
```
Recommandations : Que faire concrètement ?

🔴 Priorité 1 : [Action] → Impact : +€[X]k
🟠 Priorité 2 : [Action] → Impact : +€[Y]k
🟡 Priorité 3 : [Action] → Impact : +€[Z]k

Impact total : +€[X+Y+Z]k sur [période]
```

**Slide 10 - Prochaines étapes**
```
Prochaines étapes

1. [Action immédiate] - Deadline : [Date] - Owner : [Nom]
2. [Suivi mensuel] - KPI à tracker - Responsable : [Nom]
3. [Revue trimestrielle] - Point d'étape - Date : [Date]
```

**Slide 11 - Conclusion**
```
En résumé...

✅ [Insight clé #1]
✅ [Insight clé #2]
✅ [Insight clé #3]

➡️ Actions prioritaires : [Liste courte]

Questions ?
```

### Template 3 : Script de présentation orale

```markdown
# Script présentation : [Titre]

**Durée** : [X] minutes  
**Audience** : [Direction / Métier / Clients]  
**Date** : YYYY-MM-DD

---

## Introduction (1 min)

Bonjour à tous. Aujourd'hui, je vais vous présenter [titre de l'analyse].

[Contexte en 2 phrases : problème business + pourquoi cette analyse]

Nous allons voir ensemble [nombre] insights clés et les actions recommandées pour [objectif business].

---

## Slide X : [Titre slide]

[Script oral correspondant à la slide - ~150-200 mots]

[Indiquer les éléments visuels à pointer du doigt/laser]

**Transition** : Maintenant que nous avons vu X, regardons Y...

---

## Conclusion (1 min)

Pour conclure, retenons [nombre] points clés :

1. [Insight principal #1]
2. [Insight principal #2]
3. [Insight principal #3]

Les actions prioritaires sont [liste courte]. L'impact estimé est de [€ ou % ou temps] sur [période].

Je suis disponible pour vos questions. Merci de votre attention.

---

## FAQ anticipée

**Q1** : [Question probable]  
**R1** : [Réponse préparée avec données si possible]

**Q2** : [Question probable]  
**R2** : [Réponse préparée]

[...]
```

---

## Checklist QA interne

**Avant livraison présentation, valider** :

### Contenu
- [ ] Les 3-5 insights clés sont clairement identifiés et formulés en langage métier
- [ ] Chaque insight a une implication business explicite ("Et alors ?")
- [ ] Les recommandations sont actionnables et chiffrées (impact €/% ou temps)
- [ ] Les sources de données sont citées (bas de slide ou notes)

### Structure narrative
- [ ] La présentation suit un arc narratif clair (SCR ou autre)
- [ ] L'introduction pose le contexte et l'objectif en <2 min
- [ ] La conclusion récapitule les insights + actions + next steps
- [ ] Les transitions entre slides sont fluides et logiques

### Design visuel
- [ ] Règle 1-5-25 respectée (1 message, 5 éléments max, 25 mots max par slide)
- [ ] Les graphiques sont annotés directement (pas de légende externe complexe)
- [ ] Les axes Y commencent à 0 pour les bar charts (ou justification si non)
- [ ] Les couleurs respectent la charte visuelle (si applicable)
- [ ] Les polices sont lisibles (≥18pt pour texte, ≥24pt pour titres)

### Compréhension
- [ ] Test de compréhension naïve réalisé (graphiques compris en <5s)
- [ ] Le jargon data est évité ou expliqué (glossaire si nécessaire)
- [ ] L'executive summary tient sur 1 page A4

### Préparation orale
- [ ] Le script de présentation est rédigé (~150 mots/min)
- [ ] La présentation a été répétée et chronométrée
- [ ] Les 5-10 questions/objections probables ont des réponses préparées
- [ ] Les backup slides sont prêtes (détails supplémentaires si demandés)

---

## KPI de la skill

| KPI | Formule | Cible | Fréquence mesure |
|-----|---------|-------|------------------|
| Clarté perçue | Score moyen "La présentation était claire" (échelle 1-5) | ≥ 4,0 | Par présentation |
| Taux d'adoption recommandations | (Recommandations appliquées / Recommandations totales) x 100 | ≥ 70% | Mensuel |
| NPS post-présentation | Score NPS audience (recommanderiez-vous cette présentation ?) | ≥ 50 | Par présentation |
| Respect du timing | (Présentations respectant le temps imparti ±2 min / Présentations totales) x 100 | ≥ 90% | Mensuel |

---

## Definition of done

Une présentation data storytelling est considérée **terminée** si :

1. ✅ **Executive summary** : Synthèse 1 page produite avec insights + recommandations + impact chiffré
2. ✅ **Slides finales** : Présentation complète avec structure narrative claire (SCR ou autre)
3. ✅ **Design validé** : Règle 1-5-25 respectée, graphiques compréhensibles en <5s (test naïf réalisé)
4. ✅ **Script préparé** : Texte oral rédigé + présentation répétée et chronométrée
5. ✅ **FAQ anticipée** : 5-10 questions probables avec réponses préparées
6. ✅ **Feedback collecté** : Sondage post-présentation avec score clarté ≥4/5

---

## Exemples

### Exemple 1 : Présentation comex "Pourquoi investir dans le marché B2B ?"

**Contexte** : Convaincre le comité de direction d'allouer €500k au développement commercial B2B

**Structure** :
- Slide 1 : Titre "Le marché B2B : une opportunité de €2M+ sur 18 mois"
- Slide 2 : Contexte - 85% du CA actuel vient du B2C, mais panier moyen B2B 8x supérieur
- Slide 3 : Insight 1 - 145 clients B2B génèrent €525k CA, soit 15% du total avec <5% des clients
- Slide 4 : Insight 2 - Taux de rétention B2B 92% vs 68% B2C → LTV B2B 3,5x supérieure
- Slide 5 : Insight 3 - CAC B2B €1,200 vs B2C €45, mais ratio LTV/CAC B2B 12:1 vs B2C 4:1
- Slide 6 : Recommandation - Investir €500k (2 commerciaux + marketing B2B) → ROI 4:1 en 18 mois
- Slide 7 : Plan d'action détaillé (recrutement, formation, KPI, milestones)
- Slide 8 : Conclusion + vote décisionnel

**Résultat** : Vote favorable à l'unanimité, budget alloué

### Exemple 2 : Infographie "KPI e-commerce Q2 2024"

**Format** : A3 vertical, exportable PNG haute résolution

**Contenu** :
- En-tête : Logo + titre "Performance e-commerce Q2 2024 vs Q1 2024"
- Section 1 : 4 KPI cards (CA, Commandes, Panier moyen, Taux conversion) avec évolution % vs Q1
- Section 2 : Line chart - Évolution CA hebdomadaire sur 6 mois
- Section 3 : Top 5 produits (bar chart horizontal)
- Section 4 : Répartition géographique du CA (carte choroplèthe Europe)
- Pied de page : Sources + date + contact analyste

**Usage** : Affichage mural dans open-space commercial, diffusion newsletter interne

### Exemple 3 : Rapport 5 pages "Analyse churn client"

**Audience** : Direction marketing + Customer Success

**Structure** :
1. **Page 1 - Executive Summary** : Synthèse insights + recommandations (template ci-dessus)
2. **Page 2 - Méthodologie** : Sources données, période, définition churn, volume analysé
3. **Page 3 - Analyse descriptive** : Profil clients churnés (segment, ancienneté, panier moyen)
4. **Page 4 - Drivers de churn** : Top 3 raisons identifiées (analyse corrélation)
5. **Page 5 - Plan de rétention** : Actions recommandées + roadmap 6 mois + KPI de suivi

**Format** : PDF exportable, graphiques couleur, tableaux de données en annexe

---

## Contraintes

- **Respect RGPD** : Anonymiser ou agréger les données personnelles dans les présentations diffusées
- **Confidentialité** : Marquer les slides confidentielles (si données sensibles) + contrôler l'audience
- **Accessibilité** : Utiliser des couleurs accessibles (contraste WCAG AA min), décrire les graphiques oralement pour malvoyants
- **Archivage** : Versionner les slides dans Git ou SharePoint avec date + version

---

**Date de création** : 2026-08-04  
**Dernière mise à jour** : 2026-08-04  
**Agents propriétaires** : l'agent d'analyse de données

## Exemples d'usage

### Exemple 1 : Présenter l'évolution du délai de traitement au comité de direction
**Contexte** : Le délai médian s'est amélioré, mais la dispersion a augmenté et la direction doit décider où investir.  
**Input** : Série temporelle validée, définition du délai, segments de dossiers, période de comparaison, public et durée de présentation.  
**Output** : Récit situation-problème-recommandation, visuel lisible de tendance et dispersion, impact quantifié quand les données le permettent et limites explicitement signalées.

### Exemple 2 : Expliquer une baisse de satisfaction sans surinterpréter
**Contexte** : Une enquête montre une baisse récente et les équipes veulent communiquer les résultats aux responsables opérationnels.  
**Input** : Résultats d'enquête, taille et composition de l'échantillon, méthode de collecte, verbatims anonymisés et audience.  
**Output** : Synthèse séparant constat, interprétation et hypothèses, visuels proportionnés aux données, recommandations à tester et questions ouvertes.

# PowerPoint Design Efficiency

**Compétence** : Optimiser création présentations PowerPoint : masques et thèmes, animations/transitions professionnelles, SmartArt, export PDF/vidéo, compatibilité versions.

**Agents utilisateurs** : l'agent Microsoft 365 (principal)

## Quand l'utiliser (triggers)
- Créer masques et thèmes cohérents (charte graphique)
- Concevoir animations/transitions professionnelles
- Utiliser SmartArt et graphiques intégrés
- Exporter présentations (PDF, vidéo, formats compatibles)
- Optimiser compatibilité entre versions PowerPoint

## Hors périmètre
- Direction artistique complexe → l'agent de direction artistique
- Création illustrations/assets visuels → l'agent de direction artistique
- Vidéo montage professionnel → hors périmètre (Premiere, After Effects)
- Présentations interactives web → l'agent front-end

---

## Compétences

### 1. Masques et thèmes (cohérence visuelle)

**Description** : Créer masques de diapositives et thèmes personnalisés pour garantir cohérence charte graphique.

**Masques de diapositives (Slide Masters)** :

**Structure masque** :
```
Affichage → Masque des diapositives

Hiérarchie :
├── Masque principal (styles globaux)
│   ├── Disposition Titre (page titre)
│   ├── Disposition Titre et contenu (diapo standard)
│   ├── Disposition Section (séparateurs)
│   ├── Disposition Deux contenus (comparaison)
│   ├── Disposition Comparaison (tableaux côte à côte)
│   ├── Disposition Contenu seul (image plein écran)
│   └── Disposition Vide (personnalisation totale)

Bonnes pratiques :
- 1 masque principal par présentation
- 5-8 dispositions types maximum (éviter surcharge)
- Nommer dispositions clairement ("Titre projet", "Chiffres clés", etc.)
```

**Créer masque personnalisé** :
```
1. Affichage → Masque des diapositives
2. Sélectionner masque principal
3. Définir éléments globaux :
   - Logo entreprise (position fixe, ex: coin supérieur droit)
   - Polices titres (ex: Arial Bold 32pt, couleur #0078D4)
   - Polices corps (ex: Arial Regular 18pt, couleur #333333)
   - Numérotation diapositives (pied de page)
   - Arrière-plan (couleur ou dégradé subtil)

4. Créer disposition "Titre projet" :
   - Titre centré, grande police (44pt)
   - Sous-titre (auteur, date)
   - Image arrière-plan subtile (opacité 20%)
   - Logo entreprise

5. Créer disposition "Chiffres clés" :
   - 3 zones contenus (KPI)
   - Icônes visuelles (pictogrammes)
   - Police chiffres agrandie (36pt)

6. Enregistrer thème :
   - Fichier → Enregistrer sous → Type : Thème Office (*.thmx)
   - Partager avec équipe (cohérence présentations)
```

**Éléments masque** :
```
Espaces réservés (Placeholders) :
- Titre : Toujours présent (aide structure)
- Contenu : Zone texte/image/tableau/graphique
- Pied de page : Date, numéro diapo, nom entreprise
- Logo : Image fixe (pas modifiable par utilisateur)

Zones de texte fixes vs espaces réservés :
- Zones fixes : Logo, mentions légales (identiques toutes diapos)
- Espaces réservés : Contenu variable par diapo (texte, images)
```

**Thèmes prédéfinis vs personnalisés** :

**Personnaliser thème existant** :
```
Création → Variantes → Personnaliser

Couleurs :
- Définir palette 6-8 couleurs cohérentes
- Exemple : Bleu principal #0078D4, Gris #666666, Vert accent #28A745

Polices :
- Titres : Police impactante (Arial Black, Calibri Bold)
- Corps : Police lisible (Arial, Calibri, Segoe UI)

Effets :
- Ombres, reflets, bordures (modération recommandée)

Arrière-plans :
- Uni, dégradé, texture subtile
- Éviter images trop chargées (lisibilité texte)
```

**Livrables** :
- Masque PowerPoint personnalisé (charte graphique)
- Thème .thmx partageable
- Guide utilisation masques (dispositions, quand utiliser)

**Pièges à éviter** :
- Masques trop complexes (modifications utilisateur difficiles)
- Trop de dispositions (confusion choix)
- Modifications manuelles diapos (contourner masque = incohérence)

---

### 2. Animations et transitions professionnelles

**Description** : Utiliser animations et transitions avec parcimonie pour renforcer message sans distraire.

**Transitions entre diapositives** :

**Transitions recommandées (professionnelles)** :
```
Transitions → Choisir transition

Professionnelles (subtiles) :
- Fondu : Classique, discret
- Balayer : Élégant, directionnel
- Révéler : Moderne, fluide
- Morphose (Morph) : Animation fluide objets identiques entre diapos

À éviter (distractives) :
- Cube, Flip : Trop animées
- Rideau, Volets : Datées
- Aléatoire : Imprévisible, peu professionnel

Configuration transition :
- Durée : 0.5-1 seconde (rapide mais visible)
- Son : Désactivé (sauf contexte spécifique)
- Appliquer à toutes : Cohérence (même transition partout)
```

**Morphose (Morph Transition)** :
```
Transition intelligente PowerPoint (version 2016+)

Utilisation :
1. Diapo 1 : Objet position A
2. Dupliquer diapo (Ctrl+D)
3. Diapo 2 : Déplacer objet position B
4. Appliquer transition Morphose
5. Lecture → Objet se déplace fluidement A → B

Exemples :
- Déplacer éléments (graphiques, textes)
- Zoomer sur détail (agrandir objet entre diapos)
- Transformer formes (cercle → carré)

Contraintes :
- Objets doivent être identiques (même nom, type)
- Fonctionne uniquement PowerPoint 2016+ / Microsoft 365
```

**Animations objets** :

**Animations subtiles (recommandées)** :
```
Animations → Ajouter animation

Types animations :
1. Entrée :
   - Apparition : Instant, discret
   - Balayage : Directionnel, élégant
   - Fondu : Progressif, subtil

2. Emphase :
   - Agrandir/Réduire : Attirer attention sur élément clé
   - Couleur police : Changer couleur texte (mise en avant)

3. Sortie :
   - Disparition : Retrait discret
   - Balayer : Sortie directionnelle

4. Trajectoires :
   - Personnalisées : Déplacer objet selon tracé
   - Utiliser avec parcimonie (risque distraction)

Configuration animation :
- Déclencheur : Au clic (contrôle présentateur) ou Automatique (timing précis)
- Durée : 0.5-1 seconde (rapide)
- Délai : 0.2-0.5 seconde entre animations successives
- Ordre : Volet Animation (numéroté 1, 2, 3...)
```

**Séquence animations** :
```
Exemple : Révélation progressive graphique

Diapo "Évolution CA 2020-2026" :
1. Titre : Apparition (0.5s, au clic)
2. Graphique axes : Apparition (0.5s, après précédent)
3. Série 2020-2023 : Balayage gauche→droite (1s, après précédent)
4. Série 2024-2026 : Balayage gauche→droite (1s, après précédent)
5. Commentaire clé : Fondu (0.5s, après précédent)

Résultat : Graphique se construit progressivement (storytelling visuel)
```

**Livrables** :
- Présentation avec transitions cohérentes
- Animations clés (mise en valeur messages importants)
- Guide bonnes pratiques animations (do/don't)

**Pièges à éviter** :
- Trop d'animations (effet PowerPoint 90s, distraction)
- Animations trop lentes (> 2s = perte attention)
- Sons animations (perturbant, désactiver par défaut)
- Animations automatiques mal timées (décalage avec discours)

---

### 3. SmartArt et graphiques intégrés

**Description** : Utiliser SmartArt pour visualiser informations complexes et graphiques pour données chiffrées.

**SmartArt** :

**Types SmartArt** :
```
Insertion → SmartArt

Catégories principales :
1. Liste : Énumérations simples (puces visuelles)
2. Processus : Flux, étapes (workflow, timeline)
3. Cycle : Processus répétitifs (amélioration continue)
4. Hiérarchie : Organigrammes, arborescences
5. Relation : Connexions (diagramme Venn, balance)
6. Matrice : 2×2, 3×3 (analyse SWOT, BCG)
7. Pyramide : Hiérarchie verticale (Maslow, priorités)
8. Image : Galeries photos avec légendes
```

**Exemples SmartArt courants** :
```
Processus linéaire (étapes projet) :
SmartArt → Processus → Processus de base
- Étape 1 : Analyse besoins
- Étape 2 : Conception
- Étape 3 : Développement
- Étape 4 : Tests
- Étape 5 : Déploiement

Timeline (roadmap) :
SmartArt → Processus → Chronologie simple
- Q1 2026 : Lancement Projet A
- Q2 2026 : Migration Système B
- Q3 2026 : Refonte Site Web
- Q4 2026 : Consolidation

Organigramme :
SmartArt → Hiérarchie → Hiérarchie (type 1)
- Direction Générale
  ├── Direction Commerciale
  │   ├── Ventes France
  │   └── Ventes Export
  └── Direction Technique
      ├── R&D
      └── Production

Matrice 2×2 (BCG, SWOT) :
SmartArt → Matrice → Matrice simple
- Quadrant 1 : Stars (forte croissance, forte part marché)
- Quadrant 2 : Cash Cows (faible croissance, forte part marché)
- Quadrant 3 : Question Marks (forte croissance, faible part marché)
- Quadrant 4 : Dogs (faible croissance, faible part marché)
```

**Personnalisation SmartArt** :
```
Outils SmartArt → Création → Styles

Couleurs :
- Modifier palette (cohérence charte graphique)
- Contraste élevé (lisibilité projection)

Effets :
- 2D : Plat, moderne
- 3D : Relief (utiliser modérément)

Mise en page :
- Ajouter/Supprimer formes (Ctrl+Entrée / Suppr)
- Réorganiser ordre (flèches volet texte)
- Redimensionner proportions (glisser poignées)
```

**Graphiques Excel intégrés** :

**Types graphiques courants** :
```
Insertion → Graphique

Histogrammes (comparaisons) :
- Histogrammes groupés : Comparer catégories
- Histogrammes empilés : Montrer composition total

Courbes (évolutions) :
- Courbes simples : Tendances temporelles
- Courbes lissées : Visualisation fluide

Secteurs (proportions) :
- Camembert : Répartition simple (max 5-6 parts)
- Anneau : Multi-séries (camembert imbriqués)

Barres (classements) :
- Barres horizontales : Top 10, rankings

Nuages de points (corrélations) :
- XY : Analyser relation 2 variables

Combo (hybrides) :
- Histogramme + Courbe : CA (histogramme) + Marge (courbe)
```

**Bonnes pratiques graphiques** :
```
Do :
- Titres explicites : "Évolution CA 2020-2026 (M€)"
- Axes libellés : Unités claires (€, %, unités)
- Légende claire : Couleurs distinctives
- Couleurs cohérentes : Palette charte graphique
- Données simplifiées : Arrondir (10.234 → 10.2K)

Don't :
- Graphiques 3D : Distorsion perception (éviter)
- Trop de séries : Max 5-6 courbes/barres (lisibilité)
- Échelles trompeuses : Axe Y non à 0 (manipulation visuelle)
- Couleurs flashy : Arc-en-ciel (privilégier palette sobre)
```

**Livrables** :
- Bibliothèque SmartArt types (10-15 modèles réutilisables)
- Templates graphiques Excel (histogrammes, courbes types)
- Guide bonnes pratiques visualisation données

**Pièges à éviter** :
- SmartArt trop complexes (max 7-8 éléments par diagramme)
- Graphiques 3D (déformation, illisibilité)
- Camemberts trop détaillés (> 6 parts = confusion)
- Graphiques Excel non liés (données manuelles = erreurs mises à jour)

---

### 4. Export PDF/vidéo et compatibilité versions

**Description** : Exporter présentations dans formats universels et garantir compatibilité multi-versions.

**Export PDF** :

**Configuration export PDF** :
```
Fichier → Exporter → Créer PDF/XPS

Options recommandées :
- Qualité : Standard (pour email) ou Haute qualité (pour impression)
- Pages : Toutes ou sélection
- Options avancées :
  ✅ Optimiser pour : Taille minimale (si email < 10 Mo)
  ✅ Conforme PDF/A (archivage long terme)
  ❌ Annotations (commentaires exclus si présentation finale)

Diapositives avec notes :
- Fichier → Imprimer → Paramètres : "Pages de notes"
- Imprimer en → PDF (Microsoft Print to PDF)
- Résultat : PDF avec diapo + notes présentateur
```

**Export vidéo** :

**Créer vidéo présentation** :
```
Fichier → Exporter → Créer une vidéo

Paramètres :
1. Qualité :
   - Ultra HD (4K) : 3840×2160 (fichier volumineux, projection HD)
   - Full HD (1080p) : 1920×1080 (recommandé, équilibre qualité/taille)
   - HD (720p) : 1280×720 (partage web, taille réduite)

2. Narration et minutage :
   - Utiliser minutages et narrations enregistrés (si enregistrés)
   - Durée diapo fixe : 5 secondes par défaut (ajustable 1-999s)

3. Créer vidéo → Enregistrer .mp4

Narration (optionnel) :
- Diaporama → Enregistrer le diaporama
- Enregistrer voix + minutage transitions
- Export vidéo avec narration synchronisée
```

**Compatibilité versions PowerPoint** :

**Vérifier compatibilité** :
```
Fichier → Informations → Vérifier les problèmes → Vérifier la compatibilité

Problèmes courants :
- Morphose : Non supportée avant PowerPoint 2016
- SmartArt 3D : Convertis images statiques versions anciennes
- Vidéos embarquées : Formats non supportés (codecs manquants)
- Polices personnalisées : Substituées si non installées

Résolutions :
1. Incorporer polices :
   Fichier → Options → Enregistrement → ✅ Incorporer polices dans fichier
   (augmente taille fichier mais garantit affichage)

2. Compresser médias :
   Fichier → Informations → Compresser le média → Qualité Full HD
   (réduit taille + améliore compatibilité codecs)

3. Enregistrer version compatible :
   Fichier → Enregistrer sous → PowerPoint 97-2003 (.ppt)
   (perte animations avancées mais lecture garantie anciennes versions)
```

**Formats export** :
```
Formats courants :

.pptx (PowerPoint 2007+) :
- Format standard
- Animations, transitions, multimédia
- Éditable

.ppsx (Diaporama PowerPoint) :
- Ouvre directement en mode présentation (pas édition)
- Utile présentations finales (éviter modifications accidentelles)

.pdf :
- Universel, non éditable
- Perte animations/transitions
- Idéal partage/archivage

.mp4 (Vidéo) :
- Lecture universelle (lecteurs vidéo)
- Narration synchronisée
- Non éditable

.odp (LibreOffice Impress) :
- Open source, compatible OpenOffice
- Perte partielle mise en forme/animations
```

**Livrables** :
- Présentation .pptx (version éditable)
- PDF (partage/archivage)
- Vidéo .mp4 (si narration)
- Checklist compatibilité (vérifications avant export)

**Pièges à éviter** :
- Polices non incorporées (affichage dégradé autres PC)
- Vidéos non embarquées (liens rompus si fichier déplacé)
- Export PDF sans vérification (diapositives coupées si format non standard)
- Taille fichier excessive (> 50 Mo = problèmes envoi email)

---

## Objectif

Créer présentations PowerPoint professionnelles, cohérentes et universellement accessibles via :
- Masques/thèmes (cohérence charte graphique)
- Animations/transitions subtiles (storytelling visuel)
- SmartArt/graphiques (visualisation données)
- Exports multi-formats (PDF, vidéo, compatibilité)

---

## Inputs requis

- **Objectif présentation** : Interne, client, conférence, formation
- **Charte graphique** : Logo, couleurs, polices entreprise
- **Contenu** : Textes, données, images sources
- **Format diffusion** : Projection, PDF, vidéo, web
- **Contraintes technique** : Version PowerPoint cible, taille fichier max

---

## Sorties attendues

**Masques/Thèmes** :
- Masque PowerPoint personnalisé (.potx)
- Thème .thmx partageable
- Guide utilisation (dispositions)

**Animations** :
- Présentation avec transitions cohérentes
- Animations clés (storytelling)

**Visualisations** :
- SmartArt types (bibliothèque 10-15 modèles)
- Graphiques Excel intégrés

**Exports** :
- .pptx (éditable), .pdf, .mp4 (si vidéo)
- Checklist compatibilité

---

## Workflow recommandé

1. **Définir charte graphique** : Logo, couleurs, polices
2. **Créer masque** : Dispositions types (5-8 layouts)
3. **Enregistrer thème** : .thmx réutilisable
4. **Structurer contenu** : Plan présentation (diapos clés)
5. **Insérer visualisations** : SmartArt, graphiques
6. **Ajouter animations** : Transitions + animations clés (parcimonie)
7. **Vérifier compatibilité** : Test anciennes versions si nécessaire
8. **Exporter formats** : PDF, vidéo selon besoin
9. **Tester présentation** : Projection, timings, lisibilité
10. **Partager** : .pptx (interne) + PDF (externe)

---

## Garde-fous

- **Animations** : Max 20-30% diapositives animées (éviter surcharge)
- **SmartArt** : Max 7-8 éléments par diagramme (règle 7±2)
- **Polices** : Incorporer dans fichier (garantir affichage)
- **Vidéos** : Compresser médias (taille fichier < 50 Mo recommandé)
- **Compatibilité** : Vérifier avant envoi (éviter fonctionnalités récentes si cible PowerPoint < 2016)

---

## Template d'entrée (copier/coller)
```text
[Contexte de présentation]
- Version PowerPoint et support de diffusion : ...
- Public, objectif et durée : ...
- Charte graphique et modèles existants : ...
- Besoins de masque, animation, graphiques ou export : ...
- Contraintes d'accessibilité et de compatibilité : ...
```

## Template de sortie (copier/coller)
```text
[Livrable PowerPoint]
- Masques, thèmes et éléments configurés : ...
- Animations/visuels retenus et justification : ...
- Formats d'export et compatibilité validée : ...
- Vérifications d'accessibilité et étapes de mise à jour : ...
```

## Templates copier/coller

**Template masque diapo standard** :
```
Affichage → Masque diapositives

Disposition "Titre et contenu" :
- Titre : Arial Bold 32pt, #0078D4, alignement gauche
- Contenu : Zone espace réservé (texte/image/graphique)
- Logo : Coin supérieur droit, 100×30 px
- Pied page : Numéro diapo + nom entreprise, Arial 10pt, #666666
- Arrière-plan : Blanc avec bande couleur gauche (#0078D4, 10px largeur)
```

**Template animation progressive liste** :
```
Liste à puces (5 items) :

Animation :
1. Item 1 : Apparition, 0.5s, au clic
2. Item 2 : Apparition, 0.5s, après précédent, délai 0.3s
3. Item 3 : Apparition, 0.5s, après précédent, délai 0.3s
4. Item 4 : Apparition, 0.5s, après précédent, délai 0.3s
5. Item 5 : Apparition, 0.5s, après précédent, délai 0.3s

Résultat : Items apparaissent un par un automatiquement (rythme fluide)
```

---

## Checklist QA interne

- [ ] Masque personnalisé créé (charte graphique respectée)
- [ ] Thème .thmx enregistré (réutilisable)
- [ ] Transitions cohérentes (même transition toutes diapos)
- [ ] Animations subtiles (< 30% diapos animées)
- [ ] SmartArt lisibles (max 7-8 éléments/diagramme)
- [ ] Graphiques clairs (titres, axes, légendes explicites)
- [ ] Polices incorporées (affichage garanti)
- [ ] Compatibilité vérifiée (test version cible)
- [ ] Exports fonctionnels (PDF, vidéo si applicable)
- [ ] Taille fichier acceptable (< 50 Mo pour email)

---

## KPI

- **Temps création** : Réduction temps création présentation (heures)
- **Réutilisation thème** : Nombre présentations utilisant thème (adoption)
- **Cohérence visuelle** : % présentations conformes charte graphique (cible 100%)
- **Satisfaction** : Feedback utilisateurs/clients (échelle 1-5, cible ≥ 4)

---

## Definition of done

- [ ] Masque PowerPoint créé (5-8 dispositions)
- [ ] Thème .thmx enregistré et partagé
- [ ] Présentation avec transitions/animations validées
- [ ] SmartArt et graphiques intégrés (visualisations claires)
- [ ] Exports réalisés (.pptx, .pdf, .mp4 si applicable)
- [ ] Compatibilité vérifiée (version PowerPoint cible)
- [ ] Guide utilisateur fourni (masques, animations, exports)
- [ ] Présentation testée (projection, timings)
- [ ] Feedback positif (≥ 4/5)

---

## Exemples

**Exemple 1 : Masque présentation client**
```
Thème "Client Premium"

Masque principal :
- Polices : Calibri Bold (titres), Calibri (corps)
- Couleurs : Bleu #0078D4, Gris #666666, Vert accent #28A745
- Logo : Coin supérieur droit (toutes diapos)
- Pied page : "Entreprise X - Confidentiel" + numéro

Dispositions :
1. Titre présentation : Titre centré 44pt + sous-titre 24pt
2. Section : Fond bleu, titre blanc centré 36pt (séparateurs)
3. Titre + contenu : Standard (80% diapos)
4. Deux colonnes : Comparaison (avantages/inconvénients)
5. Citation : Texte centré 28pt italique (témoignages clients)
6. Chiffres clés : 3 zones KPI + icônes
7. Contact : Coordonnées + QR code
```

**Exemple 2 : Animation graphique évolution CA**
```
Diapo "Croissance CA 2020-2026"

Contenu :
- Titre : "Croissance CA 2020-2026 (+45%)"
- Graphique courbe : CA millions €

Animations (séquence) :
1. Titre : Apparition, 0.5s, au clic
2. Axes graphique : Balayage bas→haut, 0.8s, après précédent
3. Courbe 2020-2023 : Balayage gauche→droite, 1.2s, après précédent
4. Courbe 2024-2026 (projection) : Balayage gauche→droite pointillés, 1.2s, après précédent
5. Zone texte "+45%" : Agrandir + Emphase, 0.5s, après précédent

Résultat : Graphique se construit progressivement, mise en valeur croissance
```

**Exemple 3 : Export multi-formats projet client**
```
Présentation : "Proposition Commerciale Client X"

Exports :
1. .pptx (version interne équipe commerciale, éditable)
2. .ppsx (diaporama client, ouverture directe mode présentation)
3. .pdf (envoi email client, non éditable, optimisé < 5 Mo)
4. .mp4 (vidéo narration commerciale, diffusion site web/réseaux sociaux)

Paramètres export vidéo :
- Qualité : Full HD 1080p
- Narration : Enregistrée (voix commerciale)
- Durée totale : 8 minutes
- Taille fichier : 120 Mo (compression média appliquée)
```

---

## Contraintes

- **Versions PowerPoint** : Morphose nécessite PowerPoint 2016+ / Microsoft 365
- **Taille fichier** : Email limite souvent 25-50 Mo (compresser médias obligatoire)
- **Polices** : Incorporer polices augmente taille fichier (~500 Ko/police)
- **Vidéos** : Codecs H.264 recommandés (compatibilité universelle)
- **Compatibilité** : SmartArt 3D/effets avancés dégradés versions < 2013

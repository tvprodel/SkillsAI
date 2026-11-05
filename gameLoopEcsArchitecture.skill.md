# Game Loop & ECS Architecture

## Objectif
Produire un livrable maîtrisé : note d'architecture de boucle de jeu et de modèle de données (ECS ou data-oriented) avec stratégie de mémoire et de threading, validée par un prototype mesuré.


## Quand l'utiliser (triggers)
- Demande portant sur « Game Loop & ECS Architecture » ou sur le livrable : architecture de boucle de jeu, ECS/data-oriented design, gestion mémoire et jobs multithread.
- Besoin de vérifier ce résultat : le prototype respecte le budget de frame déclaré sur la charge de référence, sans data race détectée ni allocation inattendue dans la boucle chaude.

## Hors périmètre
- Ne pas remplacer les domaines des agents complémentaires : présenter les interfaces et transmettre les besoins à l'agent rattaché (voir table de routage).
- L'exécution système, les modifications de fichiers, les compilations, les benchmarks et les publications relèvent de l'agent rattaché (voir table de routage) ; cette skill n'accorde aucun outil supplémentaire.
- Ne pas confondre schéma d'architecture, revue statique et mesures réellement exécutées.
- Ne pas concevoir l'IA de PNJ, l'économie ni la narration : ces sujets relèvent des agents GameDev dédiés via l'agent de coordination ; l'architecture applicative non-jeu relève de l'agent d'architecture logicielle.

## Inputs requis
- Moteur ou framework cible (Godot, Bevy, autre moteur libre), langage et plateformes.
- Profil de charge de référence : nombre d'entités, composants, systèmes, budget de frame (ms) et fréquence de simulation.
- Contraintes mémoire, nombre de cœurs visés, exigences de déterminisme (réseau, replay).
- Critères d'acceptation et limites d'action ; marquer les éléments inconnus avant de conclure.

## Sorties attendues
- Note d'architecture : boucle (pas fixe, pas variable, interpolation), découpage des systèmes, modèle de composants, ordonnancement et dépendances de données.
- Stratégie mémoire (allocateurs, pools, layout SoA/AoS) et stratégie de jobs/threading avec règles de synchronisation.
- Prototype ou plan de prototype avec protocole de benchmark reproductible.
- Preuves ou références par constat ; hypothèses, exceptions et vérifications non réalisées séparées.
- Brief des décisions ou actions nécessaires pour l'agent rattaché, sans les annoncer déjà exécutées.

## Workflow recommandé
1. Cadrer les inputs : moteur, charge de référence, budget de frame, cœurs visés et exigences de déterminisme.
2. Choisir le modèle de boucle (pas fixe de simulation et rendu interpolé, ou pas variable) et justifier le choix par le besoin.
3. Définir le modèle de données : composants, archétypes ou tables, layout mémoire adapté aux accès chauds, et ordre des systèmes.
4. Définir la stratégie de multithreading : découpage en jobs, dépendances, accès exclusifs ou partagés, règles de synchronisation.
5. Vérifier le livrable par ce critère : le prototype respecte le budget de frame déclaré sur la charge de référence, sans data race détectée ni allocation inattendue dans la boucle chaude.
6. Restituer architecture, mesures, hypothèses, risques et prochaines actions ; signaler explicitement les blocages et les arbitrages non tranchés.

## Garde-fous
- Le prototype respecte le budget de frame déclaré sur la charge de référence, sans data race détectée ni allocation inattendue dans la boucle chaude.
- Ne pas adopter un ECS par principe : justifier par la charge mesurée ou attendue, sinon conserver une composition plus simple.
- Ne pas inventer de mesure ni de gain de performance ; distinguer observé, inféré et non testé.
- Documenter les compromis de déterminisme (ordre des systèmes, nombres flottants, graines aléatoires).
- Code natif multithread ou à mémoire non sûre : passage par l'agent de sécurité avant usage sensible.
- Privilégier les moteurs et bibliothèques libres maintenus, vérifier les licences et ne pas introduire de composant EOL.
- Lire la référence dans son contexte : elle éclaire la méthode, elle ne certifie pas ce livrable et n'impose pas de seuil universel.

## Templates copier/coller
### Entrée
```text
Objet : Game Loop & ECS Architecture
Inputs : moteur/framework, charge de référence (entités, systèmes), budget de frame, cœurs visés, déterminisme
Version / périmètre autorisé :
Résultat demandé : note d'architecture boucle + modèle de données + stratégie mémoire/threading, avec protocole de benchmark
Contraintes et inconnues :
```

### Sortie
```text
Résultat : note d'architecture boucle de jeu / ECS avec stratégie mémoire et threading
| Élément examiné | Preuve / source / version | Conclusion | Limite / action |
|---|---|---|---|
Budget de frame (cible / mesuré) :
Protocole de benchmark (charge, machine, version) :
Hypothèses :
Risques :
Prochaines actions :
```

## Checklist QA interne
- [ ] Les inputs et les limites d'autorisation sont identifiés.
- [ ] Les trois analyses sont documentées : modèle de boucle et ordonnancement ; layout mémoire et allocations de la boucle chaude ; jobs, dépendances et synchronisation.
- [ ] Le protocole de benchmark est reproductible (charge, machine, version, nombre d'exécutions).
- [ ] Le critère d'acceptation est vérifié ou explicitement marqué non vérifié.
- [ ] Aucun résultat de mesure n'est inventé.

## KPI reliés
- Temps de frame au 95e percentile sur la charge de référence / budget de frame déclaré.
- Nombre d'allocations dans la boucle chaude par frame (cible déclarée dans la note).
- Nombre de data races ou d'écarts de déterminisme détectés restant ouverts au critère : le prototype respecte le budget de frame sans data race ni allocation inattendue.

## Definition of done
- [ ] Note d'architecture (boucle, modèle de données, mémoire, threading) et protocole de benchmark livrés dans le périmètre convenu.
- [ ] Le prototype respecte le budget de frame déclaré sur la charge de référence, sans data race détectée ni allocation inattendue dans la boucle chaude, ou l'écart est documenté.
- [ ] Preuves, inconnues, exceptions et actions restantes sont lisibles ; aucune réussite globale en cas de vérification bloquante manquante.

## Exemples d'usage
**Cas nominal** : à partir d'un besoin de 50 000 entités simulées à 60 Hz sur 4 cœurs avec Bevy ou une extension Godot, produire la note d'architecture et le prototype, puis vérifier le critère d'acceptation ci-dessus.

**Cas limite** : la charge de référence ou la machine de mesure n'est pas définie ; livrer l'architecture conditionnelle et le protocole proposé, en indiquant que le critère de budget de frame reste non vérifié.

## Contraintes et références
- Référence officielle : [Bevy - ECS](https://docs.rs/bevy/latest/bevy/ecs/index.html). Synthèse originale, sans reproduction du texte source ; page non consultée en détail lors de la création, vérifier les versions et l'applicabilité au contexte.
- Création : DEL-20261026-GAMEDEV-CREA-AGENTS.

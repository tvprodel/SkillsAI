# Adaptive Audio Implementation

## Objectif
Produire un livrable maîtrisé : spécification d'implémentation audio adaptative pour Godot 4 (bus audio, variations, randomisation, ducking, formats d'export, budget mémoire) prête à être codée.


## Quand l'utiliser (triggers)
- Demande portant sur « Adaptive Audio Implementation » ou sur le livrable : spécification d'implémentation audio adaptative pour Godot 4 (bus audio, variations, randomisation, ducking, formats d'export, budget mémoire) prête à être codée.
- Besoin de vérifier ce résultat : chaque événement sonore a un bus, une règle de variation, un format d'export et un coût mémoire estimé, et le total respecte le budget audio déclaré.

## Hors périmètre
- Ne pas remplacer les domaines des agents complémentaires : présenter les interfaces et transmettre les besoins à l'agent rattaché (voir table de routage).
- L'exécution système, les modifications de fichiers, les tests et les publications relèvent de l'agent rattaché (voir table de routage) ; cette skill n'accorde aucun outil supplémentaire.
- Ne pas écrire le code GDScript, les scènes de gameplay ni la configuration d'export du moteur (→ l'agent de développement Godot) ; ne pas composer la musique adaptative (→ l'agent de composition musicale).
- Ne pas confondre spécification, revue statique et résultat d'une exécution réelle dans le moteur.

## Inputs requis
- Liste des événements sonores et leur déclencheur de jeu, version de Godot, plateformes cibles.
- Bibliothèque de sons livrée (durées, formats, fréquence d'échantillonnage), mix et règles de priorité issus du plan de mixage.
- Budget mémoire audio et contraintes de streaming, décisions déjà validées ; marquer les éléments inconnus avant de conclure.

## Sorties attendues
- Spécification d'implémentation : arbre des bus audio, effets par bus, règles de variation (choix aléatoire, hauteur, volume), règles de ducking, polyphonie maximale par événement.
- Table des formats d'export (WAV pour les sons courts, OGG Vorbis pour les sons longs ou la musique, à vérifier selon la version du moteur) et estimation du poids mémoire par groupe.
- Brief de code pour l'agent de développement Godot, via flux à sens unique ; décisions ou actions pour l'agent de coordination, sans les annoncer déjà exécutées.

## Workflow recommandé
1. Cadrer les événements, déclencheurs, plateformes et budget mémoire audio ; vérifier la version de Godot et les fonctionnalités audio documentées.
2. Concevoir l'arbre des bus (voix, SFX, ambiances, musique, interface) et les effets associés, en cohérence avec le plan de mixage.
3. Définir pour chaque événement les variations (nombre de samples, randomisation de hauteur et de volume, anti-répétition) et la polyphonie maximale.
4. Choisir format et mode de chargement par groupe (échantillon en mémoire ou flux) et estimer le coût mémoire.
5. Vérifier le critère : chaque événement a un bus, une règle de variation, un format et un coût estimé, et le total respecte le budget déclaré.
6. Transmettre le brief à l'agent technique du moteur de jeu et restituer résultat, hypothèses, risques et prochaines actions ; signaler ce qui n'a pas été testé dans le moteur.

## Garde-fous
- Chaque événement sonore a un bus, une règle de variation, un format d'export et un coût mémoire estimé, et le total respecte le budget audio déclaré.
- Ne pas inventer de nœud, de paramètre ni de fonctionnalité du moteur : vérifier dans la documentation de la version de Godot utilisée.
- Ne pas inventer de mesure, d'accord, de preuve ou de source ; distinguer observé, inféré et non testé.
- Ne pas transmettre d'artefact privé ou de donnée personnelle à un service tiers ; aucun secret en dur.
- Privilégier Godot et les outils libres maintenus ; middleware propriétaire (FMOD, Wwise) seulement si justifié et licence vérifiée, sans dépendance EOL.
- Tracer toute source audio externe dans `docs/imageLicencesSources.md` (format `Nomdefichier | licence | url source`).
- Lire la référence dans son contexte : elle éclaire la méthode, elle ne certifie pas ce livrable et n'impose pas de seuil universel.

## Templates copier/coller
### Entrée
```text
Objet : Adaptive Audio Implementation
Inputs : événements et déclencheurs, version de Godot, plateformes, bibliothèque de sons, plan de mixage, budget mémoire audio
Version / périmètre autorisé :
Résultat demandé : spécification audio adaptative (bus, variations, ducking, formats, budget mémoire)
Contraintes et inconnues :
```

### Sortie
```text
Résultat : spécification audio adaptative (bus, variations, ducking, formats, budget mémoire)
| Événement | Bus | Règle de variation | Format / chargement | Coût mémoire estimé | Limite / action |
|---|---|---|---|---|---|
Hypothèses :
Risques :
Prochaines actions :
```

## Checklist QA interne
- [ ] Les inputs et les limites d'autorisation sont identifiés.
- [ ] Les trois analyses sont documentées : arbre des bus et règles de ducking ; variations, randomisation et polyphonie par événement ; formats, mode de chargement et budget mémoire.
- [ ] Le critère d'acceptation est vérifié ou explicitement marqué non vérifié.
- [ ] Aucun résultat d'exécution dans le moteur ou accord humain n'est inventé.

## KPI reliés
- Couverture des événements sonores : événements spécifiés complets (bus, variation, format, coût) / événements de la liste (dénominateur conservé).
- Écart entre le coût mémoire audio estimé et le budget déclaré ; ne pas compter une estimation comme mesure.
- Nombre d'événements sans règle anti-répétition alors qu'ils sont déclenchés de façon fréquente : à maintenir à zéro.

## Definition of done
- [ ] Spécification d'implémentation audio adaptative livrée dans le périmètre convenu.
- [ ] Chaque événement a bus, variation, format et coût estimé ; le total respecte le budget déclaré.
- [ ] Preuves, inconnues, exceptions et actions restantes sont lisibles ; aucune réussite globale en cas de vérification bloquante manquante.

## Exemples d'usage
**Cas nominal** : à partir de 30 événements sonores d'un niveau, des plans de bus et d'un budget de 20 Mo, produire la table bus/variation/format/coût, vérifier le critère d'acceptation ci-dessus et transmettre le brief à l'agent technique du moteur de jeu.

**Cas limite** : le budget mémoire n'est pas fourni ; livrer la spécification avec les coûts estimés par groupe et indiquer que la conformité au budget ne peut pas être validée.

## Contraintes et références
- Référence officielle : [Godot - Audio buses](https://docs.godotengine.org/en/stable/tutorials/audio/audio_buses.html). Synthèse originale, sans reproduction du texte source ; page non consultée en détail lors de la création, vérifier les versions et l'applicabilité au contexte.
- Création : DEL-20261026-GAMEDEV-CREA-AGENTS.

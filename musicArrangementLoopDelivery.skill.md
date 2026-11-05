# Music Arrangement, Loop & Delivery

## Objectif
Produire un livrable maîtrisé : arrangement finalisé, boucles propres et lot d'exports (OGG/WAV) avec manifeste documentant tempo, tonalité, durée et points de boucle.


## Quand l'utiliser (triggers)
- Demande portant sur « Music Arrangement, Loop & Delivery » ou sur le livrable : arrangement finalisé, boucles propres et lot d'exports avec manifeste.
- Besoin de vérifier ce résultat : chaque boucle se répète sans clic, saut de niveau ni coupure de queue audible, et chaque fichier du lot figure dans le manifeste avec ses métadonnées.

## Hors périmètre
- Ne pas remplacer les domaines des agents complémentaires : présenter les interfaces et transmettre les besoins à l'agent rattaché (voir table de routage).
- L'exécution système, les modifications de fichiers, les tests et les publications relèvent de l'agent rattaché (voir table de routage) ; cette skill n'accorde aucun outil supplémentaire.
- Ne pas confondre préparation d'un protocole, revue statique et résultat d'une exécution réelle dans le logiciel.
- Ne pas faire le mixage SFX, le réglage de loudness global du jeu ni l'implémentation audio (l'agent de sound design), ni les contrats de licence (l'agent juridique via l'agent de coordination).

## Inputs requis
- Maquette ou partition validée, tempo, tonalité, métrique et longueur voulue de chaque boucle ou pièce.
- Formats et contraintes de livraison : OGG ou WAV, fréquence d'échantillonnage, mono ou stéréo, budget de taille, destinataire.
- Logiciels disponibles et versions (LMMS, Ardour, MuseScore, LilyPond, Audacity, FFmpeg), périmètre autorisé.
- Marquer les éléments inconnus avant de conclure.

## Sorties attendues
- Arrangement finalisé (partition ou session) avec parties, tessitures et équilibre vérifiés.
- Boucles propres (début et fin sur frontière de mesure, queue de réverbération gérée) et versions d'introduction ou de fin si demandées.
- Lot d'exports OGG/WAV nommés de façon cohérente, avec manifeste : fichier, durée, tempo, tonalité, métrique, point de boucle, format, source et licence.
- Brief de livraison pour l'agent de sound design et, si les stems sont prêts à intégrer, pour l'agent de développement Godot ; hypothèses et vérifications non réalisées séparées.

## Workflow recommandé
1. Cadrer les inputs : maquette validée, formats de livraison, contraintes de taille ; vérifier les préconditions et autorisations.
2. Finaliser l'arrangement : répartition des parties, doublures, tessitures, dynamiques et équilibre entre instruments.
3. Préparer les boucles : début et fin sur frontière de mesure, queue de réverbération repliée sur le début, absence de silence ou de pic parasite aux jonctions.
4. Exporter les fichiers (OGG/WAV) avec des paramètres constants, sans écrêtage, et nommer chaque fichier selon la convention camelCase du dépôt.
5. Vérifier le livrable par ce critère : chaque boucle se répète sans clic, saut de niveau ni coupure de queue audible, et chaque fichier figure dans le manifeste avec durée, tempo, tonalité et point de boucle ; écouter chaque boucle répétée au moins deux fois de suite.
6. Restituer résultat, hypothèses, risques et prochaines actions ; signaler explicitement les blocages.

## Garde-fous
- Chaque boucle est vérifiée à l'écoute en répétition ; chaque export est listé dans le manifeste avec ses métadonnées.
- Ne pas inventer de mesure, de durée, de preuve ou de source ; distinguer observé, inféré et non testé.
- Ne pas prétendre qu'un format ou un réglage d'export est pris en charge par le moteur sans confirmation de l'agent technique du moteur de jeu.
- Ne pas transmettre d'artefact privé ou de donnée personnelle à un service tiers ; minimiser les données sensibles.
- Privilégier les outils libres maintenus (LMMS, Ardour, MuseScore, LilyPond, Audacity, FFmpeg) ; toute alternative propriétaire doit être justifiée ; vérifier les versions sans introduire de dépendance EOL.
- Musique originale uniquement ou Domaine Public/CC0 ; tracer chaque source externe (échantillons, soundfonts) dans `docs/imageLicencesSources.md` (format `Nomdefichier | licence | url source`).
- Lire la référence dans son contexte : elle éclaire la méthode, elle ne certifie pas ce livrable et n'impose pas de seuil universel.

## Templates copier/coller
### Entrée
```text
Objet : Music Arrangement, Loop & Delivery
Inputs : maquette ou partition validée, tempo/tonalité/métrique, formats de livraison, contraintes de taille
Version / périmètre autorisé :
Résultat demandé : arrangement finalisé, boucles propres et lot d'exports avec manifeste
Contraintes et inconnues :
```

### Sortie
```text
Résultat : arrangement, boucles et exports livrés
| Fichier | Durée - tempo - tonalité - métrique | Point de boucle - format | Source / licence |
|---|---|---|---|
Hypothèses :
Risques :
Prochaines actions :
```

## Checklist QA interne
- [ ] Les inputs et les limites d'autorisation sont identifiés.
- [ ] Les trois analyses sont documentées : arrangement et équilibre des parties ; préparation et écoute des boucles ; paramètres d'export et manifeste.
- [ ] Le critère d'acceptation est vérifié ou explicitement marqué non vérifié.
- [ ] Aucun résultat d'exécution ou accord humain n'est inventé.

## KPI reliés
- Couverture du manifeste : fichiers exportés renseignés avec toutes leurs métadonnées / fichiers exportés (dénominateur conservé).
- Part des boucles écoutées en répétition et validées sans clic ni saut de niveau / boucles livrées ; ne pas compter une hypothèse comme preuve.
- Nombre d'écarts au critère suivant restant ouverts : chaque boucle se répète sans clic, saut de niveau ni coupure de queue audible et chaque fichier figure dans le manifeste.

## Definition of done
- [ ] Arrangement finalisé, boucles propres et lot d'exports avec manifeste livrés dans le périmètre convenu.
- [ ] Chaque boucle se répète sans clic, saut de niveau ni coupure de queue audible, et chaque fichier figure dans le manifeste avec durée, tempo, tonalité et point de boucle.
- [ ] Preuves, inconnues, exceptions et actions restantes sont lisibles ; aucune réussite globale en cas de vérification bloquante manquante.

## Exemples d'usage
**Cas nominal** : à partir d'une maquette validée en 4/4, produire une boucle de 16 mesures et sa version d'introduction, exporter en OGG et WAV, renseigner le manifeste, puis vérifier le critère d'acceptation ci-dessus.

**Cas limite** : le format d'export exigé par le moteur n'est pas confirmé ; livrer les exports dans les formats usuels documentés, indiquer l'inconnue et demander confirmation à l'agent technique du moteur de jeu via l'agent de coordination, sans substituer une valeur par défaut.

## Contraintes et références
- Référence officielle : [Ardour - Manual](https://manual.ardour.org/). Synthèse originale, sans reproduction du texte source ; page non consultée en détail lors de la création, vérifier les versions et l'applicabilité au contexte.
- Création : DEL-20261026-GAMEDEV-CREA-AGENTS.

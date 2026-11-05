# Adaptive Interactive Music & Stems

## Objectif
Produire un livrable maîtrisé : plan de musique adaptative (couches verticales, transitions horizontales) avec stems alignés et table d'états musicaux prête pour l'intégration.


## Quand l'utiliser (triggers)
- Demande portant sur « Adaptive Interactive Music & Stems » ou sur le livrable : plan de musique adaptative avec stems alignés et table d'états musicaux.
- Besoin de vérifier ce résultat : toutes les couches d'un morceau restent synchrones et chaque transition déclarée tombe sur une frontière musicale définie (mesure ou temps) sans clic ni coupure audible.

## Hors périmètre
- Ne pas remplacer les domaines des agents complémentaires : présenter les interfaces et transmettre les besoins à l'agent rattaché (voir table de routage).
- L'exécution système, les modifications de fichiers, les tests et les publications relèvent de l'agent rattaché (voir table de routage) ; cette skill n'accorde aucun outil supplémentaire.
- Ne pas confondre préparation d'un protocole, revue statique et résultat d'une exécution réelle dans le logiciel ou le moteur.
- Ne pas écrire le code du système musical dans le moteur (rôle de l'agent technique dédié) ni le mixage ou l'implémentation audio (l'agent de sound design).

## Inputs requis
- États de jeu à soutenir (exploration, tension, combat, victoire, calme) et événements déclencheurs envisagés.
- Thèmes existants, tempo, tonalité et métrique de référence, ou brief permettant de les définir.
- Contraintes du moteur cible (formats, nombre de pistes simultanées, mémoire), logiciels et versions, périmètre autorisé.
- Marquer les éléments inconnus avant de conclure.

## Sorties attendues
- Plan d'adaptation : couches verticales (ajout ou retrait de pistes) et transitions horizontales (changement de section) par état de jeu.
- Table d'états musicaux : état, couches actives, points de transition autorisés (mesure ou temps), durée de fondu, comportement en cas d'interruption.
- Stems exportés alignés (même longueur, même point de départ) avec tempo, tonalité et métrique documentés.
- Brief d'intégration pour l'agent de sound design et, pour les stems prêts à intégrer, pour l'agent de développement Godot ; hypothèses et vérifications non réalisées séparées.

## Workflow recommandé
1. Cadrer les inputs : états de jeu, événements déclencheurs, contraintes du moteur ; vérifier les préconditions et autorisations.
2. Fixer une grille commune (tempo, métrique, tonalité) compatible avec tous les états et sections.
3. Composer les couches verticales pour qu'elles s'additionnent sans conflit harmonique ni encombrement de fréquences, chacune audible et cohérente seule.
4. Concevoir les transitions horizontales : points de sortie sur frontière de mesure, segments de raccord, queues de réverbération et fins courtes.
5. Vérifier le livrable par ce critère : toutes les couches d'un morceau restent synchrones et chaque transition déclarée tombe sur une frontière musicale définie sans clic ni coupure audible ; écouter chaque combinaison de couches et chaque transition.
6. Restituer résultat, hypothèses, risques et prochaines actions ; signaler explicitement les blocages.

## Garde-fous
- Les stems partagent la même longueur et la même grille ; toute transition est rattachée à un point musical explicite.
- Ne pas inventer de mesure, d'accord, de preuve ou de source ; distinguer observé, inféré et non testé (notamment le comportement réel dans le moteur).
- Ne pas supposer une fonctionnalité du moteur ou du middleware audio : la faire confirmer par l'agent technique du moteur de jeu ou via la documentation officielle.
- Ne pas transmettre d'artefact privé ou de donnée personnelle à un service tiers ; minimiser les données sensibles.
- Privilégier les outils libres maintenus (LMMS, Ardour, Audacity, FFmpeg) et vérifier les versions applicables sans introduire de dépendance EOL.
- Musique originale uniquement ou Domaine Public/CC0 ; tracer chaque source externe (échantillons, soundfonts) dans `docs/imageLicencesSources.md` (format `Nomdefichier | licence | url source`).
- Lire la référence dans son contexte : elle éclaire la méthode, elle ne certifie pas ce livrable et n'impose pas de seuil universel.

## Templates copier/coller
### Entrée
```text
Objet : Adaptive Interactive Music & Stems
Inputs : états de jeu, événements déclencheurs, thèmes existants, tempo/tonalité/métrique, contraintes du moteur
Version / périmètre autorisé :
Résultat demandé : plan de musique adaptative avec stems alignés et table d'états musicaux
Contraintes et inconnues :
```

### Sortie
```text
Résultat : plan de musique adaptative et stems alignés
| État de jeu | Couches actives | Point de transition autorisé | Fondu / limite |
|---|---|---|---|
Stems : nom | durée | tempo | tonalité | métrique
Hypothèses :
Risques :
Prochaines actions :
```

## Checklist QA interne
- [ ] Les inputs et les limites d'autorisation sont identifiés.
- [ ] Les trois analyses sont documentées : grille commune et couches verticales ; transitions horizontales et points de sortie ; table d'états et brief d'intégration.
- [ ] Le critère d'acceptation est vérifié ou explicitement marqué non vérifié.
- [ ] Aucun résultat d'exécution dans le moteur ou accord humain n'est inventé.

## KPI reliés
- Couverture des états de jeu : états avec couches et transitions documentées / états à soutenir (dénominateur conservé).
- Part des transitions écoutées et validées sans clic ni coupure audible / transitions déclarées ; ne pas compter une hypothèse comme preuve.
- Nombre d'écarts au critère suivant restant ouverts : toutes les couches restent synchrones et chaque transition tombe sur une frontière musicale définie.

## Definition of done
- [ ] Plan de musique adaptative, stems alignés et table d'états livrés dans le périmètre convenu.
- [ ] Toutes les couches d'un morceau restent synchrones et chaque transition déclarée tombe sur une frontière musicale définie sans clic ni coupure audible.
- [ ] Preuves, inconnues, exceptions et actions restantes sont lisibles ; aucune réussite globale en cas de vérification bloquante manquante.

## Exemples d'usage
**Cas nominal** : à partir de trois états de jeu (exploration, tension, combat) et d'un thème principal, produire quatre stems alignés et la table de transitions sur frontières de mesure, puis vérifier le critère d'acceptation ci-dessus.

**Cas limite** : le moteur cible n'a pas confirmé la prise en charge de la synchronisation des couches ; livrer les stems et la table d'états, indiquer cette inconnue et demander la vérification à l'agent technique du moteur de jeu via l'agent de coordination, sans substituer une hypothèse.

## Contraintes et références
- Référence officielle : [Godot - Audio streams](https://docs.godotengine.org/en/stable/tutorials/audio/audio_streams.html). Synthèse originale, sans reproduction du texte source ; page non consultée en détail lors de la création, vérifier les versions et l'applicabilité au contexte.
- Création : DEL-20261026-GAMEDEV-CREA-AGENTS.

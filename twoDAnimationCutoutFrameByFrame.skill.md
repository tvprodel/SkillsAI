# 2D Animation Cutout & Frame-by-Frame

## Objectif
Produire un livrable maîtrisé : animation 2D (cutout ou image par image) avec planches ou clips et fiche de timing.


## Quand l'utiliser (triggers)
- Demande portant sur « 2D Animation Cutout & Frame-by-Frame » ou sur le livrable : animation 2D (cutout ou image par image) avec planches ou clips et fiche de timing.
- Besoin de vérifier ce résultat : le framerate et le timing déclarés sont respectés et l'animation s'intègre sans décalage.

## Hors périmètre
- Ne pas remplacer les domaines des agents complémentaires : présenter les interfaces et transmettre les besoins à l'agent rattaché (voir table de routage).
- L'exécution système, les modifications de fichiers, les tests et les publications relèvent de l'agent rattaché (voir table de routage) ; cette skill n'accorde aucun outil supplémentaire.
- Ne pas confondre préparation d'un protocole, revue statique et résultat d'une exécution réelle dans le logiciel.

## Inputs requis
- Personnage ou éléments 2D, style, framerate, outils (Blender Grease Pencil, Godot Skeleton2D, Krita).
- Périmètre autorisé, version des logiciels et des artefacts, sources accessibles et décisions déjà validées.
- Critères d'acceptation et limites d'action ; marquer les éléments inconnus avant de conclure.

## Sorties attendues
- Animation 2D (cutout ou image par image) avec planches ou clips et fiche de timing.
- Preuves ou références par constat ; hypothèses, exceptions et vérifications non réalisées séparées.
- Brief des décisions ou actions nécessaires pour l'agent rattaché, sans les annoncer déjà exécutées.

## Workflow recommandé
1. Cadrer les inputs : personnage ou éléments 2D, style, framerate, outils (Blender Grease Pencil, Godot Skeleton2D, Krita) ; vérifier les préconditions et autorisations.
2. Choisir la technique (cutout, image par image, Grease Pencil) selon style et budget.
3. Produire les poses clés puis les intervalles et ajuster le timing.
4. Exporter planches ou clips et documenter leur usage dans le moteur.
5. Vérifier le livrable par ce critère : le framerate et le timing déclarés sont respectés et l'animation s'intègre sans décalage.
6. Restituer résultat, hypothèses, risques et prochaines actions ; signaler explicitement les blocages.

## Garde-fous
- Le framerate et le timing déclarés sont respectés et l'animation s'intègre sans décalage.
- Ne pas inventer de mesure, d'accord, de preuve ou de source ; distinguer observé, inféré et non testé.
- Ne pas transmettre d'artefact privé ou de donnée personnelle à un service tiers ; minimiser les données sensibles.
- Privilégier les outils libres maintenus et vérifier les versions applicables sans introduire de dépendance EOL.
- Utiliser uniquement des ressources originales, du Domaine Public ou CC0 ; tracer chaque source externe dans `docs/imageLicencesSources.md` (format `Nomdefichier | licence | url source`).
- Lire la référence dans son contexte : elle éclaire la méthode, elle ne certifie pas ce livrable et n'impose pas de seuil universel.

## Templates copier/coller
### Entrée
```text
Objet : 2D Animation Cutout & Frame-by-Frame
Inputs : personnage ou éléments 2D, style, framerate, outils (Blender Grease Pencil, Godot Skeleton2D, Krita)
Version / périmètre autorisé :
Résultat demandé : animation 2D (cutout ou image par image) avec planches ou clips et fiche de timing
Contraintes et inconnues :
```

### Sortie
```text
Résultat : animation 2D (cutout ou image par image) avec planches ou clips et fiche de timing
| Élément examiné | Preuve / source / version | Conclusion | Limite / action |
|---|---|---|---|
Hypothèses :
Risques :
Prochaines actions :
```

## Checklist QA interne
- [ ] Les inputs et les limites d'autorisation sont identifiés.
- [ ] Les trois analyses sont documentées : choisir la technique (cutout, image par image, Grease Pencil) selon style et budget ; produire les poses clés puis les intervalles et ajuster le timing ; exporter planches ou clips et documenter leur usage dans le moteur.
- [ ] Le critère d'acceptation est vérifié ou explicitement marqué non vérifié.
- [ ] Aucun résultat d'exécution ou accord humain n'est inventé.

## KPI reliés
- Couverture des éléments requis : éléments documentés / éléments applicables de ce livrable (dénominateur conservé).
- Part des conclusions appuyées par une preuve ou une source datée ; ne pas compter une hypothèse comme preuve.
- Nombre d'écarts au critère suivant restant ouverts : le framerate et le timing déclarés sont respectés et l'animation s'intègre sans décalage.

## Definition of done
- [ ] Animation 2D (cutout ou image par image) avec planches ou clips et fiche de timing livré dans le périmètre convenu.
- [ ] Le framerate et le timing déclarés sont respectés et l'animation s'intègre sans décalage.
- [ ] Preuves, inconnues, exceptions et actions restantes sont lisibles ; aucune réussite globale en cas de vérification bloquante manquante.

## Exemples d'usage
**Cas nominal** : à partir de personnage ou éléments 2D, style, framerate, outils (Blender Grease Pencil, Godot Skeleton2D, Krita), produire animation 2D (cutout ou image par image) avec planches ou clips et fiche de timing puis vérifier le critère d'acceptation ci-dessus.

**Cas limite** : une preuve ou autorisation nécessaire manque ; livrer les éléments établis et indiquer précisément ce qui empêche la validation, sans substituer une valeur par défaut.

## Contraintes et références
- Référence officielle : [Godot - Animation 2D](https://docs.godotengine.org/en/stable/tutorials/animation/index.html). Synthèse originale, sans reproduction du texte source ; page non consultée en détail lors de la création, vérifier les versions et l'applicabilité au contexte.
- Création : DEL-20261025-CREA-3D-AGENTS.

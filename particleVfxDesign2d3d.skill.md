# Particle VFX Design 2D/3D

## Objectif
Produire un livrable maîtrisé : effet de particules 2D ou 3D (impact, fumée, magie, feu) conçu pour Godot 4 ou Blender, avec fiche de réglages et prévisualisation en boucle.


## Quand l'utiliser (triggers)
- Demande portant sur « Particle VFX Design 2D/3D » ou sur le livrable : effet de particules 2D ou 3D (impact, fumée, magie, feu) conçu pour Godot 4 ou Blender, avec fiche de réglages et prévisualisation en boucle.
- Besoin de vérifier ce résultat : l'effet se lit clairement à la taille d'affichage cible, reste dans le nombre maximal de particules fixé et se boucle ou se termine sans résidu visible.

## Hors périmètre
- Ne pas remplacer les domaines des agents complémentaires : présenter les interfaces et transmettre les besoins à l'agent rattaché (voir table de routage).
- L'exécution système, les modifications de fichiers, les tests et les publications relèvent de l'agent rattaché (voir table de routage) ; cette skill n'accorde aucun outil supplémentaire.
- Ne pas confondre préparation d'un protocole, revue statique et résultat d'une exécution réelle dans le logiciel.

## Inputs requis
- Intention visuelle de l'effet (référence, ambiance, durée, déclencheur), moteur et version (Godot 4.x, Blender stable), cible 2D ou 3D, taille d'affichage et plafond de particules.
- Textures ou sprites sources disponibles, avec leur licence ; palette et contraintes de lisibilité.
- Périmètre autorisé, version des logiciels et des artefacts, décisions déjà validées ; marquer les éléments inconnus avant de conclure.

## Sorties attendues
- Effet de particules (GPUParticles2D/3D ou système de particules Blender) avec fiche de réglages : durée de vie, émission, vitesse, gravité, courbes de taille, de couleur et d'alpha, mode de fusion.
- Prévisualisation en boucle ou capture de séquence, et variantes (intensité faible/forte) si demandées.
- Preuves ou références par constat ; hypothèses, exceptions et vérifications non réalisées séparées.
- Brief des décisions ou actions nécessaires pour l'agent rattaché, sans les annoncer déjà exécutées.

## Workflow recommandé
1. Cadrer l'intention : référence visuelle, moteur et version, durée, déclencheur, plafond de particules et taille d'affichage ; vérifier les autorisations et licences des textures.
2. Décomposer l'effet en couches (flash, noyau, étincelles, fumée résiduelle) et choisir pour chacune le type d'émetteur et la texture ou le flipbook.
3. Régler émission, durée de vie, vitesse, gravité et courbes (taille, couleur, alpha) ; fixer le mode de fusion adapté (additif, mélangé).
4. Prévisualiser en boucle et à l'échelle réelle ; ajuster la lisibilité sur les fonds les plus clairs et les plus sombres du jeu.
5. Vérifier le critère : l'effet se lit clairement à la taille d'affichage cible, reste dans le nombre maximal de particules fixé et se boucle ou se termine sans résidu visible.
6. Restituer fiche de réglages, hypothèses, risques et prochaines actions (transmission à l'agent technique du moteur de jeu pour le déclenchement) ; signaler explicitement les blocages.

## Garde-fous
- L'effet reste dans le plafond de particules fixé et ne laisse aucun résidu visible à la fin de sa durée de vie.
- Limiter les flashs et la stroboscopie : éviter les clignotements rapides et fortement contrastés, se référer aux lignes directrices sur la photosensibilité, et prévoir une variante atténuée.
- Ne pas inventer de mesure, d'accord, de preuve ou de source ; distinguer observé, inféré et non testé.
- Ne pas transmettre d'artefact privé ou de donnée personnelle à un service tiers ; minimiser les données sensibles.
- Privilégier les outils libres maintenus (Blender, Godot, Krita, GIMP) et vérifier les versions applicables sans introduire de dépendance EOL.
- Utiliser uniquement des ressources originales, du Domaine Public ou CC0 ; tracer chaque source externe dans `docs/imageLicencesSources.md` (format `Nomdefichier | licence | url source`).
- Lire la référence dans son contexte : elle éclaire la méthode, elle ne certifie pas ce livrable et n'impose pas de seuil universel.

## Templates copier/coller
### Entrée
```text
Objet : Particle VFX Design 2D/3D
Inputs : intention visuelle, moteur et version, cible 2D/3D, taille d'affichage, plafond de particules, textures sources et licences
Version / périmètre autorisé :
Résultat demandé : effet de particules avec fiche de réglages et prévisualisation en boucle
Contraintes et inconnues :
```

### Sortie
```text
Résultat : effet de particules (couches, émetteurs, fiche de réglages, prévisualisation)
| Couche / émetteur | Réglages clés (durée de vie, émission, courbes, fusion) | Particules max | Limite / action |
|---|---|---|---|
Hypothèses :
Risques :
Prochaines actions :
```

## Checklist QA interne
- [ ] Les inputs, les licences des textures et les limites d'autorisation sont identifiés.
- [ ] Les trois analyses sont documentées : décomposition en couches et choix des émetteurs ; réglages d'émission et courbes ; prévisualisation à l'échelle réelle sur fonds clairs et sombres.
- [ ] Le critère d'acceptation est vérifié ou explicitement marqué non vérifié.
- [ ] Le risque de flash ou de stroboscopie est évalué et une variante atténuée est proposée si nécessaire.
- [ ] Aucun résultat d'exécution ou accord humain n'est inventé.

## KPI reliés
- Couverture des éléments requis : couches et réglages documentés / éléments applicables de ce livrable (dénominateur conservé).
- Nombre maximal de particules simultanées mesuré / plafond fixé (valeur ≤ 1 attendue).
- Nombre d'écarts au critère suivant restant ouverts : lisibilité à la taille cible, respect du plafond, absence de résidu en fin d'effet.

## Definition of done
- [ ] Effet de particules avec fiche de réglages et prévisualisation livré dans le périmètre convenu.
- [ ] L'effet se lit clairement à la taille d'affichage cible, reste dans le plafond de particules et se termine sans résidu visible.
- [ ] Preuves, inconnues, exceptions et actions restantes sont lisibles ; aucune réussite globale en cas de vérification bloquante manquante.

## Exemples d'usage
**Cas nominal** : à partir d'une intention « impact d'épée avec étincelles », d'un plafond de 64 particules et de Godot 4.x, produire un effet GPUParticles2D en trois couches avec fiche de réglages, puis vérifier le critère d'acceptation ci-dessus.

**Cas limite** : une preuve ou autorisation nécessaire manque (par exemple licence d'une texture inconnue) ; livrer les éléments établis avec une texture de substitution originale et indiquer précisément ce qui empêche la validation, sans substituer une valeur par défaut.

## Contraintes et références
- Référence officielle : [Godot - Particle systems (2D)](https://docs.godotengine.org/en/stable/tutorials/2d/particles_2d.html). Synthèse originale, sans reproduction du texte source ; page non consultée en détail lors de la création, vérifier les versions et l'applicabilité au contexte.
- Création : DEL-20261026-GAMEDEV-CREA-AGENTS.

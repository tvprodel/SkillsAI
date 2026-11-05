# Inkscape Icon & Logo System Design

## Objectif
Produire un livrable maîtrisé : système d'icônes ou de logo (grille, déclinaisons, variantes de taille et de couleur).


## Quand l'utiliser (triggers)
- Demande portant sur « Inkscape Icon & Logo System Design » ou sur le livrable : système d'icônes ou de logo (grille, déclinaisons, variantes de taille et de couleur).
- Besoin de vérifier ce résultat : chaque icône respecte la grille déclarée et reste lisible à la taille minimale annoncée.

## Hors périmètre
- Ne pas remplacer les domaines des agents complémentaires : présenter les interfaces et transmettre les besoins à l'agent rattaché (voir table de routage).
- L'exécution système, les modifications de fichiers, les tests et les publications relèvent de l'agent rattaché (voir table de routage) ; cette skill n'accorde aucun outil supplémentaire.
- Ne pas confondre préparation d'un protocole, revue statique et résultat d'une exécution réelle dans le logiciel.

## Inputs requis
- Identité visuelle, usages, tailles minimales, contraintes d'accessibilité et de contraste.
- Périmètre autorisé, version des logiciels et des artefacts, sources accessibles et décisions déjà validées.
- Critères d'acceptation et limites d'action ; marquer les éléments inconnus avant de conclure.

## Sorties attendues
- Système d'icônes ou de logo (grille, déclinaisons, variantes de taille et de couleur).
- Preuves ou références par constat ; hypothèses, exceptions et vérifications non réalisées séparées.
- Brief des décisions ou actions nécessaires pour l'agent rattaché, sans les annoncer déjà exécutées.

## Workflow recommandé
1. Cadrer les inputs : identité visuelle, usages, tailles minimales, contraintes d'accessibilité et de contraste ; vérifier les préconditions et autorisations.
2. Définir la grille, l'épaisseur de trait et les règles de construction.
3. Décliner les variantes (monochrome, couleur, fond clair/sombre).
4. Vérifier la lisibilité aux tailles minimales.
5. Vérifier le livrable par ce critère : chaque icône respecte la grille déclarée et reste lisible à la taille minimale annoncée.
6. Restituer résultat, hypothèses, risques et prochaines actions ; signaler explicitement les blocages.

## Garde-fous
- Chaque icône respecte la grille déclarée et reste lisible à la taille minimale annoncée.
- Ne pas inventer de mesure, d'accord, de preuve ou de source ; distinguer observé, inféré et non testé.
- Ne pas transmettre d'artefact privé ou de donnée personnelle à un service tiers ; minimiser les données sensibles.
- Privilégier les outils libres maintenus et vérifier les versions applicables sans introduire de dépendance EOL.
- Utiliser uniquement des ressources originales, du Domaine Public ou CC0 ; tracer chaque source externe dans `docs/imageLicencesSources.md` (format `Nomdefichier | licence | url source`).
- Lire la référence dans son contexte : elle éclaire la méthode, elle ne certifie pas ce livrable et n'impose pas de seuil universel.

## Templates copier/coller
### Entrée
```text
Objet : Inkscape Icon & Logo System Design
Inputs : identité visuelle, usages, tailles minimales, contraintes d'accessibilité et de contraste
Version / périmètre autorisé :
Résultat demandé : système d'icônes ou de logo (grille, déclinaisons, variantes de taille et de couleur)
Contraintes et inconnues :
```

### Sortie
```text
Résultat : système d'icônes ou de logo (grille, déclinaisons, variantes de taille et de couleur)
| Élément examiné | Preuve / source / version | Conclusion | Limite / action |
|---|---|---|---|
Hypothèses :
Risques :
Prochaines actions :
```

## Checklist QA interne
- [ ] Les inputs et les limites d'autorisation sont identifiés.
- [ ] Les trois analyses sont documentées : définir la grille, l'épaisseur de trait et les règles de construction ; décliner les variantes (monochrome, couleur, fond clair/sombre) ; vérifier la lisibilité aux tailles minimales.
- [ ] Le critère d'acceptation est vérifié ou explicitement marqué non vérifié.
- [ ] Aucun résultat d'exécution ou accord humain n'est inventé.

## KPI reliés
- Couverture des éléments requis : éléments documentés / éléments applicables de ce livrable (dénominateur conservé).
- Part des conclusions appuyées par une preuve ou une source datée ; ne pas compter une hypothèse comme preuve.
- Nombre d'écarts au critère suivant restant ouverts : chaque icône respecte la grille déclarée et reste lisible à la taille minimale annoncée.

## Definition of done
- [ ] Système d'icônes ou de logo (grille, déclinaisons, variantes de taille et de couleur) livré dans le périmètre convenu.
- [ ] Chaque icône respecte la grille déclarée et reste lisible à la taille minimale annoncée.
- [ ] Preuves, inconnues, exceptions et actions restantes sont lisibles ; aucune réussite globale en cas de vérification bloquante manquante.

## Exemples d'usage
**Cas nominal** : à partir de identité visuelle, usages, tailles minimales, contraintes d'accessibilité et de contraste, produire système d'icônes ou de logo (grille, déclinaisons, variantes de taille et de couleur) puis vérifier le critère d'acceptation ci-dessus.

**Cas limite** : une preuve ou autorisation nécessaire manque ; livrer les éléments établis et indiquer précisément ce qui empêche la validation, sans substituer une valeur par défaut.

## Contraintes et références
- Référence officielle : [Inkscape - Documentation](https://inkscape.org/learn/). Synthèse originale, sans reproduction du texte source ; page non consultée en détail lors de la création, vérifier les versions et l'applicabilité au contexte.
- Création : DEL-20261025-CREA-3D-AGENTS.

# Inkscape Vector Production Workflow

## Objectif
Produire un livrable maîtrisé : fichier SVG structuré (calques, groupes, identifiants) avec guide de manipulation Inkscape.


## Quand l'utiliser (triggers)
- Demande portant sur « Inkscape Vector Production Workflow » ou sur le livrable : fichier SVG structuré (calques, groupes, identifiants) avec guide de manipulation Inkscape.
- Besoin de vérifier ce résultat : le SVG s'ouvre dans Inkscape stable avec des calques nommés et sans objet caché non documenté.

## Hors périmètre
- Ne pas remplacer les domaines des agents complémentaires : présenter les interfaces et transmettre les besoins à l'agent rattaché (voir table de routage).
- L'exécution système, les modifications de fichiers, les tests et les publications relèvent de l'agent rattaché (voir table de routage) ; cette skill n'accorde aucun outil supplémentaire.
- Ne pas confondre préparation d'un protocole, revue statique et résultat d'une exécution réelle dans le logiciel.

## Inputs requis
- Brief visuel, formats cibles, palette, contraintes de taille et références libres de droits.
- Périmètre autorisé, version des logiciels et des artefacts, sources accessibles et décisions déjà validées.
- Critères d'acceptation et limites d'action ; marquer les éléments inconnus avant de conclure.

## Sorties attendues
- Fichier SVG structuré (calques, groupes, identifiants) avec guide de manipulation Inkscape.
- Preuves ou références par constat ; hypothèses, exceptions et vérifications non réalisées séparées.
- Brief des décisions ou actions nécessaires pour l'agent rattaché, sans les annoncer déjà exécutées.

## Workflow recommandé
1. Cadrer les inputs : brief visuel, formats cibles, palette, contraintes de taille et références libres de droits ; vérifier les préconditions et autorisations.
2. Construire la structure calques/groupes et nommer les objets.
3. Tracer et combiner les chemins (opérations booléennes, nœuds, vectorisation d'un bitmap si nécessaire).
4. Appliquer couleurs, dégradés et traits en conservant l'éditabilité.
5. Vérifier le livrable par ce critère : le SVG s'ouvre dans Inkscape stable avec des calques nommés et sans objet caché non documenté.
6. Restituer résultat, hypothèses, risques et prochaines actions ; signaler explicitement les blocages.

## Garde-fous
- Le SVG s'ouvre dans Inkscape stable avec des calques nommés et sans objet caché non documenté.
- Ne pas inventer de mesure, d'accord, de preuve ou de source ; distinguer observé, inféré et non testé.
- Ne pas transmettre d'artefact privé ou de donnée personnelle à un service tiers ; minimiser les données sensibles.
- Privilégier les outils libres maintenus et vérifier les versions applicables sans introduire de dépendance EOL.
- Utiliser uniquement des ressources originales, du Domaine Public ou CC0 ; tracer chaque source externe dans `docs/imageLicencesSources.md` (format `Nomdefichier | licence | url source`).
- Lire la référence dans son contexte : elle éclaire la méthode, elle ne certifie pas ce livrable et n'impose pas de seuil universel.

## Templates copier/coller
### Entrée
```text
Objet : Inkscape Vector Production Workflow
Inputs : brief visuel, formats cibles, palette, contraintes de taille et références libres de droits
Version / périmètre autorisé :
Résultat demandé : fichier SVG structuré (calques, groupes, identifiants) avec guide de manipulation Inkscape
Contraintes et inconnues :
```

### Sortie
```text
Résultat : fichier SVG structuré (calques, groupes, identifiants) avec guide de manipulation Inkscape
| Élément examiné | Preuve / source / version | Conclusion | Limite / action |
|---|---|---|---|
Hypothèses :
Risques :
Prochaines actions :
```

## Checklist QA interne
- [ ] Les inputs et les limites d'autorisation sont identifiés.
- [ ] Les trois analyses sont documentées : construire la structure calques/groupes et nommer les objets ; tracer et combiner les chemins (opérations booléennes, nœuds, vectorisation d'un bitmap si nécessaire) ; appliquer couleurs, dégradés et traits en conservant l'éditabilité.
- [ ] Le critère d'acceptation est vérifié ou explicitement marqué non vérifié.
- [ ] Aucun résultat d'exécution ou accord humain n'est inventé.

## KPI reliés
- Couverture des éléments requis : éléments documentés / éléments applicables de ce livrable (dénominateur conservé).
- Part des conclusions appuyées par une preuve ou une source datée ; ne pas compter une hypothèse comme preuve.
- Nombre d'écarts au critère suivant restant ouverts : le SVG s'ouvre dans Inkscape stable avec des calques nommés et sans objet caché non documenté.

## Definition of done
- [ ] Fichier SVG structuré (calques, groupes, identifiants) avec guide de manipulation Inkscape livré dans le périmètre convenu.
- [ ] Le SVG s'ouvre dans Inkscape stable avec des calques nommés et sans objet caché non documenté.
- [ ] Preuves, inconnues, exceptions et actions restantes sont lisibles ; aucune réussite globale en cas de vérification bloquante manquante.

## Exemples d'usage
**Cas nominal** : à partir de brief visuel, formats cibles, palette, contraintes de taille et références libres de droits, produire fichier SVG structuré (calques, groupes, identifiants) avec guide de manipulation Inkscape puis vérifier le critère d'acceptation ci-dessus.

**Cas limite** : une preuve ou autorisation nécessaire manque ; livrer les éléments établis et indiquer précisément ce qui empêche la validation, sans substituer une valeur par défaut.

## Contraintes et références
- Référence officielle : [Inkscape - Documentation](https://inkscape.org/learn/). Synthèse originale, sans reproduction du texte source ; page non consultée en détail lors de la création, vérifier les versions et l'applicabilité au contexte.
- Création : DEL-20261025-CREA-3D-AGENTS.

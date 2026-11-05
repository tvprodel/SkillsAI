# Vector Illustration Construction

## Objectif
Concevoir une illustration SVG maintenable à partir d'un brief visuel explicite.


## Quand l'utiliser (triggers)
- Demande portant sur « Vector Illustration Construction » ou sur le livrable : svg structuré accompagné de ses contraintes de rendu.
- Besoin de vérifier ce résultat : le fichier garde une composition lisible aux dimensions cibles sans script embarqué inutile.

## Hors périmètre
- Ne pas remplacer les domaines des agents complémentaires : présenter les interfaces et transmettre les besoins à l'agent rattaché (voir table de routage).
- L'exécution système, les modifications de fichiers, les tests et les publications relèvent de l'agent rattaché (voir table de routage) ; cette skill n'accorde aucun outil supplémentaire.
- Ne pas confondre préparation d'un protocole, revue statique et résultat d'une exécution réelle.

## Inputs requis
- Sujet, composition, palette, dimensions et contraintes d'usage.
- Périmètre autorisé, version des artefacts, sources accessibles et décisions déjà validées.
- Critères d'acceptation et limites d'action ; marquer les éléments inconnus avant de conclure.

## Sorties attendues
- SVG structuré accompagné de ses contraintes de rendu.
- Preuves ou références par constat ; hypothèses, exceptions et vérifications non réalisées séparées.
- Brief des décisions ou actions nécessaires pour l'agent rattaché, sans les annoncer déjà exécutées.

## Workflow recommandé
1. Cadrer les inputs : sujet, composition, palette, dimensions et contraintes d'usage ; vérifier les préconditions et autorisations.
2. Décomposer la scène en formes et groupes.
3. Définir viewBox, hiérarchie et géométrie.
4. Vérifier rendu, lisibilité et absence de ressources externes non autorisées.
5. Vérifier le livrable par ce critère : le fichier garde une composition lisible aux dimensions cibles sans script embarqué inutile.
6. Restituer résultat, hypothèses, risques et prochaines actions ; signaler explicitement les blocages.

## Garde-fous
- Le fichier garde une composition lisible aux dimensions cibles sans script embarqué inutile.
- Ne pas inventer de mesure, d'accord, de preuve ou de source ; distinguer observé, inféré et non testé.
- Ne pas transmettre d'artefact privé ou de donnée personnelle à un service tiers ; minimiser les données sensibles.
- Privilégier les outils libres maintenus et vérifier les versions applicables sans introduire de dépendance EOL.
- Lire la référence dans son contexte : elle éclaire la méthode, elle ne certifie pas ce livrable et n'impose pas de seuil universel.

## Templates copier/coller
### Entrée
```text
Objet : Vector Illustration Construction
Inputs : Sujet, composition, palette, dimensions et contraintes d'usage
Version / périmètre autorisé :
Résultat demandé : SVG structuré accompagné de ses contraintes de rendu
Contraintes et inconnues :
```

### Sortie
```text
Résultat : SVG structuré accompagné de ses contraintes de rendu
| Élément examiné | Preuve / source / version | Conclusion | Limite / action |
|---|---|---|---|
Hypothèses :
Risques :
Prochaines actions :
```

## Checklist QA interne
- [ ] Les inputs et les limites d'autorisation sont identifiés.
- [ ] Les trois analyses sont documentées : décomposer la scène en formes et groupes ; définir viewbox, hiérarchie et géométrie ; vérifier rendu, lisibilité et absence de ressources externes non autorisées.
- [ ] Le critère d'acceptation est vérifié ou explicitement marqué non vérifié.
- [ ] Aucun résultat d'exécution ou accord humain n'est inventé.

## KPI reliés
- Couverture des éléments requis : éléments documentés / éléments applicables de ce livrable (dénominateur conservé).
- Part des conclusions appuyées par une preuve ou une source datée ; ne pas compter une hypothèse comme preuve.
- Nombre d'écarts au critère suivant restant ouverts : le fichier garde une composition lisible aux dimensions cibles sans script embarqué inutile.

## Definition of done
- [ ] SVG structuré accompagné de ses contraintes de rendu livré dans le périmètre convenu.
- [ ] Le fichier garde une composition lisible aux dimensions cibles sans script embarqué inutile.
- [ ] Preuves, inconnues, exceptions et actions restantes sont lisibles ; aucune réussite globale en cas de vérification bloquante manquante.

## Exemples d'usage
**Cas nominal** : à partir de sujet, composition, palette, dimensions et contraintes d'usage, produire svg structuré accompagné de ses contraintes de rendu puis vérifier le critère d'acceptation ci-dessus.

**Cas limite** : une preuve ou autorisation nécessaire manque ; livrer les éléments établis et indiquer précisément ce qui empêche la validation, sans substituer une valeur par défaut.

## Contraintes et références
- Référence officielle consultée le 2026-10-21 : [W3C SVG 2](https://www.w3.org/TR/SVG2/). Synthèse originale, sans reproduction du texte source ; vérifier les versions et l'applicabilité au contexte.
- Migration : DEL-20261021-EXCLUSIVE-SKILLS-MIGRATION.

# Accessible Alternative Text Review

## Objectif
Évaluer l'équivalence informationnelle des alternatives d'images selon leur fonction dans le parcours.


## Quand l'utiliser (triggers)
- Demande portant sur « Accessible Alternative Text Review » ou sur le livrable : inventaire image/fonction/alternative/écart/critère de relecture.
- Besoin de vérifier ce résultat : aucun contenu d'image n'est inventé et les images fonctionnelles décrivent l'action utile.

## Hors périmètre
- Ne pas remplacer les domaines des agents complémentaires : présenter les interfaces et transmettre les besoins à l'agent rattaché (voir table de routage).
- L'exécution système, les modifications de fichiers, les tests et les publications relèvent de l'agent rattaché (voir table de routage) ; cette skill n'accorde aucun outil supplémentaire.
- Ne pas confondre préparation d'un protocole, revue statique et résultat d'une exécution réelle.

## Inputs requis
- Image réellement accessible, contexte, texte adjacent et action éventuelle.
- Périmètre autorisé, version des artefacts, sources accessibles et décisions déjà validées.
- Critères d'acceptation et limites d'action ; marquer les éléments inconnus avant de conclure.

## Sorties attendues
- Inventaire image/fonction/alternative/écart/critère de relecture.
- Preuves ou références par constat ; hypothèses, exceptions et vérifications non réalisées séparées.
- Brief des décisions ou actions nécessaires pour l'agent rattaché, sans les annoncer déjà exécutées.

## Workflow recommandé
1. Cadrer les inputs : image réellement accessible, contexte, texte adjacent et action éventuelle ; vérifier les préconditions et autorisations.
2. Classifier image décorative/informative/fonctionnelle/complexe.
3. Comparer information visuelle et alternative.
4. Définir la correction ou description longue nécessaire.
5. Vérifier le livrable par ce critère : aucun contenu d'image n'est inventé et les images fonctionnelles décrivent l'action utile.
6. Restituer résultat, hypothèses, risques et prochaines actions ; signaler explicitement les blocages.

## Garde-fous
- Aucun contenu d'image n'est inventé et les images fonctionnelles décrivent l'action utile.
- Ne pas inventer de mesure, d'accord, de preuve ou de source ; distinguer observé, inféré et non testé.
- Ne pas transmettre d'artefact privé ou de donnée personnelle à un service tiers ; minimiser les données sensibles.
- Privilégier les outils libres maintenus et vérifier les versions applicables sans introduire de dépendance EOL.
- Lire la référence dans son contexte : elle éclaire la méthode, elle ne certifie pas ce livrable et n'impose pas de seuil universel.

## Templates copier/coller
### Entrée
```text
Objet : Accessible Alternative Text Review
Inputs : Image réellement accessible, contexte, texte adjacent et action éventuelle
Version / périmètre autorisé :
Résultat demandé : Inventaire image/fonction/alternative/écart/critère de relecture
Contraintes et inconnues :
```

### Sortie
```text
Résultat : Inventaire image/fonction/alternative/écart/critère de relecture
| Élément examiné | Preuve / source / version | Conclusion | Limite / action |
|---|---|---|---|
Hypothèses :
Risques :
Prochaines actions :
```

## Checklist QA interne
- [ ] Les inputs et les limites d'autorisation sont identifiés.
- [ ] Les trois analyses sont documentées : classifier image décorative/informative/fonctionnelle/complexe ; comparer information visuelle et alternative ; définir la correction ou description longue nécessaire.
- [ ] Le critère d'acceptation est vérifié ou explicitement marqué non vérifié.
- [ ] Aucun résultat d'exécution ou accord humain n'est inventé.

## KPI reliés
- Couverture des éléments requis : éléments documentés / éléments applicables de ce livrable (dénominateur conservé).
- Part des conclusions appuyées par une preuve ou une source datée ; ne pas compter une hypothèse comme preuve.
- Nombre d'écarts au critère suivant restant ouverts : aucun contenu d'image n'est inventé et les images fonctionnelles décrivent l'action utile.

## Definition of done
- [ ] Inventaire image/fonction/alternative/écart/critère de relecture livré dans le périmètre convenu.
- [ ] Aucun contenu d'image n'est inventé et les images fonctionnelles décrivent l'action utile.
- [ ] Preuves, inconnues, exceptions et actions restantes sont lisibles ; aucune réussite globale en cas de vérification bloquante manquante.

## Exemples d'usage
**Cas nominal** : à partir de image réellement accessible, contexte, texte adjacent et action éventuelle, produire inventaire image/fonction/alternative/écart/critère de relecture puis vérifier le critère d'acceptation ci-dessus.

**Cas limite** : une preuve ou autorisation nécessaire manque ; livrer les éléments établis et indiquer précisément ce qui empêche la validation, sans substituer une valeur par défaut.

## Contraintes et références
- Référence officielle consultée le 2026-10-21 : [W3C WCAG 2.2](https://www.w3.org/TR/WCAG22/). Synthèse originale, sans reproduction du texte source ; vérifier les versions et l'applicabilité au contexte.
- Migration : DEL-20261021-EXCLUSIVE-SKILLS-MIGRATION.

# Visual Identity Asset Specification

## Objectif
Définir des déclinaisons d'assets cohérentes avec une identité visuelle validée.


## Quand l'utiliser (triggers)
- Demande portant sur « Visual Identity Asset Specification » ou sur le livrable : spécification d'assets avec couleurs, formats et exemples de déclinaison.
- Besoin de vérifier ce résultat : chaque variante conserve les invariants de marque et précise ses dimensions utiles.

## Hors périmètre
- Ne pas remplacer les domaines des agents complémentaires : présenter les interfaces et transmettre les besoins à l'agent rattaché (voir table de routage).
- L'exécution système, les modifications de fichiers, les tests et les publications relèvent de l'agent rattaché (voir table de routage) ; cette skill n'accorde aucun outil supplémentaire.
- Ne pas confondre préparation d'un protocole, revue statique et résultat d'une exécution réelle.

## Inputs requis
- Charte, usages, formats et contraintes de diffusion.
- Périmètre autorisé, version des artefacts, sources accessibles et décisions déjà validées.
- Critères d'acceptation et limites d'action ; marquer les éléments inconnus avant de conclure.

## Sorties attendues
- Spécification d'assets avec couleurs, formats et exemples de déclinaison.
- Preuves ou références par constat ; hypothèses, exceptions et vérifications non réalisées séparées.
- Brief des décisions ou actions nécessaires pour l'agent rattaché, sans les annoncer déjà exécutées.

## Workflow recommandé
1. Cadrer les inputs : charte, usages, formats et contraintes de diffusion ; vérifier les préconditions et autorisations.
2. Extraire invariants graphiques.
3. Spécifier variantes et zones de protection.
4. Définir critères de réception par support.
5. Vérifier le livrable par ce critère : chaque variante conserve les invariants de marque et précise ses dimensions utiles.
6. Restituer résultat, hypothèses, risques et prochaines actions ; signaler explicitement les blocages.

## Garde-fous
- Chaque variante conserve les invariants de marque et précise ses dimensions utiles.
- Ne pas inventer de mesure, d'accord, de preuve ou de source ; distinguer observé, inféré et non testé.
- Ne pas transmettre d'artefact privé ou de donnée personnelle à un service tiers ; minimiser les données sensibles.
- Privilégier les outils libres maintenus et vérifier les versions applicables sans introduire de dépendance EOL.
- Lire la référence dans son contexte : elle éclaire la méthode, elle ne certifie pas ce livrable et n'impose pas de seuil universel.

## Templates copier/coller
### Entrée
```text
Objet : Visual Identity Asset Specification
Inputs : Charte, usages, formats et contraintes de diffusion
Version / périmètre autorisé :
Résultat demandé : Spécification d'assets avec couleurs, formats et exemples de déclinaison
Contraintes et inconnues :
```

### Sortie
```text
Résultat : Spécification d'assets avec couleurs, formats et exemples de déclinaison
| Élément examiné | Preuve / source / version | Conclusion | Limite / action |
|---|---|---|---|
Hypothèses :
Risques :
Prochaines actions :
```

## Checklist QA interne
- [ ] Les inputs et les limites d'autorisation sont identifiés.
- [ ] Les trois analyses sont documentées : extraire invariants graphiques ; spécifier variantes et zones de protection ; définir critères de réception par support.
- [ ] Le critère d'acceptation est vérifié ou explicitement marqué non vérifié.
- [ ] Aucun résultat d'exécution ou accord humain n'est inventé.

## KPI reliés
- Couverture des éléments requis : éléments documentés / éléments applicables de ce livrable (dénominateur conservé).
- Part des conclusions appuyées par une preuve ou une source datée ; ne pas compter une hypothèse comme preuve.
- Nombre d'écarts au critère suivant restant ouverts : chaque variante conserve les invariants de marque et précise ses dimensions utiles.

## Definition of done
- [ ] Spécification d'assets avec couleurs, formats et exemples de déclinaison livré dans le périmètre convenu.
- [ ] Chaque variante conserve les invariants de marque et précise ses dimensions utiles.
- [ ] Preuves, inconnues, exceptions et actions restantes sont lisibles ; aucune réussite globale en cas de vérification bloquante manquante.

## Exemples d'usage
**Cas nominal** : à partir de charte, usages, formats et contraintes de diffusion, produire spécification d'assets avec couleurs, formats et exemples de déclinaison puis vérifier le critère d'acceptation ci-dessus.

**Cas limite** : une preuve ou autorisation nécessaire manque ; livrer les éléments établis et indiquer précisément ce qui empêche la validation, sans substituer une valeur par défaut.

## Contraintes et références
- Référence officielle consultée le 2026-10-21 : [W3C SVG 2](https://www.w3.org/TR/SVG2/). Synthèse originale, sans reproduction du texte source ; vérifier les versions et l'applicabilité au contexte.
- Migration : DEL-20261021-EXCLUSIVE-SKILLS-MIGRATION.

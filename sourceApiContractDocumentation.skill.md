# Source API Contract Documentation

## Objectif
Documenter le contrat interne d'une fonction ou classe à partir du code réel.


## Quand l'utiliser (triggers)
- Demande portant sur « Source API Contract Documentation » ou sur le livrable : référence interne de symboles avec provenance dans le code.
- Besoin de vérifier ce résultat : aucun paramètre, exception ou garantie n'est inventé à partir du seul nom de fonction.

## Hors périmètre
- Ne pas remplacer les domaines des agents complémentaires : présenter les interfaces et transmettre les besoins à l'agent rattaché (voir table de routage).
- L'exécution système, les modifications de fichiers, les tests et les publications relèvent de l'agent rattaché (voir table de routage) ; cette skill n'accorde aucun outil supplémentaire.
- Ne pas confondre préparation d'un protocole, revue statique et résultat d'une exécution réelle.

## Inputs requis
- Source, signatures, types et comportements observables.
- Périmètre autorisé, version des artefacts, sources accessibles et décisions déjà validées.
- Critères d'acceptation et limites d'action ; marquer les éléments inconnus avant de conclure.

## Sorties attendues
- Référence interne de symboles avec provenance dans le code.
- Preuves ou références par constat ; hypothèses, exceptions et vérifications non réalisées séparées.
- Brief des décisions ou actions nécessaires pour l'agent rattaché, sans les annoncer déjà exécutées.

## Workflow recommandé
1. Cadrer les inputs : source, signatures, types et comportements observables ; vérifier les préconditions et autorisations.
2. Relever paramètres, retours et exceptions.
3. Identifier préconditions et effets de bord.
4. Rédiger docstrings et exemple interne vérifiable.
5. Vérifier le livrable par ce critère : aucun paramètre, exception ou garantie n'est inventé à partir du seul nom de fonction.
6. Restituer résultat, hypothèses, risques et prochaines actions ; signaler explicitement les blocages.

## Garde-fous
- Aucun paramètre, exception ou garantie n'est inventé à partir du seul nom de fonction.
- Ne pas inventer de mesure, d'accord, de preuve ou de source ; distinguer observé, inféré et non testé.
- Ne pas transmettre d'artefact privé ou de donnée personnelle à un service tiers ; minimiser les données sensibles.
- Privilégier les outils libres maintenus et vérifier les versions applicables sans introduire de dépendance EOL.
- Lire la référence dans son contexte : elle éclaire la méthode, elle ne certifie pas ce livrable et n'impose pas de seuil universel.

## Templates copier/coller
### Entrée
```text
Objet : Source API Contract Documentation
Inputs : Source, signatures, types et comportements observables
Version / périmètre autorisé :
Résultat demandé : Référence interne de symboles avec provenance dans le code
Contraintes et inconnues :
```

### Sortie
```text
Résultat : Référence interne de symboles avec provenance dans le code
| Élément examiné | Preuve / source / version | Conclusion | Limite / action |
|---|---|---|---|
Hypothèses :
Risques :
Prochaines actions :
```

## Checklist QA interne
- [ ] Les inputs et les limites d'autorisation sont identifiés.
- [ ] Les trois analyses sont documentées : relever paramètres, retours et exceptions ; identifier préconditions et effets de bord ; rédiger docstrings et exemple interne vérifiable.
- [ ] Le critère d'acceptation est vérifié ou explicitement marqué non vérifié.
- [ ] Aucun résultat d'exécution ou accord humain n'est inventé.

## KPI reliés
- Couverture des éléments requis : éléments documentés / éléments applicables de ce livrable (dénominateur conservé).
- Part des conclusions appuyées par une preuve ou une source datée ; ne pas compter une hypothèse comme preuve.
- Nombre d'écarts au critère suivant restant ouverts : aucun paramètre, exception ou garantie n'est inventé à partir du seul nom de fonction.

## Definition of done
- [ ] Référence interne de symboles avec provenance dans le code livré dans le périmètre convenu.
- [ ] Aucun paramètre, exception ou garantie n'est inventé à partir du seul nom de fonction.
- [ ] Preuves, inconnues, exceptions et actions restantes sont lisibles ; aucune réussite globale en cas de vérification bloquante manquante.

## Exemples d'usage
**Cas nominal** : à partir de source, signatures, types et comportements observables, produire référence interne de symboles avec provenance dans le code puis vérifier le critère d'acceptation ci-dessus.

**Cas limite** : une preuve ou autorisation nécessaire manque ; livrer les éléments établis et indiquer précisément ce qui empêche la validation, sans substituer une valeur par défaut.

## Contraintes et références
- Référence officielle consultée le 2026-10-21 : [Python typing](https://docs.python.org/3/library/typing.html). Synthèse originale, sans reproduction du texte source ; vérifier les versions et l'applicabilité au contexte.
- Migration : DEL-20261021-EXCLUSIVE-SKILLS-MIGRATION.

# Cross-Locale Meaning Alignment

## Objectif
Contrôler que des versions linguistiques transmettent la même intention et les mêmes contraintes.


## Quand l'utiliser (triggers)
- Demande portant sur « Cross-Locale Meaning Alignment » ou sur le livrable : matrice de correspondance du sens par langue.
- Besoin de vérifier ce résultat : aucune version ne renforce une promesse ni n'efface une condition sans validation.

## Hors périmètre
- Ne pas remplacer les domaines des agents complémentaires : présenter les interfaces et transmettre les besoins à l'agent rattaché (voir table de routage).
- L'exécution système, les modifications de fichiers, les tests et les publications relèvent de l'agent rattaché (voir table de routage) ; cette skill n'accorde aucun outil supplémentaire.
- Ne pas confondre préparation d'un protocole, revue statique et résultat d'une exécution réelle.

## Inputs requis
- Source, traductions, contexte et éléments non négociables.
- Périmètre autorisé, version des artefacts, sources accessibles et décisions déjà validées.
- Critères d'acceptation et limites d'action ; marquer les éléments inconnus avant de conclure.

## Sorties attendues
- Matrice de correspondance du sens par langue.
- Preuves ou références par constat ; hypothèses, exceptions et vérifications non réalisées séparées.
- Brief des décisions ou actions nécessaires pour l'agent rattaché, sans les annoncer déjà exécutées.

## Workflow recommandé
1. Cadrer les inputs : source, traductions, contexte et éléments non négociables ; vérifier les préconditions et autorisations.
2. Extraire propositions, conditions et degrés de certitude.
3. Comparer chaque version au sens source.
4. Documenter omissions et ajouts avec correction proposée.
5. Vérifier le livrable par ce critère : aucune version ne renforce une promesse ni n'efface une condition sans validation.
6. Restituer résultat, hypothèses, risques et prochaines actions ; signaler explicitement les blocages.

## Garde-fous
- Aucune version ne renforce une promesse ni n'efface une condition sans validation.
- Ne pas inventer de mesure, d'accord, de preuve ou de source ; distinguer observé, inféré et non testé.
- Ne pas transmettre d'artefact privé ou de donnée personnelle à un service tiers ; minimiser les données sensibles.
- Privilégier les outils libres maintenus et vérifier les versions applicables sans introduire de dépendance EOL.
- Lire la référence dans son contexte : elle éclaire la méthode, elle ne certifie pas ce livrable et n'impose pas de seuil universel.

## Templates copier/coller
### Entrée
```text
Objet : Cross-Locale Meaning Alignment
Inputs : Source, traductions, contexte et éléments non négociables
Version / périmètre autorisé :
Résultat demandé : Matrice de correspondance du sens par langue
Contraintes et inconnues :
```

### Sortie
```text
Résultat : Matrice de correspondance du sens par langue
| Élément examiné | Preuve / source / version | Conclusion | Limite / action |
|---|---|---|---|
Hypothèses :
Risques :
Prochaines actions :
```

## Checklist QA interne
- [ ] Les inputs et les limites d'autorisation sont identifiés.
- [ ] Les trois analyses sont documentées : extraire propositions, conditions et degrés de certitude ; comparer chaque version au sens source ; documenter omissions et ajouts avec correction proposée.
- [ ] Le critère d'acceptation est vérifié ou explicitement marqué non vérifié.
- [ ] Aucun résultat d'exécution ou accord humain n'est inventé.

## KPI reliés
- Couverture des éléments requis : éléments documentés / éléments applicables de ce livrable (dénominateur conservé).
- Part des conclusions appuyées par une preuve ou une source datée ; ne pas compter une hypothèse comme preuve.
- Nombre d'écarts au critère suivant restant ouverts : aucune version ne renforce une promesse ni n'efface une condition sans validation.

## Definition of done
- [ ] Matrice de correspondance du sens par langue livré dans le périmètre convenu.
- [ ] Aucune version ne renforce une promesse ni n'efface une condition sans validation.
- [ ] Preuves, inconnues, exceptions et actions restantes sont lisibles ; aucune réussite globale en cas de vérification bloquante manquante.

## Exemples d'usage
**Cas nominal** : à partir de source, traductions, contexte et éléments non négociables, produire matrice de correspondance du sens par langue puis vérifier le critère d'acceptation ci-dessus.

**Cas limite** : une preuve ou autorisation nécessaire manque ; livrer les éléments établis et indiquer précisément ce qui empêche la validation, sans substituer une valeur par défaut.

## Contraintes et références
- Référence officielle consultée le 2026-10-21 : [GOV.UK - Writing to GOV.UK standards](https://www.gov.uk/guidance/content-design). Synthèse originale, sans reproduction du texte source ; vérifier les versions et l'applicabilité au contexte.
- Migration : DEL-20261021-EXCLUSIVE-SKILLS-MIGRATION.

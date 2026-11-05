# Data Retention Policy Design

## Objectif
Définir une politique de conservation et suppression cohérente avec les usages et obligations confirmées.


## Quand l'utiliser (triggers)
- Demande portant sur « Data Retention Policy Design » ou sur le livrable : matrice catégorie/finalité/durée/déclencheur/exception/owner.
- Besoin de vérifier ce résultat : aucune durée légale n'est inventée et les sauvegardes sont prises en compte.

## Hors périmètre
- Ne pas remplacer les domaines des agents complémentaires : présenter les interfaces et transmettre les besoins à l'agent rattaché (voir table de routage).
- L'exécution système, les modifications de fichiers, les tests et les publications relèvent de l'agent rattaché (voir table de routage) ; cette skill n'accorde aucun outil supplémentaire.
- Ne pas confondre préparation d'un protocole, revue statique et résultat d'une exécution réelle.

## Inputs requis
- Catégories de données, finalités, obligations validées et contraintes de restauration.
- Périmètre autorisé, version des artefacts, sources accessibles et décisions déjà validées.
- Critères d'acceptation et limites d'action ; marquer les éléments inconnus avant de conclure.

## Sorties attendues
- Matrice catégorie/finalité/durée/déclencheur/exception/owner.
- Preuves ou références par constat ; hypothèses, exceptions et vérifications non réalisées séparées.
- Brief des décisions ou actions nécessaires pour l'agent rattaché, sans les annoncer déjà exécutées.

## Workflow recommandé
1. Cadrer les inputs : catégories de données, finalités, obligations validées et contraintes de restauration ; vérifier les préconditions et autorisations.
2. Distinguer données actives, archives et sauvegardes.
3. Associer durée justifiée et point de départ.
4. Définir exceptions, preuve de suppression et validation juridique requise.
5. Vérifier le livrable par ce critère : aucune durée légale n'est inventée et les sauvegardes sont prises en compte.
6. Restituer résultat, hypothèses, risques et prochaines actions ; signaler explicitement les blocages.

## Garde-fous
- Aucune durée légale n'est inventée et les sauvegardes sont prises en compte.
- Ne pas inventer de mesure, d'accord, de preuve ou de source ; distinguer observé, inféré et non testé.
- Ne pas transmettre d'artefact privé ou de donnée personnelle à un service tiers ; minimiser les données sensibles.
- Privilégier les outils libres maintenus et vérifier les versions applicables sans introduire de dépendance EOL.
- Lire la référence dans son contexte : elle éclaire la méthode, elle ne certifie pas ce livrable et n'impose pas de seuil universel.

## Templates copier/coller
### Entrée
```text
Objet : Data Retention Policy Design
Inputs : Catégories de données, finalités, obligations validées et contraintes de restauration
Version / périmètre autorisé :
Résultat demandé : Matrice catégorie/finalité/durée/déclencheur/exception/owner
Contraintes et inconnues :
```

### Sortie
```text
Résultat : Matrice catégorie/finalité/durée/déclencheur/exception/owner
| Élément examiné | Preuve / source / version | Conclusion | Limite / action |
|---|---|---|---|
Hypothèses :
Risques :
Prochaines actions :
```

## Checklist QA interne
- [ ] Les inputs et les limites d'autorisation sont identifiés.
- [ ] Les trois analyses sont documentées : distinguer données actives, archives et sauvegardes ; associer durée justifiée et point de départ ; définir exceptions, preuve de suppression et validation juridique requise.
- [ ] Le critère d'acceptation est vérifié ou explicitement marqué non vérifié.
- [ ] Aucun résultat d'exécution ou accord humain n'est inventé.

## KPI reliés
- Couverture des éléments requis : éléments documentés / éléments applicables de ce livrable (dénominateur conservé).
- Part des conclusions appuyées par une preuve ou une source datée ; ne pas compter une hypothèse comme preuve.
- Nombre d'écarts au critère suivant restant ouverts : aucune durée légale n'est inventée et les sauvegardes sont prises en compte.

## Definition of done
- [ ] Matrice catégorie/finalité/durée/déclencheur/exception/owner livré dans le périmètre convenu.
- [ ] Aucune durée légale n'est inventée et les sauvegardes sont prises en compte.
- [ ] Preuves, inconnues, exceptions et actions restantes sont lisibles ; aucune réussite globale en cas de vérification bloquante manquante.

## Exemples d'usage
**Cas nominal** : à partir de catégories de données, finalités, obligations validées et contraintes de restauration, produire matrice catégorie/finalité/durée/déclencheur/exception/owner puis vérifier le critère d'acceptation ci-dessus.

**Cas limite** : une preuve ou autorisation nécessaire manque ; livrer les éléments établis et indiquer précisément ce qui empêche la validation, sans substituer une valeur par défaut.

## Contraintes et références
- Référence officielle consultée le 2026-10-21 : [W3C PROV Overview](https://www.w3.org/TR/prov-overview/). Synthèse originale, sans reproduction du texte source ; vérifier les versions et l'applicabilité au contexte.
- Migration : DEL-20261021-EXCLUSIVE-SKILLS-MIGRATION.

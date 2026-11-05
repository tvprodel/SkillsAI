# Quality Rule Acceptance Design

## Objectif
Transformer les attentes métier sur une donnée en règles de qualité testables.


## Quand l'utiliser (triggers)
- Demande portant sur « Quality Rule Acceptance Design » ou sur le livrable : catalogue règle/test/seuil/owner/traitement des exceptions.
- Besoin de vérifier ce résultat : les seuils ont une justification métier et les données manquantes ne passent pas silencieusement.

## Hors périmètre
- Ne pas remplacer les domaines des agents complémentaires : présenter les interfaces et transmettre les besoins à l'agent rattaché (voir table de routage).
- L'exécution système, les modifications de fichiers, les tests et les publications relèvent de l'agent rattaché (voir table de routage) ; cette skill n'accorde aucun outil supplémentaire.
- Ne pas confondre préparation d'un protocole, revue statique et résultat d'une exécution réelle.

## Inputs requis
- Règles métier, population cible, exemples limites et tolérances convenues.
- Périmètre autorisé, version des artefacts, sources accessibles et décisions déjà validées.
- Critères d'acceptation et limites d'action ; marquer les éléments inconnus avant de conclure.

## Sorties attendues
- Catalogue règle/test/seuil/owner/traitement des exceptions.
- Preuves ou références par constat ; hypothèses, exceptions et vérifications non réalisées séparées.
- Brief des décisions ou actions nécessaires pour l'agent rattaché, sans les annoncer déjà exécutées.

## Workflow recommandé
1. Cadrer les inputs : règles métier, population cible, exemples limites et tolérances convenues ; vérifier les préconditions et autorisations.
2. Définir dimension de qualité et population.
3. Construire cas valides, invalides et inconnus.
4. Relier seuils à une décision de réception.
5. Vérifier le livrable par ce critère : les seuils ont une justification métier et les données manquantes ne passent pas silencieusement.
6. Restituer résultat, hypothèses, risques et prochaines actions ; signaler explicitement les blocages.

## Garde-fous
- Les seuils ont une justification métier et les données manquantes ne passent pas silencieusement.
- Ne pas inventer de mesure, d'accord, de preuve ou de source ; distinguer observé, inféré et non testé.
- Ne pas transmettre d'artefact privé ou de donnée personnelle à un service tiers ; minimiser les données sensibles.
- Privilégier les outils libres maintenus et vérifier les versions applicables sans introduire de dépendance EOL.
- Lire la référence dans son contexte : elle éclaire la méthode, elle ne certifie pas ce livrable et n'impose pas de seuil universel.

## Templates copier/coller
### Entrée
```text
Objet : Quality Rule Acceptance Design
Inputs : Règles métier, population cible, exemples limites et tolérances convenues
Version / périmètre autorisé :
Résultat demandé : Catalogue règle/test/seuil/owner/traitement des exceptions
Contraintes et inconnues :
```

### Sortie
```text
Résultat : Catalogue règle/test/seuil/owner/traitement des exceptions
| Élément examiné | Preuve / source / version | Conclusion | Limite / action |
|---|---|---|---|
Hypothèses :
Risques :
Prochaines actions :
```

## Checklist QA interne
- [ ] Les inputs et les limites d'autorisation sont identifiés.
- [ ] Les trois analyses sont documentées : définir dimension de qualité et population ; construire cas valides, invalides et inconnus ; relier seuils à une décision de réception.
- [ ] Le critère d'acceptation est vérifié ou explicitement marqué non vérifié.
- [ ] Aucun résultat d'exécution ou accord humain n'est inventé.

## KPI reliés
- Couverture des éléments requis : éléments documentés / éléments applicables de ce livrable (dénominateur conservé).
- Part des conclusions appuyées par une preuve ou une source datée ; ne pas compter une hypothèse comme preuve.
- Nombre d'écarts au critère suivant restant ouverts : les seuils ont une justification métier et les données manquantes ne passent pas silencieusement.

## Definition of done
- [ ] Catalogue règle/test/seuil/owner/traitement des exceptions livré dans le périmètre convenu.
- [ ] Les seuils ont une justification métier et les données manquantes ne passent pas silencieusement.
- [ ] Preuves, inconnues, exceptions et actions restantes sont lisibles ; aucune réussite globale en cas de vérification bloquante manquante.

## Exemples d'usage
**Cas nominal** : à partir de règles métier, population cible, exemples limites et tolérances convenues, produire catalogue règle/test/seuil/owner/traitement des exceptions puis vérifier le critère d'acceptation ci-dessus.

**Cas limite** : une preuve ou autorisation nécessaire manque ; livrer les éléments établis et indiquer précisément ce qui empêche la validation, sans substituer une valeur par défaut.

## Contraintes et références
- Référence officielle consultée le 2026-10-21 : [W3C Data Quality Vocabulary](https://www.w3.org/TR/vocab-dqv/). Synthèse originale, sans reproduction du texte source ; vérifier les versions et l'applicabilité au contexte.
- Migration : DEL-20261021-EXCLUSIVE-SKILLS-MIGRATION.

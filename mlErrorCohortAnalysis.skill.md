# ML Error Cohort Analysis

## Objectif
Expliquer où un modèle prédictif échoue en comparant des cohortes et exemples d'erreur.


## Quand l'utiliser (triggers)
- Demande portant sur « ML Error Cohort Analysis » ou sur le livrable : rapport de cohortes avec exemples et hypothèses testables.
- Besoin de vérifier ce résultat : une cohorte minuscule ou sélectionnée après coup est signalée comme exploratoire.

## Hors périmètre
- Ne pas remplacer les domaines des agents complémentaires : présenter les interfaces et transmettre les besoins à l'agent rattaché (voir table de routage).
- L'exécution système, les modifications de fichiers, les tests et les publications relèvent de l'agent rattaché (voir table de routage) ; cette skill n'accorde aucun outil supplémentaire.
- Ne pas confondre préparation d'un protocole, revue statique et résultat d'une exécution réelle.

## Inputs requis
- Prédictions, vérité terrain, segments autorisés et protocole de validation.
- Périmètre autorisé, version des artefacts, sources accessibles et décisions déjà validées.
- Critères d'acceptation et limites d'action ; marquer les éléments inconnus avant de conclure.

## Sorties attendues
- Rapport de cohortes avec exemples et hypothèses testables.
- Preuves ou références par constat ; hypothèses, exceptions et vérifications non réalisées séparées.
- Brief des décisions ou actions nécessaires pour l'agent rattaché, sans les annoncer déjà exécutées.

## Workflow recommandé
1. Cadrer les inputs : prédictions, vérité terrain, segments autorisés et protocole de validation ; vérifier les préconditions et autorisations.
2. Définir cohortes sans fuite de cible.
3. Comparer erreurs et incertitude par groupe.
4. Distinguer problème de données, de seuil et de modèle.
5. Vérifier le livrable par ce critère : une cohorte minuscule ou sélectionnée après coup est signalée comme exploratoire.
6. Restituer résultat, hypothèses, risques et prochaines actions ; signaler explicitement les blocages.

## Garde-fous
- Une cohorte minuscule ou sélectionnée après coup est signalée comme exploratoire.
- Ne pas inventer de mesure, d'accord, de preuve ou de source ; distinguer observé, inféré et non testé.
- Ne pas transmettre d'artefact privé ou de donnée personnelle à un service tiers ; minimiser les données sensibles.
- Privilégier les outils libres maintenus et vérifier les versions applicables sans introduire de dépendance EOL.
- Lire la référence dans son contexte : elle éclaire la méthode, elle ne certifie pas ce livrable et n'impose pas de seuil universel.

## Templates copier/coller
### Entrée
```text
Objet : ML Error Cohort Analysis
Inputs : Prédictions, vérité terrain, segments autorisés et protocole de validation
Version / périmètre autorisé :
Résultat demandé : Rapport de cohortes avec exemples et hypothèses testables
Contraintes et inconnues :
```

### Sortie
```text
Résultat : Rapport de cohortes avec exemples et hypothèses testables
| Élément examiné | Preuve / source / version | Conclusion | Limite / action |
|---|---|---|---|
Hypothèses :
Risques :
Prochaines actions :
```

## Checklist QA interne
- [ ] Les inputs et les limites d'autorisation sont identifiés.
- [ ] Les trois analyses sont documentées : définir cohortes sans fuite de cible ; comparer erreurs et incertitude par groupe ; distinguer problème de données, de seuil et de modèle.
- [ ] Le critère d'acceptation est vérifié ou explicitement marqué non vérifié.
- [ ] Aucun résultat d'exécution ou accord humain n'est inventé.

## KPI reliés
- Couverture des éléments requis : éléments documentés / éléments applicables de ce livrable (dénominateur conservé).
- Part des conclusions appuyées par une preuve ou une source datée ; ne pas compter une hypothèse comme preuve.
- Nombre d'écarts au critère suivant restant ouverts : une cohorte minuscule ou sélectionnée après coup est signalée comme exploratoire.

## Definition of done
- [ ] Rapport de cohortes avec exemples et hypothèses testables livré dans le périmètre convenu.
- [ ] Une cohorte minuscule ou sélectionnée après coup est signalée comme exploratoire.
- [ ] Preuves, inconnues, exceptions et actions restantes sont lisibles ; aucune réussite globale en cas de vérification bloquante manquante.

## Exemples d'usage
**Cas nominal** : à partir de prédictions, vérité terrain, segments autorisés et protocole de validation, produire rapport de cohortes avec exemples et hypothèses testables puis vérifier le critère d'acceptation ci-dessus.

**Cas limite** : une preuve ou autorisation nécessaire manque ; livrer les éléments établis et indiquer précisément ce qui empêche la validation, sans substituer une valeur par défaut.

## Contraintes et références
- Référence officielle consultée le 2026-10-21 : [scikit-learn - Model selection and evaluation](https://scikit-learn.org/stable/model_selection.html). Synthèse originale, sans reproduction du texte source ; vérifier les versions et l'applicabilité au contexte.
- Migration : DEL-20261021-EXCLUSIVE-SKILLS-MIGRATION.

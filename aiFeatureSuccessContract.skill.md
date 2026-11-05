# AI Feature Success Contract

## Objectif
Formaliser les conditions d'acceptation d'une fonctionnalité IA entre responsables produit, modèle et exploitation.


## Quand l'utiliser (triggers)
- Demande portant sur « AI Feature Success Contract » ou sur le livrable : contrat de succès produit ia avec critères d'acceptation et responsables.
- Besoin de vérifier ce résultat : la réussite exige à la fois valeur d'usage et respect des limites convenues, pas une seule moyenne modèle.

## Hors périmètre
- Ne pas remplacer les domaines des agents complémentaires : présenter les interfaces et transmettre les besoins à l'agent rattaché (voir table de routage).
- L'exécution système, les modifications de fichiers, les tests et les publications relèvent de l'agent rattaché (voir table de routage) ; cette skill n'accorde aucun outil supplémentaire.
- Ne pas confondre préparation d'un protocole, revue statique et résultat d'une exécution réelle.

## Inputs requis
- Usage cible, erreurs tolérables, supervision et métriques métier.
- Périmètre autorisé, version des artefacts, sources accessibles et décisions déjà validées.
- Critères d'acceptation et limites d'action ; marquer les éléments inconnus avant de conclure.

## Sorties attendues
- Contrat de succès produit IA avec critères d'acceptation et responsables.
- Preuves ou références par constat ; hypothèses, exceptions et vérifications non réalisées séparées.
- Brief des décisions ou actions nécessaires pour l'agent rattaché, sans les annoncer déjà exécutées.

## Workflow recommandé
1. Cadrer les inputs : usage cible, erreurs tolérables, supervision et métriques métier ; vérifier les préconditions et autorisations.
2. Distinguer succès utilisateur et performance modèle.
3. Définir abstention et recours humain acceptables.
4. Relier seuils convenus aux preuves de réception.
5. Vérifier le livrable par ce critère : la réussite exige à la fois valeur d'usage et respect des limites convenues, pas une seule moyenne modèle.
6. Restituer résultat, hypothèses, risques et prochaines actions ; signaler explicitement les blocages.

## Garde-fous
- La réussite exige à la fois valeur d'usage et respect des limites convenues, pas une seule moyenne modèle.
- Ne pas inventer de mesure, d'accord, de preuve ou de source ; distinguer observé, inféré et non testé.
- Ne pas transmettre d'artefact privé ou de donnée personnelle à un service tiers ; minimiser les données sensibles.
- Privilégier les outils libres maintenus et vérifier les versions applicables sans introduire de dépendance EOL.
- Lire la référence dans son contexte : elle éclaire la méthode, elle ne certifie pas ce livrable et n'impose pas de seuil universel.

## Templates copier/coller
### Entrée
```text
Objet : AI Feature Success Contract
Inputs : Usage cible, erreurs tolérables, supervision et métriques métier
Version / périmètre autorisé :
Résultat demandé : Contrat de succès produit IA avec critères d'acceptation et responsables
Contraintes et inconnues :
```

### Sortie
```text
Résultat : Contrat de succès produit IA avec critères d'acceptation et responsables
| Élément examiné | Preuve / source / version | Conclusion | Limite / action |
|---|---|---|---|
Hypothèses :
Risques :
Prochaines actions :
```

## Checklist QA interne
- [ ] Les inputs et les limites d'autorisation sont identifiés.
- [ ] Les trois analyses sont documentées : distinguer succès utilisateur et performance modèle ; définir abstention et recours humain acceptables ; relier seuils convenus aux preuves de réception.
- [ ] Le critère d'acceptation est vérifié ou explicitement marqué non vérifié.
- [ ] Aucun résultat d'exécution ou accord humain n'est inventé.

## KPI reliés
- Couverture des éléments requis : éléments documentés / éléments applicables de ce livrable (dénominateur conservé).
- Part des conclusions appuyées par une preuve ou une source datée ; ne pas compter une hypothèse comme preuve.
- Nombre d'écarts au critère suivant restant ouverts : la réussite exige à la fois valeur d'usage et respect des limites convenues, pas une seule moyenne modèle.

## Definition of done
- [ ] Contrat de succès produit IA avec critères d'acceptation et responsables livré dans le périmètre convenu.
- [ ] La réussite exige à la fois valeur d'usage et respect des limites convenues, pas une seule moyenne modèle.
- [ ] Preuves, inconnues, exceptions et actions restantes sont lisibles ; aucune réussite globale en cas de vérification bloquante manquante.

## Exemples d'usage
**Cas nominal** : à partir de usage cible, erreurs tolérables, supervision et métriques métier, produire contrat de succès produit ia avec critères d'acceptation et responsables puis vérifier le critère d'acceptation ci-dessus.

**Cas limite** : une preuve ou autorisation nécessaire manque ; livrer les éléments établis et indiquer précisément ce qui empêche la validation, sans substituer une valeur par défaut.

## Contraintes et références
- Référence officielle consultée le 2026-10-21 : [NIST AI Risk Management Framework](https://www.nist.gov/itl/ai-risk-management-framework). Synthèse originale, sans reproduction du texte source ; vérifier les versions et l'applicabilité au contexte.
- Migration : DEL-20261021-EXCLUSIVE-SKILLS-MIGRATION.

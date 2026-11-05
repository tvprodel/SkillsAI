# Cognitive Journey Barrier Review

## Objectif
Repérer dans un parcours les obstacles de compréhension et de mémoire de travail observables.


## Quand l'utiliser (triggers)
- Demande portant sur « Cognitive Journey Barrier Review » ou sur le livrable : carte étape/barrière/recommandation/scénario de vérification.
- Besoin de vérifier ce résultat : chaque recommandation cognitive est distinguée d'une exigence normative wcag.

## Hors périmètre
- Ne pas remplacer les domaines des agents complémentaires : présenter les interfaces et transmettre les besoins à l'agent rattaché (voir table de routage).
- L'exécution système, les modifications de fichiers, les tests et les publications relèvent de l'agent rattaché (voir table de routage) ; cette skill n'accorde aucun outil supplémentaire.
- Ne pas confondre préparation d'un protocole, revue statique et résultat d'une exécution réelle.

## Inputs requis
- Parcours critique, consignes, retours d'usage et contraintes.
- Périmètre autorisé, version des artefacts, sources accessibles et décisions déjà validées.
- Critères d'acceptation et limites d'action ; marquer les éléments inconnus avant de conclure.

## Sorties attendues
- Carte étape/barrière/recommandation/scénario de vérification.
- Preuves ou références par constat ; hypothèses, exceptions et vérifications non réalisées séparées.
- Brief des décisions ou actions nécessaires pour l'agent rattaché, sans les annoncer déjà exécutées.

## Workflow recommandé
1. Cadrer les inputs : parcours critique, consignes, retours d'usage et contraintes ; vérifier les préconditions et autorisations.
2. Repérer informations à retenir entre étapes.
3. Examiner erreurs, interruptions et reprise.
4. Proposer des aides vérifiables sans diagnostic utilisateur.
5. Vérifier le livrable par ce critère : chaque recommandation cognitive est distinguée d'une exigence normative wcag.
6. Restituer résultat, hypothèses, risques et prochaines actions ; signaler explicitement les blocages.

## Garde-fous
- Chaque recommandation cognitive est distinguée d'une exigence normative WCAG.
- Ne pas inventer de mesure, d'accord, de preuve ou de source ; distinguer observé, inféré et non testé.
- Ne pas transmettre d'artefact privé ou de donnée personnelle à un service tiers ; minimiser les données sensibles.
- Privilégier les outils libres maintenus et vérifier les versions applicables sans introduire de dépendance EOL.
- Lire la référence dans son contexte : elle éclaire la méthode, elle ne certifie pas ce livrable et n'impose pas de seuil universel.

## Templates copier/coller
### Entrée
```text
Objet : Cognitive Journey Barrier Review
Inputs : Parcours critique, consignes, retours d'usage et contraintes
Version / périmètre autorisé :
Résultat demandé : Carte étape/barrière/recommandation/scénario de vérification
Contraintes et inconnues :
```

### Sortie
```text
Résultat : Carte étape/barrière/recommandation/scénario de vérification
| Élément examiné | Preuve / source / version | Conclusion | Limite / action |
|---|---|---|---|
Hypothèses :
Risques :
Prochaines actions :
```

## Checklist QA interne
- [ ] Les inputs et les limites d'autorisation sont identifiés.
- [ ] Les trois analyses sont documentées : repérer informations à retenir entre étapes ; examiner erreurs, interruptions et reprise ; proposer des aides vérifiables sans diagnostic utilisateur.
- [ ] Le critère d'acceptation est vérifié ou explicitement marqué non vérifié.
- [ ] Aucun résultat d'exécution ou accord humain n'est inventé.

## KPI reliés
- Couverture des éléments requis : éléments documentés / éléments applicables de ce livrable (dénominateur conservé).
- Part des conclusions appuyées par une preuve ou une source datée ; ne pas compter une hypothèse comme preuve.
- Nombre d'écarts au critère suivant restant ouverts : chaque recommandation cognitive est distinguée d'une exigence normative wcag.

## Definition of done
- [ ] Carte étape/barrière/recommandation/scénario de vérification livré dans le périmètre convenu.
- [ ] Chaque recommandation cognitive est distinguée d'une exigence normative WCAG.
- [ ] Preuves, inconnues, exceptions et actions restantes sont lisibles ; aucune réussite globale en cas de vérification bloquante manquante.

## Exemples d'usage
**Cas nominal** : à partir de parcours critique, consignes, retours d'usage et contraintes, produire carte étape/barrière/recommandation/scénario de vérification puis vérifier le critère d'acceptation ci-dessus.

**Cas limite** : une preuve ou autorisation nécessaire manque ; livrer les éléments établis et indiquer précisément ce qui empêche la validation, sans substituer une valeur par défaut.

## Contraintes et références
- Référence officielle consultée le 2026-10-21 : [W3C COGA - Making Content Usable](https://www.w3.org/TR/coga-usable/). Synthèse originale, sans reproduction du texte source ; vérifier les versions et l'applicabilité au contexte.
- Migration : DEL-20261021-EXCLUSIVE-SKILLS-MIGRATION.

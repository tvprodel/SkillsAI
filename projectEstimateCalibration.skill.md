# Project Estimate Calibration

## Objectif
Produire une estimation projet fondée sur les hypothèses, l'incertitude et les réalisations comparables.


## Quand l'utiliser (triggers)
- Demande portant sur « Project Estimate Calibration » ou sur le livrable : estimation par lot avec intervalle et hypothèses.
- Besoin de vérifier ce résultat : aucune estimation n'est présentée comme engagement ferme sans validation.

## Hors périmètre
- Ne pas remplacer les domaines des agents complémentaires : présenter les interfaces et transmettre les besoins à l'agent rattaché (voir table de routage).
- L'exécution système, les modifications de fichiers, les tests et les publications relèvent de l'agent rattaché (voir table de routage) ; cette skill n'accorde aucun outil supplémentaire.
- Ne pas confondre préparation d'un protocole, revue statique et résultat d'une exécution réelle.

## Inputs requis
- Lots, données historiques comparables, contraintes de capacité.
- Périmètre autorisé, version des artefacts, sources accessibles et décisions déjà validées.
- Critères d'acceptation et limites d'action ; marquer les éléments inconnus avant de conclure.

## Sorties attendues
- Estimation par lot avec intervalle et hypothèses.
- Preuves ou références par constat ; hypothèses, exceptions et vérifications non réalisées séparées.
- Brief des décisions ou actions nécessaires pour l'agent rattaché, sans les annoncer déjà exécutées.

## Workflow recommandé
1. Cadrer les inputs : lots, données historiques comparables, contraintes de capacité ; vérifier les préconditions et autorisations.
2. Séparer effort, durée et attente.
3. Estimer des intervalles avec facteurs explicites.
4. Comparer estimé/réalisé pour recalibrer les prochains lots.
5. Vérifier le livrable par ce critère : aucune estimation n'est présentée comme engagement ferme sans validation.
6. Restituer résultat, hypothèses, risques et prochaines actions ; signaler explicitement les blocages.

## Garde-fous
- Aucune estimation n'est présentée comme engagement ferme sans validation.
- Ne pas inventer de mesure, d'accord, de preuve ou de source ; distinguer observé, inféré et non testé.
- Ne pas transmettre d'artefact privé ou de donnée personnelle à un service tiers ; minimiser les données sensibles.
- Privilégier les outils libres maintenus et vérifier les versions applicables sans introduire de dépendance EOL.
- Lire la référence dans son contexte : elle éclaire la méthode, elle ne certifie pas ce livrable et n'impose pas de seuil universel.

## Templates copier/coller
### Entrée
```text
Objet : Project Estimate Calibration
Inputs : Lots, données historiques comparables, contraintes de capacité
Version / périmètre autorisé :
Résultat demandé : Estimation par lot avec intervalle et hypothèses
Contraintes et inconnues :
```

### Sortie
```text
Résultat : Estimation par lot avec intervalle et hypothèses
| Élément examiné | Preuve / source / version | Conclusion | Limite / action |
|---|---|---|---|
Hypothèses :
Risques :
Prochaines actions :
```

## Checklist QA interne
- [ ] Les inputs et les limites d'autorisation sont identifiés.
- [ ] Les trois analyses sont documentées : séparer effort, durée et attente ; estimer des intervalles avec facteurs explicites ; comparer estimé/réalisé pour recalibrer les prochains lots.
- [ ] Le critère d'acceptation est vérifié ou explicitement marqué non vérifié.
- [ ] Aucun résultat d'exécution ou accord humain n'est inventé.

## KPI reliés
- Couverture des éléments requis : éléments documentés / éléments applicables de ce livrable (dénominateur conservé).
- Part des conclusions appuyées par une preuve ou une source datée ; ne pas compter une hypothèse comme preuve.
- Nombre d'écarts au critère suivant restant ouverts : aucune estimation n'est présentée comme engagement ferme sans validation.

## Definition of done
- [ ] Estimation par lot avec intervalle et hypothèses livré dans le périmètre convenu.
- [ ] Aucune estimation n'est présentée comme engagement ferme sans validation.
- [ ] Preuves, inconnues, exceptions et actions restantes sont lisibles ; aucune réussite globale en cas de vérification bloquante manquante.

## Exemples d'usage
**Cas nominal** : à partir de lots, données historiques comparables, contraintes de capacité, produire estimation par lot avec intervalle et hypothèses puis vérifier le critère d'acceptation ci-dessus.

**Cas limite** : une preuve ou autorisation nécessaire manque ; livrer les éléments établis et indiquer précisément ce qui empêche la validation, sans substituer une valeur par défaut.

## Contraintes et références
- Référence officielle consultée le 2026-10-21 : [W3C PROV Overview](https://www.w3.org/TR/prov-overview/). Synthèse originale, sans reproduction du texte source ; vérifier les versions et l'applicabilité au contexte.
- Migration : DEL-20261021-EXCLUSIVE-SKILLS-MIGRATION.

# Product Prioritization Decision

## Objectif
Arbitrer un backlog produit selon une méthode de valeur explicite et les contraintes disponibles.


## Quand l'utiliser (triggers)
- Demande portant sur « Product Prioritization Decision » ou sur le livrable : tableau de priorisation et justification des arbitrages.
- Besoin de vérifier ce résultat : le classement reste explicable si une estimation change et ne remplace pas la décision humaine.

## Hors périmètre
- Ne pas remplacer les domaines des agents complémentaires : présenter les interfaces et transmettre les besoins à l'agent rattaché (voir table de routage).
- L'exécution système, les modifications de fichiers, les tests et les publications relèvent de l'agent rattaché (voir table de routage) ; cette skill n'accorde aucun outil supplémentaire.
- Ne pas confondre préparation d'un protocole, revue statique et résultat d'une exécution réelle.

## Inputs requis
- Options, objectifs, estimation d'effort, confiance et dépendances.
- Périmètre autorisé, version des artefacts, sources accessibles et décisions déjà validées.
- Critères d'acceptation et limites d'action ; marquer les éléments inconnus avant de conclure.

## Sorties attendues
- Tableau de priorisation et justification des arbitrages.
- Preuves ou références par constat ; hypothèses, exceptions et vérifications non réalisées séparées.
- Brief des décisions ou actions nécessaires pour l'agent rattaché, sans les annoncer déjà exécutées.

## Workflow recommandé
1. Cadrer les inputs : options, objectifs, estimation d'effort, confiance et dépendances ; vérifier les préconditions et autorisations.
2. Choisir une méthode adaptée plutôt qu'un score imposé.
3. Calculer et expliquer les contributions.
4. Tester les classements sensibles aux hypothèses.
5. Vérifier le livrable par ce critère : le classement reste explicable si une estimation change et ne remplace pas la décision humaine.
6. Restituer résultat, hypothèses, risques et prochaines actions ; signaler explicitement les blocages.

## Garde-fous
- Le classement reste explicable si une estimation change et ne remplace pas la décision humaine.
- Ne pas inventer de mesure, d'accord, de preuve ou de source ; distinguer observé, inféré et non testé.
- Ne pas transmettre d'artefact privé ou de donnée personnelle à un service tiers ; minimiser les données sensibles.
- Privilégier les outils libres maintenus et vérifier les versions applicables sans introduire de dépendance EOL.
- Lire la référence dans son contexte : elle éclaire la méthode, elle ne certifie pas ce livrable et n'impose pas de seuil universel.

## Templates copier/coller
### Entrée
```text
Objet : Product Prioritization Decision
Inputs : Options, objectifs, estimation d'effort, confiance et dépendances
Version / périmètre autorisé :
Résultat demandé : Tableau de priorisation et justification des arbitrages
Contraintes et inconnues :
```

### Sortie
```text
Résultat : Tableau de priorisation et justification des arbitrages
| Élément examiné | Preuve / source / version | Conclusion | Limite / action |
|---|---|---|---|
Hypothèses :
Risques :
Prochaines actions :
```

## Checklist QA interne
- [ ] Les inputs et les limites d'autorisation sont identifiés.
- [ ] Les trois analyses sont documentées : choisir une méthode adaptée plutôt qu'un score imposé ; calculer et expliquer les contributions ; tester les classements sensibles aux hypothèses.
- [ ] Le critère d'acceptation est vérifié ou explicitement marqué non vérifié.
- [ ] Aucun résultat d'exécution ou accord humain n'est inventé.

## KPI reliés
- Couverture des éléments requis : éléments documentés / éléments applicables de ce livrable (dénominateur conservé).
- Part des conclusions appuyées par une preuve ou une source datée ; ne pas compter une hypothèse comme preuve.
- Nombre d'écarts au critère suivant restant ouverts : le classement reste explicable si une estimation change et ne remplace pas la décision humaine.

## Definition of done
- [ ] Tableau de priorisation et justification des arbitrages livré dans le périmètre convenu.
- [ ] Le classement reste explicable si une estimation change et ne remplace pas la décision humaine.
- [ ] Preuves, inconnues, exceptions et actions restantes sont lisibles ; aucune réussite globale en cas de vérification bloquante manquante.

## Exemples d'usage
**Cas nominal** : à partir de options, objectifs, estimation d'effort, confiance et dépendances, produire tableau de priorisation et justification des arbitrages puis vérifier le critère d'acceptation ci-dessus.

**Cas limite** : une preuve ou autorisation nécessaire manque ; livrer les éléments établis et indiquer précisément ce qui empêche la validation, sans substituer une valeur par défaut.

## Contraintes et références
- Référence officielle consultée le 2026-10-21 : [W3C PROV Overview](https://www.w3.org/TR/prov-overview/). Synthèse originale, sans reproduction du texte source ; vérifier les versions et l'applicabilité au contexte.
- Migration : DEL-20261021-EXCLUSIVE-SKILLS-MIGRATION.

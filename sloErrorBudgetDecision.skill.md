# SLO and Error-Budget Decision

## Objectif
Relier les objectifs de fiabilité aux décisions de changement d'une plateforme.


## Quand l'utiliser (triggers)
- Demande portant sur « SLO and Error-Budget Decision » ou sur le livrable : politique slo/budget/décision avec exemples calculés.
- Besoin de vérifier ce résultat : les objectifs et fenêtres sont approuvés et aucun taux n'est calculé sans dénominateur.

## Hors périmètre
- Ne pas remplacer les domaines des agents complémentaires : présenter les interfaces et transmettre les besoins à l'agent rattaché (voir table de routage).
- L'exécution système, les modifications de fichiers, les tests et les publications relèvent de l'agent rattaché (voir table de routage) ; cette skill n'accorde aucun outil supplémentaire.
- Ne pas confondre préparation d'un protocole, revue statique et résultat d'une exécution réelle.

## Inputs requis
- Parcours critiques, SLI, historique et tolérance convenue.
- Périmètre autorisé, version des artefacts, sources accessibles et décisions déjà validées.
- Critères d'acceptation et limites d'action ; marquer les éléments inconnus avant de conclure.

## Sorties attendues
- Politique SLO/budget/décision avec exemples calculés.
- Preuves ou références par constat ; hypothèses, exceptions et vérifications non réalisées séparées.
- Brief des décisions ou actions nécessaires pour l'agent rattaché, sans les annoncer déjà exécutées.

## Workflow recommandé
1. Cadrer les inputs : parcours critiques, sli, historique et tolérance convenue ; vérifier les préconditions et autorisations.
2. Définir bon événement et population.
3. Calculer budget et consommation sur fenêtre explicite.
4. Associer épuisement du budget à une décision de changement.
5. Vérifier le livrable par ce critère : les objectifs et fenêtres sont approuvés et aucun taux n'est calculé sans dénominateur.
6. Restituer résultat, hypothèses, risques et prochaines actions ; signaler explicitement les blocages.

## Garde-fous
- Les objectifs et fenêtres sont approuvés et aucun taux n'est calculé sans dénominateur.
- Ne pas inventer de mesure, d'accord, de preuve ou de source ; distinguer observé, inféré et non testé.
- Ne pas transmettre d'artefact privé ou de donnée personnelle à un service tiers ; minimiser les données sensibles.
- Privilégier les outils libres maintenus et vérifier les versions applicables sans introduire de dépendance EOL.
- Lire la référence dans son contexte : elle éclaire la méthode, elle ne certifie pas ce livrable et n'impose pas de seuil universel.

## Templates copier/coller
### Entrée
```text
Objet : SLO and Error-Budget Decision
Inputs : Parcours critiques, SLI, historique et tolérance convenue
Version / périmètre autorisé :
Résultat demandé : Politique SLO/budget/décision avec exemples calculés
Contraintes et inconnues :
```

### Sortie
```text
Résultat : Politique SLO/budget/décision avec exemples calculés
| Élément examiné | Preuve / source / version | Conclusion | Limite / action |
|---|---|---|---|
Hypothèses :
Risques :
Prochaines actions :
```

## Checklist QA interne
- [ ] Les inputs et les limites d'autorisation sont identifiés.
- [ ] Les trois analyses sont documentées : définir bon événement et population ; calculer budget et consommation sur fenêtre explicite ; associer épuisement du budget à une décision de changement.
- [ ] Le critère d'acceptation est vérifié ou explicitement marqué non vérifié.
- [ ] Aucun résultat d'exécution ou accord humain n'est inventé.

## KPI reliés
- Couverture des éléments requis : éléments documentés / éléments applicables de ce livrable (dénominateur conservé).
- Part des conclusions appuyées par une preuve ou une source datée ; ne pas compter une hypothèse comme preuve.
- Nombre d'écarts au critère suivant restant ouverts : les objectifs et fenêtres sont approuvés et aucun taux n'est calculé sans dénominateur.

## Definition of done
- [ ] Politique SLO/budget/décision avec exemples calculés livré dans le périmètre convenu.
- [ ] Les objectifs et fenêtres sont approuvés et aucun taux n'est calculé sans dénominateur.
- [ ] Preuves, inconnues, exceptions et actions restantes sont lisibles ; aucune réussite globale en cas de vérification bloquante manquante.

## Exemples d'usage
**Cas nominal** : à partir de parcours critiques, sli, historique et tolérance convenue, produire politique slo/budget/décision avec exemples calculés puis vérifier le critère d'acceptation ci-dessus.

**Cas limite** : une preuve ou autorisation nécessaire manque ; livrer les éléments établis et indiquer précisément ce qui empêche la validation, sans substituer une valeur par défaut.

## Contraintes et références
- Référence officielle consultée le 2026-10-21 : [Google SRE Workbook](https://sre.google/workbook/table-of-contents/). Synthèse originale, sans reproduction du texte source ; vérifier les versions et l'applicabilité au contexte.
- Migration : DEL-20261021-EXCLUSIVE-SKILLS-MIGRATION.

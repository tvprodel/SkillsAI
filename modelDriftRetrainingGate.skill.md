# Model Drift Retraining Gate

## Objectif
Définir quand une dérive observée justifie une investigation ou un réentraînement.


## Quand l'utiliser (triggers)
- Demande portant sur « Model Drift Retraining Gate » ou sur le livrable : matrice signal/action avec gate de promotion du modèle.
- Besoin de vérifier ce résultat : une alerte de drift ne provoque pas une promotion automatique sans validation.

## Hors périmètre
- Ne pas remplacer les domaines des agents complémentaires : présenter les interfaces et transmettre les besoins à l'agent rattaché (voir table de routage).
- L'exécution système, les modifications de fichiers, les tests et les publications relèvent de l'agent rattaché (voir table de routage) ; cette skill n'accorde aucun outil supplémentaire.
- Ne pas confondre préparation d'un protocole, revue statique et résultat d'une exécution réelle.

## Inputs requis
- Référence, données récentes, performance étiquetée et coûts de réentraînement.
- Périmètre autorisé, version des artefacts, sources accessibles et décisions déjà validées.
- Critères d'acceptation et limites d'action ; marquer les éléments inconnus avant de conclure.

## Sorties attendues
- Matrice signal/action avec gate de promotion du modèle.
- Preuves ou références par constat ; hypothèses, exceptions et vérifications non réalisées séparées.
- Brief des décisions ou actions nécessaires pour l'agent rattaché, sans les annoncer déjà exécutées.

## Workflow recommandé
1. Cadrer les inputs : référence, données récentes, performance étiquetée et coûts de réentraînement ; vérifier les préconditions et autorisations.
2. Séparer dérive d'entrée et baisse de performance.
3. Associer seuils à preuves et délais d'étiquetage.
4. Définir conditions entraîner/valider/promouvoir ou conserver.
5. Vérifier le livrable par ce critère : une alerte de drift ne provoque pas une promotion automatique sans validation.
6. Restituer résultat, hypothèses, risques et prochaines actions ; signaler explicitement les blocages.

## Garde-fous
- Une alerte de drift ne provoque pas une promotion automatique sans validation.
- Ne pas inventer de mesure, d'accord, de preuve ou de source ; distinguer observé, inféré et non testé.
- Ne pas transmettre d'artefact privé ou de donnée personnelle à un service tiers ; minimiser les données sensibles.
- Privilégier les outils libres maintenus et vérifier les versions applicables sans introduire de dépendance EOL.
- Lire la référence dans son contexte : elle éclaire la méthode, elle ne certifie pas ce livrable et n'impose pas de seuil universel.

## Templates copier/coller
### Entrée
```text
Objet : Model Drift Retraining Gate
Inputs : Référence, données récentes, performance étiquetée et coûts de réentraînement
Version / périmètre autorisé :
Résultat demandé : Matrice signal/action avec gate de promotion du modèle
Contraintes et inconnues :
```

### Sortie
```text
Résultat : Matrice signal/action avec gate de promotion du modèle
| Élément examiné | Preuve / source / version | Conclusion | Limite / action |
|---|---|---|---|
Hypothèses :
Risques :
Prochaines actions :
```

## Checklist QA interne
- [ ] Les inputs et les limites d'autorisation sont identifiés.
- [ ] Les trois analyses sont documentées : séparer dérive d'entrée et baisse de performance ; associer seuils à preuves et délais d'étiquetage ; définir conditions entraîner/valider/promouvoir ou conserver.
- [ ] Le critère d'acceptation est vérifié ou explicitement marqué non vérifié.
- [ ] Aucun résultat d'exécution ou accord humain n'est inventé.

## KPI reliés
- Couverture des éléments requis : éléments documentés / éléments applicables de ce livrable (dénominateur conservé).
- Part des conclusions appuyées par une preuve ou une source datée ; ne pas compter une hypothèse comme preuve.
- Nombre d'écarts au critère suivant restant ouverts : une alerte de drift ne provoque pas une promotion automatique sans validation.

## Definition of done
- [ ] Matrice signal/action avec gate de promotion du modèle livré dans le périmètre convenu.
- [ ] Une alerte de drift ne provoque pas une promotion automatique sans validation.
- [ ] Preuves, inconnues, exceptions et actions restantes sont lisibles ; aucune réussite globale en cas de vérification bloquante manquante.

## Exemples d'usage
**Cas nominal** : à partir de référence, données récentes, performance étiquetée et coûts de réentraînement, produire matrice signal/action avec gate de promotion du modèle puis vérifier le critère d'acceptation ci-dessus.

**Cas limite** : une preuve ou autorisation nécessaire manque ; livrer les éléments établis et indiquer précisément ce qui empêche la validation, sans substituer une valeur par défaut.

## Contraintes et références
- Référence officielle consultée le 2026-10-21 : [scikit-learn - Model selection and evaluation](https://scikit-learn.org/stable/model_selection.html). Synthèse originale, sans reproduction du texte source ; vérifier les versions et l'applicabilité au contexte.
- Migration : DEL-20261021-EXCLUSIVE-SKILLS-MIGRATION.

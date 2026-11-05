# AI Model Release Value Decision

## Objectif
Éclairer le go/no-go produit d'une nouvelle version de modèle selon sa valeur d'usage.


## Quand l'utiliser (triggers)
- Demande portant sur « AI Model Release Value Decision » ou sur le livrable : note de décision produit avec critères de succès et d'arrêt.
- Besoin de vérifier ce résultat : l'amélioration d'une métrique modèle seule ne suffit pas à justifier le lancement.

## Hors périmètre
- Ne pas remplacer les domaines des agents complémentaires : présenter les interfaces et transmettre les besoins à l'agent rattaché (voir table de routage).
- L'exécution système, les modifications de fichiers, les tests et les publications relèvent de l'agent rattaché (voir table de routage) ; cette skill n'accorde aucun outil supplémentaire.
- Ne pas confondre préparation d'un protocole, revue statique et résultat d'une exécution réelle.

## Inputs requis
- Objectifs produit, évaluation modèle, coûts, risques et feedback.
- Périmètre autorisé, version des artefacts, sources accessibles et décisions déjà validées.
- Critères d'acceptation et limites d'action ; marquer les éléments inconnus avant de conclure.

## Sorties attendues
- Note de décision produit avec critères de succès et d'arrêt.
- Preuves ou références par constat ; hypothèses, exceptions et vérifications non réalisées séparées.
- Brief des décisions ou actions nécessaires pour l'agent rattaché, sans les annoncer déjà exécutées.

## Workflow recommandé
1. Cadrer les inputs : objectifs produit, évaluation modèle, coûts, risques et feedback ; vérifier les préconditions et autorisations.
2. Comparer bénéfice attendu et régressions.
3. Définir population pilote et garde-fous produit.
4. Préparer critères adopter/retarder/retirer.
5. Vérifier le livrable par ce critère : l'amélioration d'une métrique modèle seule ne suffit pas à justifier le lancement.
6. Restituer résultat, hypothèses, risques et prochaines actions ; signaler explicitement les blocages.

## Garde-fous
- L'amélioration d'une métrique modèle seule ne suffit pas à justifier le lancement.
- Ne pas inventer de mesure, d'accord, de preuve ou de source ; distinguer observé, inféré et non testé.
- Ne pas transmettre d'artefact privé ou de donnée personnelle à un service tiers ; minimiser les données sensibles.
- Privilégier les outils libres maintenus et vérifier les versions applicables sans introduire de dépendance EOL.
- Lire la référence dans son contexte : elle éclaire la méthode, elle ne certifie pas ce livrable et n'impose pas de seuil universel.

## Templates copier/coller
### Entrée
```text
Objet : AI Model Release Value Decision
Inputs : Objectifs produit, évaluation modèle, coûts, risques et feedback
Version / périmètre autorisé :
Résultat demandé : Note de décision produit avec critères de succès et d'arrêt
Contraintes et inconnues :
```

### Sortie
```text
Résultat : Note de décision produit avec critères de succès et d'arrêt
| Élément examiné | Preuve / source / version | Conclusion | Limite / action |
|---|---|---|---|
Hypothèses :
Risques :
Prochaines actions :
```

## Checklist QA interne
- [ ] Les inputs et les limites d'autorisation sont identifiés.
- [ ] Les trois analyses sont documentées : comparer bénéfice attendu et régressions ; définir population pilote et garde-fous produit ; préparer critères adopter/retarder/retirer.
- [ ] Le critère d'acceptation est vérifié ou explicitement marqué non vérifié.
- [ ] Aucun résultat d'exécution ou accord humain n'est inventé.

## KPI reliés
- Couverture des éléments requis : éléments documentés / éléments applicables de ce livrable (dénominateur conservé).
- Part des conclusions appuyées par une preuve ou une source datée ; ne pas compter une hypothèse comme preuve.
- Nombre d'écarts au critère suivant restant ouverts : l'amélioration d'une métrique modèle seule ne suffit pas à justifier le lancement.

## Definition of done
- [ ] Note de décision produit avec critères de succès et d'arrêt livré dans le périmètre convenu.
- [ ] L'amélioration d'une métrique modèle seule ne suffit pas à justifier le lancement.
- [ ] Preuves, inconnues, exceptions et actions restantes sont lisibles ; aucune réussite globale en cas de vérification bloquante manquante.

## Exemples d'usage
**Cas nominal** : à partir de objectifs produit, évaluation modèle, coûts, risques et feedback, produire note de décision produit avec critères de succès et d'arrêt puis vérifier le critère d'acceptation ci-dessus.

**Cas limite** : une preuve ou autorisation nécessaire manque ; livrer les éléments établis et indiquer précisément ce qui empêche la validation, sans substituer une valeur par défaut.

## Contraintes et références
- Référence officielle consultée le 2026-10-21 : [NIST AI Risk Management Framework](https://www.nist.gov/itl/ai-risk-management-framework). Synthèse originale, sans reproduction du texte source ; vérifier les versions et l'applicabilité au contexte.
- Migration : DEL-20261021-EXCLUSIVE-SKILLS-MIGRATION.

# Architecture Quality Scenario

## Objectif
Rendre une exigence de qualité architecturale testable par un scénario concret.


## Quand l'utiliser (triggers)
- Demande portant sur « Architecture Quality Scenario » ou sur le livrable : scénario qualité avec mesure de réponse et preuve attendue.
- Besoin de vérifier ce résultat : une exigence comme scalable est remplacée par un scénario mesurable convenu.

## Hors périmètre
- Ne pas remplacer les domaines des agents complémentaires : présenter les interfaces et transmettre les besoins à l'agent rattaché (voir table de routage).
- L'exécution système, les modifications de fichiers, les tests et les publications relèvent de l'agent rattaché (voir table de routage) ; cette skill n'accorde aucun outil supplémentaire.
- Ne pas confondre préparation d'un protocole, revue statique et résultat d'une exécution réelle.

## Inputs requis
- Exigences de disponibilité, performance ou évolutivité et contraintes.
- Périmètre autorisé, version des artefacts, sources accessibles et décisions déjà validées.
- Critères d'acceptation et limites d'action ; marquer les éléments inconnus avant de conclure.

## Sorties attendues
- Scénario qualité avec mesure de réponse et preuve attendue.
- Preuves ou références par constat ; hypothèses, exceptions et vérifications non réalisées séparées.
- Brief des décisions ou actions nécessaires pour l'agent rattaché, sans les annoncer déjà exécutées.

## Workflow recommandé
1. Cadrer les inputs : exigences de disponibilité, performance ou évolutivité et contraintes ; vérifier les préconditions et autorisations.
2. Définir stimulus, environnement et réponse attendue.
3. Associer mesure et budget.
4. Décrire expérience de validation et limites.
5. Vérifier le livrable par ce critère : une exigence comme scalable est remplacée par un scénario mesurable convenu.
6. Restituer résultat, hypothèses, risques et prochaines actions ; signaler explicitement les blocages.

## Garde-fous
- Une exigence comme scalable est remplacée par un scénario mesurable convenu.
- Ne pas inventer de mesure, d'accord, de preuve ou de source ; distinguer observé, inféré et non testé.
- Ne pas transmettre d'artefact privé ou de donnée personnelle à un service tiers ; minimiser les données sensibles.
- Privilégier les outils libres maintenus et vérifier les versions applicables sans introduire de dépendance EOL.
- Lire la référence dans son contexte : elle éclaire la méthode, elle ne certifie pas ce livrable et n'impose pas de seuil universel.

## Templates copier/coller
### Entrée
```text
Objet : Architecture Quality Scenario
Inputs : Exigences de disponibilité, performance ou évolutivité et contraintes
Version / périmètre autorisé :
Résultat demandé : Scénario qualité avec mesure de réponse et preuve attendue
Contraintes et inconnues :
```

### Sortie
```text
Résultat : Scénario qualité avec mesure de réponse et preuve attendue
| Élément examiné | Preuve / source / version | Conclusion | Limite / action |
|---|---|---|---|
Hypothèses :
Risques :
Prochaines actions :
```

## Checklist QA interne
- [ ] Les inputs et les limites d'autorisation sont identifiés.
- [ ] Les trois analyses sont documentées : définir stimulus, environnement et réponse attendue ; associer mesure et budget ; décrire expérience de validation et limites.
- [ ] Le critère d'acceptation est vérifié ou explicitement marqué non vérifié.
- [ ] Aucun résultat d'exécution ou accord humain n'est inventé.

## KPI reliés
- Couverture des éléments requis : éléments documentés / éléments applicables de ce livrable (dénominateur conservé).
- Part des conclusions appuyées par une preuve ou une source datée ; ne pas compter une hypothèse comme preuve.
- Nombre d'écarts au critère suivant restant ouverts : une exigence comme scalable est remplacée par un scénario mesurable convenu.

## Definition of done
- [ ] Scénario qualité avec mesure de réponse et preuve attendue livré dans le périmètre convenu.
- [ ] Une exigence comme scalable est remplacée par un scénario mesurable convenu.
- [ ] Preuves, inconnues, exceptions et actions restantes sont lisibles ; aucune réussite globale en cas de vérification bloquante manquante.

## Exemples d'usage
**Cas nominal** : à partir de exigences de disponibilité, performance ou évolutivité et contraintes, produire scénario qualité avec mesure de réponse et preuve attendue puis vérifier le critère d'acceptation ci-dessus.

**Cas limite** : une preuve ou autorisation nécessaire manque ; livrer les éléments établis et indiquer précisément ce qui empêche la validation, sans substituer une valeur par défaut.

## Contraintes et références
- Référence officielle consultée le 2026-10-21 : [Google SRE Workbook](https://sre.google/workbook/table-of-contents/). Synthèse originale, sans reproduction du texte source ; vérifier les versions et l'applicabilité au contexte.
- Migration : DEL-20261021-EXCLUSIVE-SKILLS-MIGRATION.

# Business Insight Narrative

## Objectif
Transformer des résultats analytiques métier en conclusion actionnable sans confondre corrélation et causalité.


## Quand l'utiliser (triggers)
- Demande portant sur « Business Insight Narrative » ou sur le livrable : note décisionnelle avec chiffres sourcés et réserves.
- Besoin de vérifier ce résultat : chaque affirmation chiffrée renvoie à un calcul reproductible et un périmètre temporel.

## Hors périmètre
- Ne pas remplacer les domaines des agents complémentaires : présenter les interfaces et transmettre les besoins à l'agent rattaché (voir table de routage).
- L'exécution système, les modifications de fichiers, les tests et les publications relèvent de l'agent rattaché (voir table de routage) ; cette skill n'accorde aucun outil supplémentaire.
- Ne pas confondre préparation d'un protocole, revue statique et résultat d'une exécution réelle.

## Inputs requis
- Calculs validés, période, population, décision attendue.
- Périmètre autorisé, version des artefacts, sources accessibles et décisions déjà validées.
- Critères d'acceptation et limites d'action ; marquer les éléments inconnus avant de conclure.

## Sorties attendues
- Note décisionnelle avec chiffres sourcés et réserves.
- Preuves ou références par constat ; hypothèses, exceptions et vérifications non réalisées séparées.
- Brief des décisions ou actions nécessaires pour l'agent rattaché, sans les annoncer déjà exécutées.

## Workflow recommandé
1. Cadrer les inputs : calculs validés, période, population, décision attendue ; vérifier les préconditions et autorisations.
2. Relier les métriques à la question métier.
3. Séparer constat, explication possible et preuve manquante.
4. Formuler options et limites de la décision.
5. Vérifier le livrable par ce critère : chaque affirmation chiffrée renvoie à un calcul reproductible et un périmètre temporel.
6. Restituer résultat, hypothèses, risques et prochaines actions ; signaler explicitement les blocages.

## Garde-fous
- Chaque affirmation chiffrée renvoie à un calcul reproductible et un périmètre temporel.
- Ne pas inventer de mesure, d'accord, de preuve ou de source ; distinguer observé, inféré et non testé.
- Ne pas transmettre d'artefact privé ou de donnée personnelle à un service tiers ; minimiser les données sensibles.
- Privilégier les outils libres maintenus et vérifier les versions applicables sans introduire de dépendance EOL.
- Lire la référence dans son contexte : elle éclaire la méthode, elle ne certifie pas ce livrable et n'impose pas de seuil universel.

## Templates copier/coller
### Entrée
```text
Objet : Business Insight Narrative
Inputs : Calculs validés, période, population, décision attendue
Version / périmètre autorisé :
Résultat demandé : Note décisionnelle avec chiffres sourcés et réserves
Contraintes et inconnues :
```

### Sortie
```text
Résultat : Note décisionnelle avec chiffres sourcés et réserves
| Élément examiné | Preuve / source / version | Conclusion | Limite / action |
|---|---|---|---|
Hypothèses :
Risques :
Prochaines actions :
```

## Checklist QA interne
- [ ] Les inputs et les limites d'autorisation sont identifiés.
- [ ] Les trois analyses sont documentées : relier les métriques à la question métier ; séparer constat, explication possible et preuve manquante ; formuler options et limites de la décision.
- [ ] Le critère d'acceptation est vérifié ou explicitement marqué non vérifié.
- [ ] Aucun résultat d'exécution ou accord humain n'est inventé.

## KPI reliés
- Couverture des éléments requis : éléments documentés / éléments applicables de ce livrable (dénominateur conservé).
- Part des conclusions appuyées par une preuve ou une source datée ; ne pas compter une hypothèse comme preuve.
- Nombre d'écarts au critère suivant restant ouverts : chaque affirmation chiffrée renvoie à un calcul reproductible et un périmètre temporel.

## Definition of done
- [ ] Note décisionnelle avec chiffres sourcés et réserves livré dans le périmètre convenu.
- [ ] Chaque affirmation chiffrée renvoie à un calcul reproductible et un périmètre temporel.
- [ ] Preuves, inconnues, exceptions et actions restantes sont lisibles ; aucune réussite globale en cas de vérification bloquante manquante.

## Exemples d'usage
**Cas nominal** : à partir de calculs validés, période, population, décision attendue, produire note décisionnelle avec chiffres sourcés et réserves puis vérifier le critère d'acceptation ci-dessus.

**Cas limite** : une preuve ou autorisation nécessaire manque ; livrer les éléments établis et indiquer précisément ce qui empêche la validation, sans substituer une valeur par défaut.

## Contraintes et références
- Référence officielle consultée le 2026-10-21 : [W3C PROV Overview](https://www.w3.org/TR/prov-overview/). Synthèse originale, sans reproduction du texte source ; vérifier les versions et l'applicabilité au contexte.
- Migration : DEL-20261021-EXCLUSIVE-SKILLS-MIGRATION.

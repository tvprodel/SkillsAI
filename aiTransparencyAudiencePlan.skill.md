# AI Transparency Audience Plan

## Objectif
Adapter les informations de transparence IA aux décisions de chaque public concerné.


## Quand l'utiliser (triggers)
- Demande portant sur « AI Transparency Audience Plan » ou sur le livrable : plan de transparence par audience avec contenu et preuve.
- Besoin de vérifier ce résultat : une explication compréhensible ne devient pas une garantie de fiabilité du modèle.

## Hors périmètre
- Ne pas remplacer les domaines des agents complémentaires : présenter les interfaces et transmettre les besoins à l'agent rattaché (voir table de routage).
- L'exécution système, les modifications de fichiers, les tests et les publications relèvent de l'agent rattaché (voir table de routage) ; cette skill n'accorde aucun outil supplémentaire.
- Ne pas confondre préparation d'un protocole, revue statique et résultat d'une exécution réelle.

## Inputs requis
- Publics, décisions, capacités réelles et limites connues.
- Périmètre autorisé, version des artefacts, sources accessibles et décisions déjà validées.
- Critères d'acceptation et limites d'action ; marquer les éléments inconnus avant de conclure.

## Sorties attendues
- Plan de transparence par audience avec contenu et preuve.
- Preuves ou références par constat ; hypothèses, exceptions et vérifications non réalisées séparées.
- Brief des décisions ou actions nécessaires pour l'agent rattaché, sans les annoncer déjà exécutées.

## Workflow recommandé
1. Cadrer les inputs : publics, décisions, capacités réelles et limites connues ; vérifier les préconditions et autorisations.
2. Identifier ce que chaque public doit comprendre.
3. Relier explication, preuve et action possible.
4. Prévoir recours humain et mise à jour des limites.
5. Vérifier le livrable par ce critère : une explication compréhensible ne devient pas une garantie de fiabilité du modèle.
6. Restituer résultat, hypothèses, risques et prochaines actions ; signaler explicitement les blocages.

## Garde-fous
- Une explication compréhensible ne devient pas une garantie de fiabilité du modèle.
- Ne pas inventer de mesure, d'accord, de preuve ou de source ; distinguer observé, inféré et non testé.
- Ne pas transmettre d'artefact privé ou de donnée personnelle à un service tiers ; minimiser les données sensibles.
- Privilégier les outils libres maintenus et vérifier les versions applicables sans introduire de dépendance EOL.
- Lire la référence dans son contexte : elle éclaire la méthode, elle ne certifie pas ce livrable et n'impose pas de seuil universel.

## Templates copier/coller
### Entrée
```text
Objet : AI Transparency Audience Plan
Inputs : Publics, décisions, capacités réelles et limites connues
Version / périmètre autorisé :
Résultat demandé : Plan de transparence par audience avec contenu et preuve
Contraintes et inconnues :
```

### Sortie
```text
Résultat : Plan de transparence par audience avec contenu et preuve
| Élément examiné | Preuve / source / version | Conclusion | Limite / action |
|---|---|---|---|
Hypothèses :
Risques :
Prochaines actions :
```

## Checklist QA interne
- [ ] Les inputs et les limites d'autorisation sont identifiés.
- [ ] Les trois analyses sont documentées : identifier ce que chaque public doit comprendre ; relier explication, preuve et action possible ; prévoir recours humain et mise à jour des limites.
- [ ] Le critère d'acceptation est vérifié ou explicitement marqué non vérifié.
- [ ] Aucun résultat d'exécution ou accord humain n'est inventé.

## KPI reliés
- Couverture des éléments requis : éléments documentés / éléments applicables de ce livrable (dénominateur conservé).
- Part des conclusions appuyées par une preuve ou une source datée ; ne pas compter une hypothèse comme preuve.
- Nombre d'écarts au critère suivant restant ouverts : une explication compréhensible ne devient pas une garantie de fiabilité du modèle.

## Definition of done
- [ ] Plan de transparence par audience avec contenu et preuve livré dans le périmètre convenu.
- [ ] Une explication compréhensible ne devient pas une garantie de fiabilité du modèle.
- [ ] Preuves, inconnues, exceptions et actions restantes sont lisibles ; aucune réussite globale en cas de vérification bloquante manquante.

## Exemples d'usage
**Cas nominal** : à partir de publics, décisions, capacités réelles et limites connues, produire plan de transparence par audience avec contenu et preuve puis vérifier le critère d'acceptation ci-dessus.

**Cas limite** : une preuve ou autorisation nécessaire manque ; livrer les éléments établis et indiquer précisément ce qui empêche la validation, sans substituer une valeur par défaut.

## Contraintes et références
- Référence officielle consultée le 2026-10-21 : [NIST AI Risk Management Framework](https://www.nist.gov/itl/ai-risk-management-framework). Synthèse originale, sans reproduction du texte source ; vérifier les versions et l'applicabilité au contexte.
- Migration : DEL-20261021-EXCLUSIVE-SKILLS-MIGRATION.

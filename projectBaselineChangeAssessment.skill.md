# Project Baseline Change Assessment

## Objectif
Mesurer l'effet d'une demande de changement sur une référence projet approuvée.


## Quand l'utiliser (triggers)
- Demande portant sur « Project Baseline Change Assessment » ou sur le livrable : note de changement avec différence par rapport à la référence.
- Besoin de vérifier ce résultat : aucun changement de référence n'est annoncé approuvé sans décision tracée.

## Hors périmètre
- Ne pas remplacer les domaines des agents complémentaires : présenter les interfaces et transmettre les besoins à l'agent rattaché (voir table de routage).
- L'exécution système, les modifications de fichiers, les tests et les publications relèvent de l'agent rattaché (voir table de routage) ; cette skill n'accorde aucun outil supplémentaire.
- Ne pas confondre préparation d'un protocole, revue statique et résultat d'une exécution réelle.

## Inputs requis
- Demande, référence de périmètre, dépendances, coûts et décisionnaires.
- Périmètre autorisé, version des artefacts, sources accessibles et décisions déjà validées.
- Critères d'acceptation et limites d'action ; marquer les éléments inconnus avant de conclure.

## Sorties attendues
- Note de changement avec différence par rapport à la référence.
- Preuves ou références par constat ; hypothèses, exceptions et vérifications non réalisées séparées.
- Brief des décisions ou actions nécessaires pour l'agent rattaché, sans les annoncer déjà exécutées.

## Workflow recommandé
1. Cadrer les inputs : demande, référence de périmètre, dépendances, coûts et décisionnaires ; vérifier les préconditions et autorisations.
2. Identifier lots et critères affectés.
3. Comparer options accepter/différer/refuser.
4. Tracer impacts et décision d'approbation.
5. Vérifier le livrable par ce critère : aucun changement de référence n'est annoncé approuvé sans décision tracée.
6. Restituer résultat, hypothèses, risques et prochaines actions ; signaler explicitement les blocages.

## Garde-fous
- Aucun changement de référence n'est annoncé approuvé sans décision tracée.
- Ne pas inventer de mesure, d'accord, de preuve ou de source ; distinguer observé, inféré et non testé.
- Ne pas transmettre d'artefact privé ou de donnée personnelle à un service tiers ; minimiser les données sensibles.
- Privilégier les outils libres maintenus et vérifier les versions applicables sans introduire de dépendance EOL.
- Lire la référence dans son contexte : elle éclaire la méthode, elle ne certifie pas ce livrable et n'impose pas de seuil universel.

## Templates copier/coller
### Entrée
```text
Objet : Project Baseline Change Assessment
Inputs : Demande, référence de périmètre, dépendances, coûts et décisionnaires
Version / périmètre autorisé :
Résultat demandé : Note de changement avec différence par rapport à la référence
Contraintes et inconnues :
```

### Sortie
```text
Résultat : Note de changement avec différence par rapport à la référence
| Élément examiné | Preuve / source / version | Conclusion | Limite / action |
|---|---|---|---|
Hypothèses :
Risques :
Prochaines actions :
```

## Checklist QA interne
- [ ] Les inputs et les limites d'autorisation sont identifiés.
- [ ] Les trois analyses sont documentées : identifier lots et critères affectés ; comparer options accepter/différer/refuser ; tracer impacts et décision d'approbation.
- [ ] Le critère d'acceptation est vérifié ou explicitement marqué non vérifié.
- [ ] Aucun résultat d'exécution ou accord humain n'est inventé.

## KPI reliés
- Couverture des éléments requis : éléments documentés / éléments applicables de ce livrable (dénominateur conservé).
- Part des conclusions appuyées par une preuve ou une source datée ; ne pas compter une hypothèse comme preuve.
- Nombre d'écarts au critère suivant restant ouverts : aucun changement de référence n'est annoncé approuvé sans décision tracée.

## Definition of done
- [ ] Note de changement avec différence par rapport à la référence livré dans le périmètre convenu.
- [ ] Aucun changement de référence n'est annoncé approuvé sans décision tracée.
- [ ] Preuves, inconnues, exceptions et actions restantes sont lisibles ; aucune réussite globale en cas de vérification bloquante manquante.

## Exemples d'usage
**Cas nominal** : à partir de demande, référence de périmètre, dépendances, coûts et décisionnaires, produire note de changement avec différence par rapport à la référence puis vérifier le critère d'acceptation ci-dessus.

**Cas limite** : une preuve ou autorisation nécessaire manque ; livrer les éléments établis et indiquer précisément ce qui empêche la validation, sans substituer une valeur par défaut.

## Contraintes et références
- Référence officielle consultée le 2026-10-21 : [W3C PROV Overview](https://www.w3.org/TR/prov-overview/). Synthèse originale, sans reproduction du texte source ; vérifier les versions et l'applicabilité au contexte.
- Migration : DEL-20261021-EXCLUSIVE-SKILLS-MIGRATION.

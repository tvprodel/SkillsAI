# Localization Context Adaptation

## Objectif
Adapter des formulations aux usages culturels et au contexte du public sans altérer le fond.


## Quand l'utiliser (triggers)
- Demande portant sur « Localization Context Adaptation » ou sur le livrable : variantes localisées accompagnées de justification culturelle.
- Besoin de vérifier ce résultat : les adaptations restent distinctes des changements de politique ou de promesse.

## Hors périmètre
- Ne pas remplacer les domaines des agents complémentaires : présenter les interfaces et transmettre les besoins à l'agent rattaché (voir table de routage).
- L'exécution système, les modifications de fichiers, les tests et les publications relèvent de l'agent rattaché (voir table de routage) ; cette skill n'accorde aucun outil supplémentaire.
- Ne pas confondre préparation d'un protocole, revue statique et résultat d'une exécution réelle.

## Inputs requis
- Texte, locale cible, registre, public et contraintes UI.
- Périmètre autorisé, version des artefacts, sources accessibles et décisions déjà validées.
- Critères d'acceptation et limites d'action ; marquer les éléments inconnus avant de conclure.

## Sorties attendues
- Variantes localisées accompagnées de justification culturelle.
- Preuves ou références par constat ; hypothèses, exceptions et vérifications non réalisées séparées.
- Brief des décisions ou actions nécessaires pour l'agent rattaché, sans les annoncer déjà exécutées.

## Workflow recommandé
1. Cadrer les inputs : texte, locale cible, registre, public et contraintes ui ; vérifier les préconditions et autorisations.
2. Repérer idiomes, conventions et références culturelles.
3. Proposer équivalents contextualisés.
4. Vérifier lisibilité et cohérence avec l'intention source.
5. Vérifier le livrable par ce critère : les adaptations restent distinctes des changements de politique ou de promesse.
6. Restituer résultat, hypothèses, risques et prochaines actions ; signaler explicitement les blocages.

## Garde-fous
- Les adaptations restent distinctes des changements de politique ou de promesse.
- Ne pas inventer de mesure, d'accord, de preuve ou de source ; distinguer observé, inféré et non testé.
- Ne pas transmettre d'artefact privé ou de donnée personnelle à un service tiers ; minimiser les données sensibles.
- Privilégier les outils libres maintenus et vérifier les versions applicables sans introduire de dépendance EOL.
- Lire la référence dans son contexte : elle éclaire la méthode, elle ne certifie pas ce livrable et n'impose pas de seuil universel.

## Templates copier/coller
### Entrée
```text
Objet : Localization Context Adaptation
Inputs : Texte, locale cible, registre, public et contraintes UI
Version / périmètre autorisé :
Résultat demandé : Variantes localisées accompagnées de justification culturelle
Contraintes et inconnues :
```

### Sortie
```text
Résultat : Variantes localisées accompagnées de justification culturelle
| Élément examiné | Preuve / source / version | Conclusion | Limite / action |
|---|---|---|---|
Hypothèses :
Risques :
Prochaines actions :
```

## Checklist QA interne
- [ ] Les inputs et les limites d'autorisation sont identifiés.
- [ ] Les trois analyses sont documentées : repérer idiomes, conventions et références culturelles ; proposer équivalents contextualisés ; vérifier lisibilité et cohérence avec l'intention source.
- [ ] Le critère d'acceptation est vérifié ou explicitement marqué non vérifié.
- [ ] Aucun résultat d'exécution ou accord humain n'est inventé.

## KPI reliés
- Couverture des éléments requis : éléments documentés / éléments applicables de ce livrable (dénominateur conservé).
- Part des conclusions appuyées par une preuve ou une source datée ; ne pas compter une hypothèse comme preuve.
- Nombre d'écarts au critère suivant restant ouverts : les adaptations restent distinctes des changements de politique ou de promesse.

## Definition of done
- [ ] Variantes localisées accompagnées de justification culturelle livré dans le périmètre convenu.
- [ ] Les adaptations restent distinctes des changements de politique ou de promesse.
- [ ] Preuves, inconnues, exceptions et actions restantes sont lisibles ; aucune réussite globale en cas de vérification bloquante manquante.

## Exemples d'usage
**Cas nominal** : à partir de texte, locale cible, registre, public et contraintes ui, produire variantes localisées accompagnées de justification culturelle puis vérifier le critère d'acceptation ci-dessus.

**Cas limite** : une preuve ou autorisation nécessaire manque ; livrer les éléments établis et indiquer précisément ce qui empêche la validation, sans substituer une valeur par défaut.

## Contraintes et références
- Référence officielle consultée le 2026-10-21 : [GOV.UK - Writing to GOV.UK standards](https://www.gov.uk/guidance/content-design). Synthèse originale, sans reproduction du texte source ; vérifier les versions et l'applicabilité au contexte.
- Migration : DEL-20261021-EXCLUSIVE-SKILLS-MIGRATION.

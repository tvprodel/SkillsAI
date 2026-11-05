# Grammatical Ambiguity Resolution

## Objectif
Résoudre les ambiguïtés syntaxiques et d'accord sans changer l'intention d'un texte rédigé.


## Quand l'utiliser (triggers)
- Demande portant sur « Grammatical Ambiguity Resolution » ou sur le livrable : différentiel original/correction/règle/ambiguïté restante.
- Besoin de vérifier ce résultat : une correction nécessitant un choix de sens non établi est signalée et non imposée.

## Hors périmètre
- Ne pas remplacer les domaines des agents complémentaires : présenter les interfaces et transmettre les besoins à l'agent rattaché (voir table de routage).
- L'exécution système, les modifications de fichiers, les tests et les publications relèvent de l'agent rattaché (voir table de routage) ; cette skill n'accorde aucun outil supplémentaire.
- Ne pas confondre préparation d'un protocole, revue statique et résultat d'une exécution réelle.

## Inputs requis
- Texte, langue, antécédents et intention confirmable.
- Périmètre autorisé, version des artefacts, sources accessibles et décisions déjà validées.
- Critères d'acceptation et limites d'action ; marquer les éléments inconnus avant de conclure.

## Sorties attendues
- Différentiel original/correction/règle/ambiguïté restante.
- Preuves ou références par constat ; hypothèses, exceptions et vérifications non réalisées séparées.
- Brief des décisions ou actions nécessaires pour l'agent rattaché, sans les annoncer déjà exécutées.

## Workflow recommandé
1. Cadrer les inputs : texte, langue, antécédents et intention confirmable ; vérifier les préconditions et autorisations.
2. Identifier les analyses grammaticales possibles.
3. Déterminer les accords et rattachements permis.
4. Proposer une correction minimale ou demander confirmation du sens.
5. Vérifier le livrable par ce critère : une correction nécessitant un choix de sens non établi est signalée et non imposée.
6. Restituer résultat, hypothèses, risques et prochaines actions ; signaler explicitement les blocages.

## Garde-fous
- Une correction nécessitant un choix de sens non établi est signalée et non imposée.
- Ne pas inventer de mesure, d'accord, de preuve ou de source ; distinguer observé, inféré et non testé.
- Ne pas transmettre d'artefact privé ou de donnée personnelle à un service tiers ; minimiser les données sensibles.
- Privilégier les outils libres maintenus et vérifier les versions applicables sans introduire de dépendance EOL.
- Lire la référence dans son contexte : elle éclaire la méthode, elle ne certifie pas ce livrable et n'impose pas de seuil universel.

## Templates copier/coller
### Entrée
```text
Objet : Grammatical Ambiguity Resolution
Inputs : Texte, langue, antécédents et intention confirmable
Version / périmètre autorisé :
Résultat demandé : Différentiel original/correction/règle/ambiguïté restante
Contraintes et inconnues :
```

### Sortie
```text
Résultat : Différentiel original/correction/règle/ambiguïté restante
| Élément examiné | Preuve / source / version | Conclusion | Limite / action |
|---|---|---|---|
Hypothèses :
Risques :
Prochaines actions :
```

## Checklist QA interne
- [ ] Les inputs et les limites d'autorisation sont identifiés.
- [ ] Les trois analyses sont documentées : identifier les analyses grammaticales possibles ; déterminer les accords et rattachements permis ; proposer une correction minimale ou demander confirmation du sens.
- [ ] Le critère d'acceptation est vérifié ou explicitement marqué non vérifié.
- [ ] Aucun résultat d'exécution ou accord humain n'est inventé.

## KPI reliés
- Couverture des éléments requis : éléments documentés / éléments applicables de ce livrable (dénominateur conservé).
- Part des conclusions appuyées par une preuve ou une source datée ; ne pas compter une hypothèse comme preuve.
- Nombre d'écarts au critère suivant restant ouverts : une correction nécessitant un choix de sens non établi est signalée et non imposée.

## Definition of done
- [ ] Différentiel original/correction/règle/ambiguïté restante livré dans le périmètre convenu.
- [ ] Une correction nécessitant un choix de sens non établi est signalée et non imposée.
- [ ] Preuves, inconnues, exceptions et actions restantes sont lisibles ; aucune réussite globale en cas de vérification bloquante manquante.

## Exemples d'usage
**Cas nominal** : à partir de texte, langue, antécédents et intention confirmable, produire différentiel original/correction/règle/ambiguïté restante puis vérifier le critère d'acceptation ci-dessus.

**Cas limite** : une preuve ou autorisation nécessaire manque ; livrer les éléments établis et indiquer précisément ce qui empêche la validation, sans substituer une valeur par défaut.

## Contraintes et références
- Référence officielle consultée le 2026-10-21 : [GOV.UK - Writing to GOV.UK standards](https://www.gov.uk/guidance/content-design). Synthèse originale, sans reproduction du texte source ; vérifier les versions et l'applicabilité au contexte.
- Migration : DEL-20261021-EXCLUSIVE-SKILLS-MIGRATION.

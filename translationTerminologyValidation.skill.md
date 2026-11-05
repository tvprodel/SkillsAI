# Translation Terminology Validation

## Objectif
Valider l'emploi en contexte des équivalents traduits d'un glossaire approuvé.


## Quand l'utiliser (triggers)
- Demande portant sur « Translation Terminology Validation » ou sur le livrable : table terme/équivalent/contexte/statut de validation.
- Besoin de vérifier ce résultat : un nouvel équivalent n'est pas proclamé terme officiel sans approbation de gouvernance.

## Hors périmètre
- Ne pas remplacer les domaines des agents complémentaires : présenter les interfaces et transmettre les besoins à l'agent rattaché (voir table de routage).
- L'exécution système, les modifications de fichiers, les tests et les publications relèvent de l'agent rattaché (voir table de routage) ; cette skill n'accorde aucun outil supplémentaire.
- Ne pas confondre préparation d'un protocole, revue statique et résultat d'une exécution réelle.

## Inputs requis
- Glossaire, langues, domaine et occurrences traduites.
- Périmètre autorisé, version des artefacts, sources accessibles et décisions déjà validées.
- Critères d'acceptation et limites d'action ; marquer les éléments inconnus avant de conclure.

## Sorties attendues
- Table terme/équivalent/contexte/statut de validation.
- Preuves ou références par constat ; hypothèses, exceptions et vérifications non réalisées séparées.
- Brief des décisions ou actions nécessaires pour l'agent rattaché, sans les annoncer déjà exécutées.

## Workflow recommandé
1. Cadrer les inputs : glossaire, langues, domaine et occurrences traduites ; vérifier les préconditions et autorisations.
2. Vérifier sens métier et polysémie.
3. Comparer équivalents au contexte de chaque occurrence.
4. Signaler les cas exigeant décision du responsable terminologique.
5. Vérifier le livrable par ce critère : un nouvel équivalent n'est pas proclamé terme officiel sans approbation de gouvernance.
6. Restituer résultat, hypothèses, risques et prochaines actions ; signaler explicitement les blocages.

## Garde-fous
- Un nouvel équivalent n'est pas proclamé terme officiel sans approbation de gouvernance.
- Ne pas inventer de mesure, d'accord, de preuve ou de source ; distinguer observé, inféré et non testé.
- Ne pas transmettre d'artefact privé ou de donnée personnelle à un service tiers ; minimiser les données sensibles.
- Privilégier les outils libres maintenus et vérifier les versions applicables sans introduire de dépendance EOL.
- Lire la référence dans son contexte : elle éclaire la méthode, elle ne certifie pas ce livrable et n'impose pas de seuil universel.

## Templates copier/coller
### Entrée
```text
Objet : Translation Terminology Validation
Inputs : Glossaire, langues, domaine et occurrences traduites
Version / périmètre autorisé :
Résultat demandé : Table terme/équivalent/contexte/statut de validation
Contraintes et inconnues :
```

### Sortie
```text
Résultat : Table terme/équivalent/contexte/statut de validation
| Élément examiné | Preuve / source / version | Conclusion | Limite / action |
|---|---|---|---|
Hypothèses :
Risques :
Prochaines actions :
```

## Checklist QA interne
- [ ] Les inputs et les limites d'autorisation sont identifiés.
- [ ] Les trois analyses sont documentées : vérifier sens métier et polysémie ; comparer équivalents au contexte de chaque occurrence ; signaler les cas exigeant décision du responsable terminologique.
- [ ] Le critère d'acceptation est vérifié ou explicitement marqué non vérifié.
- [ ] Aucun résultat d'exécution ou accord humain n'est inventé.

## KPI reliés
- Couverture des éléments requis : éléments documentés / éléments applicables de ce livrable (dénominateur conservé).
- Part des conclusions appuyées par une preuve ou une source datée ; ne pas compter une hypothèse comme preuve.
- Nombre d'écarts au critère suivant restant ouverts : un nouvel équivalent n'est pas proclamé terme officiel sans approbation de gouvernance.

## Definition of done
- [ ] Table terme/équivalent/contexte/statut de validation livré dans le périmètre convenu.
- [ ] Un nouvel équivalent n'est pas proclamé terme officiel sans approbation de gouvernance.
- [ ] Preuves, inconnues, exceptions et actions restantes sont lisibles ; aucune réussite globale en cas de vérification bloquante manquante.

## Exemples d'usage
**Cas nominal** : à partir de glossaire, langues, domaine et occurrences traduites, produire table terme/équivalent/contexte/statut de validation puis vérifier le critère d'acceptation ci-dessus.

**Cas limite** : une preuve ou autorisation nécessaire manque ; livrer les éléments établis et indiquer précisément ce qui empêche la validation, sans substituer une valeur par défaut.

## Contraintes et références
- Référence officielle consultée le 2026-10-21 : [W3C SKOS Primer](https://www.w3.org/TR/skos-primer/). Synthèse originale, sans reproduction du texte source ; vérifier les versions et l'applicabilité au contexte.
- Migration : DEL-20261021-EXCLUSIVE-SKILLS-MIGRATION.

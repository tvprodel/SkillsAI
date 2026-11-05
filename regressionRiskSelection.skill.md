# Regression Risk Selection

## Objectif
Choisir la couverture de non-régression selon les comportements affectés par un changement.


## Quand l'utiliser (triggers)
- Demande portant sur « Regression Risk Selection » ou sur le livrable : plan de tests ciblés avec justification et limites.
- Besoin de vérifier ce résultat : l'absence de test sélectionné n'est pas assimilée à une preuve d'absence de régression.

## Hors périmètre
- Ne pas remplacer les domaines des agents complémentaires : présenter les interfaces et transmettre les besoins à l'agent rattaché (voir table de routage).
- L'exécution système, les modifications de fichiers, les tests et les publications relèvent de l'agent rattaché (voir table de routage) ; cette skill n'accorde aucun outil supplémentaire.
- Ne pas confondre préparation d'un protocole, revue statique et résultat d'une exécution réelle.

## Inputs requis
- Diff, dépendances, criticité et tests disponibles.
- Périmètre autorisé, version des artefacts, sources accessibles et décisions déjà validées.
- Critères d'acceptation et limites d'action ; marquer les éléments inconnus avant de conclure.

## Sorties attendues
- Plan de tests ciblés avec justification et limites.
- Preuves ou références par constat ; hypothèses, exceptions et vérifications non réalisées séparées.
- Brief des décisions ou actions nécessaires pour l'agent rattaché, sans les annoncer déjà exécutées.

## Workflow recommandé
1. Cadrer les inputs : diff, dépendances, criticité et tests disponibles ; vérifier les préconditions et autorisations.
2. Cartographier impact et cas critiques.
3. Sélectionner tests et lacunes justifiées.
4. Définir conditions d'escalade vers une suite plus large.
5. Vérifier le livrable par ce critère : l'absence de test sélectionné n'est pas assimilée à une preuve d'absence de régression.
6. Restituer résultat, hypothèses, risques et prochaines actions ; signaler explicitement les blocages.

## Garde-fous
- L'absence de test sélectionné n'est pas assimilée à une preuve d'absence de régression.
- Ne pas inventer de mesure, d'accord, de preuve ou de source ; distinguer observé, inféré et non testé.
- Ne pas transmettre d'artefact privé ou de donnée personnelle à un service tiers ; minimiser les données sensibles.
- Privilégier les outils libres maintenus et vérifier les versions applicables sans introduire de dépendance EOL.
- Lire la référence dans son contexte : elle éclaire la méthode, elle ne certifie pas ce livrable et n'impose pas de seuil universel.

## Templates copier/coller
### Entrée
```text
Objet : Regression Risk Selection
Inputs : Diff, dépendances, criticité et tests disponibles
Version / périmètre autorisé :
Résultat demandé : Plan de tests ciblés avec justification et limites
Contraintes et inconnues :
```

### Sortie
```text
Résultat : Plan de tests ciblés avec justification et limites
| Élément examiné | Preuve / source / version | Conclusion | Limite / action |
|---|---|---|---|
Hypothèses :
Risques :
Prochaines actions :
```

## Checklist QA interne
- [ ] Les inputs et les limites d'autorisation sont identifiés.
- [ ] Les trois analyses sont documentées : cartographier impact et cas critiques ; sélectionner tests et lacunes justifiées ; définir conditions d'escalade vers une suite plus large.
- [ ] Le critère d'acceptation est vérifié ou explicitement marqué non vérifié.
- [ ] Aucun résultat d'exécution ou accord humain n'est inventé.

## KPI reliés
- Couverture des éléments requis : éléments documentés / éléments applicables de ce livrable (dénominateur conservé).
- Part des conclusions appuyées par une preuve ou une source datée ; ne pas compter une hypothèse comme preuve.
- Nombre d'écarts au critère suivant restant ouverts : l'absence de test sélectionné n'est pas assimilée à une preuve d'absence de régression.

## Definition of done
- [ ] Plan de tests ciblés avec justification et limites livré dans le périmètre convenu.
- [ ] L'absence de test sélectionné n'est pas assimilée à une preuve d'absence de régression.
- [ ] Preuves, inconnues, exceptions et actions restantes sont lisibles ; aucune réussite globale en cas de vérification bloquante manquante.

## Exemples d'usage
**Cas nominal** : à partir de diff, dépendances, criticité et tests disponibles, produire plan de tests ciblés avec justification et limites puis vérifier le critère d'acceptation ci-dessus.

**Cas limite** : une preuve ou autorisation nécessaire manque ; livrer les éléments établis et indiquer précisément ce qui empêche la validation, sans substituer une valeur par défaut.

## Contraintes et références
- Référence officielle consultée le 2026-10-21 : [Python unittest](https://docs.python.org/3/library/unittest.html). Synthèse originale, sans reproduction du texte source ; vérifier les versions et l'applicabilité au contexte.
- Migration : DEL-20261021-EXCLUSIVE-SKILLS-MIGRATION.

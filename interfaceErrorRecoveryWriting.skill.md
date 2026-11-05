# Interface Error-Recovery Writing

## Objectif
Rédiger des erreurs d'interface qui expliquent le problème et une reprise réellement possible.


## Quand l'utiliser (triggers)
- Demande portant sur « Interface Error-Recovery Writing » ou sur le livrable : microcopies par erreur avec action et variante courte.
- Besoin de vérifier ce résultat : le message ne demande pas une action impossible et ne révèle pas d'information sensible.

## Hors périmètre
- Ne pas remplacer les domaines des agents complémentaires : présenter les interfaces et transmettre les besoins à l'agent rattaché (voir table de routage).
- L'exécution système, les modifications de fichiers, les tests et les publications relèvent de l'agent rattaché (voir table de routage) ; cette skill n'accorde aucun outil supplémentaire.
- Ne pas confondre préparation d'un protocole, revue statique et résultat d'une exécution réelle.

## Inputs requis
- État d'erreur, cause exposable, actions possibles et contraintes UI.
- Périmètre autorisé, version des artefacts, sources accessibles et décisions déjà validées.
- Critères d'acceptation et limites d'action ; marquer les éléments inconnus avant de conclure.

## Sorties attendues
- Microcopies par erreur avec action et variante courte.
- Preuves ou références par constat ; hypothèses, exceptions et vérifications non réalisées séparées.
- Brief des décisions ou actions nécessaires pour l'agent rattaché, sans les annoncer déjà exécutées.

## Workflow recommandé
1. Cadrer les inputs : état d'erreur, cause exposable, actions possibles et contraintes ui ; vérifier les préconditions et autorisations.
2. Distinguer erreur utilisateur, système et permission.
3. Écrire message et action réparatrice.
4. Vérifier contexte lecteur d'écran et absence de blâme.
5. Vérifier le livrable par ce critère : le message ne demande pas une action impossible et ne révèle pas d'information sensible.
6. Restituer résultat, hypothèses, risques et prochaines actions ; signaler explicitement les blocages.

## Garde-fous
- Le message ne demande pas une action impossible et ne révèle pas d'information sensible.
- Ne pas inventer de mesure, d'accord, de preuve ou de source ; distinguer observé, inféré et non testé.
- Ne pas transmettre d'artefact privé ou de donnée personnelle à un service tiers ; minimiser les données sensibles.
- Privilégier les outils libres maintenus et vérifier les versions applicables sans introduire de dépendance EOL.
- Lire la référence dans son contexte : elle éclaire la méthode, elle ne certifie pas ce livrable et n'impose pas de seuil universel.

## Templates copier/coller
### Entrée
```text
Objet : Interface Error-Recovery Writing
Inputs : État d'erreur, cause exposable, actions possibles et contraintes UI
Version / périmètre autorisé :
Résultat demandé : Microcopies par erreur avec action et variante courte
Contraintes et inconnues :
```

### Sortie
```text
Résultat : Microcopies par erreur avec action et variante courte
| Élément examiné | Preuve / source / version | Conclusion | Limite / action |
|---|---|---|---|
Hypothèses :
Risques :
Prochaines actions :
```

## Checklist QA interne
- [ ] Les inputs et les limites d'autorisation sont identifiés.
- [ ] Les trois analyses sont documentées : distinguer erreur utilisateur, système et permission ; écrire message et action réparatrice ; vérifier contexte lecteur d'écran et absence de blâme.
- [ ] Le critère d'acceptation est vérifié ou explicitement marqué non vérifié.
- [ ] Aucun résultat d'exécution ou accord humain n'est inventé.

## KPI reliés
- Couverture des éléments requis : éléments documentés / éléments applicables de ce livrable (dénominateur conservé).
- Part des conclusions appuyées par une preuve ou une source datée ; ne pas compter une hypothèse comme preuve.
- Nombre d'écarts au critère suivant restant ouverts : le message ne demande pas une action impossible et ne révèle pas d'information sensible.

## Definition of done
- [ ] Microcopies par erreur avec action et variante courte livré dans le périmètre convenu.
- [ ] Le message ne demande pas une action impossible et ne révèle pas d'information sensible.
- [ ] Preuves, inconnues, exceptions et actions restantes sont lisibles ; aucune réussite globale en cas de vérification bloquante manquante.

## Exemples d'usage
**Cas nominal** : à partir de état d'erreur, cause exposable, actions possibles et contraintes ui, produire microcopies par erreur avec action et variante courte puis vérifier le critère d'acceptation ci-dessus.

**Cas limite** : une preuve ou autorisation nécessaire manque ; livrer les éléments établis et indiquer précisément ce qui empêche la validation, sans substituer une valeur par défaut.

## Contraintes et références
- Référence officielle consultée le 2026-10-21 : [W3C COGA - Making Content Usable](https://www.w3.org/TR/coga-usable/). Synthèse originale, sans reproduction du texte source ; vérifier les versions et l'applicabilité au contexte.
- Migration : DEL-20261021-EXCLUSIVE-SKILLS-MIGRATION.

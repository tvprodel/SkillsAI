# AppSec Trust-Boundary Review

## Objectif
Définir les frontières de confiance à examiner dans une application autorisée.


## Quand l'utiliser (triggers)
- Demande portant sur « AppSec Trust-Boundary Review » ou sur le livrable : carte de frontières et grille de contrôles à vérifier.
- Besoin de vérifier ce résultat : toute conclusion distingue contrôle observé, hypothèse et test non exécuté.

## Hors périmètre
- Ne pas remplacer les domaines des agents complémentaires : présenter les interfaces et transmettre les besoins à l'agent rattaché (voir table de routage).
- L'exécution système, les modifications de fichiers, les tests et les publications relèvent de l'agent rattaché (voir table de routage) ; cette skill n'accorde aucun outil supplémentaire.
- Ne pas confondre préparation d'un protocole, revue statique et résultat d'une exécution réelle.

## Inputs requis
- Flux, acteurs, données, entrées non fiables et autorisations.
- Périmètre autorisé, version des artefacts, sources accessibles et décisions déjà validées.
- Critères d'acceptation et limites d'action ; marquer les éléments inconnus avant de conclure.

## Sorties attendues
- Carte de frontières et grille de contrôles à vérifier.
- Preuves ou références par constat ; hypothèses, exceptions et vérifications non réalisées séparées.
- Brief des décisions ou actions nécessaires pour l'agent rattaché, sans les annoncer déjà exécutées.

## Workflow recommandé
1. Cadrer les inputs : flux, acteurs, données, entrées non fiables et autorisations ; vérifier les préconditions et autorisations.
2. Cartographier sources et puits sensibles.
3. Vérifier contrôles attendus aux franchissements.
4. Préparer scénarios défensifs avec données synthétiques.
5. Vérifier le livrable par ce critère : toute conclusion distingue contrôle observé, hypothèse et test non exécuté.
6. Restituer résultat, hypothèses, risques et prochaines actions ; signaler explicitement les blocages.

## Garde-fous
- Toute conclusion distingue contrôle observé, hypothèse et test non exécuté.
- Ne pas inventer de mesure, d'accord, de preuve ou de source ; distinguer observé, inféré et non testé.
- Ne pas transmettre d'artefact privé ou de donnée personnelle à un service tiers ; minimiser les données sensibles.
- Privilégier les outils libres maintenus et vérifier les versions applicables sans introduire de dépendance EOL.
- Lire la référence dans son contexte : elle éclaire la méthode, elle ne certifie pas ce livrable et n'impose pas de seuil universel.

## Templates copier/coller
### Entrée
```text
Objet : AppSec Trust-Boundary Review
Inputs : Flux, acteurs, données, entrées non fiables et autorisations
Version / périmètre autorisé :
Résultat demandé : Carte de frontières et grille de contrôles à vérifier
Contraintes et inconnues :
```

### Sortie
```text
Résultat : Carte de frontières et grille de contrôles à vérifier
| Élément examiné | Preuve / source / version | Conclusion | Limite / action |
|---|---|---|---|
Hypothèses :
Risques :
Prochaines actions :
```

## Checklist QA interne
- [ ] Les inputs et les limites d'autorisation sont identifiés.
- [ ] Les trois analyses sont documentées : cartographier sources et puits sensibles ; vérifier contrôles attendus aux franchissements ; préparer scénarios défensifs avec données synthétiques.
- [ ] Le critère d'acceptation est vérifié ou explicitement marqué non vérifié.
- [ ] Aucun résultat d'exécution ou accord humain n'est inventé.

## KPI reliés
- Couverture des éléments requis : éléments documentés / éléments applicables de ce livrable (dénominateur conservé).
- Part des conclusions appuyées par une preuve ou une source datée ; ne pas compter une hypothèse comme preuve.
- Nombre d'écarts au critère suivant restant ouverts : toute conclusion distingue contrôle observé, hypothèse et test non exécuté.

## Definition of done
- [ ] Carte de frontières et grille de contrôles à vérifier livré dans le périmètre convenu.
- [ ] Toute conclusion distingue contrôle observé, hypothèse et test non exécuté.
- [ ] Preuves, inconnues, exceptions et actions restantes sont lisibles ; aucune réussite globale en cas de vérification bloquante manquante.

## Exemples d'usage
**Cas nominal** : à partir de flux, acteurs, données, entrées non fiables et autorisations, produire carte de frontières et grille de contrôles à vérifier puis vérifier le critère d'acceptation ci-dessus.

**Cas limite** : une preuve ou autorisation nécessaire manque ; livrer les éléments établis et indiquer précisément ce qui empêche la validation, sans substituer une valeur par défaut.

## Contraintes et références
- Référence officielle consultée le 2026-10-21 : [OWASP Input Validation Cheat Sheet](https://cheatsheetseries.owasp.org/cheatsheets/Input_Validation_Cheat_Sheet.html). Synthèse originale, sans reproduction du texte source ; vérifier les versions et l'applicabilité au contexte.
- Migration : DEL-20261021-EXCLUSIVE-SKILLS-MIGRATION.

# Campaign Claim Evidence Review

## Objectif
Vérifier que les affirmations d'un contenu marketing correspondent aux preuves disponibles.


## Quand l'utiliser (triggers)
- Demande portant sur « Campaign Claim Evidence Review » ou sur le livrable : matrice claim/preuve/périmètre/reformulation.
- Besoin de vérifier ce résultat : aucune absence de preuve n'est remplacée par une formule plus persuasive mais toujours trompeuse.

## Hors périmètre
- Ne pas remplacer les domaines des agents complémentaires : présenter les interfaces et transmettre les besoins à l'agent rattaché (voir table de routage).
- L'exécution système, les modifications de fichiers, les tests et les publications relèvent de l'agent rattaché (voir table de routage) ; cette skill n'accorde aucun outil supplémentaire.
- Ne pas confondre préparation d'un protocole, revue statique et résultat d'une exécution réelle.

## Inputs requis
- Texte, données sources, comparaisons et restrictions de l'offre.
- Périmètre autorisé, version des artefacts, sources accessibles et décisions déjà validées.
- Critères d'acceptation et limites d'action ; marquer les éléments inconnus avant de conclure.

## Sorties attendues
- Matrice claim/preuve/périmètre/reformulation.
- Preuves ou références par constat ; hypothèses, exceptions et vérifications non réalisées séparées.
- Brief des décisions ou actions nécessaires pour l'agent rattaché, sans les annoncer déjà exécutées.

## Workflow recommandé
1. Cadrer les inputs : texte, données sources, comparaisons et restrictions de l'offre ; vérifier les préconditions et autorisations.
2. Extraire affirmations vérifiables.
3. Relier chaque affirmation à une preuve et ses limites.
4. Proposer reformulation ou suppression des claims non étayés.
5. Vérifier le livrable par ce critère : aucune absence de preuve n'est remplacée par une formule plus persuasive mais toujours trompeuse.
6. Restituer résultat, hypothèses, risques et prochaines actions ; signaler explicitement les blocages.

## Garde-fous
- Aucune absence de preuve n'est remplacée par une formule plus persuasive mais toujours trompeuse.
- Ne pas inventer de mesure, d'accord, de preuve ou de source ; distinguer observé, inféré et non testé.
- Ne pas transmettre d'artefact privé ou de donnée personnelle à un service tiers ; minimiser les données sensibles.
- Privilégier les outils libres maintenus et vérifier les versions applicables sans introduire de dépendance EOL.
- Lire la référence dans son contexte : elle éclaire la méthode, elle ne certifie pas ce livrable et n'impose pas de seuil universel.

## Templates copier/coller
### Entrée
```text
Objet : Campaign Claim Evidence Review
Inputs : Texte, données sources, comparaisons et restrictions de l'offre
Version / périmètre autorisé :
Résultat demandé : Matrice claim/preuve/périmètre/reformulation
Contraintes et inconnues :
```

### Sortie
```text
Résultat : Matrice claim/preuve/périmètre/reformulation
| Élément examiné | Preuve / source / version | Conclusion | Limite / action |
|---|---|---|---|
Hypothèses :
Risques :
Prochaines actions :
```

## Checklist QA interne
- [ ] Les inputs et les limites d'autorisation sont identifiés.
- [ ] Les trois analyses sont documentées : extraire affirmations vérifiables ; relier chaque affirmation à une preuve et ses limites ; proposer reformulation ou suppression des claims non étayés.
- [ ] Le critère d'acceptation est vérifié ou explicitement marqué non vérifié.
- [ ] Aucun résultat d'exécution ou accord humain n'est inventé.

## KPI reliés
- Couverture des éléments requis : éléments documentés / éléments applicables de ce livrable (dénominateur conservé).
- Part des conclusions appuyées par une preuve ou une source datée ; ne pas compter une hypothèse comme preuve.
- Nombre d'écarts au critère suivant restant ouverts : aucune absence de preuve n'est remplacée par une formule plus persuasive mais toujours trompeuse.

## Definition of done
- [ ] Matrice claim/preuve/périmètre/reformulation livré dans le périmètre convenu.
- [ ] Aucune absence de preuve n'est remplacée par une formule plus persuasive mais toujours trompeuse.
- [ ] Preuves, inconnues, exceptions et actions restantes sont lisibles ; aucune réussite globale en cas de vérification bloquante manquante.

## Exemples d'usage
**Cas nominal** : à partir de texte, données sources, comparaisons et restrictions de l'offre, produire matrice claim/preuve/périmètre/reformulation puis vérifier le critère d'acceptation ci-dessus.

**Cas limite** : une preuve ou autorisation nécessaire manque ; livrer les éléments établis et indiquer précisément ce qui empêche la validation, sans substituer une valeur par défaut.

## Contraintes et références
- Référence officielle consultée le 2026-10-21 : [W3C PROV Overview](https://www.w3.org/TR/prov-overview/). Synthèse originale, sans reproduction du texte source ; vérifier les versions et l'applicabilité au contexte.
- Migration : DEL-20261021-EXCLUSIVE-SKILLS-MIGRATION.

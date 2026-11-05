# Cloud Migration Wave Acceptance

## Objectif
Définir les critères de réception et de retour arrière d'une vague de migration cloud.


## Quand l'utiliser (triggers)
- Demande portant sur « Cloud Migration Wave Acceptance » ou sur le livrable : dossier de vague avec validations et responsables.
- Besoin de vérifier ce résultat : le transfert technique seul ne vaut pas réception fonctionnelle ou cohérence des données.

## Hors périmètre
- Ne pas remplacer les domaines des agents complémentaires : présenter les interfaces et transmettre les besoins à l'agent rattaché (voir table de routage).
- L'exécution système, les modifications de fichiers, les tests et les publications relèvent de l'agent rattaché (voir table de routage) ; cette skill n'accorde aucun outil supplémentaire.
- Ne pas confondre préparation d'un protocole, revue statique et résultat d'une exécution réelle.

## Inputs requis
- Applications, dépendances, données, fenêtre et critères convenus.
- Périmètre autorisé, version des artefacts, sources accessibles et décisions déjà validées.
- Critères d'acceptation et limites d'action ; marquer les éléments inconnus avant de conclure.

## Sorties attendues
- Dossier de vague avec validations et responsables.
- Preuves ou références par constat ; hypothèses, exceptions et vérifications non réalisées séparées.
- Brief des décisions ou actions nécessaires pour l'agent rattaché, sans les annoncer déjà exécutées.

## Workflow recommandé
1. Cadrer les inputs : applications, dépendances, données, fenêtre et critères convenus ; vérifier les préconditions et autorisations.
2. Découper des vagues selon dépendances.
3. Fixer preuves fonctionnelles et de cohérence.
4. Préparer go/no-go et seuils de retour arrière.
5. Vérifier le livrable par ce critère : le transfert technique seul ne vaut pas réception fonctionnelle ou cohérence des données.
6. Restituer résultat, hypothèses, risques et prochaines actions ; signaler explicitement les blocages.

## Garde-fous
- Le transfert technique seul ne vaut pas réception fonctionnelle ou cohérence des données.
- Ne pas inventer de mesure, d'accord, de preuve ou de source ; distinguer observé, inféré et non testé.
- Ne pas transmettre d'artefact privé ou de donnée personnelle à un service tiers ; minimiser les données sensibles.
- Privilégier les outils libres maintenus et vérifier les versions applicables sans introduire de dépendance EOL.
- Lire la référence dans son contexte : elle éclaire la méthode, elle ne certifie pas ce livrable et n'impose pas de seuil universel.

## Templates copier/coller
### Entrée
```text
Objet : Cloud Migration Wave Acceptance
Inputs : Applications, dépendances, données, fenêtre et critères convenus
Version / périmètre autorisé :
Résultat demandé : Dossier de vague avec validations et responsables
Contraintes et inconnues :
```

### Sortie
```text
Résultat : Dossier de vague avec validations et responsables
| Élément examiné | Preuve / source / version | Conclusion | Limite / action |
|---|---|---|---|
Hypothèses :
Risques :
Prochaines actions :
```

## Checklist QA interne
- [ ] Les inputs et les limites d'autorisation sont identifiés.
- [ ] Les trois analyses sont documentées : découper des vagues selon dépendances ; fixer preuves fonctionnelles et de cohérence ; préparer go/no-go et seuils de retour arrière.
- [ ] Le critère d'acceptation est vérifié ou explicitement marqué non vérifié.
- [ ] Aucun résultat d'exécution ou accord humain n'est inventé.

## KPI reliés
- Couverture des éléments requis : éléments documentés / éléments applicables de ce livrable (dénominateur conservé).
- Part des conclusions appuyées par une preuve ou une source datée ; ne pas compter une hypothèse comme preuve.
- Nombre d'écarts au critère suivant restant ouverts : le transfert technique seul ne vaut pas réception fonctionnelle ou cohérence des données.

## Definition of done
- [ ] Dossier de vague avec validations et responsables livré dans le périmètre convenu.
- [ ] Le transfert technique seul ne vaut pas réception fonctionnelle ou cohérence des données.
- [ ] Preuves, inconnues, exceptions et actions restantes sont lisibles ; aucune réussite globale en cas de vérification bloquante manquante.

## Exemples d'usage
**Cas nominal** : à partir de applications, dépendances, données, fenêtre et critères convenus, produire dossier de vague avec validations et responsables puis vérifier le critère d'acceptation ci-dessus.

**Cas limite** : une preuve ou autorisation nécessaire manque ; livrer les éléments établis et indiquer précisément ce qui empêche la validation, sans substituer une valeur par défaut.

## Contraintes et références
- Référence officielle consultée le 2026-10-21 : [Google SRE Workbook](https://sre.google/workbook/table-of-contents/). Synthèse originale, sans reproduction du texte source ; vérifier les versions et l'applicabilité au contexte.
- Migration : DEL-20261021-EXCLUSIVE-SKILLS-MIGRATION.

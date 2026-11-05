# Security Remediation Verification

## Objectif
Vérifier qu'un correctif ferme la cause d'une faiblesse sans masquer l'erreur.


## Quand l'utiliser (triggers)
- Demande portant sur « Security Remediation Verification » ou sur le livrable : rapport avant/après avec preuves et réserves.
- Besoin de vérifier ce résultat : un changement de message d'erreur seul ne vaut pas preuve de correction de la cause.

## Hors périmètre
- Ne pas remplacer les domaines des agents complémentaires : présenter les interfaces et transmettre les besoins à l'agent rattaché (voir table de routage).
- L'exécution système, les modifications de fichiers, les tests et les publications relèvent de l'agent rattaché (voir table de routage) ; cette skill n'accorde aucun outil supplémentaire.
- Ne pas confondre préparation d'un protocole, revue statique et résultat d'une exécution réelle.

## Inputs requis
- Constat autorisé, correctif, reproducer sûr et comportement attendu.
- Périmètre autorisé, version des artefacts, sources accessibles et décisions déjà validées.
- Critères d'acceptation et limites d'action ; marquer les éléments inconnus avant de conclure.

## Sorties attendues
- Rapport avant/après avec preuves et réserves.
- Preuves ou références par constat ; hypothèses, exceptions et vérifications non réalisées séparées.
- Brief des décisions ou actions nécessaires pour l'agent rattaché, sans les annoncer déjà exécutées.

## Workflow recommandé
1. Cadrer les inputs : constat autorisé, correctif, reproducer sûr et comportement attendu ; vérifier les préconditions et autorisations.
2. Relier le correctif au chemin vulnérable.
3. Préparer tests négatifs et comportement légitime.
4. Vérifier régression et limites du périmètre.
5. Vérifier le livrable par ce critère : un changement de message d'erreur seul ne vaut pas preuve de correction de la cause.
6. Restituer résultat, hypothèses, risques et prochaines actions ; signaler explicitement les blocages.

## Garde-fous
- Un changement de message d'erreur seul ne vaut pas preuve de correction de la cause.
- Ne pas inventer de mesure, d'accord, de preuve ou de source ; distinguer observé, inféré et non testé.
- Ne pas transmettre d'artefact privé ou de donnée personnelle à un service tiers ; minimiser les données sensibles.
- Privilégier les outils libres maintenus et vérifier les versions applicables sans introduire de dépendance EOL.
- Lire la référence dans son contexte : elle éclaire la méthode, elle ne certifie pas ce livrable et n'impose pas de seuil universel.

## Templates copier/coller
### Entrée
```text
Objet : Security Remediation Verification
Inputs : Constat autorisé, correctif, reproducer sûr et comportement attendu
Version / périmètre autorisé :
Résultat demandé : Rapport avant/après avec preuves et réserves
Contraintes et inconnues :
```

### Sortie
```text
Résultat : Rapport avant/après avec preuves et réserves
| Élément examiné | Preuve / source / version | Conclusion | Limite / action |
|---|---|---|---|
Hypothèses :
Risques :
Prochaines actions :
```

## Checklist QA interne
- [ ] Les inputs et les limites d'autorisation sont identifiés.
- [ ] Les trois analyses sont documentées : relier le correctif au chemin vulnérable ; préparer tests négatifs et comportement légitime ; vérifier régression et limites du périmètre.
- [ ] Le critère d'acceptation est vérifié ou explicitement marqué non vérifié.
- [ ] Aucun résultat d'exécution ou accord humain n'est inventé.

## KPI reliés
- Couverture des éléments requis : éléments documentés / éléments applicables de ce livrable (dénominateur conservé).
- Part des conclusions appuyées par une preuve ou une source datée ; ne pas compter une hypothèse comme preuve.
- Nombre d'écarts au critère suivant restant ouverts : un changement de message d'erreur seul ne vaut pas preuve de correction de la cause.

## Definition of done
- [ ] Rapport avant/après avec preuves et réserves livré dans le périmètre convenu.
- [ ] Un changement de message d'erreur seul ne vaut pas preuve de correction de la cause.
- [ ] Preuves, inconnues, exceptions et actions restantes sont lisibles ; aucune réussite globale en cas de vérification bloquante manquante.

## Exemples d'usage
**Cas nominal** : à partir de constat autorisé, correctif, reproducer sûr et comportement attendu, produire rapport avant/après avec preuves et réserves puis vérifier le critère d'acceptation ci-dessus.

**Cas limite** : une preuve ou autorisation nécessaire manque ; livrer les éléments établis et indiquer précisément ce qui empêche la validation, sans substituer une valeur par défaut.

## Contraintes et références
- Référence officielle consultée le 2026-10-21 : [OWASP Input Validation Cheat Sheet](https://cheatsheetseries.owasp.org/cheatsheets/Input_Validation_Cheat_Sheet.html). Synthèse originale, sans reproduction du texte source ; vérifier les versions et l'applicabilité au contexte.
- Migration : DEL-20261021-EXCLUSIVE-SKILLS-MIGRATION.

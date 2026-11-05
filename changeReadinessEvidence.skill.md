# Change Readiness Evidence

## Objectif
Consolider les preuves nécessaires à un go/no-go de changement plateforme.


## Quand l'utiliser (triggers)
- Demande portant sur « Change Readiness Evidence » ou sur le livrable : dossier de readiness avec preuves et conditions de rollback.
- Besoin de vérifier ce résultat : un test manquant ou périmé ne se transforme pas en avis favorable implicite.

## Hors périmètre
- Ne pas remplacer les domaines des agents complémentaires : présenter les interfaces et transmettre les besoins à l'agent rattaché (voir table de routage).
- L'exécution système, les modifications de fichiers, les tests et les publications relèvent de l'agent rattaché (voir table de routage) ; cette skill n'accorde aucun outil supplémentaire.
- Ne pas confondre préparation d'un protocole, revue statique et résultat d'une exécution réelle.

## Inputs requis
- Changement/version, tests, dépendances, capacité et rollback.
- Périmètre autorisé, version des artefacts, sources accessibles et décisions déjà validées.
- Critères d'acceptation et limites d'action ; marquer les éléments inconnus avant de conclure.

## Sorties attendues
- Dossier de readiness avec preuves et conditions de rollback.
- Preuves ou références par constat ; hypothèses, exceptions et vérifications non réalisées séparées.
- Brief des décisions ou actions nécessaires pour l'agent rattaché, sans les annoncer déjà exécutées.

## Workflow recommandé
1. Cadrer les inputs : changement/version, tests, dépendances, capacité et rollback ; vérifier les préconditions et autorisations.
2. Relier risques aux preuves attendues.
3. Contrôler fraîcheur et version des résultats.
4. Présenter réserves et décision humaine attendue.
5. Vérifier le livrable par ce critère : un test manquant ou périmé ne se transforme pas en avis favorable implicite.
6. Restituer résultat, hypothèses, risques et prochaines actions ; signaler explicitement les blocages.

## Garde-fous
- Un test manquant ou périmé ne se transforme pas en avis favorable implicite.
- Ne pas inventer de mesure, d'accord, de preuve ou de source ; distinguer observé, inféré et non testé.
- Ne pas transmettre d'artefact privé ou de donnée personnelle à un service tiers ; minimiser les données sensibles.
- Privilégier les outils libres maintenus et vérifier les versions applicables sans introduire de dépendance EOL.
- Lire la référence dans son contexte : elle éclaire la méthode, elle ne certifie pas ce livrable et n'impose pas de seuil universel.

## Templates copier/coller
### Entrée
```text
Objet : Change Readiness Evidence
Inputs : Changement/version, tests, dépendances, capacité et rollback
Version / périmètre autorisé :
Résultat demandé : Dossier de readiness avec preuves et conditions de rollback
Contraintes et inconnues :
```

### Sortie
```text
Résultat : Dossier de readiness avec preuves et conditions de rollback
| Élément examiné | Preuve / source / version | Conclusion | Limite / action |
|---|---|---|---|
Hypothèses :
Risques :
Prochaines actions :
```

## Checklist QA interne
- [ ] Les inputs et les limites d'autorisation sont identifiés.
- [ ] Les trois analyses sont documentées : relier risques aux preuves attendues ; contrôler fraîcheur et version des résultats ; présenter réserves et décision humaine attendue.
- [ ] Le critère d'acceptation est vérifié ou explicitement marqué non vérifié.
- [ ] Aucun résultat d'exécution ou accord humain n'est inventé.

## KPI reliés
- Couverture des éléments requis : éléments documentés / éléments applicables de ce livrable (dénominateur conservé).
- Part des conclusions appuyées par une preuve ou une source datée ; ne pas compter une hypothèse comme preuve.
- Nombre d'écarts au critère suivant restant ouverts : un test manquant ou périmé ne se transforme pas en avis favorable implicite.

## Definition of done
- [ ] Dossier de readiness avec preuves et conditions de rollback livré dans le périmètre convenu.
- [ ] Un test manquant ou périmé ne se transforme pas en avis favorable implicite.
- [ ] Preuves, inconnues, exceptions et actions restantes sont lisibles ; aucune réussite globale en cas de vérification bloquante manquante.

## Exemples d'usage
**Cas nominal** : à partir de changement/version, tests, dépendances, capacité et rollback, produire dossier de readiness avec preuves et conditions de rollback puis vérifier le critère d'acceptation ci-dessus.

**Cas limite** : une preuve ou autorisation nécessaire manque ; livrer les éléments établis et indiquer précisément ce qui empêche la validation, sans substituer une valeur par défaut.

## Contraintes et références
- Référence officielle consultée le 2026-10-21 : [Google SRE Workbook](https://sre.google/workbook/table-of-contents/). Synthèse originale, sans reproduction du texte source ; vérifier les versions et l'applicabilité au contexte.
- Migration : DEL-20261021-EXCLUSIVE-SKILLS-MIGRATION.

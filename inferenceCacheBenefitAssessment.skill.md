# Inference Cache Benefit Assessment

## Objectif
Évaluer si un cache d'inférence apporte un gain sans réutiliser des réponses inadéquates.


## Quand l'utiliser (triggers)
- Demande portant sur « Inference Cache Benefit Assessment » ou sur le livrable : étude de cache avec conditions d'invalidation et mesure du bénéfice.
- Besoin de vérifier ce résultat : aucune donnée d'un utilisateur n'est exposée à un autre via une clé trop large.

## Hors périmètre
- Ne pas remplacer les domaines des agents complémentaires : présenter les interfaces et transmettre les besoins à l'agent rattaché (voir table de routage).
- L'exécution système, les modifications de fichiers, les tests et les publications relèvent de l'agent rattaché (voir table de routage) ; cette skill n'accorde aucun outil supplémentaire.
- Ne pas confondre préparation d'un protocole, revue statique et résultat d'une exécution réelle.

## Inputs requis
- Distribution des requêtes, taux de répétition, fraîcheur et isolation des données.
- Périmètre autorisé, version des artefacts, sources accessibles et décisions déjà validées.
- Critères d'acceptation et limites d'action ; marquer les éléments inconnus avant de conclure.

## Sorties attendues
- Étude de cache avec conditions d'invalidation et mesure du bénéfice.
- Preuves ou références par constat ; hypothèses, exceptions et vérifications non réalisées séparées.
- Brief des décisions ou actions nécessaires pour l'agent rattaché, sans les annoncer déjà exécutées.

## Workflow recommandé
1. Cadrer les inputs : distribution des requêtes, taux de répétition, fraîcheur et isolation des données ; vérifier les préconditions et autorisations.
2. Définir clé, scope utilisateur et invalidation.
3. Estimer hit rate et coût de maintenance.
4. Comparer coût/latence et erreurs de fraîcheur.
5. Vérifier le livrable par ce critère : aucune donnée d'un utilisateur n'est exposée à un autre via une clé trop large.
6. Restituer résultat, hypothèses, risques et prochaines actions ; signaler explicitement les blocages.

## Garde-fous
- Aucune donnée d'un utilisateur n'est exposée à un autre via une clé trop large.
- Ne pas inventer de mesure, d'accord, de preuve ou de source ; distinguer observé, inféré et non testé.
- Ne pas transmettre d'artefact privé ou de donnée personnelle à un service tiers ; minimiser les données sensibles.
- Privilégier les outils libres maintenus et vérifier les versions applicables sans introduire de dépendance EOL.
- Lire la référence dans son contexte : elle éclaire la méthode, elle ne certifie pas ce livrable et n'impose pas de seuil universel.

## Templates copier/coller
### Entrée
```text
Objet : Inference Cache Benefit Assessment
Inputs : Distribution des requêtes, taux de répétition, fraîcheur et isolation des données
Version / périmètre autorisé :
Résultat demandé : Étude de cache avec conditions d'invalidation et mesure du bénéfice
Contraintes et inconnues :
```

### Sortie
```text
Résultat : Étude de cache avec conditions d'invalidation et mesure du bénéfice
| Élément examiné | Preuve / source / version | Conclusion | Limite / action |
|---|---|---|---|
Hypothèses :
Risques :
Prochaines actions :
```

## Checklist QA interne
- [ ] Les inputs et les limites d'autorisation sont identifiés.
- [ ] Les trois analyses sont documentées : définir clé, scope utilisateur et invalidation ; estimer hit rate et coût de maintenance ; comparer coût/latence et erreurs de fraîcheur.
- [ ] Le critère d'acceptation est vérifié ou explicitement marqué non vérifié.
- [ ] Aucun résultat d'exécution ou accord humain n'est inventé.

## KPI reliés
- Couverture des éléments requis : éléments documentés / éléments applicables de ce livrable (dénominateur conservé).
- Part des conclusions appuyées par une preuve ou une source datée ; ne pas compter une hypothèse comme preuve.
- Nombre d'écarts au critère suivant restant ouverts : aucune donnée d'un utilisateur n'est exposée à un autre via une clé trop large.

## Definition of done
- [ ] Étude de cache avec conditions d'invalidation et mesure du bénéfice livré dans le périmètre convenu.
- [ ] Aucune donnée d'un utilisateur n'est exposée à un autre via une clé trop large.
- [ ] Preuves, inconnues, exceptions et actions restantes sont lisibles ; aucune réussite globale en cas de vérification bloquante manquante.

## Exemples d'usage
**Cas nominal** : à partir de distribution des requêtes, taux de répétition, fraîcheur et isolation des données, produire étude de cache avec conditions d'invalidation et mesure du bénéfice puis vérifier le critère d'acceptation ci-dessus.

**Cas limite** : une preuve ou autorisation nécessaire manque ; livrer les éléments établis et indiquer précisément ce qui empêche la validation, sans substituer une valeur par défaut.

## Contraintes et références
- Référence officielle consultée le 2026-10-21 : [Google SRE Workbook](https://sre.google/workbook/table-of-contents/). Synthèse originale, sans reproduction du texte source ; vérifier les versions et l'applicabilité au contexte.
- Migration : DEL-20261021-EXCLUSIVE-SKILLS-MIGRATION.

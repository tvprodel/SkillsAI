# Documentation Example Verification

## Objectif
Vérifier qu'un exemple de documentation interne reste compatible avec le code et son environnement.


## Quand l'utiliser (triggers)
- Demande portant sur « Documentation Example Verification » ou sur le livrable : rapport exemple/prérequis/attendu/observé.
- Besoin de vérifier ce résultat : un exemple non exécuté n'est pas marqué validé à l'exécution.

## Hors périmètre
- Ne pas remplacer les domaines des agents complémentaires : présenter les interfaces et transmettre les besoins à l'agent rattaché (voir table de routage).
- L'exécution système, les modifications de fichiers, les tests et les publications relèvent de l'agent rattaché (voir table de routage) ; cette skill n'accorde aucun outil supplémentaire.
- Ne pas confondre préparation d'un protocole, revue statique et résultat d'une exécution réelle.

## Inputs requis
- Exemple, dépendances déclarées, API cible et résultat attendu.
- Périmètre autorisé, version des artefacts, sources accessibles et décisions déjà validées.
- Critères d'acceptation et limites d'action ; marquer les éléments inconnus avant de conclure.

## Sorties attendues
- Rapport exemple/prérequis/attendu/observé.
- Preuves ou références par constat ; hypothèses, exceptions et vérifications non réalisées séparées.
- Brief des décisions ou actions nécessaires pour l'agent rattaché, sans les annoncer déjà exécutées.

## Workflow recommandé
1. Cadrer les inputs : exemple, dépendances déclarées, api cible et résultat attendu ; vérifier les préconditions et autorisations.
2. Relever hypothèses et prérequis.
3. Préparer exécution isolée ou comparaison de signature.
4. Comparer sortie réelle et texte documentaire.
5. Vérifier le livrable par ce critère : un exemple non exécuté n'est pas marqué validé à l'exécution.
6. Restituer résultat, hypothèses, risques et prochaines actions ; signaler explicitement les blocages.

## Garde-fous
- Un exemple non exécuté n'est pas marqué validé à l'exécution.
- Ne pas inventer de mesure, d'accord, de preuve ou de source ; distinguer observé, inféré et non testé.
- Ne pas transmettre d'artefact privé ou de donnée personnelle à un service tiers ; minimiser les données sensibles.
- Privilégier les outils libres maintenus et vérifier les versions applicables sans introduire de dépendance EOL.
- Lire la référence dans son contexte : elle éclaire la méthode, elle ne certifie pas ce livrable et n'impose pas de seuil universel.

## Templates copier/coller
### Entrée
```text
Objet : Documentation Example Verification
Inputs : Exemple, dépendances déclarées, API cible et résultat attendu
Version / périmètre autorisé :
Résultat demandé : Rapport exemple/prérequis/attendu/observé
Contraintes et inconnues :
```

### Sortie
```text
Résultat : Rapport exemple/prérequis/attendu/observé
| Élément examiné | Preuve / source / version | Conclusion | Limite / action |
|---|---|---|---|
Hypothèses :
Risques :
Prochaines actions :
```

## Checklist QA interne
- [ ] Les inputs et les limites d'autorisation sont identifiés.
- [ ] Les trois analyses sont documentées : relever hypothèses et prérequis ; préparer exécution isolée ou comparaison de signature ; comparer sortie réelle et texte documentaire.
- [ ] Le critère d'acceptation est vérifié ou explicitement marqué non vérifié.
- [ ] Aucun résultat d'exécution ou accord humain n'est inventé.

## KPI reliés
- Couverture des éléments requis : éléments documentés / éléments applicables de ce livrable (dénominateur conservé).
- Part des conclusions appuyées par une preuve ou une source datée ; ne pas compter une hypothèse comme preuve.
- Nombre d'écarts au critère suivant restant ouverts : un exemple non exécuté n'est pas marqué validé à l'exécution.

## Definition of done
- [ ] Rapport exemple/prérequis/attendu/observé livré dans le périmètre convenu.
- [ ] Un exemple non exécuté n'est pas marqué validé à l'exécution.
- [ ] Preuves, inconnues, exceptions et actions restantes sont lisibles ; aucune réussite globale en cas de vérification bloquante manquante.

## Exemples d'usage
**Cas nominal** : à partir de exemple, dépendances déclarées, api cible et résultat attendu, produire rapport exemple/prérequis/attendu/observé puis vérifier le critère d'acceptation ci-dessus.

**Cas limite** : une preuve ou autorisation nécessaire manque ; livrer les éléments établis et indiquer précisément ce qui empêche la validation, sans substituer une valeur par défaut.

## Contraintes et références
- Référence officielle consultée le 2026-10-21 : [Python unittest](https://docs.python.org/3/library/unittest.html). Synthèse originale, sans reproduction du texte source ; vérifier les versions et l'applicabilité au contexte.
- Migration : DEL-20261021-EXCLUSIVE-SKILLS-MIGRATION.

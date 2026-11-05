# Cloud Failure-Domain Placement

## Objectif
Répartir les composants cloud selon les pannes qu'ils doivent tolérer.


## Quand l'utiliser (triggers)
- Demande portant sur « Cloud Failure-Domain Placement » ou sur le livrable : plan de placement avec domaines de panne et hypothèses.
- Besoin de vérifier ce résultat : la redondance n'est pas revendiquée pour des copies partageant une dépendance unique non tolérée.

## Hors périmètre
- Ne pas remplacer les domaines des agents complémentaires : présenter les interfaces et transmettre les besoins à l'agent rattaché (voir table de routage).
- L'exécution système, les modifications de fichiers, les tests et les publications relèvent de l'agent rattaché (voir table de routage) ; cette skill n'accorde aucun outil supplémentaire.
- Ne pas confondre préparation d'un protocole, revue statique et résultat d'une exécution réelle.

## Inputs requis
- Objectifs de disponibilité, services, régions/zones et dépendances.
- Périmètre autorisé, version des artefacts, sources accessibles et décisions déjà validées.
- Critères d'acceptation et limites d'action ; marquer les éléments inconnus avant de conclure.

## Sorties attendues
- Plan de placement avec domaines de panne et hypothèses.
- Preuves ou références par constat ; hypothèses, exceptions et vérifications non réalisées séparées.
- Brief des décisions ou actions nécessaires pour l'agent rattaché, sans les annoncer déjà exécutées.

## Workflow recommandé
1. Cadrer les inputs : objectifs de disponibilité, services, régions/zones et dépendances ; vérifier les préconditions et autorisations.
2. Identifier défaillances communes.
3. Comparer placements et contraintes de réplication.
4. Définir comportement dégradé et preuve de bascule.
5. Vérifier le livrable par ce critère : la redondance n'est pas revendiquée pour des copies partageant une dépendance unique non tolérée.
6. Restituer résultat, hypothèses, risques et prochaines actions ; signaler explicitement les blocages.

## Garde-fous
- La redondance n'est pas revendiquée pour des copies partageant une dépendance unique non tolérée.
- Ne pas inventer de mesure, d'accord, de preuve ou de source ; distinguer observé, inféré et non testé.
- Ne pas transmettre d'artefact privé ou de donnée personnelle à un service tiers ; minimiser les données sensibles.
- Privilégier les outils libres maintenus et vérifier les versions applicables sans introduire de dépendance EOL.
- Lire la référence dans son contexte : elle éclaire la méthode, elle ne certifie pas ce livrable et n'impose pas de seuil universel.

## Templates copier/coller
### Entrée
```text
Objet : Cloud Failure-Domain Placement
Inputs : Objectifs de disponibilité, services, régions/zones et dépendances
Version / périmètre autorisé :
Résultat demandé : Plan de placement avec domaines de panne et hypothèses
Contraintes et inconnues :
```

### Sortie
```text
Résultat : Plan de placement avec domaines de panne et hypothèses
| Élément examiné | Preuve / source / version | Conclusion | Limite / action |
|---|---|---|---|
Hypothèses :
Risques :
Prochaines actions :
```

## Checklist QA interne
- [ ] Les inputs et les limites d'autorisation sont identifiés.
- [ ] Les trois analyses sont documentées : identifier défaillances communes ; comparer placements et contraintes de réplication ; définir comportement dégradé et preuve de bascule.
- [ ] Le critère d'acceptation est vérifié ou explicitement marqué non vérifié.
- [ ] Aucun résultat d'exécution ou accord humain n'est inventé.

## KPI reliés
- Couverture des éléments requis : éléments documentés / éléments applicables de ce livrable (dénominateur conservé).
- Part des conclusions appuyées par une preuve ou une source datée ; ne pas compter une hypothèse comme preuve.
- Nombre d'écarts au critère suivant restant ouverts : la redondance n'est pas revendiquée pour des copies partageant une dépendance unique non tolérée.

## Definition of done
- [ ] Plan de placement avec domaines de panne et hypothèses livré dans le périmètre convenu.
- [ ] La redondance n'est pas revendiquée pour des copies partageant une dépendance unique non tolérée.
- [ ] Preuves, inconnues, exceptions et actions restantes sont lisibles ; aucune réussite globale en cas de vérification bloquante manquante.

## Exemples d'usage
**Cas nominal** : à partir de objectifs de disponibilité, services, régions/zones et dépendances, produire plan de placement avec domaines de panne et hypothèses puis vérifier le critère d'acceptation ci-dessus.

**Cas limite** : une preuve ou autorisation nécessaire manque ; livrer les éléments établis et indiquer précisément ce qui empêche la validation, sans substituer une valeur par défaut.

## Contraintes et références
- Référence officielle consultée le 2026-10-21 : [Google SRE Workbook](https://sre.google/workbook/table-of-contents/). Synthèse originale, sans reproduction du texte source ; vérifier les versions et l'applicabilité au contexte.
- Migration : DEL-20261021-EXCLUSIVE-SKILLS-MIGRATION.

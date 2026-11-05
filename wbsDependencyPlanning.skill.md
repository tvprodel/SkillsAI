# WBS and Dependency Planning

## Objectif
Décomposer un livrable projet en lots vérifiables et ordonner leurs dépendances réelles.


## Quand l'utiliser (triggers)
- Demande portant sur « WBS and Dependency Planning » ou sur le livrable : wbs avec réseau de dépendances et jalons de réception.
- Besoin de vérifier ce résultat : tout lot a un résultat vérifiable et aucune dépendance n'est déduite du seul ordre d'affichage.

## Hors périmètre
- Ne pas remplacer les domaines des agents complémentaires : présenter les interfaces et transmettre les besoins à l'agent rattaché (voir table de routage).
- L'exécution système, les modifications de fichiers, les tests et les publications relèvent de l'agent rattaché (voir table de routage) ; cette skill n'accorde aucun outil supplémentaire.
- Ne pas confondre préparation d'un protocole, revue statique et résultat d'une exécution réelle.

## Inputs requis
- Livrables, limites de périmètre, capacités et contraintes externes.
- Périmètre autorisé, version des artefacts, sources accessibles et décisions déjà validées.
- Critères d'acceptation et limites d'action ; marquer les éléments inconnus avant de conclure.

## Sorties attendues
- WBS avec réseau de dépendances et jalons de réception.
- Preuves ou références par constat ; hypothèses, exceptions et vérifications non réalisées séparées.
- Brief des décisions ou actions nécessaires pour l'agent rattaché, sans les annoncer déjà exécutées.

## Workflow recommandé
1. Cadrer les inputs : livrables, limites de périmètre, capacités et contraintes externes ; vérifier les préconditions et autorisations.
2. Définir les résultats de chaque lot.
3. Identifier dépendances et interfaces.
4. Vérifier absence de cycle et déterminer chemin critique si les durées sont disponibles.
5. Vérifier le livrable par ce critère : tout lot a un résultat vérifiable et aucune dépendance n'est déduite du seul ordre d'affichage.
6. Restituer résultat, hypothèses, risques et prochaines actions ; signaler explicitement les blocages.

## Garde-fous
- Tout lot a un résultat vérifiable et aucune dépendance n'est déduite du seul ordre d'affichage.
- Ne pas inventer de mesure, d'accord, de preuve ou de source ; distinguer observé, inféré et non testé.
- Ne pas transmettre d'artefact privé ou de donnée personnelle à un service tiers ; minimiser les données sensibles.
- Privilégier les outils libres maintenus et vérifier les versions applicables sans introduire de dépendance EOL.
- Lire la référence dans son contexte : elle éclaire la méthode, elle ne certifie pas ce livrable et n'impose pas de seuil universel.

## Templates copier/coller
### Entrée
```text
Objet : WBS and Dependency Planning
Inputs : Livrables, limites de périmètre, capacités et contraintes externes
Version / périmètre autorisé :
Résultat demandé : WBS avec réseau de dépendances et jalons de réception
Contraintes et inconnues :
```

### Sortie
```text
Résultat : WBS avec réseau de dépendances et jalons de réception
| Élément examiné | Preuve / source / version | Conclusion | Limite / action |
|---|---|---|---|
Hypothèses :
Risques :
Prochaines actions :
```

## Checklist QA interne
- [ ] Les inputs et les limites d'autorisation sont identifiés.
- [ ] Les trois analyses sont documentées : définir les résultats de chaque lot ; identifier dépendances et interfaces ; vérifier absence de cycle et déterminer chemin critique si les durées sont disponibles.
- [ ] Le critère d'acceptation est vérifié ou explicitement marqué non vérifié.
- [ ] Aucun résultat d'exécution ou accord humain n'est inventé.

## KPI reliés
- Couverture des éléments requis : éléments documentés / éléments applicables de ce livrable (dénominateur conservé).
- Part des conclusions appuyées par une preuve ou une source datée ; ne pas compter une hypothèse comme preuve.
- Nombre d'écarts au critère suivant restant ouverts : tout lot a un résultat vérifiable et aucune dépendance n'est déduite du seul ordre d'affichage.

## Definition of done
- [ ] WBS avec réseau de dépendances et jalons de réception livré dans le périmètre convenu.
- [ ] Tout lot a un résultat vérifiable et aucune dépendance n'est déduite du seul ordre d'affichage.
- [ ] Preuves, inconnues, exceptions et actions restantes sont lisibles ; aucune réussite globale en cas de vérification bloquante manquante.

## Exemples d'usage
**Cas nominal** : à partir de livrables, limites de périmètre, capacités et contraintes externes, produire wbs avec réseau de dépendances et jalons de réception puis vérifier le critère d'acceptation ci-dessus.

**Cas limite** : une preuve ou autorisation nécessaire manque ; livrer les éléments établis et indiquer précisément ce qui empêche la validation, sans substituer une valeur par défaut.

## Contraintes et références
- Référence officielle consultée le 2026-10-21 : [W3C PROV Overview](https://www.w3.org/TR/prov-overview/). Synthèse originale, sans reproduction du texte source ; vérifier les versions et l'applicabilité au contexte.
- Migration : DEL-20261021-EXCLUSIVE-SKILLS-MIGRATION.

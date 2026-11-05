# Message Delivery Recovery Design

## Objectif
Définir comment un échange asynchrone gère doublons, erreurs et reprises.


## Quand l'utiliser (triggers)
- Demande portant sur « Message Delivery Recovery Design » ou sur le livrable : protocole de livraison avec scénarios de panne.
- Besoin de vérifier ce résultat : la livraison exactement une fois n'est pas promise sans garanties de bout en bout démontrées.

## Hors périmètre
- Ne pas remplacer les domaines des agents complémentaires : présenter les interfaces et transmettre les besoins à l'agent rattaché (voir table de routage).
- L'exécution système, les modifications de fichiers, les tests et les publications relèvent de l'agent rattaché (voir table de routage) ; cette skill n'accorde aucun outil supplémentaire.
- Ne pas confondre préparation d'un protocole, revue statique et résultat d'une exécution réelle.

## Inputs requis
- Producteur, consommateur, clés métier, ordering et garanties réelles.
- Périmètre autorisé, version des artefacts, sources accessibles et décisions déjà validées.
- Critères d'acceptation et limites d'action ; marquer les éléments inconnus avant de conclure.

## Sorties attendues
- Protocole de livraison avec scénarios de panne.
- Preuves ou références par constat ; hypothèses, exceptions et vérifications non réalisées séparées.
- Brief des décisions ou actions nécessaires pour l'agent rattaché, sans les annoncer déjà exécutées.

## Workflow recommandé
1. Cadrer les inputs : producteur, consommateur, clés métier, ordering et garanties réelles ; vérifier les préconditions et autorisations.
2. Choisir acquittement et déduplication.
3. Définir retry borné et file d'échec.
4. Préparer reprise et mesure des pertes/doublons.
5. Vérifier le livrable par ce critère : la livraison exactement une fois n'est pas promise sans garanties de bout en bout démontrées.
6. Restituer résultat, hypothèses, risques et prochaines actions ; signaler explicitement les blocages.

## Garde-fous
- La livraison exactement une fois n'est pas promise sans garanties de bout en bout démontrées.
- Ne pas inventer de mesure, d'accord, de preuve ou de source ; distinguer observé, inféré et non testé.
- Ne pas transmettre d'artefact privé ou de donnée personnelle à un service tiers ; minimiser les données sensibles.
- Privilégier les outils libres maintenus et vérifier les versions applicables sans introduire de dépendance EOL.
- Lire la référence dans son contexte : elle éclaire la méthode, elle ne certifie pas ce livrable et n'impose pas de seuil universel.

## Templates copier/coller
### Entrée
```text
Objet : Message Delivery Recovery Design
Inputs : Producteur, consommateur, clés métier, ordering et garanties réelles
Version / périmètre autorisé :
Résultat demandé : Protocole de livraison avec scénarios de panne
Contraintes et inconnues :
```

### Sortie
```text
Résultat : Protocole de livraison avec scénarios de panne
| Élément examiné | Preuve / source / version | Conclusion | Limite / action |
|---|---|---|---|
Hypothèses :
Risques :
Prochaines actions :
```

## Checklist QA interne
- [ ] Les inputs et les limites d'autorisation sont identifiés.
- [ ] Les trois analyses sont documentées : choisir acquittement et déduplication ; définir retry borné et file d'échec ; préparer reprise et mesure des pertes/doublons.
- [ ] Le critère d'acceptation est vérifié ou explicitement marqué non vérifié.
- [ ] Aucun résultat d'exécution ou accord humain n'est inventé.

## KPI reliés
- Couverture des éléments requis : éléments documentés / éléments applicables de ce livrable (dénominateur conservé).
- Part des conclusions appuyées par une preuve ou une source datée ; ne pas compter une hypothèse comme preuve.
- Nombre d'écarts au critère suivant restant ouverts : la livraison exactement une fois n'est pas promise sans garanties de bout en bout démontrées.

## Definition of done
- [ ] Protocole de livraison avec scénarios de panne livré dans le périmètre convenu.
- [ ] La livraison exactement une fois n'est pas promise sans garanties de bout en bout démontrées.
- [ ] Preuves, inconnues, exceptions et actions restantes sont lisibles ; aucune réussite globale en cas de vérification bloquante manquante.

## Exemples d'usage
**Cas nominal** : à partir de producteur, consommateur, clés métier, ordering et garanties réelles, produire protocole de livraison avec scénarios de panne puis vérifier le critère d'acceptation ci-dessus.

**Cas limite** : une preuve ou autorisation nécessaire manque ; livrer les éléments établis et indiquer précisément ce qui empêche la validation, sans substituer une valeur par défaut.

## Contraintes et références
- Référence officielle consultée le 2026-10-21 : [Google SRE Workbook](https://sre.google/workbook/table-of-contents/). Synthèse originale, sans reproduction du texte source ; vérifier les versions et l'applicabilité au contexte.
- Migration : DEL-20261021-EXCLUSIVE-SKILLS-MIGRATION.

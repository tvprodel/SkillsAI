# Software Boundary ADR

## Objectif
Documenter une décision de frontière logicielle entre modules ou services.


## Quand l'utiliser (triggers)
- Demande portant sur « Software Boundary ADR » ou sur le livrable : adr de frontière avec alternatives et conséquences.
- Besoin de vérifier ce résultat : chaque responsabilité possède un owner et la décision explique les alternatives rejetées.

## Hors périmètre
- Ne pas remplacer les domaines des agents complémentaires : présenter les interfaces et transmettre les besoins à l'agent rattaché (voir table de routage).
- L'exécution système, les modifications de fichiers, les tests et les publications relèvent de l'agent rattaché (voir table de routage) ; cette skill n'accorde aucun outil supplémentaire.
- Ne pas confondre préparation d'un protocole, revue statique et résultat d'une exécution réelle.

## Inputs requis
- Responsabilités métier, flux, contraintes et alternatives.
- Périmètre autorisé, version des artefacts, sources accessibles et décisions déjà validées.
- Critères d'acceptation et limites d'action ; marquer les éléments inconnus avant de conclure.

## Sorties attendues
- ADR de frontière avec alternatives et conséquences.
- Preuves ou références par constat ; hypothèses, exceptions et vérifications non réalisées séparées.
- Brief des décisions ou actions nécessaires pour l'agent rattaché, sans les annoncer déjà exécutées.

## Workflow recommandé
1. Cadrer les inputs : responsabilités métier, flux, contraintes et alternatives ; vérifier les préconditions et autorisations.
2. Définir invariants et dépendances autorisées.
3. Comparer modularité, couplage et coût opérationnel.
4. Tracer décision et conditions de réexamen.
5. Vérifier le livrable par ce critère : chaque responsabilité possède un owner et la décision explique les alternatives rejetées.
6. Restituer résultat, hypothèses, risques et prochaines actions ; signaler explicitement les blocages.

## Garde-fous
- Chaque responsabilité possède un owner et la décision explique les alternatives rejetées.
- Ne pas inventer de mesure, d'accord, de preuve ou de source ; distinguer observé, inféré et non testé.
- Ne pas transmettre d'artefact privé ou de donnée personnelle à un service tiers ; minimiser les données sensibles.
- Privilégier les outils libres maintenus et vérifier les versions applicables sans introduire de dépendance EOL.
- Lire la référence dans son contexte : elle éclaire la méthode, elle ne certifie pas ce livrable et n'impose pas de seuil universel.

## Templates copier/coller
### Entrée
```text
Objet : Software Boundary ADR
Inputs : Responsabilités métier, flux, contraintes et alternatives
Version / périmètre autorisé :
Résultat demandé : ADR de frontière avec alternatives et conséquences
Contraintes et inconnues :
```

### Sortie
```text
Résultat : ADR de frontière avec alternatives et conséquences
| Élément examiné | Preuve / source / version | Conclusion | Limite / action |
|---|---|---|---|
Hypothèses :
Risques :
Prochaines actions :
```

## Checklist QA interne
- [ ] Les inputs et les limites d'autorisation sont identifiés.
- [ ] Les trois analyses sont documentées : définir invariants et dépendances autorisées ; comparer modularité, couplage et coût opérationnel ; tracer décision et conditions de réexamen.
- [ ] Le critère d'acceptation est vérifié ou explicitement marqué non vérifié.
- [ ] Aucun résultat d'exécution ou accord humain n'est inventé.

## KPI reliés
- Couverture des éléments requis : éléments documentés / éléments applicables de ce livrable (dénominateur conservé).
- Part des conclusions appuyées par une preuve ou une source datée ; ne pas compter une hypothèse comme preuve.
- Nombre d'écarts au critère suivant restant ouverts : chaque responsabilité possède un owner et la décision explique les alternatives rejetées.

## Definition of done
- [ ] ADR de frontière avec alternatives et conséquences livré dans le périmètre convenu.
- [ ] Chaque responsabilité possède un owner et la décision explique les alternatives rejetées.
- [ ] Preuves, inconnues, exceptions et actions restantes sont lisibles ; aucune réussite globale en cas de vérification bloquante manquante.

## Exemples d'usage
**Cas nominal** : à partir de responsabilités métier, flux, contraintes et alternatives, produire adr de frontière avec alternatives et conséquences puis vérifier le critère d'acceptation ci-dessus.

**Cas limite** : une preuve ou autorisation nécessaire manque ; livrer les éléments établis et indiquer précisément ce qui empêche la validation, sans substituer une valeur par défaut.

## Contraintes et références
- Référence officielle consultée le 2026-10-21 : [OpenAPI Specification](https://spec.openapis.org/oas/latest.html). Synthèse originale, sans reproduction du texte source ; vérifier les versions et l'applicabilité au contexte.
- Migration : DEL-20261021-EXCLUSIVE-SKILLS-MIGRATION.

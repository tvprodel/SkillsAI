# Code Architecture Trace Documentation

## Objectif
Relier une description d'architecture interne aux symboles et appels qui la réalisent.


## Quand l'utiliser (triggers)
- Demande portant sur « Code Architecture Trace Documentation » ou sur le livrable : diagramme interne et liens vers les symboles sources.
- Besoin de vérifier ce résultat : chaque relation décrite repose sur une dépendance ou un appel observable.

## Hors périmètre
- Ne pas remplacer les domaines des agents complémentaires : présenter les interfaces et transmettre les besoins à l'agent rattaché (voir table de routage).
- L'exécution système, les modifications de fichiers, les tests et les publications relèvent de l'agent rattaché (voir table de routage) ; cette skill n'accorde aucun outil supplémentaire.
- Ne pas confondre préparation d'un protocole, revue statique et résultat d'une exécution réelle.

## Inputs requis
- Code, points d'entrée, composants et décisions d'architecture.
- Périmètre autorisé, version des artefacts, sources accessibles et décisions déjà validées.
- Critères d'acceptation et limites d'action ; marquer les éléments inconnus avant de conclure.

## Sorties attendues
- Diagramme interne et liens vers les symboles sources.
- Preuves ou références par constat ; hypothèses, exceptions et vérifications non réalisées séparées.
- Brief des décisions ou actions nécessaires pour l'agent rattaché, sans les annoncer déjà exécutées.

## Workflow recommandé
1. Cadrer les inputs : code, points d'entrée, composants et décisions d'architecture ; vérifier les préconditions et autorisations.
2. Tracer un parcours représentatif.
3. Associer chaque étape aux symboles observés.
4. Dessiner relations et indiquer zones non vérifiées.
5. Vérifier le livrable par ce critère : chaque relation décrite repose sur une dépendance ou un appel observable.
6. Restituer résultat, hypothèses, risques et prochaines actions ; signaler explicitement les blocages.

## Garde-fous
- Chaque relation décrite repose sur une dépendance ou un appel observable.
- Ne pas inventer de mesure, d'accord, de preuve ou de source ; distinguer observé, inféré et non testé.
- Ne pas transmettre d'artefact privé ou de donnée personnelle à un service tiers ; minimiser les données sensibles.
- Privilégier les outils libres maintenus et vérifier les versions applicables sans introduire de dépendance EOL.
- Lire la référence dans son contexte : elle éclaire la méthode, elle ne certifie pas ce livrable et n'impose pas de seuil universel.

## Templates copier/coller
### Entrée
```text
Objet : Code Architecture Trace Documentation
Inputs : Code, points d'entrée, composants et décisions d'architecture
Version / périmètre autorisé :
Résultat demandé : Diagramme interne et liens vers les symboles sources
Contraintes et inconnues :
```

### Sortie
```text
Résultat : Diagramme interne et liens vers les symboles sources
| Élément examiné | Preuve / source / version | Conclusion | Limite / action |
|---|---|---|---|
Hypothèses :
Risques :
Prochaines actions :
```

## Checklist QA interne
- [ ] Les inputs et les limites d'autorisation sont identifiés.
- [ ] Les trois analyses sont documentées : tracer un parcours représentatif ; associer chaque étape aux symboles observés ; dessiner relations et indiquer zones non vérifiées.
- [ ] Le critère d'acceptation est vérifié ou explicitement marqué non vérifié.
- [ ] Aucun résultat d'exécution ou accord humain n'est inventé.

## KPI reliés
- Couverture des éléments requis : éléments documentés / éléments applicables de ce livrable (dénominateur conservé).
- Part des conclusions appuyées par une preuve ou une source datée ; ne pas compter une hypothèse comme preuve.
- Nombre d'écarts au critère suivant restant ouverts : chaque relation décrite repose sur une dépendance ou un appel observable.

## Definition of done
- [ ] Diagramme interne et liens vers les symboles sources livré dans le périmètre convenu.
- [ ] Chaque relation décrite repose sur une dépendance ou un appel observable.
- [ ] Preuves, inconnues, exceptions et actions restantes sont lisibles ; aucune réussite globale en cas de vérification bloquante manquante.

## Exemples d'usage
**Cas nominal** : à partir de code, points d'entrée, composants et décisions d'architecture, produire diagramme interne et liens vers les symboles sources puis vérifier le critère d'acceptation ci-dessus.

**Cas limite** : une preuve ou autorisation nécessaire manque ; livrer les éléments établis et indiquer précisément ce qui empêche la validation, sans substituer une valeur par défaut.

## Contraintes et références
- Référence officielle consultée le 2026-10-21 : [Python ast](https://docs.python.org/3/library/ast.html). Synthèse originale, sans reproduction du texte source ; vérifier les versions et l'applicabilité au contexte.
- Migration : DEL-20261021-EXCLUSIVE-SKILLS-MIGRATION.

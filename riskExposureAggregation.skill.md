# Risk Exposure Aggregation

## Objectif
Évaluer l'exposition consolidée d'un projet sans additionner abusivement des risques corrélés.


## Quand l'utiliser (triggers)
- Demande portant sur « Risk Exposure Aggregation » ou sur le livrable : vue consolidée des expositions et hypothèses de dépendance.
- Besoin de vérifier ce résultat : chaque agrégat est relié à une méthode explicite et à ses limites.

## Hors périmètre
- Ne pas remplacer les domaines des agents complémentaires : présenter les interfaces et transmettre les besoins à l'agent rattaché (voir table de routage).
- L'exécution système, les modifications de fichiers, les tests et les publications relèvent de l'agent rattaché (voir table de routage) ; cette skill n'accorde aucun outil supplémentaire.
- Ne pas confondre préparation d'un protocole, revue statique et résultat d'une exécution réelle.

## Inputs requis
- Registre coté, échelles de probabilité/impact, dépendances et tolérance.
- Périmètre autorisé, version des artefacts, sources accessibles et décisions déjà validées.
- Critères d'acceptation et limites d'action ; marquer les éléments inconnus avant de conclure.

## Sorties attendues
- Vue consolidée des expositions et hypothèses de dépendance.
- Preuves ou références par constat ; hypothèses, exceptions et vérifications non réalisées séparées.
- Brief des décisions ou actions nécessaires pour l'agent rattaché, sans les annoncer déjà exécutées.

## Workflow recommandé
1. Cadrer les inputs : registre coté, échelles de probabilité/impact, dépendances et tolérance ; vérifier les préconditions et autorisations.
2. Repérer causes communes et corrélations.
3. Comparer scénarios indépendants et cumulés.
4. Documenter sensibilité des conclusions aux estimations.
5. Vérifier le livrable par ce critère : chaque agrégat est relié à une méthode explicite et à ses limites.
6. Restituer résultat, hypothèses, risques et prochaines actions ; signaler explicitement les blocages.

## Garde-fous
- Chaque agrégat est relié à une méthode explicite et à ses limites.
- Ne pas inventer de mesure, d'accord, de preuve ou de source ; distinguer observé, inféré et non testé.
- Ne pas transmettre d'artefact privé ou de donnée personnelle à un service tiers ; minimiser les données sensibles.
- Privilégier les outils libres maintenus et vérifier les versions applicables sans introduire de dépendance EOL.
- Lire la référence dans son contexte : elle éclaire la méthode, elle ne certifie pas ce livrable et n'impose pas de seuil universel.

## Templates copier/coller
### Entrée
```text
Objet : Risk Exposure Aggregation
Inputs : Registre coté, échelles de probabilité/impact, dépendances et tolérance
Version / périmètre autorisé :
Résultat demandé : Vue consolidée des expositions et hypothèses de dépendance
Contraintes et inconnues :
```

### Sortie
```text
Résultat : Vue consolidée des expositions et hypothèses de dépendance
| Élément examiné | Preuve / source / version | Conclusion | Limite / action |
|---|---|---|---|
Hypothèses :
Risques :
Prochaines actions :
```

## Checklist QA interne
- [ ] Les inputs et les limites d'autorisation sont identifiés.
- [ ] Les trois analyses sont documentées : repérer causes communes et corrélations ; comparer scénarios indépendants et cumulés ; documenter sensibilité des conclusions aux estimations.
- [ ] Le critère d'acceptation est vérifié ou explicitement marqué non vérifié.
- [ ] Aucun résultat d'exécution ou accord humain n'est inventé.

## KPI reliés
- Couverture des éléments requis : éléments documentés / éléments applicables de ce livrable (dénominateur conservé).
- Part des conclusions appuyées par une preuve ou une source datée ; ne pas compter une hypothèse comme preuve.
- Nombre d'écarts au critère suivant restant ouverts : chaque agrégat est relié à une méthode explicite et à ses limites.

## Definition of done
- [ ] Vue consolidée des expositions et hypothèses de dépendance livré dans le périmètre convenu.
- [ ] Chaque agrégat est relié à une méthode explicite et à ses limites.
- [ ] Preuves, inconnues, exceptions et actions restantes sont lisibles ; aucune réussite globale en cas de vérification bloquante manquante.

## Exemples d'usage
**Cas nominal** : à partir de registre coté, échelles de probabilité/impact, dépendances et tolérance, produire vue consolidée des expositions et hypothèses de dépendance puis vérifier le critère d'acceptation ci-dessus.

**Cas limite** : une preuve ou autorisation nécessaire manque ; livrer les éléments établis et indiquer précisément ce qui empêche la validation, sans substituer une valeur par défaut.

## Contraintes et références
- Référence officielle consultée le 2026-10-21 : [NIST AI Risk Management Framework](https://www.nist.gov/itl/ai-risk-management-framework). Synthèse originale, sans reproduction du texte source ; vérifier les versions et l'applicabilité au contexte.
- Migration : DEL-20261021-EXCLUSIVE-SKILLS-MIGRATION.

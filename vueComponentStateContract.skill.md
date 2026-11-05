# Vue Component State Contract

## Objectif
Définir l'interface et le cycle de vie d'un composant Vue sans état implicite incontrôlé.


## Quand l'utiliser (triggers)
- Demande portant sur « Vue Component State Contract » ou sur le livrable : composant ou contrat props/events avec scénarios de transition.
- Besoin de vérifier ce résultat : les props ne sont pas mutées et chaque transition observable possède un résultat attendu.

## Hors périmètre
- Ne pas remplacer les domaines des agents complémentaires : présenter les interfaces et transmettre les besoins à l'agent rattaché (voir table de routage).
- L'exécution système, les modifications de fichiers, les tests et les publications relèvent de l'agent rattaché (voir table de routage) ; cette skill n'accorde aucun outil supplémentaire.
- Ne pas confondre préparation d'un protocole, revue statique et résultat d'une exécution réelle.

## Inputs requis
- Props, événements, états UI, contraintes d'accessibilité et composition.
- Périmètre autorisé, version des artefacts, sources accessibles et décisions déjà validées.
- Critères d'acceptation et limites d'action ; marquer les éléments inconnus avant de conclure.

## Sorties attendues
- Composant ou contrat props/events avec scénarios de transition.
- Preuves ou références par constat ; hypothèses, exceptions et vérifications non réalisées séparées.
- Brief des décisions ou actions nécessaires pour l'agent rattaché, sans les annoncer déjà exécutées.

## Workflow recommandé
1. Cadrer les inputs : props, événements, états ui, contraintes d'accessibilité et composition ; vérifier les préconditions et autorisations.
2. Distinguer état possédé et dérivé.
3. Définir mutations et émissions.
4. Prévoir chargement, erreur, destruction et réutilisation.
5. Vérifier le livrable par ce critère : les props ne sont pas mutées et chaque transition observable possède un résultat attendu.
6. Restituer résultat, hypothèses, risques et prochaines actions ; signaler explicitement les blocages.

## Garde-fous
- Les props ne sont pas mutées et chaque transition observable possède un résultat attendu.
- Ne pas inventer de mesure, d'accord, de preuve ou de source ; distinguer observé, inféré et non testé.
- Ne pas transmettre d'artefact privé ou de donnée personnelle à un service tiers ; minimiser les données sensibles.
- Privilégier les outils libres maintenus et vérifier les versions applicables sans introduire de dépendance EOL.
- Lire la référence dans son contexte : elle éclaire la méthode, elle ne certifie pas ce livrable et n'impose pas de seuil universel.

## Templates copier/coller
### Entrée
```text
Objet : Vue Component State Contract
Inputs : Props, événements, états UI, contraintes d'accessibilité et composition
Version / périmètre autorisé :
Résultat demandé : Composant ou contrat props/events avec scénarios de transition
Contraintes et inconnues :
```

### Sortie
```text
Résultat : Composant ou contrat props/events avec scénarios de transition
| Élément examiné | Preuve / source / version | Conclusion | Limite / action |
|---|---|---|---|
Hypothèses :
Risques :
Prochaines actions :
```

## Checklist QA interne
- [ ] Les inputs et les limites d'autorisation sont identifiés.
- [ ] Les trois analyses sont documentées : distinguer état possédé et dérivé ; définir mutations et émissions ; prévoir chargement, erreur, destruction et réutilisation.
- [ ] Le critère d'acceptation est vérifié ou explicitement marqué non vérifié.
- [ ] Aucun résultat d'exécution ou accord humain n'est inventé.

## KPI reliés
- Couverture des éléments requis : éléments documentés / éléments applicables de ce livrable (dénominateur conservé).
- Part des conclusions appuyées par une preuve ou une source datée ; ne pas compter une hypothèse comme preuve.
- Nombre d'écarts au critère suivant restant ouverts : les props ne sont pas mutées et chaque transition observable possède un résultat attendu.

## Definition of done
- [ ] Composant ou contrat props/events avec scénarios de transition livré dans le périmètre convenu.
- [ ] Les props ne sont pas mutées et chaque transition observable possède un résultat attendu.
- [ ] Preuves, inconnues, exceptions et actions restantes sont lisibles ; aucune réussite globale en cas de vérification bloquante manquante.

## Exemples d'usage
**Cas nominal** : à partir de props, événements, états ui, contraintes d'accessibilité et composition, produire composant ou contrat props/events avec scénarios de transition puis vérifier le critère d'acceptation ci-dessus.

**Cas limite** : une preuve ou autorisation nécessaire manque ; livrer les éléments établis et indiquer précisément ce qui empêche la validation, sans substituer une valeur par défaut.

## Contraintes et références
- Référence officielle consultée le 2026-10-21 : [Vue - Component Registration](https://vuejs.org/guide/components/registration.html). Synthèse originale, sans reproduction du texte source ; vérifier les versions et l'applicabilité au contexte.
- Migration : DEL-20261021-EXCLUSIVE-SKILLS-MIGRATION.

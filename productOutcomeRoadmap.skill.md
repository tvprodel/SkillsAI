# Product Outcome Roadmap

## Objectif
Relier les initiatives produit à des résultats mesurables sans transformer la roadmap en planning détaillé.


## Quand l'utiliser (triggers)
- Demande portant sur « Product Outcome Roadmap » ou sur le livrable : roadmap orientée résultats avec métriques et décisions de revue.
- Besoin de vérifier ce résultat : chaque initiative possède un résultat attendu et une règle de réévaluation.

## Hors périmètre
- Ne pas remplacer les domaines des agents complémentaires : présenter les interfaces et transmettre les besoins à l'agent rattaché (voir table de routage).
- L'exécution système, les modifications de fichiers, les tests et les publications relèvent de l'agent rattaché (voir table de routage) ; cette skill n'accorde aucun outil supplémentaire.
- Ne pas confondre préparation d'un protocole, revue statique et résultat d'une exécution réelle.

## Inputs requis
- Vision, objectifs, indicateurs, contraintes de capacité et dépendances.
- Périmètre autorisé, version des artefacts, sources accessibles et décisions déjà validées.
- Critères d'acceptation et limites d'action ; marquer les éléments inconnus avant de conclure.

## Sorties attendues
- Roadmap orientée résultats avec métriques et décisions de revue.
- Preuves ou références par constat ; hypothèses, exceptions et vérifications non réalisées séparées.
- Brief des décisions ou actions nécessaires pour l'agent rattaché, sans les annoncer déjà exécutées.

## Workflow recommandé
1. Cadrer les inputs : vision, objectifs, indicateurs, contraintes de capacité et dépendances ; vérifier les préconditions et autorisations.
2. Définir résultats cibles et signaux de succès.
3. Relier les initiatives à ces résultats.
4. Prévoir revues apprendre/poursuivre/arrêter.
5. Vérifier le livrable par ce critère : chaque initiative possède un résultat attendu et une règle de réévaluation.
6. Restituer résultat, hypothèses, risques et prochaines actions ; signaler explicitement les blocages.

## Garde-fous
- Chaque initiative possède un résultat attendu et une règle de réévaluation.
- Ne pas inventer de mesure, d'accord, de preuve ou de source ; distinguer observé, inféré et non testé.
- Ne pas transmettre d'artefact privé ou de donnée personnelle à un service tiers ; minimiser les données sensibles.
- Privilégier les outils libres maintenus et vérifier les versions applicables sans introduire de dépendance EOL.
- Lire la référence dans son contexte : elle éclaire la méthode, elle ne certifie pas ce livrable et n'impose pas de seuil universel.

## Templates copier/coller
### Entrée
```text
Objet : Product Outcome Roadmap
Inputs : Vision, objectifs, indicateurs, contraintes de capacité et dépendances
Version / périmètre autorisé :
Résultat demandé : Roadmap orientée résultats avec métriques et décisions de revue
Contraintes et inconnues :
```

### Sortie
```text
Résultat : Roadmap orientée résultats avec métriques et décisions de revue
| Élément examiné | Preuve / source / version | Conclusion | Limite / action |
|---|---|---|---|
Hypothèses :
Risques :
Prochaines actions :
```

## Checklist QA interne
- [ ] Les inputs et les limites d'autorisation sont identifiés.
- [ ] Les trois analyses sont documentées : définir résultats cibles et signaux de succès ; relier les initiatives à ces résultats ; prévoir revues apprendre/poursuivre/arrêter.
- [ ] Le critère d'acceptation est vérifié ou explicitement marqué non vérifié.
- [ ] Aucun résultat d'exécution ou accord humain n'est inventé.

## KPI reliés
- Couverture des éléments requis : éléments documentés / éléments applicables de ce livrable (dénominateur conservé).
- Part des conclusions appuyées par une preuve ou une source datée ; ne pas compter une hypothèse comme preuve.
- Nombre d'écarts au critère suivant restant ouverts : chaque initiative possède un résultat attendu et une règle de réévaluation.

## Definition of done
- [ ] Roadmap orientée résultats avec métriques et décisions de revue livré dans le périmètre convenu.
- [ ] Chaque initiative possède un résultat attendu et une règle de réévaluation.
- [ ] Preuves, inconnues, exceptions et actions restantes sont lisibles ; aucune réussite globale en cas de vérification bloquante manquante.

## Exemples d'usage
**Cas nominal** : à partir de vision, objectifs, indicateurs, contraintes de capacité et dépendances, produire roadmap orientée résultats avec métriques et décisions de revue puis vérifier le critère d'acceptation ci-dessus.

**Cas limite** : une preuve ou autorisation nécessaire manque ; livrer les éléments établis et indiquer précisément ce qui empêche la validation, sans substituer une valeur par défaut.

## Contraintes et références
- Référence officielle consultée le 2026-10-21 : [W3C PROV Overview](https://www.w3.org/TR/prov-overview/). Synthèse originale, sans reproduction du texte source ; vérifier les versions et l'applicabilité au contexte.
- Migration : DEL-20261021-EXCLUSIVE-SKILLS-MIGRATION.

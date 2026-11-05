# AI Ethical Impact Decision Record

## Objectif
Formaliser un arbitrage éthique sur un usage IA et les responsabilités humaines associées.


## Quand l'utiliser (triggers)
- Demande portant sur « AI Ethical Impact Decision Record » ou sur le livrable : fiche d'arbitrage éthique versionnée avec réserves.
- Besoin de vérifier ce résultat : les intérêts affectés et les hypothèses de jugement sont visibles sans certification implicite.

## Hors périmètre
- Ne pas remplacer les domaines des agents complémentaires : présenter les interfaces et transmettre les besoins à l'agent rattaché (voir table de routage).
- L'exécution système, les modifications de fichiers, les tests et les publications relèvent de l'agent rattaché (voir table de routage) ; cette skill n'accorde aucun outil supplémentaire.
- Ne pas confondre préparation d'un protocole, revue statique et résultat d'une exécution réelle.

## Inputs requis
- Usage, parties affectées, impacts possibles et options.
- Périmètre autorisé, version des artefacts, sources accessibles et décisions déjà validées.
- Critères d'acceptation et limites d'action ; marquer les éléments inconnus avant de conclure.

## Sorties attendues
- Fiche d'arbitrage éthique versionnée avec réserves.
- Preuves ou références par constat ; hypothèses, exceptions et vérifications non réalisées séparées.
- Brief des décisions ou actions nécessaires pour l'agent rattaché, sans les annoncer déjà exécutées.

## Workflow recommandé
1. Cadrer les inputs : usage, parties affectées, impacts possibles et options ; vérifier les préconditions et autorisations.
2. Décrire bénéfices et préjudices sans les confondre.
3. Comparer alternatives et mesures de réduction.
4. Documenter désaccords et décision de réexamen.
5. Vérifier le livrable par ce critère : les intérêts affectés et les hypothèses de jugement sont visibles sans certification implicite.
6. Restituer résultat, hypothèses, risques et prochaines actions ; signaler explicitement les blocages.

## Garde-fous
- Les intérêts affectés et les hypothèses de jugement sont visibles sans certification implicite.
- Ne pas inventer de mesure, d'accord, de preuve ou de source ; distinguer observé, inféré et non testé.
- Ne pas transmettre d'artefact privé ou de donnée personnelle à un service tiers ; minimiser les données sensibles.
- Privilégier les outils libres maintenus et vérifier les versions applicables sans introduire de dépendance EOL.
- Lire la référence dans son contexte : elle éclaire la méthode, elle ne certifie pas ce livrable et n'impose pas de seuil universel.

## Templates copier/coller
### Entrée
```text
Objet : AI Ethical Impact Decision Record
Inputs : Usage, parties affectées, impacts possibles et options
Version / périmètre autorisé :
Résultat demandé : Fiche d'arbitrage éthique versionnée avec réserves
Contraintes et inconnues :
```

### Sortie
```text
Résultat : Fiche d'arbitrage éthique versionnée avec réserves
| Élément examiné | Preuve / source / version | Conclusion | Limite / action |
|---|---|---|---|
Hypothèses :
Risques :
Prochaines actions :
```

## Checklist QA interne
- [ ] Les inputs et les limites d'autorisation sont identifiés.
- [ ] Les trois analyses sont documentées : décrire bénéfices et préjudices sans les confondre ; comparer alternatives et mesures de réduction ; documenter désaccords et décision de réexamen.
- [ ] Le critère d'acceptation est vérifié ou explicitement marqué non vérifié.
- [ ] Aucun résultat d'exécution ou accord humain n'est inventé.

## KPI reliés
- Couverture des éléments requis : éléments documentés / éléments applicables de ce livrable (dénominateur conservé).
- Part des conclusions appuyées par une preuve ou une source datée ; ne pas compter une hypothèse comme preuve.
- Nombre d'écarts au critère suivant restant ouverts : les intérêts affectés et les hypothèses de jugement sont visibles sans certification implicite.

## Definition of done
- [ ] Fiche d'arbitrage éthique versionnée avec réserves livré dans le périmètre convenu.
- [ ] Les intérêts affectés et les hypothèses de jugement sont visibles sans certification implicite.
- [ ] Preuves, inconnues, exceptions et actions restantes sont lisibles ; aucune réussite globale en cas de vérification bloquante manquante.

## Exemples d'usage
**Cas nominal** : à partir de usage, parties affectées, impacts possibles et options, produire fiche d'arbitrage éthique versionnée avec réserves puis vérifier le critère d'acceptation ci-dessus.

**Cas limite** : une preuve ou autorisation nécessaire manque ; livrer les éléments établis et indiquer précisément ce qui empêche la validation, sans substituer une valeur par défaut.

## Contraintes et références
- Référence officielle consultée le 2026-10-21 : [NIST AI Risk Management Framework](https://www.nist.gov/itl/ai-risk-management-framework). Synthèse originale, sans reproduction du texte source ; vérifier les versions et l'applicabilité au contexte.
- Migration : DEL-20261021-EXCLUSIVE-SKILLS-MIGRATION.

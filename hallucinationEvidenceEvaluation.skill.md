# Hallucination Evidence Evaluation

## Objectif
Mesurer l'appui factuel des réponses d'un agent sur un jeu de référence vérifiable.


## Quand l'utiliser (triggers)
- Demande portant sur « Hallucination Evidence Evaluation » ou sur le livrable : grille d'affirmations avec verdict justifié et taux documentés.
- Besoin de vérifier ce résultat : le dénominateur, les cas ambigus et les sources du benchmark sont conservés.

## Hors périmètre
- Ne pas remplacer les domaines des agents complémentaires : présenter les interfaces et transmettre les besoins à l'agent rattaché (voir table de routage).
- L'exécution système, les modifications de fichiers, les tests et les publications relèvent de l'agent rattaché (voir table de routage) ; cette skill n'accorde aucun outil supplémentaire.
- Ne pas confondre préparation d'un protocole, revue statique et résultat d'une exécution réelle.

## Inputs requis
- Questions, sources autorisées, réponses et critères de vérité.
- Périmètre autorisé, version des artefacts, sources accessibles et décisions déjà validées.
- Critères d'acceptation et limites d'action ; marquer les éléments inconnus avant de conclure.

## Sorties attendues
- Grille d'affirmations avec verdict justifié et taux documentés.
- Preuves ou références par constat ; hypothèses, exceptions et vérifications non réalisées séparées.
- Brief des décisions ou actions nécessaires pour l'agent rattaché, sans les annoncer déjà exécutées.

## Workflow recommandé
1. Cadrer les inputs : questions, sources autorisées, réponses et critères de vérité ; vérifier les préconditions et autorisations.
2. Décomposer les réponses en affirmations.
3. Relier chaque affirmation à une source ou abstention attendue.
4. Distinguer erreur, absence de preuve et contradiction.
5. Vérifier le livrable par ce critère : le dénominateur, les cas ambigus et les sources du benchmark sont conservés.
6. Restituer résultat, hypothèses, risques et prochaines actions ; signaler explicitement les blocages.

## Garde-fous
- Le dénominateur, les cas ambigus et les sources du benchmark sont conservés.
- Ne pas inventer de mesure, d'accord, de preuve ou de source ; distinguer observé, inféré et non testé.
- Ne pas transmettre d'artefact privé ou de donnée personnelle à un service tiers ; minimiser les données sensibles.
- Privilégier les outils libres maintenus et vérifier les versions applicables sans introduire de dépendance EOL.
- Lire la référence dans son contexte : elle éclaire la méthode, elle ne certifie pas ce livrable et n'impose pas de seuil universel.

## Templates copier/coller
### Entrée
```text
Objet : Hallucination Evidence Evaluation
Inputs : Questions, sources autorisées, réponses et critères de vérité
Version / périmètre autorisé :
Résultat demandé : Grille d'affirmations avec verdict justifié et taux documentés
Contraintes et inconnues :
```

### Sortie
```text
Résultat : Grille d'affirmations avec verdict justifié et taux documentés
| Élément examiné | Preuve / source / version | Conclusion | Limite / action |
|---|---|---|---|
Hypothèses :
Risques :
Prochaines actions :
```

## Checklist QA interne
- [ ] Les inputs et les limites d'autorisation sont identifiés.
- [ ] Les trois analyses sont documentées : décomposer les réponses en affirmations ; relier chaque affirmation à une source ou abstention attendue ; distinguer erreur, absence de preuve et contradiction.
- [ ] Le critère d'acceptation est vérifié ou explicitement marqué non vérifié.
- [ ] Aucun résultat d'exécution ou accord humain n'est inventé.

## KPI reliés
- Couverture des éléments requis : éléments documentés / éléments applicables de ce livrable (dénominateur conservé).
- Part des conclusions appuyées par une preuve ou une source datée ; ne pas compter une hypothèse comme preuve.
- Nombre d'écarts au critère suivant restant ouverts : le dénominateur, les cas ambigus et les sources du benchmark sont conservés.

## Definition of done
- [ ] Grille d'affirmations avec verdict justifié et taux documentés livré dans le périmètre convenu.
- [ ] Le dénominateur, les cas ambigus et les sources du benchmark sont conservés.
- [ ] Preuves, inconnues, exceptions et actions restantes sont lisibles ; aucune réussite globale en cas de vérification bloquante manquante.

## Exemples d'usage
**Cas nominal** : à partir de questions, sources autorisées, réponses et critères de vérité, produire grille d'affirmations avec verdict justifié et taux documentés puis vérifier le critère d'acceptation ci-dessus.

**Cas limite** : une preuve ou autorisation nécessaire manque ; livrer les éléments établis et indiquer précisément ce qui empêche la validation, sans substituer une valeur par défaut.

## Contraintes et références
- Référence officielle consultée le 2026-10-21 : [W3C PROV Overview](https://www.w3.org/TR/prov-overview/). Synthèse originale, sans reproduction du texte source ; vérifier les versions et l'applicabilité au contexte.
- Migration : DEL-20261021-EXCLUSIVE-SKILLS-MIGRATION.

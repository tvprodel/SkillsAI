# Onboarding Instruction Design

## Objectif
Rédiger les consignes d'un parcours de prise en main sans surcharge de mémoire.


## Quand l'utiliser (triggers)
- Demande portant sur « Onboarding Instruction Design » ou sur le livrable : jeu de consignes par étape avec critères de compréhension.
- Besoin de vérifier ce résultat : chaque étape explique l'action attendue et le résultat observable sans promesse cachée.

## Hors périmètre
- Ne pas remplacer les domaines des agents complémentaires : présenter les interfaces et transmettre les besoins à l'agent rattaché (voir table de routage).
- L'exécution système, les modifications de fichiers, les tests et les publications relèvent de l'agent rattaché (voir table de routage) ; cette skill n'accorde aucun outil supplémentaire.
- Ne pas confondre préparation d'un protocole, revue statique et résultat d'une exécution réelle.

## Inputs requis
- Étapes, prérequis, objectif utilisateur et erreurs fréquentes.
- Périmètre autorisé, version des artefacts, sources accessibles et décisions déjà validées.
- Critères d'acceptation et limites d'action ; marquer les éléments inconnus avant de conclure.

## Sorties attendues
- Jeu de consignes par étape avec critères de compréhension.
- Preuves ou références par constat ; hypothèses, exceptions et vérifications non réalisées séparées.
- Brief des décisions ou actions nécessaires pour l'agent rattaché, sans les annoncer déjà exécutées.

## Workflow recommandé
1. Cadrer les inputs : étapes, prérequis, objectif utilisateur et erreurs fréquentes ; vérifier les préconditions et autorisations.
2. Placer la consigne au point d'action.
3. Réduire implicite et informations à retenir.
4. Prévoir aide, reprise et état vide.
5. Vérifier le livrable par ce critère : chaque étape explique l'action attendue et le résultat observable sans promesse cachée.
6. Restituer résultat, hypothèses, risques et prochaines actions ; signaler explicitement les blocages.

## Garde-fous
- Chaque étape explique l'action attendue et le résultat observable sans promesse cachée.
- Ne pas inventer de mesure, d'accord, de preuve ou de source ; distinguer observé, inféré et non testé.
- Ne pas transmettre d'artefact privé ou de donnée personnelle à un service tiers ; minimiser les données sensibles.
- Privilégier les outils libres maintenus et vérifier les versions applicables sans introduire de dépendance EOL.
- Lire la référence dans son contexte : elle éclaire la méthode, elle ne certifie pas ce livrable et n'impose pas de seuil universel.

## Templates copier/coller
### Entrée
```text
Objet : Onboarding Instruction Design
Inputs : Étapes, prérequis, objectif utilisateur et erreurs fréquentes
Version / périmètre autorisé :
Résultat demandé : Jeu de consignes par étape avec critères de compréhension
Contraintes et inconnues :
```

### Sortie
```text
Résultat : Jeu de consignes par étape avec critères de compréhension
| Élément examiné | Preuve / source / version | Conclusion | Limite / action |
|---|---|---|---|
Hypothèses :
Risques :
Prochaines actions :
```

## Checklist QA interne
- [ ] Les inputs et les limites d'autorisation sont identifiés.
- [ ] Les trois analyses sont documentées : placer la consigne au point d'action ; réduire implicite et informations à retenir ; prévoir aide, reprise et état vide.
- [ ] Le critère d'acceptation est vérifié ou explicitement marqué non vérifié.
- [ ] Aucun résultat d'exécution ou accord humain n'est inventé.

## KPI reliés
- Couverture des éléments requis : éléments documentés / éléments applicables de ce livrable (dénominateur conservé).
- Part des conclusions appuyées par une preuve ou une source datée ; ne pas compter une hypothèse comme preuve.
- Nombre d'écarts au critère suivant restant ouverts : chaque étape explique l'action attendue et le résultat observable sans promesse cachée.

## Definition of done
- [ ] Jeu de consignes par étape avec critères de compréhension livré dans le périmètre convenu.
- [ ] Chaque étape explique l'action attendue et le résultat observable sans promesse cachée.
- [ ] Preuves, inconnues, exceptions et actions restantes sont lisibles ; aucune réussite globale en cas de vérification bloquante manquante.

## Exemples d'usage
**Cas nominal** : à partir de étapes, prérequis, objectif utilisateur et erreurs fréquentes, produire jeu de consignes par étape avec critères de compréhension puis vérifier le critère d'acceptation ci-dessus.

**Cas limite** : une preuve ou autorisation nécessaire manque ; livrer les éléments établis et indiquer précisément ce qui empêche la validation, sans substituer une valeur par défaut.

## Contraintes et références
- Référence officielle consultée le 2026-10-21 : [W3C COGA - Making Content Usable](https://www.w3.org/TR/coga-usable/). Synthèse originale, sans reproduction du texte source ; vérifier les versions et l'applicabilité au contexte.
- Migration : DEL-20261021-EXCLUSIVE-SKILLS-MIGRATION.

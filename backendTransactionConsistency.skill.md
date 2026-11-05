# Backend Transaction Consistency

## Objectif
Préserver les invariants métier lors d'écritures backend concurrentes ou interrompues.


## Quand l'utiliser (triggers)
- Demande portant sur « Backend Transaction Consistency » ou sur le livrable : plan ou implémentation transactionnelle avec scénarios de concurrence.
- Besoin de vérifier ce résultat : une répétition de requête ne crée pas un second effet métier non prévu.

## Hors périmètre
- Ne pas remplacer les domaines des agents complémentaires : présenter les interfaces et transmettre les besoins à l'agent rattaché (voir table de routage).
- L'exécution système, les modifications de fichiers, les tests et les publications relèvent de l'agent rattaché (voir table de routage) ; cette skill n'accorde aucun outil supplémentaire.
- Ne pas confondre préparation d'un protocole, revue statique et résultat d'une exécution réelle.

## Inputs requis
- Invariants, données modifiées, frontières transactionnelles et I/O externes.
- Périmètre autorisé, version des artefacts, sources accessibles et décisions déjà validées.
- Critères d'acceptation et limites d'action ; marquer les éléments inconnus avant de conclure.

## Sorties attendues
- Plan ou implémentation transactionnelle avec scénarios de concurrence.
- Preuves ou références par constat ; hypothèses, exceptions et vérifications non réalisées séparées.
- Brief des décisions ou actions nécessaires pour l'agent rattaché, sans les annoncer déjà exécutées.

## Workflow recommandé
1. Cadrer les inputs : invariants, données modifiées, frontières transactionnelles et i/o externes ; vérifier les préconditions et autorisations.
2. Définir atomique et non atomique.
3. Choisir contrôle de concurrence et stratégie d'effet externe.
4. Tester rollback et double soumission.
5. Vérifier le livrable par ce critère : une répétition de requête ne crée pas un second effet métier non prévu.
6. Restituer résultat, hypothèses, risques et prochaines actions ; signaler explicitement les blocages.

## Garde-fous
- Une répétition de requête ne crée pas un second effet métier non prévu.
- Ne pas inventer de mesure, d'accord, de preuve ou de source ; distinguer observé, inféré et non testé.
- Ne pas transmettre d'artefact privé ou de donnée personnelle à un service tiers ; minimiser les données sensibles.
- Privilégier les outils libres maintenus et vérifier les versions applicables sans introduire de dépendance EOL.
- Lire la référence dans son contexte : elle éclaire la méthode, elle ne certifie pas ce livrable et n'impose pas de seuil universel.

## Templates copier/coller
### Entrée
```text
Objet : Backend Transaction Consistency
Inputs : Invariants, données modifiées, frontières transactionnelles et I/O externes
Version / périmètre autorisé :
Résultat demandé : Plan ou implémentation transactionnelle avec scénarios de concurrence
Contraintes et inconnues :
```

### Sortie
```text
Résultat : Plan ou implémentation transactionnelle avec scénarios de concurrence
| Élément examiné | Preuve / source / version | Conclusion | Limite / action |
|---|---|---|---|
Hypothèses :
Risques :
Prochaines actions :
```

## Checklist QA interne
- [ ] Les inputs et les limites d'autorisation sont identifiés.
- [ ] Les trois analyses sont documentées : définir atomique et non atomique ; choisir contrôle de concurrence et stratégie d'effet externe ; tester rollback et double soumission.
- [ ] Le critère d'acceptation est vérifié ou explicitement marqué non vérifié.
- [ ] Aucun résultat d'exécution ou accord humain n'est inventé.

## KPI reliés
- Couverture des éléments requis : éléments documentés / éléments applicables de ce livrable (dénominateur conservé).
- Part des conclusions appuyées par une preuve ou une source datée ; ne pas compter une hypothèse comme preuve.
- Nombre d'écarts au critère suivant restant ouverts : une répétition de requête ne crée pas un second effet métier non prévu.

## Definition of done
- [ ] Plan ou implémentation transactionnelle avec scénarios de concurrence livré dans le périmètre convenu.
- [ ] Une répétition de requête ne crée pas un second effet métier non prévu.
- [ ] Preuves, inconnues, exceptions et actions restantes sont lisibles ; aucune réussite globale en cas de vérification bloquante manquante.

## Exemples d'usage
**Cas nominal** : à partir de invariants, données modifiées, frontières transactionnelles et i/o externes, produire plan ou implémentation transactionnelle avec scénarios de concurrence puis vérifier le critère d'acceptation ci-dessus.

**Cas limite** : une preuve ou autorisation nécessaire manque ; livrer les éléments établis et indiquer précisément ce qui empêche la validation, sans substituer une valeur par défaut.

## Contraintes et références
- Référence officielle consultée le 2026-10-21 : [OpenAPI Specification](https://spec.openapis.org/oas/latest.html). Synthèse originale, sans reproduction du texte source ; vérifier les versions et l'applicabilité au contexte.
- Migration : DEL-20261021-EXCLUSIVE-SKILLS-MIGRATION.

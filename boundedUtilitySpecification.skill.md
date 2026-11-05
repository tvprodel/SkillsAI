# Bounded Utility Specification

## Objectif
Définir une petite tâche technique généraliste assez précisément pour une exécution sûre par l'agent de coordination.


## Quand l'utiliser (triggers)
- Demande portant sur « Bounded Utility Specification » ou sur le livrable : brief d'utilitaire borné avec exemples et conditions d'arrêt.
- Besoin de vérifier ce résultat : aucune action système n'est exécutée par le worker et les transformations destructives exigent accord.

## Hors périmètre
- Usage de secours uniquement après qualification qu'aucun agent spécialisé ne couvre la demande.
- Ne pas traiter de fond juridique, médical, financier, sécurité ou développement spécialisé ; remettre le brief pour routage.
- L'exécution système, les modifications de fichiers, les tests et les publications relèvent de l'agent rattaché (voir table de routage) ; cette skill n'accorde aucun outil supplémentaire.
- Ne pas confondre préparation d'un protocole, revue statique et résultat d'une exécution réelle.

## Inputs requis
- Entrées, sorties, formats, volume et opérations autorisées.
- Périmètre autorisé, version des artefacts, sources accessibles et décisions déjà validées.
- Critères d'acceptation et limites d'action ; marquer les éléments inconnus avant de conclure.

## Sorties attendues
- Brief d'utilitaire borné avec exemples et conditions d'arrêt.
- Preuves ou références par constat ; hypothèses, exceptions et vérifications non réalisées séparées.
- Brief des décisions ou actions nécessaires pour l'agent rattaché, sans les annoncer déjà exécutées.

## Workflow recommandé
1. Cadrer les inputs : entrées, sorties, formats, volume et opérations autorisées ; vérifier les préconditions et autorisations.
2. Limiter le périmètre et exclure les cas spécialisés.
3. Définir erreurs et invariants.
4. Fournir cas d'acceptation avant production du script.
5. Vérifier le livrable par ce critère : aucune action système n'est exécutée par le worker et les transformations destructives exigent accord.
6. Restituer résultat, hypothèses, risques et prochaines actions ; signaler explicitement les blocages.

## Garde-fous
- Aucune action système n'est exécutée par le Worker et les transformations destructives exigent accord.
- Ne pas inventer de mesure, d'accord, de preuve ou de source ; distinguer observé, inféré et non testé.
- Ne pas transmettre d'artefact privé ou de donnée personnelle à un service tiers ; minimiser les données sensibles.
- Privilégier les outils libres maintenus et vérifier les versions applicables sans introduire de dépendance EOL.
- Lire la référence dans son contexte : elle éclaire la méthode, elle ne certifie pas ce livrable et n'impose pas de seuil universel.

## Templates copier/coller
### Entrée
```text
Objet : Bounded Utility Specification
Inputs : Entrées, sorties, formats, volume et opérations autorisées
Version / périmètre autorisé :
Résultat demandé : Brief d'utilitaire borné avec exemples et conditions d'arrêt
Contraintes et inconnues :
```

### Sortie
```text
Résultat : Brief d'utilitaire borné avec exemples et conditions d'arrêt
| Élément examiné | Preuve / source / version | Conclusion | Limite / action |
|---|---|---|---|
Hypothèses :
Risques :
Prochaines actions :
```

## Checklist QA interne
- [ ] Les inputs et les limites d'autorisation sont identifiés.
- [ ] Les trois analyses sont documentées : limiter le périmètre et exclure les cas spécialisés ; définir erreurs et invariants ; fournir cas d'acceptation avant production du script.
- [ ] Le critère d'acceptation est vérifié ou explicitement marqué non vérifié.
- [ ] Aucun résultat d'exécution ou accord humain n'est inventé.

## KPI reliés
- Couverture des éléments requis : éléments documentés / éléments applicables de ce livrable (dénominateur conservé).
- Part des conclusions appuyées par une preuve ou une source datée ; ne pas compter une hypothèse comme preuve.
- Nombre d'écarts au critère suivant restant ouverts : aucune action système n'est exécutée par le worker et les transformations destructives exigent accord.

## Definition of done
- [ ] Brief d'utilitaire borné avec exemples et conditions d'arrêt livré dans le périmètre convenu.
- [ ] Aucune action système n'est exécutée par le Worker et les transformations destructives exigent accord.
- [ ] Preuves, inconnues, exceptions et actions restantes sont lisibles ; aucune réussite globale en cas de vérification bloquante manquante.

## Exemples d'usage
**Cas nominal** : à partir de entrées, sorties, formats, volume et opérations autorisées, produire brief d'utilitaire borné avec exemples et conditions d'arrêt puis vérifier le critère d'acceptation ci-dessus.

**Cas limite** : une preuve ou autorisation nécessaire manque ; livrer les éléments établis et indiquer précisément ce qui empêche la validation, sans substituer une valeur par défaut.

## Contraintes et références
- Référence officielle consultée le 2026-10-21 : [Python unittest](https://docs.python.org/3/library/unittest.html). Synthèse originale, sans reproduction du texte source ; vérifier les versions et l'applicabilité au contexte.
- Migration : DEL-20261021-EXCLUSIVE-SKILLS-MIGRATION.

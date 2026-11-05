# Artifact Dependency Inventory

## Objectif
Inventorier les références explicites entre artefacts dans une exploration généraliste.


## Quand l'utiliser (triggers)
- Demande portant sur « Artifact Dependency Inventory » ou sur le livrable : inventaire source/cible/type/preuve.
- Besoin de vérifier ce résultat : une dépendance non observée n'est pas inventée pour compléter une carte.

## Hors périmètre
- Usage de secours uniquement après qualification qu'aucun agent spécialisé ne couvre la demande.
- Ne pas traiter de fond juridique, médical, financier, sécurité ou développement spécialisé ; remettre le brief pour routage.
- L'exécution système, les modifications de fichiers, les tests et les publications relèvent de l'agent rattaché (voir table de routage) ; cette skill n'accorde aucun outil supplémentaire.
- Ne pas confondre préparation d'un protocole, revue statique et résultat d'une exécution réelle.

## Inputs requis
- Documents et fichiers autorisés, formats de liens et périmètre.
- Périmètre autorisé, version des artefacts, sources accessibles et décisions déjà validées.
- Critères d'acceptation et limites d'action ; marquer les éléments inconnus avant de conclure.

## Sorties attendues
- Inventaire source/cible/type/preuve.
- Preuves ou références par constat ; hypothèses, exceptions et vérifications non réalisées séparées.
- Brief des décisions ou actions nécessaires pour l'agent rattaché, sans les annoncer déjà exécutées.

## Workflow recommandé
1. Cadrer les inputs : documents et fichiers autorisés, formats de liens et périmètre ; vérifier les préconditions et autorisations.
2. Relever liens et imports explicites.
3. Distinguer référence observée et relation supposée.
4. Repérer références introuvables dans le périmètre.
5. Vérifier le livrable par ce critère : une dépendance non observée n'est pas inventée pour compléter une carte.
6. Restituer résultat, hypothèses, risques et prochaines actions ; signaler explicitement les blocages.

## Garde-fous
- Une dépendance non observée n'est pas inventée pour compléter une carte.
- Ne pas inventer de mesure, d'accord, de preuve ou de source ; distinguer observé, inféré et non testé.
- Ne pas transmettre d'artefact privé ou de donnée personnelle à un service tiers ; minimiser les données sensibles.
- Privilégier les outils libres maintenus et vérifier les versions applicables sans introduire de dépendance EOL.
- Lire la référence dans son contexte : elle éclaire la méthode, elle ne certifie pas ce livrable et n'impose pas de seuil universel.

## Templates copier/coller
### Entrée
```text
Objet : Artifact Dependency Inventory
Inputs : Documents et fichiers autorisés, formats de liens et périmètre
Version / périmètre autorisé :
Résultat demandé : Inventaire source/cible/type/preuve
Contraintes et inconnues :
```

### Sortie
```text
Résultat : Inventaire source/cible/type/preuve
| Élément examiné | Preuve / source / version | Conclusion | Limite / action |
|---|---|---|---|
Hypothèses :
Risques :
Prochaines actions :
```

## Checklist QA interne
- [ ] Les inputs et les limites d'autorisation sont identifiés.
- [ ] Les trois analyses sont documentées : relever liens et imports explicites ; distinguer référence observée et relation supposée ; repérer références introuvables dans le périmètre.
- [ ] Le critère d'acceptation est vérifié ou explicitement marqué non vérifié.
- [ ] Aucun résultat d'exécution ou accord humain n'est inventé.

## KPI reliés
- Couverture des éléments requis : éléments documentés / éléments applicables de ce livrable (dénominateur conservé).
- Part des conclusions appuyées par une preuve ou une source datée ; ne pas compter une hypothèse comme preuve.
- Nombre d'écarts au critère suivant restant ouverts : une dépendance non observée n'est pas inventée pour compléter une carte.

## Definition of done
- [ ] Inventaire source/cible/type/preuve livré dans le périmètre convenu.
- [ ] Une dépendance non observée n'est pas inventée pour compléter une carte.
- [ ] Preuves, inconnues, exceptions et actions restantes sont lisibles ; aucune réussite globale en cas de vérification bloquante manquante.

## Exemples d'usage
**Cas nominal** : à partir de documents et fichiers autorisés, formats de liens et périmètre, produire inventaire source/cible/type/preuve puis vérifier le critère d'acceptation ci-dessus.

**Cas limite** : une preuve ou autorisation nécessaire manque ; livrer les éléments établis et indiquer précisément ce qui empêche la validation, sans substituer une valeur par défaut.

## Contraintes et références
- Référence officielle consultée le 2026-10-21 : [Git - git-ls-files](https://git-scm.com/docs/git-ls-files). Synthèse originale, sans reproduction du texte source ; vérifier les versions et l'applicabilité au contexte.
- Migration : DEL-20261021-EXCLUSIVE-SKILLS-MIGRATION.

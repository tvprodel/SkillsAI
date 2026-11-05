# Repository Entry-Point Survey

## Objectif
Cartographier les points d'entrée documentaires et techniques d'un dépôt sans audit spécialisé.


## Quand l'utiliser (triggers)
- Demande portant sur « Repository Entry-Point Survey » ou sur le livrable : carte d'orientation avec chemins et rôle observé.
- Besoin de vérifier ce résultat : aucun dossier privé ou exclu n'est lu et aucune exécution n'est inférée du seul nom de fichier.

## Hors périmètre
- Usage de secours uniquement après qualification qu'aucun agent spécialisé ne couvre la demande.
- Ne pas traiter de fond juridique, médical, financier, sécurité ou développement spécialisé ; remettre le brief pour routage.
- L'exécution système, les modifications de fichiers, les tests et les publications relèvent de l'agent rattaché (voir table de routage) ; cette skill n'accorde aucun outil supplémentaire.
- Ne pas confondre préparation d'un protocole, revue statique et résultat d'une exécution réelle.

## Inputs requis
- Périmètre autorisé, arborescence et manifests accessibles.
- Périmètre autorisé, version des artefacts, sources accessibles et décisions déjà validées.
- Critères d'acceptation et limites d'action ; marquer les éléments inconnus avant de conclure.

## Sorties attendues
- Carte d'orientation avec chemins et rôle observé.
- Preuves ou références par constat ; hypothèses, exceptions et vérifications non réalisées séparées.
- Brief des décisions ou actions nécessaires pour l'agent rattaché, sans les annoncer déjà exécutées.

## Workflow recommandé
1. Cadrer les inputs : périmètre autorisé, arborescence et manifests accessibles ; vérifier les préconditions et autorisations.
2. Repérer guides et points d'entrée déclarés.
3. Distinguer sources, générés et archives.
4. Signaler les chemins exclus sans les lire.
5. Vérifier le livrable par ce critère : aucun dossier privé ou exclu n'est lu et aucune exécution n'est inférée du seul nom de fichier.
6. Restituer résultat, hypothèses, risques et prochaines actions ; signaler explicitement les blocages.

## Garde-fous
- Aucun dossier privé ou exclu n'est lu et aucune exécution n'est inférée du seul nom de fichier.
- Ne pas inventer de mesure, d'accord, de preuve ou de source ; distinguer observé, inféré et non testé.
- Ne pas transmettre d'artefact privé ou de donnée personnelle à un service tiers ; minimiser les données sensibles.
- Privilégier les outils libres maintenus et vérifier les versions applicables sans introduire de dépendance EOL.
- Lire la référence dans son contexte : elle éclaire la méthode, elle ne certifie pas ce livrable et n'impose pas de seuil universel.

## Templates copier/coller
### Entrée
```text
Objet : Repository Entry-Point Survey
Inputs : Périmètre autorisé, arborescence et manifests accessibles
Version / périmètre autorisé :
Résultat demandé : Carte d'orientation avec chemins et rôle observé
Contraintes et inconnues :
```

### Sortie
```text
Résultat : Carte d'orientation avec chemins et rôle observé
| Élément examiné | Preuve / source / version | Conclusion | Limite / action |
|---|---|---|---|
Hypothèses :
Risques :
Prochaines actions :
```

## Checklist QA interne
- [ ] Les inputs et les limites d'autorisation sont identifiés.
- [ ] Les trois analyses sont documentées : repérer guides et points d'entrée déclarés ; distinguer sources, générés et archives ; signaler les chemins exclus sans les lire.
- [ ] Le critère d'acceptation est vérifié ou explicitement marqué non vérifié.
- [ ] Aucun résultat d'exécution ou accord humain n'est inventé.

## KPI reliés
- Couverture des éléments requis : éléments documentés / éléments applicables de ce livrable (dénominateur conservé).
- Part des conclusions appuyées par une preuve ou une source datée ; ne pas compter une hypothèse comme preuve.
- Nombre d'écarts au critère suivant restant ouverts : aucun dossier privé ou exclu n'est lu et aucune exécution n'est inférée du seul nom de fichier.

## Definition of done
- [ ] Carte d'orientation avec chemins et rôle observé livré dans le périmètre convenu.
- [ ] Aucun dossier privé ou exclu n'est lu et aucune exécution n'est inférée du seul nom de fichier.
- [ ] Preuves, inconnues, exceptions et actions restantes sont lisibles ; aucune réussite globale en cas de vérification bloquante manquante.

## Exemples d'usage
**Cas nominal** : à partir de périmètre autorisé, arborescence et manifests accessibles, produire carte d'orientation avec chemins et rôle observé puis vérifier le critère d'acceptation ci-dessus.

**Cas limite** : une preuve ou autorisation nécessaire manque ; livrer les éléments établis et indiquer précisément ce qui empêche la validation, sans substituer une valeur par défaut.

## Contraintes et références
- Référence officielle consultée le 2026-10-21 : [Git - git-ls-files](https://git-scm.com/docs/git-ls-files). Synthèse originale, sans reproduction du texte source ; vérifier les versions et l'applicabilité au contexte.
- Migration : DEL-20261021-EXCLUSIVE-SKILLS-MIGRATION.

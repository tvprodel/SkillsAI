# Blender Hard Surface & Organic Modeling

## Objectif
Produire un livrable maîtrisé : modèle 3D (.blend) avec topologie propre, échelle correcte et notes de construction.


## Quand l'utiliser (triggers)
- Demande portant sur « Blender Hard Surface & Organic Modeling » ou sur le livrable : modèle 3D (.blend) avec topologie propre, échelle correcte et notes de construction.
- Besoin de vérifier ce résultat : le modèle respecte le budget de polygones annoncé, avec échelle et transformations appliquées.

## Hors périmètre
- Ne pas remplacer les domaines des agents complémentaires : présenter les interfaces et transmettre les besoins à l'agent rattaché (voir table de routage).
- L'exécution système, les modifications de fichiers, les tests et les publications relèvent de l'agent rattaché (voir table de routage) ; cette skill n'accorde aucun outil supplémentaire.
- Ne pas confondre préparation d'un protocole, revue statique et résultat d'une exécution réelle dans le logiciel.

## Inputs requis
- Références visuelles, budget de polygones, échelle et usage (rendu, jeu temps réel).
- Périmètre autorisé, version des logiciels et des artefacts, sources accessibles et décisions déjà validées.
- Critères d'acceptation et limites d'action ; marquer les éléments inconnus avant de conclure.

## Sorties attendues
- Modèle 3D (.blend) avec topologie propre, échelle correcte et notes de construction.
- Preuves ou références par constat ; hypothèses, exceptions et vérifications non réalisées séparées.
- Brief des décisions ou actions nécessaires pour l'agent rattaché, sans les annoncer déjà exécutées.

## Workflow recommandé
1. Cadrer les inputs : références visuelles, budget de polygones, échelle et usage (rendu, jeu temps réel) ; vérifier les préconditions et autorisations.
2. Bloquer les volumes et valider les proportions.
3. Affiner la topologie (hard surface, sculpt ou retopologie).
4. Contrôler normales, échelle, application des transformations et budget.
5. Vérifier le livrable par ce critère : le modèle respecte le budget de polygones annoncé, avec échelle et transformations appliquées.
6. Restituer résultat, hypothèses, risques et prochaines actions ; signaler explicitement les blocages.

## Garde-fous
- Le modèle respecte le budget de polygones annoncé, avec échelle et transformations appliquées.
- Ne pas inventer de mesure, d'accord, de preuve ou de source ; distinguer observé, inféré et non testé.
- Ne pas transmettre d'artefact privé ou de donnée personnelle à un service tiers ; minimiser les données sensibles.
- Privilégier les outils libres maintenus et vérifier les versions applicables sans introduire de dépendance EOL.
- Utiliser uniquement des ressources originales, du Domaine Public ou CC0 ; tracer chaque source externe dans `docs/imageLicencesSources.md` (format `Nomdefichier | licence | url source`).
- Lire la référence dans son contexte : elle éclaire la méthode, elle ne certifie pas ce livrable et n'impose pas de seuil universel.

## Templates copier/coller
### Entrée
```text
Objet : Blender Hard Surface & Organic Modeling
Inputs : références visuelles, budget de polygones, échelle et usage (rendu, jeu temps réel)
Version / périmètre autorisé :
Résultat demandé : modèle 3D (.blend) avec topologie propre, échelle correcte et notes de construction
Contraintes et inconnues :
```

### Sortie
```text
Résultat : modèle 3D (.blend) avec topologie propre, échelle correcte et notes de construction
| Élément examiné | Preuve / source / version | Conclusion | Limite / action |
|---|---|---|---|
Hypothèses :
Risques :
Prochaines actions :
```

## Checklist QA interne
- [ ] Les inputs et les limites d'autorisation sont identifiés.
- [ ] Les trois analyses sont documentées : bloquer les volumes et valider les proportions ; affiner la topologie (hard surface, sculpt ou retopologie) ; contrôler normales, échelle, application des transformations et budget.
- [ ] Le critère d'acceptation est vérifié ou explicitement marqué non vérifié.
- [ ] Aucun résultat d'exécution ou accord humain n'est inventé.

## KPI reliés
- Couverture des éléments requis : éléments documentés / éléments applicables de ce livrable (dénominateur conservé).
- Part des conclusions appuyées par une preuve ou une source datée ; ne pas compter une hypothèse comme preuve.
- Nombre d'écarts au critère suivant restant ouverts : le modèle respecte le budget de polygones annoncé, avec échelle et transformations appliquées.

## Definition of done
- [ ] Modèle 3D (.blend) avec topologie propre, échelle correcte et notes de construction livré dans le périmètre convenu.
- [ ] Le modèle respecte le budget de polygones annoncé, avec échelle et transformations appliquées.
- [ ] Preuves, inconnues, exceptions et actions restantes sont lisibles ; aucune réussite globale en cas de vérification bloquante manquante.

## Exemples d'usage
**Cas nominal** : à partir de références visuelles, budget de polygones, échelle et usage (rendu, jeu temps réel), produire modèle 3D (.blend) avec topologie propre, échelle correcte et notes de construction puis vérifier le critère d'acceptation ci-dessus.

**Cas limite** : une preuve ou autorisation nécessaire manque ; livrer les éléments établis et indiquer précisément ce qui empêche la validation, sans substituer une valeur par défaut.

## Contraintes et références
- Référence officielle : [Blender - Manuel officiel](https://docs.blender.org/manual/en/latest/). Synthèse originale, sans reproduction du texte source ; page non consultée en détail lors de la création, vérifier les versions et l'applicabilité au contexte.
- Création : DEL-20261025-CREA-3D-AGENTS.

# Bitmap Texture & Sprite Sheet Preparation

## Objectif
Produire un livrable maîtrisé : textures et planches de sprites prêtes pour un moteur, avec spécification de découpage.


## Quand l'utiliser (triggers)
- Demande portant sur « Bitmap Texture & Sprite Sheet Preparation » ou sur le livrable : textures et planches de sprites prêtes pour un moteur, avec spécification de découpage.
- Besoin de vérifier ce résultat : les dimensions et le découpage sont documentés et l'import ne produit ni halo ni décalage.

## Hors périmètre
- Ne pas remplacer les domaines des agents complémentaires : présenter les interfaces et transmettre les besoins à l'agent rattaché (voir table de routage).
- L'exécution système, les modifications de fichiers, les tests et les publications relèvent de l'agent rattaché (voir table de routage) ; cette skill n'accorde aucun outil supplémentaire.
- Ne pas confondre préparation d'un protocole, revue statique et résultat d'une exécution réelle dans le logiciel.

## Inputs requis
- Assets sources, taille de cellule, moteur cible, contraintes de mémoire et de filtrage.
- Périmètre autorisé, version des logiciels et des artefacts, sources accessibles et décisions déjà validées.
- Critères d'acceptation et limites d'action ; marquer les éléments inconnus avant de conclure.

## Sorties attendues
- Textures et planches de sprites prêtes pour un moteur, avec spécification de découpage.
- Preuves ou références par constat ; hypothèses, exceptions et vérifications non réalisées séparées.
- Brief des décisions ou actions nécessaires pour l'agent rattaché, sans les annoncer déjà exécutées.

## Workflow recommandé
1. Cadrer les inputs : assets sources, taille de cellule, moteur cible, contraintes de mémoire et de filtrage ; vérifier les préconditions et autorisations.
2. Définir dimensions, marges et convention de nommage.
3. Préparer canal alpha, répétition (tiling) et bords sans halo.
4. Documenter le découpage pour l'import dans le moteur.
5. Vérifier le livrable par ce critère : les dimensions et le découpage sont documentés et l'import ne produit ni halo ni décalage.
6. Restituer résultat, hypothèses, risques et prochaines actions ; signaler explicitement les blocages.

## Garde-fous
- Les dimensions et le découpage sont documentés et l'import ne produit ni halo ni décalage.
- Ne pas inventer de mesure, d'accord, de preuve ou de source ; distinguer observé, inféré et non testé.
- Ne pas transmettre d'artefact privé ou de donnée personnelle à un service tiers ; minimiser les données sensibles.
- Privilégier les outils libres maintenus et vérifier les versions applicables sans introduire de dépendance EOL.
- Utiliser uniquement des ressources originales, du Domaine Public ou CC0 ; tracer chaque source externe dans `docs/imageLicencesSources.md` (format `Nomdefichier | licence | url source`).
- Lire la référence dans son contexte : elle éclaire la méthode, elle ne certifie pas ce livrable et n'impose pas de seuil universel.

## Templates copier/coller
### Entrée
```text
Objet : Bitmap Texture & Sprite Sheet Preparation
Inputs : assets sources, taille de cellule, moteur cible, contraintes de mémoire et de filtrage
Version / périmètre autorisé :
Résultat demandé : textures et planches de sprites prêtes pour un moteur, avec spécification de découpage
Contraintes et inconnues :
```

### Sortie
```text
Résultat : textures et planches de sprites prêtes pour un moteur, avec spécification de découpage
| Élément examiné | Preuve / source / version | Conclusion | Limite / action |
|---|---|---|---|
Hypothèses :
Risques :
Prochaines actions :
```

## Checklist QA interne
- [ ] Les inputs et les limites d'autorisation sont identifiés.
- [ ] Les trois analyses sont documentées : définir dimensions, marges et convention de nommage ; préparer canal alpha, répétition (tiling) et bords sans halo ; documenter le découpage pour l'import dans le moteur.
- [ ] Le critère d'acceptation est vérifié ou explicitement marqué non vérifié.
- [ ] Aucun résultat d'exécution ou accord humain n'est inventé.

## KPI reliés
- Couverture des éléments requis : éléments documentés / éléments applicables de ce livrable (dénominateur conservé).
- Part des conclusions appuyées par une preuve ou une source datée ; ne pas compter une hypothèse comme preuve.
- Nombre d'écarts au critère suivant restant ouverts : les dimensions et le découpage sont documentés et l'import ne produit ni halo ni décalage.

## Definition of done
- [ ] Textures et planches de sprites prêtes pour un moteur, avec spécification de découpage livré dans le périmètre convenu.
- [ ] Les dimensions et le découpage sont documentés et l'import ne produit ni halo ni décalage.
- [ ] Preuves, inconnues, exceptions et actions restantes sont lisibles ; aucune réussite globale en cas de vérification bloquante manquante.

## Exemples d'usage
**Cas nominal** : à partir de assets sources, taille de cellule, moteur cible, contraintes de mémoire et de filtrage, produire textures et planches de sprites prêtes pour un moteur, avec spécification de découpage puis vérifier le critère d'acceptation ci-dessus.

**Cas limite** : une preuve ou autorisation nécessaire manque ; livrer les éléments établis et indiquer précisément ce qui empêche la validation, sans substituer une valeur par défaut.

## Contraintes et références
- Référence officielle : [Krita - Manuel officiel](https://docs.krita.org/en/). Synthèse originale, sans reproduction du texte source ; page non consultée en détail lors de la création, vérifier les versions et l'applicabilité au contexte.
- Création : DEL-20261025-CREA-3D-AGENTS.

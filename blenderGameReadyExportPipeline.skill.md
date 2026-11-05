# Blender Game-Ready Export Pipeline

## Objectif
Produire un livrable maîtrisé : export glTF 2.0 (ou FBX si justifié) avec paramètres, checklist et test d'import.


## Quand l'utiliser (triggers)
- Demande portant sur « Blender Game-Ready Export Pipeline » ou sur le livrable : export glTF 2.0 (ou FBX si justifié) avec paramètres, checklist et test d'import.
- Besoin de vérifier ce résultat : l'asset exporté s'importe dans le moteur cible avec échelle, orientation et matériaux conformes.

## Hors périmètre
- Ne pas remplacer les domaines des agents complémentaires : présenter les interfaces et transmettre les besoins à l'agent rattaché (voir table de routage).
- L'exécution système, les modifications de fichiers, les tests et les publications relèvent de l'agent rattaché (voir table de routage) ; cette skill n'accorde aucun outil supplémentaire.
- Ne pas confondre préparation d'un protocole, revue statique et résultat d'une exécution réelle dans le logiciel.

## Inputs requis
- Scène Blender, moteur cible et version, conventions de nommage, besoins d'animation.
- Périmètre autorisé, version des logiciels et des artefacts, sources accessibles et décisions déjà validées.
- Critères d'acceptation et limites d'action ; marquer les éléments inconnus avant de conclure.

## Sorties attendues
- Export glTF 2.0 (ou FBX si justifié) avec paramètres, checklist et test d'import.
- Preuves ou références par constat ; hypothèses, exceptions et vérifications non réalisées séparées.
- Brief des décisions ou actions nécessaires pour l'agent rattaché, sans les annoncer déjà exécutées.

## Workflow recommandé
1. Cadrer les inputs : scène Blender, moteur cible et version, conventions de nommage, besoins d'animation ; vérifier les préconditions et autorisations.
2. Nettoyer la scène (hiérarchie, pivots, échelle, noms).
3. Régler les options d'export glTF et les matériaux.
4. Tester l'import dans le moteur cible et corriger les écarts.
5. Vérifier le livrable par ce critère : l'asset exporté s'importe dans le moteur cible avec échelle, orientation et matériaux conformes.
6. Restituer résultat, hypothèses, risques et prochaines actions ; signaler explicitement les blocages.

## Garde-fous
- L'asset exporté s'importe dans le moteur cible avec échelle, orientation et matériaux conformes.
- Ne pas inventer de mesure, d'accord, de preuve ou de source ; distinguer observé, inféré et non testé.
- Ne pas transmettre d'artefact privé ou de donnée personnelle à un service tiers ; minimiser les données sensibles.
- Privilégier les outils libres maintenus et vérifier les versions applicables sans introduire de dépendance EOL.
- Utiliser uniquement des ressources originales, du Domaine Public ou CC0 ; tracer chaque source externe dans `docs/imageLicencesSources.md` (format `Nomdefichier | licence | url source`).
- Lire la référence dans son contexte : elle éclaire la méthode, elle ne certifie pas ce livrable et n'impose pas de seuil universel.

## Templates copier/coller
### Entrée
```text
Objet : Blender Game-Ready Export Pipeline
Inputs : scène Blender, moteur cible et version, conventions de nommage, besoins d'animation
Version / périmètre autorisé :
Résultat demandé : export glTF 2.0 (ou FBX si justifié) avec paramètres, checklist et test d'import
Contraintes et inconnues :
```

### Sortie
```text
Résultat : export glTF 2.0 (ou FBX si justifié) avec paramètres, checklist et test d'import
| Élément examiné | Preuve / source / version | Conclusion | Limite / action |
|---|---|---|---|
Hypothèses :
Risques :
Prochaines actions :
```

## Checklist QA interne
- [ ] Les inputs et les limites d'autorisation sont identifiés.
- [ ] Les trois analyses sont documentées : nettoyer la scène (hiérarchie, pivots, échelle, noms) ; régler les options d'export glTF et les matériaux ; tester l'import dans le moteur cible et corriger les écarts.
- [ ] Le critère d'acceptation est vérifié ou explicitement marqué non vérifié.
- [ ] Aucun résultat d'exécution ou accord humain n'est inventé.

## KPI reliés
- Couverture des éléments requis : éléments documentés / éléments applicables de ce livrable (dénominateur conservé).
- Part des conclusions appuyées par une preuve ou une source datée ; ne pas compter une hypothèse comme preuve.
- Nombre d'écarts au critère suivant restant ouverts : l'asset exporté s'importe dans le moteur cible avec échelle, orientation et matériaux conformes.

## Definition of done
- [ ] Export glTF 2.0 (ou FBX si justifié) avec paramètres, checklist et test d'import livré dans le périmètre convenu.
- [ ] L'asset exporté s'importe dans le moteur cible avec échelle, orientation et matériaux conformes.
- [ ] Preuves, inconnues, exceptions et actions restantes sont lisibles ; aucune réussite globale en cas de vérification bloquante manquante.

## Exemples d'usage
**Cas nominal** : à partir de scène Blender, moteur cible et version, conventions de nommage, besoins d'animation, produire export glTF 2.0 (ou FBX si justifié) avec paramètres, checklist et test d'import puis vérifier le critère d'acceptation ci-dessus.

**Cas limite** : une preuve ou autorisation nécessaire manque ; livrer les éléments établis et indiquer précisément ce qui empêche la validation, sans substituer une valeur par défaut.

## Contraintes et références
- Référence officielle : [Blender - Manuel officiel (glTF 2.0)](https://docs.blender.org/manual/en/latest/addons/import_export/scene_gltf2.html). Synthèse originale, sans reproduction du texte source ; page non consultée en détail lors de la création, vérifier les versions et l'applicabilité au contexte.
- Création : DEL-20261025-CREA-3D-AGENTS.

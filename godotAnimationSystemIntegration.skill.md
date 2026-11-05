# Godot Animation System Integration

## Objectif
Produire un livrable maîtrisé : intégration d'animations dans Godot 4 (AnimationPlayer, AnimationTree, Skeleton) avec scène de test.


## Quand l'utiliser (triggers)
- Demande portant sur « Godot Animation System Integration » ou sur le livrable : intégration d'animations dans Godot 4 (AnimationPlayer, AnimationTree, Skeleton) avec scène de test.
- Besoin de vérifier ce résultat : les états et transitions déclarés se déclenchent dans une scène de test sans saccade ni pose cassée.

## Hors périmètre
- Ne pas remplacer les domaines des agents complémentaires : présenter les interfaces et transmettre les besoins à l'agent rattaché (voir table de routage).
- L'exécution système, les modifications de fichiers, les tests et les publications relèvent de l'agent rattaché (voir table de routage) ; cette skill n'accorde aucun outil supplémentaire.
- Ne pas confondre préparation d'un protocole, revue statique et résultat d'une exécution réelle dans le logiciel.

## Inputs requis
- Assets animés importés, version de Godot, états et transitions voulus, contraintes de performance.
- Périmètre autorisé, version des logiciels et des artefacts, sources accessibles et décisions déjà validées.
- Critères d'acceptation et limites d'action ; marquer les éléments inconnus avant de conclure.

## Sorties attendues
- Intégration d'animations dans Godot 4 (AnimationPlayer, AnimationTree, Skeleton) avec scène de test.
- Preuves ou références par constat ; hypothèses, exceptions et vérifications non réalisées séparées.
- Brief des décisions ou actions nécessaires pour l'agent rattaché, sans les annoncer déjà exécutées.

## Workflow recommandé
1. Cadrer les inputs : assets animés importés, version de Godot, états et transitions voulus, contraintes de performance ; vérifier les préconditions et autorisations.
2. Vérifier l'import (squelette, clips, échelle) et les réglages d'animation.
3. Construire AnimationPlayer ou AnimationTree avec ses états et transitions.
4. Tester les transitions et transmettre à l'agent technique du moteur de jeu les points de code (signaux, déclencheurs).
5. Vérifier le livrable par ce critère : les états et transitions déclarés se déclenchent dans une scène de test sans saccade ni pose cassée.
6. Restituer résultat, hypothèses, risques et prochaines actions ; signaler explicitement les blocages.

## Garde-fous
- Les états et transitions déclarés se déclenchent dans une scène de test sans saccade ni pose cassée.
- Ne pas inventer de mesure, d'accord, de preuve ou de source ; distinguer observé, inféré et non testé.
- Ne pas transmettre d'artefact privé ou de donnée personnelle à un service tiers ; minimiser les données sensibles.
- Privilégier les outils libres maintenus et vérifier les versions applicables sans introduire de dépendance EOL.
- Utiliser uniquement des ressources originales, du Domaine Public ou CC0 ; tracer chaque source externe dans `docs/imageLicencesSources.md` (format `Nomdefichier | licence | url source`).
- Lire la référence dans son contexte : elle éclaire la méthode, elle ne certifie pas ce livrable et n'impose pas de seuil universel.

## Templates copier/coller
### Entrée
```text
Objet : Godot Animation System Integration
Inputs : assets animés importés, version de Godot, états et transitions voulus, contraintes de performance
Version / périmètre autorisé :
Résultat demandé : intégration d'animations dans Godot 4 (AnimationPlayer, AnimationTree, Skeleton) avec scène de test
Contraintes et inconnues :
```

### Sortie
```text
Résultat : intégration d'animations dans Godot 4 (AnimationPlayer, AnimationTree, Skeleton) avec scène de test
| Élément examiné | Preuve / source / version | Conclusion | Limite / action |
|---|---|---|---|
Hypothèses :
Risques :
Prochaines actions :
```

## Checklist QA interne
- [ ] Les inputs et les limites d'autorisation sont identifiés.
- [ ] Les trois analyses sont documentées : vérifier l'import (squelette, clips, échelle) et les réglages d'animation ; construire AnimationPlayer ou AnimationTree avec ses états et transitions ; tester les transitions et transmettre à l'agent technique du moteur de jeu les points de code (signaux, déclencheurs).
- [ ] Le critère d'acceptation est vérifié ou explicitement marqué non vérifié.
- [ ] Aucun résultat d'exécution ou accord humain n'est inventé.

## KPI reliés
- Couverture des éléments requis : éléments documentés / éléments applicables de ce livrable (dénominateur conservé).
- Part des conclusions appuyées par une preuve ou une source datée ; ne pas compter une hypothèse comme preuve.
- Nombre d'écarts au critère suivant restant ouverts : les états et transitions déclarés se déclenchent dans une scène de test sans saccade ni pose cassée.

## Definition of done
- [ ] Intégration d'animations dans Godot 4 (AnimationPlayer, AnimationTree, Skeleton) avec scène de test livré dans le périmètre convenu.
- [ ] Les états et transitions déclarés se déclenchent dans une scène de test sans saccade ni pose cassée.
- [ ] Preuves, inconnues, exceptions et actions restantes sont lisibles ; aucune réussite globale en cas de vérification bloquante manquante.

## Exemples d'usage
**Cas nominal** : à partir de assets animés importés, version de Godot, états et transitions voulus, contraintes de performance, produire intégration d'animations dans Godot 4 (AnimationPlayer, AnimationTree, Skeleton) avec scène de test puis vérifier le critère d'acceptation ci-dessus.

**Cas limite** : une preuve ou autorisation nécessaire manque ; livrer les éléments établis et indiquer précisément ce qui empêche la validation, sans substituer une valeur par défaut.

## Contraintes et références
- Référence officielle : [Godot - Animation](https://docs.godotengine.org/en/stable/tutorials/animation/index.html). Synthèse originale, sans reproduction du texte source ; page non consultée en détail lors de la création, vérifier les versions et l'applicabilité au contexte.
- Création : DEL-20261025-CREA-3D-AGENTS.

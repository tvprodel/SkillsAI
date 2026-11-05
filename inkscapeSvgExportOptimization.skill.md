# Inkscape SVG Export & Optimization

## Objectif
Produire un livrable maîtrisé : jeu d'exports (SVG optimisé, PNG, PDF) avec rapport de poids et de compatibilité.


## Quand l'utiliser (triggers)
- Demande portant sur « Inkscape SVG Export & Optimization » ou sur le livrable : jeu d'exports (SVG optimisé, PNG, PDF) avec rapport de poids et de compatibilité.
- Besoin de vérifier ce résultat : le rendu optimisé reste visuellement équivalent à la source sur chaque cible déclarée.

## Hors périmètre
- Ne pas remplacer les domaines des agents complémentaires : présenter les interfaces et transmettre les besoins à l'agent rattaché (voir table de routage).
- L'exécution système, les modifications de fichiers, les tests et les publications relèvent de l'agent rattaché (voir table de routage) ; cette skill n'accorde aucun outil supplémentaire.
- Ne pas confondre préparation d'un protocole, revue statique et résultat d'une exécution réelle dans le logiciel.

## Inputs requis
- SVG source, cibles d'usage (web, jeu, impression), tailles et résolutions attendues.
- Périmètre autorisé, version des logiciels et des artefacts, sources accessibles et décisions déjà validées.
- Critères d'acceptation et limites d'action ; marquer les éléments inconnus avant de conclure.

## Sorties attendues
- Jeu d'exports (SVG optimisé, PNG, PDF) avec rapport de poids et de compatibilité.
- Preuves ou références par constat ; hypothèses, exceptions et vérifications non réalisées séparées.
- Brief des décisions ou actions nécessaires pour l'agent rattaché, sans les annoncer déjà exécutées.

## Workflow recommandé
1. Cadrer les inputs : SVG source, cibles d'usage (web, jeu, impression), tailles et résolutions attendues ; vérifier les préconditions et autorisations.
2. Choisir le format et la résolution par cible.
3. Nettoyer le SVG (métadonnées, définitions inutilisées, précision des coordonnées).
4. Comparer rendu et poids avant/après export.
5. Vérifier le livrable par ce critère : le rendu optimisé reste visuellement équivalent à la source sur chaque cible déclarée.
6. Restituer résultat, hypothèses, risques et prochaines actions ; signaler explicitement les blocages.

## Garde-fous
- Le rendu optimisé reste visuellement équivalent à la source sur chaque cible déclarée.
- Ne pas inventer de mesure, d'accord, de preuve ou de source ; distinguer observé, inféré et non testé.
- Ne pas transmettre d'artefact privé ou de donnée personnelle à un service tiers ; minimiser les données sensibles.
- Privilégier les outils libres maintenus et vérifier les versions applicables sans introduire de dépendance EOL.
- Utiliser uniquement des ressources originales, du Domaine Public ou CC0 ; tracer chaque source externe dans `docs/imageLicencesSources.md` (format `Nomdefichier | licence | url source`).
- Lire la référence dans son contexte : elle éclaire la méthode, elle ne certifie pas ce livrable et n'impose pas de seuil universel.

## Templates copier/coller
### Entrée
```text
Objet : Inkscape SVG Export & Optimization
Inputs : SVG source, cibles d'usage (web, jeu, impression), tailles et résolutions attendues
Version / périmètre autorisé :
Résultat demandé : jeu d'exports (SVG optimisé, PNG, PDF) avec rapport de poids et de compatibilité
Contraintes et inconnues :
```

### Sortie
```text
Résultat : jeu d'exports (SVG optimisé, PNG, PDF) avec rapport de poids et de compatibilité
| Élément examiné | Preuve / source / version | Conclusion | Limite / action |
|---|---|---|---|
Hypothèses :
Risques :
Prochaines actions :
```

## Checklist QA interne
- [ ] Les inputs et les limites d'autorisation sont identifiés.
- [ ] Les trois analyses sont documentées : choisir le format et la résolution par cible ; nettoyer le SVG (métadonnées, définitions inutilisées, précision des coordonnées) ; comparer rendu et poids avant/après export.
- [ ] Le critère d'acceptation est vérifié ou explicitement marqué non vérifié.
- [ ] Aucun résultat d'exécution ou accord humain n'est inventé.

## KPI reliés
- Couverture des éléments requis : éléments documentés / éléments applicables de ce livrable (dénominateur conservé).
- Part des conclusions appuyées par une preuve ou une source datée ; ne pas compter une hypothèse comme preuve.
- Nombre d'écarts au critère suivant restant ouverts : le rendu optimisé reste visuellement équivalent à la source sur chaque cible déclarée.

## Definition of done
- [ ] Jeu d'exports (SVG optimisé, PNG, PDF) avec rapport de poids et de compatibilité livré dans le périmètre convenu.
- [ ] Le rendu optimisé reste visuellement équivalent à la source sur chaque cible déclarée.
- [ ] Preuves, inconnues, exceptions et actions restantes sont lisibles ; aucune réussite globale en cas de vérification bloquante manquante.

## Exemples d'usage
**Cas nominal** : à partir de SVG source, cibles d'usage (web, jeu, impression), tailles et résolutions attendues, produire jeu d'exports (SVG optimisé, PNG, PDF) avec rapport de poids et de compatibilité puis vérifier le critère d'acceptation ci-dessus.

**Cas limite** : une preuve ou autorisation nécessaire manque ; livrer les éléments établis et indiquer précisément ce qui empêche la validation, sans substituer une valeur par défaut.

## Contraintes et références
- Référence officielle : [Inkscape - Documentation](https://inkscape.org/learn/). Synthèse originale, sans reproduction du texte source ; page non consultée en détail lors de la création, vérifier les versions et l'applicabilité au contexte.
- Création : DEL-20261025-CREA-3D-AGENTS.

# Krita Digital Painting Workflow

## Objectif
Produire un livrable maîtrisé : illustration ou concept art en calques (fichier .kra) avec notes de pinceaux et de palette.


## Quand l'utiliser (triggers)
- Demande portant sur « Krita Digital Painting Workflow » ou sur le livrable : illustration ou concept art en calques (fichier .kra) avec notes de pinceaux et de palette.
- Besoin de vérifier ce résultat : la source .kra conserve des calques nommés et les exports respectent dimensions et profil annoncés.

## Hors périmètre
- Ne pas remplacer les domaines des agents complémentaires : présenter les interfaces et transmettre les besoins à l'agent rattaché (voir table de routage).
- L'exécution système, les modifications de fichiers, les tests et les publications relèvent de l'agent rattaché (voir table de routage) ; cette skill n'accorde aucun outil supplémentaire.
- Ne pas confondre préparation d'un protocole, revue statique et résultat d'une exécution réelle dans le logiciel.

## Inputs requis
- Brief visuel, dimensions et résolution, style de référence, contraintes de livraison.
- Périmètre autorisé, version des logiciels et des artefacts, sources accessibles et décisions déjà validées.
- Critères d'acceptation et limites d'action ; marquer les éléments inconnus avant de conclure.

## Sorties attendues
- Illustration ou concept art en calques (fichier .kra) avec notes de pinceaux et de palette.
- Preuves ou références par constat ; hypothèses, exceptions et vérifications non réalisées séparées.
- Brief des décisions ou actions nécessaires pour l'agent rattaché, sans les annoncer déjà exécutées.

## Workflow recommandé
1. Cadrer les inputs : brief visuel, dimensions et résolution, style de référence, contraintes de livraison ; vérifier les préconditions et autorisations.
2. Préparer le canevas, la palette et l'organisation des calques.
3. Construire valeurs, couleurs et détails par passes successives.
4. Exporter les versions demandées en conservant la source en calques.
5. Vérifier le livrable par ce critère : la source .kra conserve des calques nommés et les exports respectent dimensions et profil annoncés.
6. Restituer résultat, hypothèses, risques et prochaines actions ; signaler explicitement les blocages.

## Garde-fous
- La source .kra conserve des calques nommés et les exports respectent dimensions et profil annoncés.
- Ne pas inventer de mesure, d'accord, de preuve ou de source ; distinguer observé, inféré et non testé.
- Ne pas transmettre d'artefact privé ou de donnée personnelle à un service tiers ; minimiser les données sensibles.
- Privilégier les outils libres maintenus et vérifier les versions applicables sans introduire de dépendance EOL.
- Utiliser uniquement des ressources originales, du Domaine Public ou CC0 ; tracer chaque source externe dans `docs/imageLicencesSources.md` (format `Nomdefichier | licence | url source`).
- Lire la référence dans son contexte : elle éclaire la méthode, elle ne certifie pas ce livrable et n'impose pas de seuil universel.

## Templates copier/coller
### Entrée
```text
Objet : Krita Digital Painting Workflow
Inputs : brief visuel, dimensions et résolution, style de référence, contraintes de livraison
Version / périmètre autorisé :
Résultat demandé : illustration ou concept art en calques (fichier .kra) avec notes de pinceaux et de palette
Contraintes et inconnues :
```

### Sortie
```text
Résultat : illustration ou concept art en calques (fichier .kra) avec notes de pinceaux et de palette
| Élément examiné | Preuve / source / version | Conclusion | Limite / action |
|---|---|---|---|
Hypothèses :
Risques :
Prochaines actions :
```

## Checklist QA interne
- [ ] Les inputs et les limites d'autorisation sont identifiés.
- [ ] Les trois analyses sont documentées : préparer le canevas, la palette et l'organisation des calques ; construire valeurs, couleurs et détails par passes successives ; exporter les versions demandées en conservant la source en calques.
- [ ] Le critère d'acceptation est vérifié ou explicitement marqué non vérifié.
- [ ] Aucun résultat d'exécution ou accord humain n'est inventé.

## KPI reliés
- Couverture des éléments requis : éléments documentés / éléments applicables de ce livrable (dénominateur conservé).
- Part des conclusions appuyées par une preuve ou une source datée ; ne pas compter une hypothèse comme preuve.
- Nombre d'écarts au critère suivant restant ouverts : la source .kra conserve des calques nommés et les exports respectent dimensions et profil annoncés.

## Definition of done
- [ ] Illustration ou concept art en calques (fichier .kra) avec notes de pinceaux et de palette livré dans le périmètre convenu.
- [ ] La source .kra conserve des calques nommés et les exports respectent dimensions et profil annoncés.
- [ ] Preuves, inconnues, exceptions et actions restantes sont lisibles ; aucune réussite globale en cas de vérification bloquante manquante.

## Exemples d'usage
**Cas nominal** : à partir de brief visuel, dimensions et résolution, style de référence, contraintes de livraison, produire illustration ou concept art en calques (fichier .kra) avec notes de pinceaux et de palette puis vérifier le critère d'acceptation ci-dessus.

**Cas limite** : une preuve ou autorisation nécessaire manque ; livrer les éléments établis et indiquer précisément ce qui empêche la validation, sans substituer une valeur par défaut.

## Contraintes et références
- Référence officielle : [Krita - Manuel officiel](https://docs.krita.org/en/). Synthèse originale, sans reproduction du texte source ; page non consultée en détail lors de la création, vérifier les versions et l'applicabilité au contexte.
- Création : DEL-20261025-CREA-3D-AGENTS.

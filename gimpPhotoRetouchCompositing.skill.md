# GIMP Photo Retouch & Compositing

## Objectif
Produire un livrable maîtrisé : image retouchée ou composite (fichier .xcf) avec journal des opérations non destructives.


## Quand l'utiliser (triggers)
- Demande portant sur « GIMP Photo Retouch & Compositing » ou sur le livrable : image retouchée ou composite (fichier .xcf) avec journal des opérations non destructives.
- Besoin de vérifier ce résultat : les corrections restent réversibles dans le .xcf et toute source externe est tracée avec sa licence.

## Hors périmètre
- Ne pas remplacer les domaines des agents complémentaires : présenter les interfaces et transmettre les besoins à l'agent rattaché (voir table de routage).
- L'exécution système, les modifications de fichiers, les tests et les publications relèvent de l'agent rattaché (voir table de routage) ; cette skill n'accorde aucun outil supplémentaire.
- Ne pas confondre préparation d'un protocole, revue statique et résultat d'une exécution réelle dans le logiciel.

## Inputs requis
- Images sources avec licences, résultat attendu, format et profil colorimétrique de sortie.
- Périmètre autorisé, version des logiciels et des artefacts, sources accessibles et décisions déjà validées.
- Critères d'acceptation et limites d'action ; marquer les éléments inconnus avant de conclure.

## Sorties attendues
- Image retouchée ou composite (fichier .xcf) avec journal des opérations non destructives.
- Preuves ou références par constat ; hypothèses, exceptions et vérifications non réalisées séparées.
- Brief des décisions ou actions nécessaires pour l'agent rattaché, sans les annoncer déjà exécutées.

## Workflow recommandé
1. Cadrer les inputs : images sources avec licences, résultat attendu, format et profil colorimétrique de sortie ; vérifier les préconditions et autorisations.
2. Vérifier licences et qualité des sources.
3. Retoucher avec calques, masques et réglages réversibles.
4. Exporter et comparer le rendu avec la source.
5. Vérifier le livrable par ce critère : les corrections restent réversibles dans le .xcf et toute source externe est tracée avec sa licence.
6. Restituer résultat, hypothèses, risques et prochaines actions ; signaler explicitement les blocages.

## Garde-fous
- Les corrections restent réversibles dans le .xcf et toute source externe est tracée avec sa licence.
- Ne pas inventer de mesure, d'accord, de preuve ou de source ; distinguer observé, inféré et non testé.
- Ne pas transmettre d'artefact privé ou de donnée personnelle à un service tiers ; minimiser les données sensibles.
- Privilégier les outils libres maintenus et vérifier les versions applicables sans introduire de dépendance EOL.
- Utiliser uniquement des ressources originales, du Domaine Public ou CC0 ; tracer chaque source externe dans `docs/imageLicencesSources.md` (format `Nomdefichier | licence | url source`).
- Lire la référence dans son contexte : elle éclaire la méthode, elle ne certifie pas ce livrable et n'impose pas de seuil universel.

## Templates copier/coller
### Entrée
```text
Objet : GIMP Photo Retouch & Compositing
Inputs : images sources avec licences, résultat attendu, format et profil colorimétrique de sortie
Version / périmètre autorisé :
Résultat demandé : image retouchée ou composite (fichier .xcf) avec journal des opérations non destructives
Contraintes et inconnues :
```

### Sortie
```text
Résultat : image retouchée ou composite (fichier .xcf) avec journal des opérations non destructives
| Élément examiné | Preuve / source / version | Conclusion | Limite / action |
|---|---|---|---|
Hypothèses :
Risques :
Prochaines actions :
```

## Checklist QA interne
- [ ] Les inputs et les limites d'autorisation sont identifiés.
- [ ] Les trois analyses sont documentées : vérifier licences et qualité des sources ; retoucher avec calques, masques et réglages réversibles ; exporter et comparer le rendu avec la source.
- [ ] Le critère d'acceptation est vérifié ou explicitement marqué non vérifié.
- [ ] Aucun résultat d'exécution ou accord humain n'est inventé.

## KPI reliés
- Couverture des éléments requis : éléments documentés / éléments applicables de ce livrable (dénominateur conservé).
- Part des conclusions appuyées par une preuve ou une source datée ; ne pas compter une hypothèse comme preuve.
- Nombre d'écarts au critère suivant restant ouverts : les corrections restent réversibles dans le .xcf et toute source externe est tracée avec sa licence.

## Definition of done
- [ ] Image retouchée ou composite (fichier .xcf) avec journal des opérations non destructives livré dans le périmètre convenu.
- [ ] Les corrections restent réversibles dans le .xcf et toute source externe est tracée avec sa licence.
- [ ] Preuves, inconnues, exceptions et actions restantes sont lisibles ; aucune réussite globale en cas de vérification bloquante manquante.

## Exemples d'usage
**Cas nominal** : à partir de images sources avec licences, résultat attendu, format et profil colorimétrique de sortie, produire image retouchée ou composite (fichier .xcf) avec journal des opérations non destructives puis vérifier le critère d'acceptation ci-dessus.

**Cas limite** : une preuve ou autorisation nécessaire manque ; livrer les éléments établis et indiquer précisément ce qui empêche la validation, sans substituer une valeur par défaut.

## Contraintes et références
- Référence officielle : [GIMP - Documentation](https://docs.gimp.org/). Synthèse originale, sans reproduction du texte source ; page non consultée en détail lors de la création, vérifier les versions et l'applicabilité au contexte.
- Création : DEL-20261025-CREA-3D-AGENTS.

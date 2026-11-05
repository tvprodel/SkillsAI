# Small File-Format Transformation

## Objectif
Préparer une transformation ponctuelle entre formats simples sans altérer les données non visées.


## Quand l'utiliser (triggers)
- Demande portant sur « Small File-Format Transformation » ou sur le livrable : spécification ou code d'utilitaire avec fixtures.
- Besoin de vérifier ce résultat : toute perte de champ ou de précision est annoncée et acceptée avant exécution par l'agent compétent.

## Hors périmètre
- Usage de secours uniquement après qualification qu'aucun agent spécialisé ne couvre la demande.
- Ne pas traiter de fond juridique, médical, financier, sécurité ou développement spécialisé ; remettre le brief pour routage.
- L'exécution système, les modifications de fichiers, les tests et les publications relèvent de l'agent rattaché (voir table de routage) ; cette skill n'accorde aucun outil supplémentaire.
- Ne pas confondre préparation d'un protocole, revue statique et résultat d'une exécution réelle.

## Inputs requis
- Fichier d'exemple autorisé, formats, encodage et politique de perte.
- Périmètre autorisé, version des artefacts, sources accessibles et décisions déjà validées.
- Critères d'acceptation et limites d'action ; marquer les éléments inconnus avant de conclure.

## Sorties attendues
- Spécification ou code d'utilitaire avec fixtures.
- Preuves ou références par constat ; hypothèses, exceptions et vérifications non réalisées séparées.
- Brief des décisions ou actions nécessaires pour l'agent rattaché, sans les annoncer déjà exécutées.

## Workflow recommandé
1. Cadrer les inputs : fichier d'exemple autorisé, formats, encodage et politique de perte ; vérifier les préconditions et autorisations.
2. Définir mapping et délimiteurs.
3. Traiter valeurs manquantes et caractères spéciaux.
4. Comparer comptages et échantillons avant/après.
5. Vérifier le livrable par ce critère : toute perte de champ ou de précision est annoncée et acceptée avant exécution par l'agent compétent.
6. Restituer résultat, hypothèses, risques et prochaines actions ; signaler explicitement les blocages.

## Garde-fous
- Toute perte de champ ou de précision est annoncée et acceptée avant exécution par l'agent de coordination.
- Ne pas inventer de mesure, d'accord, de preuve ou de source ; distinguer observé, inféré et non testé.
- Ne pas transmettre d'artefact privé ou de donnée personnelle à un service tiers ; minimiser les données sensibles.
- Privilégier les outils libres maintenus et vérifier les versions applicables sans introduire de dépendance EOL.
- Lire la référence dans son contexte : elle éclaire la méthode, elle ne certifie pas ce livrable et n'impose pas de seuil universel.

## Templates copier/coller
### Entrée
```text
Objet : Small File-Format Transformation
Inputs : Fichier d'exemple autorisé, formats, encodage et politique de perte
Version / périmètre autorisé :
Résultat demandé : Spécification ou code d'utilitaire avec fixtures
Contraintes et inconnues :
```

### Sortie
```text
Résultat : Spécification ou code d'utilitaire avec fixtures
| Élément examiné | Preuve / source / version | Conclusion | Limite / action |
|---|---|---|---|
Hypothèses :
Risques :
Prochaines actions :
```

## Checklist QA interne
- [ ] Les inputs et les limites d'autorisation sont identifiés.
- [ ] Les trois analyses sont documentées : définir mapping et délimiteurs ; traiter valeurs manquantes et caractères spéciaux ; comparer comptages et échantillons avant/après.
- [ ] Le critère d'acceptation est vérifié ou explicitement marqué non vérifié.
- [ ] Aucun résultat d'exécution ou accord humain n'est inventé.

## KPI reliés
- Couverture des éléments requis : éléments documentés / éléments applicables de ce livrable (dénominateur conservé).
- Part des conclusions appuyées par une preuve ou une source datée ; ne pas compter une hypothèse comme preuve.
- Nombre d'écarts au critère suivant restant ouverts : toute perte de champ ou de précision est annoncée et acceptée avant exécution par l'agent compétent.

## Definition of done
- [ ] Spécification ou code d'utilitaire avec fixtures livré dans le périmètre convenu.
- [ ] Toute perte de champ ou de précision est annoncée et acceptée avant exécution par l'agent de coordination.
- [ ] Preuves, inconnues, exceptions et actions restantes sont lisibles ; aucune réussite globale en cas de vérification bloquante manquante.

## Exemples d'usage
**Cas nominal** : à partir de fichier d'exemple autorisé, formats, encodage et politique de perte, produire spécification ou code d'utilitaire avec fixtures puis vérifier le critère d'acceptation ci-dessus.

**Cas limite** : une preuve ou autorisation nécessaire manque ; livrer les éléments établis et indiquer précisément ce qui empêche la validation, sans substituer une valeur par défaut.

## Contraintes et références
- Référence officielle consultée le 2026-10-21 : [Python unittest](https://docs.python.org/3/library/unittest.html). Synthèse originale, sans reproduction du texte source ; vérifier les versions et l'applicabilité au contexte.
- Migration : DEL-20261021-EXCLUSIVE-SKILLS-MIGRATION.

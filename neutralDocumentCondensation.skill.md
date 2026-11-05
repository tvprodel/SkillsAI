# Neutral Document Condensation

## Objectif
Réduire un document généraliste en préservant décisions, réserves et relations logiques.


## Quand l'utiliser (triggers)
- Demande portant sur « Neutral Document Condensation » ou sur le livrable : résumé neutre avec renvois aux passages importants.
- Besoin de vérifier ce résultat : aucun ajout de certitude, d'obligation ou de promesse n'est introduit.

## Hors périmètre
- Usage de secours uniquement après qualification qu'aucun agent spécialisé ne couvre la demande.
- Ne pas traiter de fond juridique, médical, financier, sécurité ou développement spécialisé ; remettre le brief pour routage.
- L'exécution système, les modifications de fichiers, les tests et les publications relèvent de l'agent rattaché (voir table de routage) ; cette skill n'accorde aucun outil supplémentaire.
- Ne pas confondre préparation d'un protocole, revue statique et résultat d'une exécution réelle.

## Inputs requis
- Texte autorisé, audience et longueur cible.
- Périmètre autorisé, version des artefacts, sources accessibles et décisions déjà validées.
- Critères d'acceptation et limites d'action ; marquer les éléments inconnus avant de conclure.

## Sorties attendues
- Résumé neutre avec renvois aux passages importants.
- Preuves ou références par constat ; hypothèses, exceptions et vérifications non réalisées séparées.
- Brief des décisions ou actions nécessaires pour l'agent rattaché, sans les annoncer déjà exécutées.

## Workflow recommandé
1. Cadrer les inputs : texte autorisé, audience et longueur cible ; vérifier les préconditions et autorisations.
2. Identifier messages et conditions essentiels.
3. Condensation sans ajouter d'opinion.
4. Comparer chaque élément résumé à sa source.
5. Vérifier le livrable par ce critère : aucun ajout de certitude, d'obligation ou de promesse n'est introduit.
6. Restituer résultat, hypothèses, risques et prochaines actions ; signaler explicitement les blocages.

## Garde-fous
- Aucun ajout de certitude, d'obligation ou de promesse n'est introduit.
- Ne pas inventer de mesure, d'accord, de preuve ou de source ; distinguer observé, inféré et non testé.
- Ne pas transmettre d'artefact privé ou de donnée personnelle à un service tiers ; minimiser les données sensibles.
- Privilégier les outils libres maintenus et vérifier les versions applicables sans introduire de dépendance EOL.
- Lire la référence dans son contexte : elle éclaire la méthode, elle ne certifie pas ce livrable et n'impose pas de seuil universel.

## Templates copier/coller
### Entrée
```text
Objet : Neutral Document Condensation
Inputs : Texte autorisé, audience et longueur cible
Version / périmètre autorisé :
Résultat demandé : Résumé neutre avec renvois aux passages importants
Contraintes et inconnues :
```

### Sortie
```text
Résultat : Résumé neutre avec renvois aux passages importants
| Élément examiné | Preuve / source / version | Conclusion | Limite / action |
|---|---|---|---|
Hypothèses :
Risques :
Prochaines actions :
```

## Checklist QA interne
- [ ] Les inputs et les limites d'autorisation sont identifiés.
- [ ] Les trois analyses sont documentées : identifier messages et conditions essentiels ; condensation sans ajouter d'opinion ; comparer chaque élément résumé à sa source.
- [ ] Le critère d'acceptation est vérifié ou explicitement marqué non vérifié.
- [ ] Aucun résultat d'exécution ou accord humain n'est inventé.

## KPI reliés
- Couverture des éléments requis : éléments documentés / éléments applicables de ce livrable (dénominateur conservé).
- Part des conclusions appuyées par une preuve ou une source datée ; ne pas compter une hypothèse comme preuve.
- Nombre d'écarts au critère suivant restant ouverts : aucun ajout de certitude, d'obligation ou de promesse n'est introduit.

## Definition of done
- [ ] Résumé neutre avec renvois aux passages importants livré dans le périmètre convenu.
- [ ] Aucun ajout de certitude, d'obligation ou de promesse n'est introduit.
- [ ] Preuves, inconnues, exceptions et actions restantes sont lisibles ; aucune réussite globale en cas de vérification bloquante manquante.

## Exemples d'usage
**Cas nominal** : à partir de texte autorisé, audience et longueur cible, produire résumé neutre avec renvois aux passages importants puis vérifier le critère d'acceptation ci-dessus.

**Cas limite** : une preuve ou autorisation nécessaire manque ; livrer les éléments établis et indiquer précisément ce qui empêche la validation, sans substituer une valeur par défaut.

## Contraintes et références
- Référence officielle consultée le 2026-10-21 : [GOV.UK - Writing to GOV.UK standards](https://www.gov.uk/guidance/content-design). Synthèse originale, sans reproduction du texte source ; vérifier les versions et l'applicabilité au contexte.
- Migration : DEL-20261021-EXCLUSIVE-SKILLS-MIGRATION.

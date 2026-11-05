# Meeting Decision Extraction

## Objectif
Extraire d'un compte rendu les décisions réellement prises et les actions explicitement attribuées.


## Quand l'utiliser (triggers)
- Demande portant sur « Meeting Decision Extraction » ou sur le livrable : table décisions/actions/owner/preuve/statut de confirmation.
- Besoin de vérifier ce résultat : une proposition non approuvée ne devient pas une tâche engagée.

## Hors périmètre
- Usage de secours uniquement après qualification qu'aucun agent spécialisé ne couvre la demande.
- Ne pas traiter de fond juridique, médical, financier, sécurité ou développement spécialisé ; remettre le brief pour routage.
- L'exécution système, les modifications de fichiers, les tests et les publications relèvent de l'agent rattaché (voir table de routage) ; cette skill n'accorde aucun outil supplémentaire.
- Ne pas confondre préparation d'un protocole, revue statique et résultat d'une exécution réelle.

## Inputs requis
- Notes autorisées, participants et conventions de validation.
- Périmètre autorisé, version des artefacts, sources accessibles et décisions déjà validées.
- Critères d'acceptation et limites d'action ; marquer les éléments inconnus avant de conclure.

## Sorties attendues
- Table décisions/actions/owner/preuve/statut de confirmation.
- Preuves ou références par constat ; hypothèses, exceptions et vérifications non réalisées séparées.
- Brief des décisions ou actions nécessaires pour l'agent rattaché, sans les annoncer déjà exécutées.

## Workflow recommandé
1. Cadrer les inputs : notes autorisées, participants et conventions de validation ; vérifier les préconditions et autorisations.
2. Séparer discussion, proposition et décision.
3. Relever owner et condition sans les inventer.
4. Présenter ambiguïtés à confirmer par l'agent de coordination.
5. Vérifier le livrable par ce critère : une proposition non approuvée ne devient pas une tâche engagée.
6. Restituer résultat, hypothèses, risques et prochaines actions ; signaler explicitement les blocages.

## Garde-fous
- Une proposition non approuvée ne devient pas une tâche engagée.
- Ne pas inventer de mesure, d'accord, de preuve ou de source ; distinguer observé, inféré et non testé.
- Ne pas transmettre d'artefact privé ou de donnée personnelle à un service tiers ; minimiser les données sensibles.
- Privilégier les outils libres maintenus et vérifier les versions applicables sans introduire de dépendance EOL.
- Lire la référence dans son contexte : elle éclaire la méthode, elle ne certifie pas ce livrable et n'impose pas de seuil universel.

## Templates copier/coller
### Entrée
```text
Objet : Meeting Decision Extraction
Inputs : Notes autorisées, participants et conventions de validation
Version / périmètre autorisé :
Résultat demandé : Table décisions/actions/owner/preuve/statut de confirmation
Contraintes et inconnues :
```

### Sortie
```text
Résultat : Table décisions/actions/owner/preuve/statut de confirmation
| Élément examiné | Preuve / source / version | Conclusion | Limite / action |
|---|---|---|---|
Hypothèses :
Risques :
Prochaines actions :
```

## Checklist QA interne
- [ ] Les inputs et les limites d'autorisation sont identifiés.
- [ ] Les trois analyses sont documentées : séparer discussion, proposition et décision ; relever owner et condition sans les inventer ; présenter ambiguïtés à confirmer par l'agent compétent.
- [ ] Le critère d'acceptation est vérifié ou explicitement marqué non vérifié.
- [ ] Aucun résultat d'exécution ou accord humain n'est inventé.

## KPI reliés
- Couverture des éléments requis : éléments documentés / éléments applicables de ce livrable (dénominateur conservé).
- Part des conclusions appuyées par une preuve ou une source datée ; ne pas compter une hypothèse comme preuve.
- Nombre d'écarts au critère suivant restant ouverts : une proposition non approuvée ne devient pas une tâche engagée.

## Definition of done
- [ ] Table décisions/actions/owner/preuve/statut de confirmation livré dans le périmètre convenu.
- [ ] Une proposition non approuvée ne devient pas une tâche engagée.
- [ ] Preuves, inconnues, exceptions et actions restantes sont lisibles ; aucune réussite globale en cas de vérification bloquante manquante.

## Exemples d'usage
**Cas nominal** : à partir de notes autorisées, participants et conventions de validation, produire table décisions/actions/owner/preuve/statut de confirmation puis vérifier le critère d'acceptation ci-dessus.

**Cas limite** : une preuve ou autorisation nécessaire manque ; livrer les éléments établis et indiquer précisément ce qui empêche la validation, sans substituer une valeur par défaut.

## Contraintes et références
- Référence officielle consultée le 2026-10-21 : [W3C PROV Overview](https://www.w3.org/TR/prov-overview/). Synthèse originale, sans reproduction du texte source ; vérifier les versions et l'applicabilité au contexte.
- Migration : DEL-20261021-EXCLUSIVE-SKILLS-MIGRATION.

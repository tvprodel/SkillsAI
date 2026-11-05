# Deliverable Completeness Review

## Objectif
Vérifier la complétude d'un livrable généraliste par rapport au brief explicite.


## Quand l'utiliser (triggers)
- Demande portant sur « Deliverable Completeness Review » ou sur le livrable : grille de réception avec statut par exigence.
- Besoin de vérifier ce résultat : la conformité formelle ne remplace pas l'expertise métier ni une validation technique spécialisée.

## Hors périmètre
- Usage de secours uniquement après qualification qu'aucun agent spécialisé ne couvre la demande.
- Ne pas traiter de fond juridique, médical, financier, sécurité ou développement spécialisé ; remettre le brief pour routage.
- L'exécution système, les modifications de fichiers, les tests et les publications relèvent de l'agent rattaché (voir table de routage) ; cette skill n'accorde aucun outil supplémentaire.
- Ne pas confondre préparation d'un protocole, revue statique et résultat d'une exécution réelle.

## Inputs requis
- Brief, livrable, contraintes et critères de réception.
- Périmètre autorisé, version des artefacts, sources accessibles et décisions déjà validées.
- Critères d'acceptation et limites d'action ; marquer les éléments inconnus avant de conclure.

## Sorties attendues
- Grille de réception avec statut par exigence.
- Preuves ou références par constat ; hypothèses, exceptions et vérifications non réalisées séparées.
- Brief des décisions ou actions nécessaires pour l'agent rattaché, sans les annoncer déjà exécutées.

## Workflow recommandé
1. Cadrer les inputs : brief, livrable, contraintes et critères de réception ; vérifier les préconditions et autorisations.
2. Transformer attentes en checklist.
3. Localiser la preuve de chaque élément.
4. Signaler manquant, hors périmètre et ambiguïté.
5. Vérifier le livrable par ce critère : la conformité formelle ne remplace pas l'expertise métier ni une validation technique spécialisée.
6. Restituer résultat, hypothèses, risques et prochaines actions ; signaler explicitement les blocages.

## Garde-fous
- La conformité formelle ne remplace pas l'expertise métier ni une validation technique spécialisée.
- Ne pas inventer de mesure, d'accord, de preuve ou de source ; distinguer observé, inféré et non testé.
- Ne pas transmettre d'artefact privé ou de donnée personnelle à un service tiers ; minimiser les données sensibles.
- Privilégier les outils libres maintenus et vérifier les versions applicables sans introduire de dépendance EOL.
- Lire la référence dans son contexte : elle éclaire la méthode, elle ne certifie pas ce livrable et n'impose pas de seuil universel.

## Templates copier/coller
### Entrée
```text
Objet : Deliverable Completeness Review
Inputs : Brief, livrable, contraintes et critères de réception
Version / périmètre autorisé :
Résultat demandé : Grille de réception avec statut par exigence
Contraintes et inconnues :
```

### Sortie
```text
Résultat : Grille de réception avec statut par exigence
| Élément examiné | Preuve / source / version | Conclusion | Limite / action |
|---|---|---|---|
Hypothèses :
Risques :
Prochaines actions :
```

## Checklist QA interne
- [ ] Les inputs et les limites d'autorisation sont identifiés.
- [ ] Les trois analyses sont documentées : transformer attentes en checklist ; localiser la preuve de chaque élément ; signaler manquant, hors périmètre et ambiguïté.
- [ ] Le critère d'acceptation est vérifié ou explicitement marqué non vérifié.
- [ ] Aucun résultat d'exécution ou accord humain n'est inventé.

## KPI reliés
- Couverture des éléments requis : éléments documentés / éléments applicables de ce livrable (dénominateur conservé).
- Part des conclusions appuyées par une preuve ou une source datée ; ne pas compter une hypothèse comme preuve.
- Nombre d'écarts au critère suivant restant ouverts : la conformité formelle ne remplace pas l'expertise métier ni une validation technique spécialisée.

## Definition of done
- [ ] Grille de réception avec statut par exigence livré dans le périmètre convenu.
- [ ] La conformité formelle ne remplace pas l'expertise métier ni une validation technique spécialisée.
- [ ] Preuves, inconnues, exceptions et actions restantes sont lisibles ; aucune réussite globale en cas de vérification bloquante manquante.

## Exemples d'usage
**Cas nominal** : à partir de brief, livrable, contraintes et critères de réception, produire grille de réception avec statut par exigence puis vérifier le critère d'acceptation ci-dessus.

**Cas limite** : une preuve ou autorisation nécessaire manque ; livrer les éléments établis et indiquer précisément ce qui empêche la validation, sans substituer une valeur par défaut.

## Contraintes et références
- Référence officielle consultée le 2026-10-21 : [W3C PROV Overview](https://www.w3.org/TR/prov-overview/). Synthèse originale, sans reproduction du texte source ; vérifier les versions et l'applicabilité au contexte.
- Migration : DEL-20261021-EXCLUSIVE-SKILLS-MIGRATION.

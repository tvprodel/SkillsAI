# Meaning-Preserving Reformulation

## Objectif
Reformuler un texte généraliste sans changer son intention ni son degré de certitude.


## Quand l'utiliser (triggers)
- Demande portant sur « Meaning-Preserving Reformulation » ou sur le livrable : version reformulée et liste des ambiguïtés conservées.
- Besoin de vérifier ce résultat : les termes contractuels ou spécialisés sont escaladés plutôt que réinterprétés.

## Hors périmètre
- Usage de secours uniquement après qualification qu'aucun agent spécialisé ne couvre la demande.
- Ne pas traiter de fond juridique, médical, financier, sécurité ou développement spécialisé ; remettre le brief pour routage.
- L'exécution système, les modifications de fichiers, les tests et les publications relèvent de l'agent rattaché (voir table de routage) ; cette skill n'accorde aucun outil supplémentaire.
- Ne pas confondre préparation d'un protocole, revue statique et résultat d'une exécution réelle.

## Inputs requis
- Texte, objectif de reformulation, public et éléments à conserver.
- Périmètre autorisé, version des artefacts, sources accessibles et décisions déjà validées.
- Critères d'acceptation et limites d'action ; marquer les éléments inconnus avant de conclure.

## Sorties attendues
- Version reformulée et liste des ambiguïtés conservées.
- Preuves ou références par constat ; hypothèses, exceptions et vérifications non réalisées séparées.
- Brief des décisions ou actions nécessaires pour l'agent rattaché, sans les annoncer déjà exécutées.

## Workflow recommandé
1. Cadrer les inputs : texte, objectif de reformulation, public et éléments à conserver ; vérifier les préconditions et autorisations.
2. Extraire conditions et nuances.
3. Rédiger variante claire.
4. Comparer négations, quantificateurs et engagements.
5. Vérifier le livrable par ce critère : les termes contractuels ou spécialisés sont escaladés plutôt que réinterprétés.
6. Restituer résultat, hypothèses, risques et prochaines actions ; signaler explicitement les blocages.

## Garde-fous
- Les termes contractuels ou spécialisés sont escaladés plutôt que réinterprétés.
- Ne pas inventer de mesure, d'accord, de preuve ou de source ; distinguer observé, inféré et non testé.
- Ne pas transmettre d'artefact privé ou de donnée personnelle à un service tiers ; minimiser les données sensibles.
- Privilégier les outils libres maintenus et vérifier les versions applicables sans introduire de dépendance EOL.
- Lire la référence dans son contexte : elle éclaire la méthode, elle ne certifie pas ce livrable et n'impose pas de seuil universel.

## Templates copier/coller
### Entrée
```text
Objet : Meaning-Preserving Reformulation
Inputs : Texte, objectif de reformulation, public et éléments à conserver
Version / périmètre autorisé :
Résultat demandé : Version reformulée et liste des ambiguïtés conservées
Contraintes et inconnues :
```

### Sortie
```text
Résultat : Version reformulée et liste des ambiguïtés conservées
| Élément examiné | Preuve / source / version | Conclusion | Limite / action |
|---|---|---|---|
Hypothèses :
Risques :
Prochaines actions :
```

## Checklist QA interne
- [ ] Les inputs et les limites d'autorisation sont identifiés.
- [ ] Les trois analyses sont documentées : extraire conditions et nuances ; rédiger variante claire ; comparer négations, quantificateurs et engagements.
- [ ] Le critère d'acceptation est vérifié ou explicitement marqué non vérifié.
- [ ] Aucun résultat d'exécution ou accord humain n'est inventé.

## KPI reliés
- Couverture des éléments requis : éléments documentés / éléments applicables de ce livrable (dénominateur conservé).
- Part des conclusions appuyées par une preuve ou une source datée ; ne pas compter une hypothèse comme preuve.
- Nombre d'écarts au critère suivant restant ouverts : les termes contractuels ou spécialisés sont escaladés plutôt que réinterprétés.

## Definition of done
- [ ] Version reformulée et liste des ambiguïtés conservées livré dans le périmètre convenu.
- [ ] Les termes contractuels ou spécialisés sont escaladés plutôt que réinterprétés.
- [ ] Preuves, inconnues, exceptions et actions restantes sont lisibles ; aucune réussite globale en cas de vérification bloquante manquante.

## Exemples d'usage
**Cas nominal** : à partir de texte, objectif de reformulation, public et éléments à conserver, produire version reformulée et liste des ambiguïtés conservées puis vérifier le critère d'acceptation ci-dessus.

**Cas limite** : une preuve ou autorisation nécessaire manque ; livrer les éléments établis et indiquer précisément ce qui empêche la validation, sans substituer une valeur par défaut.

## Contraintes et références
- Référence officielle consultée le 2026-10-21 : [GOV.UK - Writing to GOV.UK standards](https://www.gov.uk/guidance/content-design). Synthèse originale, sans reproduction du texte source ; vérifier les versions et l'applicabilité au contexte.
- Migration : DEL-20261021-EXCLUSIVE-SKILLS-MIGRATION.

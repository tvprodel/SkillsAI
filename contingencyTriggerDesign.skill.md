# Contingency Trigger Design

## Objectif
Définir quand un risque suivi doit déclencher une mesure de contingence plutôt qu'une simple surveillance.


## Quand l'utiliser (triggers)
- Demande portant sur « Contingency Trigger Design » ou sur le livrable : fiches signal/seuil/décideur/action/condition de sortie.
- Besoin de vérifier ce résultat : chaque déclencheur possède une source observable et une action réversible ou approuvée.

## Hors périmètre
- Ne pas remplacer les domaines des agents complémentaires : présenter les interfaces et transmettre les besoins à l'agent rattaché (voir table de routage).
- L'exécution système, les modifications de fichiers, les tests et les publications relèvent de l'agent rattaché (voir table de routage) ; cette skill n'accorde aucun outil supplémentaire.
- Ne pas confondre préparation d'un protocole, revue statique et résultat d'une exécution réelle.

## Inputs requis
- Risques prioritaires, indicateurs observables, responsables et options autorisées.
- Périmètre autorisé, version des artefacts, sources accessibles et décisions déjà validées.
- Critères d'acceptation et limites d'action ; marquer les éléments inconnus avant de conclure.

## Sorties attendues
- Fiches signal/seuil/décideur/action/condition de sortie.
- Preuves ou références par constat ; hypothèses, exceptions et vérifications non réalisées séparées.
- Brief des décisions ou actions nécessaires pour l'agent rattaché, sans les annoncer déjà exécutées.

## Workflow recommandé
1. Cadrer les inputs : risques prioritaires, indicateurs observables, responsables et options autorisées ; vérifier les préconditions et autorisations.
2. Définir signaux précoces et seuils justifiés.
3. Associer décision et autorité d'activation.
4. Préparer sortie du mode contingence et retour au suivi.
5. Vérifier le livrable par ce critère : chaque déclencheur possède une source observable et une action réversible ou approuvée.
6. Restituer résultat, hypothèses, risques et prochaines actions ; signaler explicitement les blocages.

## Garde-fous
- Chaque déclencheur possède une source observable et une action réversible ou approuvée.
- Ne pas inventer de mesure, d'accord, de preuve ou de source ; distinguer observé, inféré et non testé.
- Ne pas transmettre d'artefact privé ou de donnée personnelle à un service tiers ; minimiser les données sensibles.
- Privilégier les outils libres maintenus et vérifier les versions applicables sans introduire de dépendance EOL.
- Lire la référence dans son contexte : elle éclaire la méthode, elle ne certifie pas ce livrable et n'impose pas de seuil universel.

## Templates copier/coller
### Entrée
```text
Objet : Contingency Trigger Design
Inputs : Risques prioritaires, indicateurs observables, responsables et options autorisées
Version / périmètre autorisé :
Résultat demandé : Fiches signal/seuil/décideur/action/condition de sortie
Contraintes et inconnues :
```

### Sortie
```text
Résultat : Fiches signal/seuil/décideur/action/condition de sortie
| Élément examiné | Preuve / source / version | Conclusion | Limite / action |
|---|---|---|---|
Hypothèses :
Risques :
Prochaines actions :
```

## Checklist QA interne
- [ ] Les inputs et les limites d'autorisation sont identifiés.
- [ ] Les trois analyses sont documentées : définir signaux précoces et seuils justifiés ; associer décision et autorité d'activation ; préparer sortie du mode contingence et retour au suivi.
- [ ] Le critère d'acceptation est vérifié ou explicitement marqué non vérifié.
- [ ] Aucun résultat d'exécution ou accord humain n'est inventé.

## KPI reliés
- Couverture des éléments requis : éléments documentés / éléments applicables de ce livrable (dénominateur conservé).
- Part des conclusions appuyées par une preuve ou une source datée ; ne pas compter une hypothèse comme preuve.
- Nombre d'écarts au critère suivant restant ouverts : chaque déclencheur possède une source observable et une action réversible ou approuvée.

## Definition of done
- [ ] Fiches signal/seuil/décideur/action/condition de sortie livré dans le périmètre convenu.
- [ ] Chaque déclencheur possède une source observable et une action réversible ou approuvée.
- [ ] Preuves, inconnues, exceptions et actions restantes sont lisibles ; aucune réussite globale en cas de vérification bloquante manquante.

## Exemples d'usage
**Cas nominal** : à partir de risques prioritaires, indicateurs observables, responsables et options autorisées, produire fiches signal/seuil/décideur/action/condition de sortie puis vérifier le critère d'acceptation ci-dessus.

**Cas limite** : une preuve ou autorisation nécessaire manque ; livrer les éléments établis et indiquer précisément ce qui empêche la validation, sans substituer une valeur par défaut.

## Contraintes et références
- Référence officielle consultée le 2026-10-21 : [Google SRE Workbook](https://sre.google/workbook/table-of-contents/). Synthèse originale, sans reproduction du texte source ; vérifier les versions et l'applicabilité au contexte.
- Migration : DEL-20261021-EXCLUSIVE-SKILLS-MIGRATION.

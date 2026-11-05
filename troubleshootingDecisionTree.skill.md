# Troubleshooting Decision Tree

## Objectif
Transformer des symptômes documentés en parcours de dépannage utilisateur prudent.


## Quand l'utiliser (triggers)
- Demande portant sur « Troubleshooting Decision Tree » ou sur le livrable : arbre symptôme/vérification/résultat/action/escalade.
- Besoin de vérifier ce résultat : chaque branche possède une condition observable et une sortie sans boucle.

## Hors périmètre
- Ne pas remplacer les domaines des agents complémentaires : présenter les interfaces et transmettre les besoins à l'agent rattaché (voir table de routage).
- L'exécution système, les modifications de fichiers, les tests et les publications relèvent de l'agent rattaché (voir table de routage) ; cette skill n'accorde aucun outil supplémentaire.
- Ne pas confondre préparation d'un protocole, revue statique et résultat d'une exécution réelle.

## Inputs requis
- Symptômes, causes confirmées, actions autorisées et escalades.
- Périmètre autorisé, version des artefacts, sources accessibles et décisions déjà validées.
- Critères d'acceptation et limites d'action ; marquer les éléments inconnus avant de conclure.

## Sorties attendues
- Arbre symptôme/vérification/résultat/action/escalade.
- Preuves ou références par constat ; hypothèses, exceptions et vérifications non réalisées séparées.
- Brief des décisions ou actions nécessaires pour l'agent rattaché, sans les annoncer déjà exécutées.

## Workflow recommandé
1. Cadrer les inputs : symptômes, causes confirmées, actions autorisées et escalades ; vérifier les préconditions et autorisations.
2. Choisir observations non destructrices.
3. Organiser branches selon résultats observables.
4. Arrêter avant toute manipulation réservée à un administrateur.
5. Vérifier le livrable par ce critère : chaque branche possède une condition observable et une sortie sans boucle.
6. Restituer résultat, hypothèses, risques et prochaines actions ; signaler explicitement les blocages.

## Garde-fous
- Chaque branche possède une condition observable et une sortie sans boucle.
- Ne pas inventer de mesure, d'accord, de preuve ou de source ; distinguer observé, inféré et non testé.
- Ne pas transmettre d'artefact privé ou de donnée personnelle à un service tiers ; minimiser les données sensibles.
- Privilégier les outils libres maintenus et vérifier les versions applicables sans introduire de dépendance EOL.
- Lire la référence dans son contexte : elle éclaire la méthode, elle ne certifie pas ce livrable et n'impose pas de seuil universel.

## Templates copier/coller
### Entrée
```text
Objet : Troubleshooting Decision Tree
Inputs : Symptômes, causes confirmées, actions autorisées et escalades
Version / périmètre autorisé :
Résultat demandé : Arbre symptôme/vérification/résultat/action/escalade
Contraintes et inconnues :
```

### Sortie
```text
Résultat : Arbre symptôme/vérification/résultat/action/escalade
| Élément examiné | Preuve / source / version | Conclusion | Limite / action |
|---|---|---|---|
Hypothèses :
Risques :
Prochaines actions :
```

## Checklist QA interne
- [ ] Les inputs et les limites d'autorisation sont identifiés.
- [ ] Les trois analyses sont documentées : choisir observations non destructrices ; organiser branches selon résultats observables ; arrêter avant toute manipulation réservée à un administrateur.
- [ ] Le critère d'acceptation est vérifié ou explicitement marqué non vérifié.
- [ ] Aucun résultat d'exécution ou accord humain n'est inventé.

## KPI reliés
- Couverture des éléments requis : éléments documentés / éléments applicables de ce livrable (dénominateur conservé).
- Part des conclusions appuyées par une preuve ou une source datée ; ne pas compter une hypothèse comme preuve.
- Nombre d'écarts au critère suivant restant ouverts : chaque branche possède une condition observable et une sortie sans boucle.

## Definition of done
- [ ] Arbre symptôme/vérification/résultat/action/escalade livré dans le périmètre convenu.
- [ ] Chaque branche possède une condition observable et une sortie sans boucle.
- [ ] Preuves, inconnues, exceptions et actions restantes sont lisibles ; aucune réussite globale en cas de vérification bloquante manquante.

## Exemples d'usage
**Cas nominal** : à partir de symptômes, causes confirmées, actions autorisées et escalades, produire arbre symptôme/vérification/résultat/action/escalade puis vérifier le critère d'acceptation ci-dessus.

**Cas limite** : une preuve ou autorisation nécessaire manque ; livrer les éléments établis et indiquer précisément ce qui empêche la validation, sans substituer une valeur par défaut.

## Contraintes et références
- Référence officielle consultée le 2026-10-21 : [GOV.UK - Writing to GOV.UK standards](https://www.gov.uk/guidance/content-design). Synthèse originale, sans reproduction du texte source ; vérifier les versions et l'applicabilité au contexte.
- Migration : DEL-20261021-EXCLUSIVE-SKILLS-MIGRATION.

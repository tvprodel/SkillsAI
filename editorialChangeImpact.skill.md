# Editorial Change Impact

## Objectif
Identifier les contenus affectés par une modification terminologique ou éditoriale approuvée.


## Quand l'utiliser (triggers)
- Demande portant sur « Editorial Change Impact » ou sur le livrable : matrice changement/contenu/impact/contrôle de non-régression.
- Besoin de vérifier ce résultat : aucune propagation automatique ne modifie une citation ou un terme historique sans examen.

## Hors périmètre
- Ne pas remplacer les domaines des agents complémentaires : présenter les interfaces et transmettre les besoins à l'agent rattaché (voir table de routage).
- L'exécution système, les modifications de fichiers, les tests et les publications relèvent de l'agent rattaché (voir table de routage) ; cette skill n'accorde aucun outil supplémentaire.
- Ne pas confondre préparation d'un protocole, revue statique et résultat d'une exécution réelle.

## Inputs requis
- Changement proposé, corpus, références et règles de wording.
- Périmètre autorisé, version des artefacts, sources accessibles et décisions déjà validées.
- Critères d'acceptation et limites d'action ; marquer les éléments inconnus avant de conclure.

## Sorties attendues
- Matrice changement/contenu/impact/contrôle de non-régression.
- Preuves ou références par constat ; hypothèses, exceptions et vérifications non réalisées séparées.
- Brief des décisions ou actions nécessaires pour l'agent rattaché, sans les annoncer déjà exécutées.

## Workflow recommandé
1. Cadrer les inputs : changement proposé, corpus, références et règles de wording ; vérifier les préconditions et autorisations.
2. Repérer occurrences et dépendances entre documents.
3. Classer mise à jour obligatoire, optionnelle ou exclue.
4. Définir vérifications après harmonisation.
5. Vérifier le livrable par ce critère : aucune propagation automatique ne modifie une citation ou un terme historique sans examen.
6. Restituer résultat, hypothèses, risques et prochaines actions ; signaler explicitement les blocages.

## Garde-fous
- Aucune propagation automatique ne modifie une citation ou un terme historique sans examen.
- Ne pas inventer de mesure, d'accord, de preuve ou de source ; distinguer observé, inféré et non testé.
- Ne pas transmettre d'artefact privé ou de donnée personnelle à un service tiers ; minimiser les données sensibles.
- Privilégier les outils libres maintenus et vérifier les versions applicables sans introduire de dépendance EOL.
- Lire la référence dans son contexte : elle éclaire la méthode, elle ne certifie pas ce livrable et n'impose pas de seuil universel.

## Templates copier/coller
### Entrée
```text
Objet : Editorial Change Impact
Inputs : Changement proposé, corpus, références et règles de wording
Version / périmètre autorisé :
Résultat demandé : Matrice changement/contenu/impact/contrôle de non-régression
Contraintes et inconnues :
```

### Sortie
```text
Résultat : Matrice changement/contenu/impact/contrôle de non-régression
| Élément examiné | Preuve / source / version | Conclusion | Limite / action |
|---|---|---|---|
Hypothèses :
Risques :
Prochaines actions :
```

## Checklist QA interne
- [ ] Les inputs et les limites d'autorisation sont identifiés.
- [ ] Les trois analyses sont documentées : repérer occurrences et dépendances entre documents ; classer mise à jour obligatoire, optionnelle ou exclue ; définir vérifications après harmonisation.
- [ ] Le critère d'acceptation est vérifié ou explicitement marqué non vérifié.
- [ ] Aucun résultat d'exécution ou accord humain n'est inventé.

## KPI reliés
- Couverture des éléments requis : éléments documentés / éléments applicables de ce livrable (dénominateur conservé).
- Part des conclusions appuyées par une preuve ou une source datée ; ne pas compter une hypothèse comme preuve.
- Nombre d'écarts au critère suivant restant ouverts : aucune propagation automatique ne modifie une citation ou un terme historique sans examen.

## Definition of done
- [ ] Matrice changement/contenu/impact/contrôle de non-régression livré dans le périmètre convenu.
- [ ] Aucune propagation automatique ne modifie une citation ou un terme historique sans examen.
- [ ] Preuves, inconnues, exceptions et actions restantes sont lisibles ; aucune réussite globale en cas de vérification bloquante manquante.

## Exemples d'usage
**Cas nominal** : à partir de changement proposé, corpus, références et règles de wording, produire matrice changement/contenu/impact/contrôle de non-régression puis vérifier le critère d'acceptation ci-dessus.

**Cas limite** : une preuve ou autorisation nécessaire manque ; livrer les éléments établis et indiquer précisément ce qui empêche la validation, sans substituer une valeur par défaut.

## Contraintes et références
- Référence officielle consultée le 2026-10-21 : [W3C SKOS Primer](https://www.w3.org/TR/skos-primer/). Synthèse originale, sans reproduction du texte source ; vérifier les versions et l'applicabilité au contexte.
- Migration : DEL-20261021-EXCLUSIVE-SKILLS-MIGRATION.

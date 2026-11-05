# Exploration Coverage Boundary

## Objectif
Rendre visible ce qui a été et n'a pas été examiné lors d'une cartographie.


## Quand l'utiliser (triggers)
- Demande portant sur « Exploration Coverage Boundary » ou sur le livrable : matrice périmètre/méthode/couverture/limites.
- Besoin de vérifier ce résultat : aucune exploration partielle n'est présentée comme audit exhaustif.

## Hors périmètre
- Usage de secours uniquement après qualification qu'aucun agent spécialisé ne couvre la demande.
- Ne pas traiter de fond juridique, médical, financier, sécurité ou développement spécialisé ; remettre le brief pour routage.
- L'exécution système, les modifications de fichiers, les tests et les publications relèvent de l'agent rattaché (voir table de routage) ; cette skill n'accorde aucun outil supplémentaire.
- Ne pas confondre préparation d'un protocole, revue statique et résultat d'une exécution réelle.

## Inputs requis
- Question, fichiers autorisés, exclusions et observations.
- Périmètre autorisé, version des artefacts, sources accessibles et décisions déjà validées.
- Critères d'acceptation et limites d'action ; marquer les éléments inconnus avant de conclure.

## Sorties attendues
- Matrice périmètre/méthode/couverture/limites.
- Preuves ou références par constat ; hypothèses, exceptions et vérifications non réalisées séparées.
- Brief des décisions ou actions nécessaires pour l'agent rattaché, sans les annoncer déjà exécutées.

## Workflow recommandé
1. Cadrer les inputs : question, fichiers autorisés, exclusions et observations ; vérifier les préconditions et autorisations.
2. Définir critères de sélection.
3. Tracer zones lues, échantillonnées et non lues.
4. Limiter les conclusions à l'évidence disponible.
5. Vérifier le livrable par ce critère : aucune exploration partielle n'est présentée comme audit exhaustif.
6. Restituer résultat, hypothèses, risques et prochaines actions ; signaler explicitement les blocages.

## Garde-fous
- Aucune exploration partielle n'est présentée comme audit exhaustif.
- Ne pas inventer de mesure, d'accord, de preuve ou de source ; distinguer observé, inféré et non testé.
- Ne pas transmettre d'artefact privé ou de donnée personnelle à un service tiers ; minimiser les données sensibles.
- Privilégier les outils libres maintenus et vérifier les versions applicables sans introduire de dépendance EOL.
- Lire la référence dans son contexte : elle éclaire la méthode, elle ne certifie pas ce livrable et n'impose pas de seuil universel.

## Templates copier/coller
### Entrée
```text
Objet : Exploration Coverage Boundary
Inputs : Question, fichiers autorisés, exclusions et observations
Version / périmètre autorisé :
Résultat demandé : Matrice périmètre/méthode/couverture/limites
Contraintes et inconnues :
```

### Sortie
```text
Résultat : Matrice périmètre/méthode/couverture/limites
| Élément examiné | Preuve / source / version | Conclusion | Limite / action |
|---|---|---|---|
Hypothèses :
Risques :
Prochaines actions :
```

## Checklist QA interne
- [ ] Les inputs et les limites d'autorisation sont identifiés.
- [ ] Les trois analyses sont documentées : définir critères de sélection ; tracer zones lues, échantillonnées et non lues ; limiter les conclusions à l'évidence disponible.
- [ ] Le critère d'acceptation est vérifié ou explicitement marqué non vérifié.
- [ ] Aucun résultat d'exécution ou accord humain n'est inventé.

## KPI reliés
- Couverture des éléments requis : éléments documentés / éléments applicables de ce livrable (dénominateur conservé).
- Part des conclusions appuyées par une preuve ou une source datée ; ne pas compter une hypothèse comme preuve.
- Nombre d'écarts au critère suivant restant ouverts : aucune exploration partielle n'est présentée comme audit exhaustif.

## Definition of done
- [ ] Matrice périmètre/méthode/couverture/limites livré dans le périmètre convenu.
- [ ] Aucune exploration partielle n'est présentée comme audit exhaustif.
- [ ] Preuves, inconnues, exceptions et actions restantes sont lisibles ; aucune réussite globale en cas de vérification bloquante manquante.

## Exemples d'usage
**Cas nominal** : à partir de question, fichiers autorisés, exclusions et observations, produire matrice périmètre/méthode/couverture/limites puis vérifier le critère d'acceptation ci-dessus.

**Cas limite** : une preuve ou autorisation nécessaire manque ; livrer les éléments établis et indiquer précisément ce qui empêche la validation, sans substituer une valeur par défaut.

## Contraintes et références
- Référence officielle consultée le 2026-10-21 : [W3C PROV Overview](https://www.w3.org/TR/prov-overview/). Synthèse originale, sans reproduction du texte source ; vérifier les versions et l'applicabilité au contexte.
- Migration : DEL-20261021-EXCLUSIVE-SKILLS-MIGRATION.

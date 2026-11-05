# Cloud IAM Responsibility Blueprint

## Objectif
Traduire les responsabilités cloud en exigences d'accès minimales et vérifiables.


## Quand l'utiliser (triggers)
- Demande portant sur « Cloud IAM Responsibility Blueprint » ou sur le livrable : matrice acteur/action/ressource/justification/revue.
- Besoin de vérifier ce résultat : aucun droit global n'est accordé par défaut pour contourner une permission inconnue.

## Hors périmètre
- Ne pas remplacer les domaines des agents complémentaires : présenter les interfaces et transmettre les besoins à l'agent rattaché (voir table de routage).
- L'exécution système, les modifications de fichiers, les tests et les publications relèvent de l'agent rattaché (voir table de routage) ; cette skill n'accorde aucun outil supplémentaire.
- Ne pas confondre préparation d'un protocole, revue statique et résultat d'une exécution réelle.

## Inputs requis
- Acteurs, actions autorisées, ressources et périmètres d'administration.
- Périmètre autorisé, version des artefacts, sources accessibles et décisions déjà validées.
- Critères d'acceptation et limites d'action ; marquer les éléments inconnus avant de conclure.

## Sorties attendues
- Matrice acteur/action/ressource/justification/revue.
- Preuves ou références par constat ; hypothèses, exceptions et vérifications non réalisées séparées.
- Brief des décisions ou actions nécessaires pour l'agent rattaché, sans les annoncer déjà exécutées.

## Workflow recommandé
1. Cadrer les inputs : acteurs, actions autorisées, ressources et périmètres d'administration ; vérifier les préconditions et autorisations.
2. Distinguer identités humaines et services.
3. Associer privilèges aux tâches nécessaires.
4. Définir séparation des devoirs et contrôle périodique.
5. Vérifier le livrable par ce critère : aucun droit global n'est accordé par défaut pour contourner une permission inconnue.
6. Restituer résultat, hypothèses, risques et prochaines actions ; signaler explicitement les blocages.

## Garde-fous
- Aucun droit global n'est accordé par défaut pour contourner une permission inconnue.
- Ne pas inventer de mesure, d'accord, de preuve ou de source ; distinguer observé, inféré et non testé.
- Ne pas transmettre d'artefact privé ou de donnée personnelle à un service tiers ; minimiser les données sensibles.
- Privilégier les outils libres maintenus et vérifier les versions applicables sans introduire de dépendance EOL.
- Lire la référence dans son contexte : elle éclaire la méthode, elle ne certifie pas ce livrable et n'impose pas de seuil universel.

## Templates copier/coller
### Entrée
```text
Objet : Cloud IAM Responsibility Blueprint
Inputs : Acteurs, actions autorisées, ressources et périmètres d'administration
Version / périmètre autorisé :
Résultat demandé : Matrice acteur/action/ressource/justification/revue
Contraintes et inconnues :
```

### Sortie
```text
Résultat : Matrice acteur/action/ressource/justification/revue
| Élément examiné | Preuve / source / version | Conclusion | Limite / action |
|---|---|---|---|
Hypothèses :
Risques :
Prochaines actions :
```

## Checklist QA interne
- [ ] Les inputs et les limites d'autorisation sont identifiés.
- [ ] Les trois analyses sont documentées : distinguer identités humaines et services ; associer privilèges aux tâches nécessaires ; définir séparation des devoirs et contrôle périodique.
- [ ] Le critère d'acceptation est vérifié ou explicitement marqué non vérifié.
- [ ] Aucun résultat d'exécution ou accord humain n'est inventé.

## KPI reliés
- Couverture des éléments requis : éléments documentés / éléments applicables de ce livrable (dénominateur conservé).
- Part des conclusions appuyées par une preuve ou une source datée ; ne pas compter une hypothèse comme preuve.
- Nombre d'écarts au critère suivant restant ouverts : aucun droit global n'est accordé par défaut pour contourner une permission inconnue.

## Definition of done
- [ ] Matrice acteur/action/ressource/justification/revue livré dans le périmètre convenu.
- [ ] Aucun droit global n'est accordé par défaut pour contourner une permission inconnue.
- [ ] Preuves, inconnues, exceptions et actions restantes sont lisibles ; aucune réussite globale en cas de vérification bloquante manquante.

## Exemples d'usage
**Cas nominal** : à partir de acteurs, actions autorisées, ressources et périmètres d'administration, produire matrice acteur/action/ressource/justification/revue puis vérifier le critère d'acceptation ci-dessus.

**Cas limite** : une preuve ou autorisation nécessaire manque ; livrer les éléments établis et indiquer précisément ce qui empêche la validation, sans substituer une valeur par défaut.

## Contraintes et références
- Référence officielle consultée le 2026-10-21 : [NIST AI Risk Management Framework](https://www.nist.gov/itl/ai-risk-management-framework). Synthèse originale, sans reproduction du texte source ; vérifier les versions et l'applicabilité au contexte.
- Migration : DEL-20261021-EXCLUSIVE-SKILLS-MIGRATION.

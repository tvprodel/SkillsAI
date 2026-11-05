# Agent Role Regression Campaign

## Objectif
Vérifier qu'une modification de configuration préserve rôle, escalade et format d'un agent.


## Quand l'utiliser (triggers)
- Demande portant sur « Agent Role Regression Campaign » ou sur le livrable : campagne versionnée avec résultats réels et cas non exécutés.
- Besoin de vérifier ce résultat : une simulation de configuration n'est jamais présentée comme une invocation réelle réussie.

## Hors périmètre
- Ne pas remplacer les domaines des agents complémentaires : présenter les interfaces et transmettre les besoins à l'agent rattaché (voir table de routage).
- L'exécution système, les modifications de fichiers, les tests et les publications relèvent de l'agent rattaché (voir table de routage) ; cette skill n'accorde aucun outil supplémentaire.
- Ne pas confondre préparation d'un protocole, revue statique et résultat d'une exécution réelle.

## Inputs requis
- Versions comparées, cas autorisés/hors périmètre et critères d'acceptation.
- Périmètre autorisé, version des artefacts, sources accessibles et décisions déjà validées.
- Critères d'acceptation et limites d'action ; marquer les éléments inconnus avant de conclure.

## Sorties attendues
- Campagne versionnée avec résultats réels et cas non exécutés.
- Preuves ou références par constat ; hypothèses, exceptions et vérifications non réalisées séparées.
- Brief des décisions ou actions nécessaires pour l'agent rattaché, sans les annoncer déjà exécutées.

## Workflow recommandé
1. Cadrer les inputs : versions comparées, cas autorisés/hors périmètre et critères d'acceptation ; vérifier les préconditions et autorisations.
2. Construire cas nominaux et contradictoires.
3. Exécuter en environnement contrôlé via l'agent de coordination.
4. Comparer résultats et isoler les régressions.
5. Vérifier le livrable par ce critère : une simulation de configuration n'est jamais présentée comme une invocation réelle réussie.
6. Restituer résultat, hypothèses, risques et prochaines actions ; signaler explicitement les blocages.

## Garde-fous
- Une simulation de configuration n'est jamais présentée comme une invocation réelle réussie.
- Ne pas inventer de mesure, d'accord, de preuve ou de source ; distinguer observé, inféré et non testé.
- Ne pas transmettre d'artefact privé ou de donnée personnelle à un service tiers ; minimiser les données sensibles.
- Privilégier les outils libres maintenus et vérifier les versions applicables sans introduire de dépendance EOL.
- Lire la référence dans son contexte : elle éclaire la méthode, elle ne certifie pas ce livrable et n'impose pas de seuil universel.

## Templates copier/coller
### Entrée
```text
Objet : Agent Role Regression Campaign
Inputs : Versions comparées, cas autorisés/hors périmètre et critères d'acceptation
Version / périmètre autorisé :
Résultat demandé : Campagne versionnée avec résultats réels et cas non exécutés
Contraintes et inconnues :
```

### Sortie
```text
Résultat : Campagne versionnée avec résultats réels et cas non exécutés
| Élément examiné | Preuve / source / version | Conclusion | Limite / action |
|---|---|---|---|
Hypothèses :
Risques :
Prochaines actions :
```

## Checklist QA interne
- [ ] Les inputs et les limites d'autorisation sont identifiés.
- [ ] Les trois analyses sont documentées : construire cas nominaux et contradictoires ; exécuter en environnement contrôlé via l'agent concerné ; comparer résultats et isoler les régressions.
- [ ] Le critère d'acceptation est vérifié ou explicitement marqué non vérifié.
- [ ] Aucun résultat d'exécution ou accord humain n'est inventé.

## KPI reliés
- Couverture des éléments requis : éléments documentés / éléments applicables de ce livrable (dénominateur conservé).
- Part des conclusions appuyées par une preuve ou une source datée ; ne pas compter une hypothèse comme preuve.
- Nombre d'écarts au critère suivant restant ouverts : une simulation de configuration n'est jamais présentée comme une invocation réelle réussie.

## Definition of done
- [ ] Campagne versionnée avec résultats réels et cas non exécutés livré dans le périmètre convenu.
- [ ] Une simulation de configuration n'est jamais présentée comme une invocation réelle réussie.
- [ ] Preuves, inconnues, exceptions et actions restantes sont lisibles ; aucune réussite globale en cas de vérification bloquante manquante.

## Exemples d'usage
**Cas nominal** : à partir de versions comparées, cas autorisés/hors périmètre et critères d'acceptation, produire campagne versionnée avec résultats réels et cas non exécutés puis vérifier le critère d'acceptation ci-dessus.

**Cas limite** : une preuve ou autorisation nécessaire manque ; livrer les éléments établis et indiquer précisément ce qui empêche la validation, sans substituer une valeur par défaut.

## Contraintes et références
- Référence officielle consultée le 2026-10-21 : [Python unittest](https://docs.python.org/3/library/unittest.html). Synthèse originale, sans reproduction du texte source ; vérifier les versions et l'applicabilité au contexte.
- Migration : DEL-20261021-EXCLUSIVE-SKILLS-MIGRATION.

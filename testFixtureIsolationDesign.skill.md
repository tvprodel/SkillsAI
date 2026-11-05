# Test Fixture Isolation Design

## Objectif
Isoler les données et ressources d'une suite de tests pour éviter dépendances d'ordre et effets externes.


## Quand l'utiliser (triggers)
- Demande portant sur « Test Fixture Isolation Design » ou sur le livrable : stratégie de fixtures avec règles de nettoyage et tests d'isolation.
- Besoin de vérifier ce résultat : un test peut être rejoué seul sans dépendre d'un précédent ni toucher une ressource de production.

## Hors périmètre
- Ne pas remplacer les domaines des agents complémentaires : présenter les interfaces et transmettre les besoins à l'agent rattaché (voir table de routage).
- L'exécution système, les modifications de fichiers, les tests et les publications relèvent de l'agent rattaché (voir table de routage) ; cette skill n'accorde aucun outil supplémentaire.
- Ne pas confondre préparation d'un protocole, revue statique et résultat d'une exécution réelle.

## Inputs requis
- Tests, état partagé, services externes et contraintes de parallélisme.
- Périmètre autorisé, version des artefacts, sources accessibles et décisions déjà validées.
- Critères d'acceptation et limites d'action ; marquer les éléments inconnus avant de conclure.

## Sorties attendues
- Stratégie de fixtures avec règles de nettoyage et tests d'isolation.
- Preuves ou références par constat ; hypothèses, exceptions et vérifications non réalisées séparées.
- Brief des décisions ou actions nécessaires pour l'agent rattaché, sans les annoncer déjà exécutées.

## Workflow recommandé
1. Cadrer les inputs : tests, état partagé, services externes et contraintes de parallélisme ; vérifier les préconditions et autorisations.
2. Inventorier ressources créées et modifiées.
3. Définir setup/teardown et doubles aux frontières.
4. Tester indépendance par réordonnancement et rejeu.
5. Vérifier le livrable par ce critère : un test peut être rejoué seul sans dépendre d'un précédent ni toucher une ressource de production.
6. Restituer résultat, hypothèses, risques et prochaines actions ; signaler explicitement les blocages.

## Garde-fous
- Un test peut être rejoué seul sans dépendre d'un précédent ni toucher une ressource de production.
- Ne pas inventer de mesure, d'accord, de preuve ou de source ; distinguer observé, inféré et non testé.
- Ne pas transmettre d'artefact privé ou de donnée personnelle à un service tiers ; minimiser les données sensibles.
- Privilégier les outils libres maintenus et vérifier les versions applicables sans introduire de dépendance EOL.
- Lire la référence dans son contexte : elle éclaire la méthode, elle ne certifie pas ce livrable et n'impose pas de seuil universel.

## Templates copier/coller
### Entrée
```text
Objet : Test Fixture Isolation Design
Inputs : Tests, état partagé, services externes et contraintes de parallélisme
Version / périmètre autorisé :
Résultat demandé : Stratégie de fixtures avec règles de nettoyage et tests d'isolation
Contraintes et inconnues :
```

### Sortie
```text
Résultat : Stratégie de fixtures avec règles de nettoyage et tests d'isolation
| Élément examiné | Preuve / source / version | Conclusion | Limite / action |
|---|---|---|---|
Hypothèses :
Risques :
Prochaines actions :
```

## Checklist QA interne
- [ ] Les inputs et les limites d'autorisation sont identifiés.
- [ ] Les trois analyses sont documentées : inventorier ressources créées et modifiées ; définir setup/teardown et doubles aux frontières ; tester indépendance par réordonnancement et rejeu.
- [ ] Le critère d'acceptation est vérifié ou explicitement marqué non vérifié.
- [ ] Aucun résultat d'exécution ou accord humain n'est inventé.

## KPI reliés
- Couverture des éléments requis : éléments documentés / éléments applicables de ce livrable (dénominateur conservé).
- Part des conclusions appuyées par une preuve ou une source datée ; ne pas compter une hypothèse comme preuve.
- Nombre d'écarts au critère suivant restant ouverts : un test peut être rejoué seul sans dépendre d'un précédent ni toucher une ressource de production.

## Definition of done
- [ ] Stratégie de fixtures avec règles de nettoyage et tests d'isolation livré dans le périmètre convenu.
- [ ] Un test peut être rejoué seul sans dépendre d'un précédent ni toucher une ressource de production.
- [ ] Preuves, inconnues, exceptions et actions restantes sont lisibles ; aucune réussite globale en cas de vérification bloquante manquante.

## Exemples d'usage
**Cas nominal** : à partir de tests, état partagé, services externes et contraintes de parallélisme, produire stratégie de fixtures avec règles de nettoyage et tests d'isolation puis vérifier le critère d'acceptation ci-dessus.

**Cas limite** : une preuve ou autorisation nécessaire manque ; livrer les éléments établis et indiquer précisément ce qui empêche la validation, sans substituer une valeur par défaut.

## Contraintes et références
- Référence officielle consultée le 2026-10-21 : [Python unittest](https://docs.python.org/3/library/unittest.html). Synthèse originale, sans reproduction du texte source ; vérifier les versions et l'applicabilité au contexte.
- Migration : DEL-20261021-EXCLUSIVE-SKILLS-MIGRATION.

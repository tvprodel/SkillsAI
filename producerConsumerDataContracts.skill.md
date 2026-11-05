# Producer-Consumer Data Contracts

## Objectif
Spécifier les engagements d'échange entre un producteur et ses consommateurs de données.


## Quand l'utiliser (triggers)
- Demande portant sur « Producer-Consumer Data Contracts » ou sur le livrable : contrat versionné avec schéma, règles, sla convenus et tests.
- Besoin de vérifier ce résultat : chaque changement incompatible comporte une stratégie de transition validable.

## Hors périmètre
- Ne pas remplacer les domaines des agents complémentaires : présenter les interfaces et transmettre les besoins à l'agent rattaché (voir table de routage).
- L'exécution système, les modifications de fichiers, les tests et les publications relèvent de l'agent rattaché (voir table de routage) ; cette skill n'accorde aucun outil supplémentaire.
- Ne pas confondre préparation d'un protocole, revue statique et résultat d'une exécution réelle.

## Inputs requis
- Schéma, sémantique, fraîcheur attendue, versions et propriétaires.
- Périmètre autorisé, version des artefacts, sources accessibles et décisions déjà validées.
- Critères d'acceptation et limites d'action ; marquer les éléments inconnus avant de conclure.

## Sorties attendues
- Contrat versionné avec schéma, règles, SLA convenus et tests.
- Preuves ou références par constat ; hypothèses, exceptions et vérifications non réalisées séparées.
- Brief des décisions ou actions nécessaires pour l'agent rattaché, sans les annoncer déjà exécutées.

## Workflow recommandé
1. Cadrer les inputs : schéma, sémantique, fraîcheur attendue, versions et propriétaires ; vérifier les préconditions et autorisations.
2. Définir contraintes et compatibilité.
3. Associer chaque exigence à un test.
4. Prévoir annonce de rupture et migration des consommateurs.
5. Vérifier le livrable par ce critère : chaque changement incompatible comporte une stratégie de transition validable.
6. Restituer résultat, hypothèses, risques et prochaines actions ; signaler explicitement les blocages.

## Garde-fous
- Chaque changement incompatible comporte une stratégie de transition validable.
- Ne pas inventer de mesure, d'accord, de preuve ou de source ; distinguer observé, inféré et non testé.
- Ne pas transmettre d'artefact privé ou de donnée personnelle à un service tiers ; minimiser les données sensibles.
- Privilégier les outils libres maintenus et vérifier les versions applicables sans introduire de dépendance EOL.
- Lire la référence dans son contexte : elle éclaire la méthode, elle ne certifie pas ce livrable et n'impose pas de seuil universel.

## Templates copier/coller
### Entrée
```text
Objet : Producer-Consumer Data Contracts
Inputs : Schéma, sémantique, fraîcheur attendue, versions et propriétaires
Version / périmètre autorisé :
Résultat demandé : Contrat versionné avec schéma, règles, SLA convenus et tests
Contraintes et inconnues :
```

### Sortie
```text
Résultat : Contrat versionné avec schéma, règles, SLA convenus et tests
| Élément examiné | Preuve / source / version | Conclusion | Limite / action |
|---|---|---|---|
Hypothèses :
Risques :
Prochaines actions :
```

## Checklist QA interne
- [ ] Les inputs et les limites d'autorisation sont identifiés.
- [ ] Les trois analyses sont documentées : définir contraintes et compatibilité ; associer chaque exigence à un test ; prévoir annonce de rupture et migration des consommateurs.
- [ ] Le critère d'acceptation est vérifié ou explicitement marqué non vérifié.
- [ ] Aucun résultat d'exécution ou accord humain n'est inventé.

## KPI reliés
- Couverture des éléments requis : éléments documentés / éléments applicables de ce livrable (dénominateur conservé).
- Part des conclusions appuyées par une preuve ou une source datée ; ne pas compter une hypothèse comme preuve.
- Nombre d'écarts au critère suivant restant ouverts : chaque changement incompatible comporte une stratégie de transition validable.

## Definition of done
- [ ] Contrat versionné avec schéma, règles, SLA convenus et tests livré dans le périmètre convenu.
- [ ] Chaque changement incompatible comporte une stratégie de transition validable.
- [ ] Preuves, inconnues, exceptions et actions restantes sont lisibles ; aucune réussite globale en cas de vérification bloquante manquante.

## Exemples d'usage
**Cas nominal** : à partir de schéma, sémantique, fraîcheur attendue, versions et propriétaires, produire contrat versionné avec schéma, règles, sla convenus et tests puis vérifier le critère d'acceptation ci-dessus.

**Cas limite** : une preuve ou autorisation nécessaire manque ; livrer les éléments établis et indiquer précisément ce qui empêche la validation, sans substituer une valeur par défaut.

## Contraintes et références
- Référence officielle consultée le 2026-10-21 : [OpenAPI Specification](https://spec.openapis.org/oas/latest.html). Synthèse originale, sans reproduction du texte source ; vérifier les versions et l'applicabilité au contexte.
- Migration : DEL-20261021-EXCLUSIVE-SKILLS-MIGRATION.

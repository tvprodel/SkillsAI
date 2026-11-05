# Data Stewardship Responsibility Design

## Objectif
Définir qui décide et qui agit sur les données partagées d'un domaine.


## Quand l'utiliser (triggers)
- Demande portant sur « Data Stewardship Responsibility Design » ou sur le livrable : matrice de responsabilités et protocole d'arbitrage data.
- Besoin de vérifier ce résultat : chaque décision critique possède un responsable identifiable et une voie d'escalade.

## Hors périmètre
- Ne pas remplacer les domaines des agents complémentaires : présenter les interfaces et transmettre les besoins à l'agent rattaché (voir table de routage).
- L'exécution système, les modifications de fichiers, les tests et les publications relèvent de l'agent rattaché (voir table de routage) ; cette skill n'accorde aucun outil supplémentaire.
- Ne pas confondre préparation d'un protocole, revue statique et résultat d'une exécution réelle.

## Inputs requis
- Domaines, producteurs, consommateurs et décisions à gouverner.
- Périmètre autorisé, version des artefacts, sources accessibles et décisions déjà validées.
- Critères d'acceptation et limites d'action ; marquer les éléments inconnus avant de conclure.

## Sorties attendues
- Matrice de responsabilités et protocole d'arbitrage data.
- Preuves ou références par constat ; hypothèses, exceptions et vérifications non réalisées séparées.
- Brief des décisions ou actions nécessaires pour l'agent rattaché, sans les annoncer déjà exécutées.

## Workflow recommandé
1. Cadrer les inputs : domaines, producteurs, consommateurs et décisions à gouverner ; vérifier les préconditions et autorisations.
2. Séparer propriétaire métier, steward et dépositaire technique.
3. Associer décisions et escalades.
4. Éprouver la répartition sur un incident de qualité.
5. Vérifier le livrable par ce critère : chaque décision critique possède un responsable identifiable et une voie d'escalade.
6. Restituer résultat, hypothèses, risques et prochaines actions ; signaler explicitement les blocages.

## Garde-fous
- Chaque décision critique possède un responsable identifiable et une voie d'escalade.
- Ne pas inventer de mesure, d'accord, de preuve ou de source ; distinguer observé, inféré et non testé.
- Ne pas transmettre d'artefact privé ou de donnée personnelle à un service tiers ; minimiser les données sensibles.
- Privilégier les outils libres maintenus et vérifier les versions applicables sans introduire de dépendance EOL.
- Lire la référence dans son contexte : elle éclaire la méthode, elle ne certifie pas ce livrable et n'impose pas de seuil universel.

## Templates copier/coller
### Entrée
```text
Objet : Data Stewardship Responsibility Design
Inputs : Domaines, producteurs, consommateurs et décisions à gouverner
Version / périmètre autorisé :
Résultat demandé : Matrice de responsabilités et protocole d'arbitrage data
Contraintes et inconnues :
```

### Sortie
```text
Résultat : Matrice de responsabilités et protocole d'arbitrage data
| Élément examiné | Preuve / source / version | Conclusion | Limite / action |
|---|---|---|---|
Hypothèses :
Risques :
Prochaines actions :
```

## Checklist QA interne
- [ ] Les inputs et les limites d'autorisation sont identifiés.
- [ ] Les trois analyses sont documentées : séparer propriétaire métier, steward et dépositaire technique ; associer décisions et escalades ; éprouver la répartition sur un incident de qualité.
- [ ] Le critère d'acceptation est vérifié ou explicitement marqué non vérifié.
- [ ] Aucun résultat d'exécution ou accord humain n'est inventé.

## KPI reliés
- Couverture des éléments requis : éléments documentés / éléments applicables de ce livrable (dénominateur conservé).
- Part des conclusions appuyées par une preuve ou une source datée ; ne pas compter une hypothèse comme preuve.
- Nombre d'écarts au critère suivant restant ouverts : chaque décision critique possède un responsable identifiable et une voie d'escalade.

## Definition of done
- [ ] Matrice de responsabilités et protocole d'arbitrage data livré dans le périmètre convenu.
- [ ] Chaque décision critique possède un responsable identifiable et une voie d'escalade.
- [ ] Preuves, inconnues, exceptions et actions restantes sont lisibles ; aucune réussite globale en cas de vérification bloquante manquante.

## Exemples d'usage
**Cas nominal** : à partir de domaines, producteurs, consommateurs et décisions à gouverner, produire matrice de responsabilités et protocole d'arbitrage data puis vérifier le critère d'acceptation ci-dessus.

**Cas limite** : une preuve ou autorisation nécessaire manque ; livrer les éléments établis et indiquer précisément ce qui empêche la validation, sans substituer une valeur par défaut.

## Contraintes et références
- Référence officielle consultée le 2026-10-21 : [W3C Data Quality Vocabulary](https://www.w3.org/TR/vocab-dqv/). Synthèse originale, sans reproduction du texte source ; vérifier les versions et l'applicabilité au contexte.
- Migration : DEL-20261021-EXCLUSIVE-SKILLS-MIGRATION.

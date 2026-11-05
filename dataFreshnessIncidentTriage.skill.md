# Data Freshness Incident Triage

## Objectif
Qualifier une rupture de fraîcheur d'un jeu de données et son impact consommateur.


## Quand l'utiliser (triggers)
- Demande portant sur « Data Freshness Incident Triage » ou sur le livrable : diagnostic temporel et plan de reprise à faire exécuter par l'agent compétent.
- Besoin de vérifier ce résultat : l'incident ne se clôture pas sur la seule arrivée d'un fichier sans vérification de sa période.

## Hors périmètre
- Ne pas remplacer les domaines des agents complémentaires : présenter les interfaces et transmettre les besoins à l'agent rattaché (voir table de routage).
- L'exécution système, les modifications de fichiers, les tests et les publications relèvent de l'agent rattaché (voir table de routage) ; cette skill n'accorde aucun outil supplémentaire.
- Ne pas confondre préparation d'un protocole, revue statique et résultat d'une exécution réelle.

## Inputs requis
- Horodatages source/ingestion/publication, cadence convenue et dépendances.
- Périmètre autorisé, version des artefacts, sources accessibles et décisions déjà validées.
- Critères d'acceptation et limites d'action ; marquer les éléments inconnus avant de conclure.

## Sorties attendues
- Diagnostic temporel et plan de reprise à faire exécuter par l'agent de coordination.
- Preuves ou références par constat ; hypothèses, exceptions et vérifications non réalisées séparées.
- Brief des décisions ou actions nécessaires pour l'agent rattaché, sans les annoncer déjà exécutées.

## Workflow recommandé
1. Cadrer les inputs : horodatages source/ingestion/publication, cadence convenue et dépendances ; vérifier les préconditions et autorisations.
2. Séparer absence de production et retard de transport.
3. Identifier consommateurs et fenêtres affectés.
4. Préparer reprise avec contrôle des doublons et preuve de rattrapage.
5. Vérifier le livrable par ce critère : l'incident ne se clôture pas sur la seule arrivée d'un fichier sans vérification de sa période.
6. Restituer résultat, hypothèses, risques et prochaines actions ; signaler explicitement les blocages.

## Garde-fous
- L'incident ne se clôture pas sur la seule arrivée d'un fichier sans vérification de sa période.
- Ne pas inventer de mesure, d'accord, de preuve ou de source ; distinguer observé, inféré et non testé.
- Ne pas transmettre d'artefact privé ou de donnée personnelle à un service tiers ; minimiser les données sensibles.
- Privilégier les outils libres maintenus et vérifier les versions applicables sans introduire de dépendance EOL.
- Lire la référence dans son contexte : elle éclaire la méthode, elle ne certifie pas ce livrable et n'impose pas de seuil universel.

## Templates copier/coller
### Entrée
```text
Objet : Data Freshness Incident Triage
Inputs : Horodatages source/ingestion/publication, cadence convenue et dépendances
Version / périmètre autorisé :
Résultat demandé : Diagnostic temporel et plan de reprise à faire exécuter par l'agent de coordination
Contraintes et inconnues :
```

### Sortie
```text
Résultat : Diagnostic temporel et plan de reprise à faire exécuter par l'agent de coordination
| Élément examiné | Preuve / source / version | Conclusion | Limite / action |
|---|---|---|---|
Hypothèses :
Risques :
Prochaines actions :
```

## Checklist QA interne
- [ ] Les inputs et les limites d'autorisation sont identifiés.
- [ ] Les trois analyses sont documentées : séparer absence de production et retard de transport ; identifier consommateurs et fenêtres affectés ; préparer reprise avec contrôle des doublons et preuve de rattrapage.
- [ ] Le critère d'acceptation est vérifié ou explicitement marqué non vérifié.
- [ ] Aucun résultat d'exécution ou accord humain n'est inventé.

## KPI reliés
- Couverture des éléments requis : éléments documentés / éléments applicables de ce livrable (dénominateur conservé).
- Part des conclusions appuyées par une preuve ou une source datée ; ne pas compter une hypothèse comme preuve.
- Nombre d'écarts au critère suivant restant ouverts : l'incident ne se clôture pas sur la seule arrivée d'un fichier sans vérification de sa période.

## Definition of done
- [ ] Diagnostic temporel et plan de reprise à faire exécuter par l'agent de coordination livré dans le périmètre convenu.
- [ ] L'incident ne se clôture pas sur la seule arrivée d'un fichier sans vérification de sa période.
- [ ] Preuves, inconnues, exceptions et actions restantes sont lisibles ; aucune réussite globale en cas de vérification bloquante manquante.

## Exemples d'usage
**Cas nominal** : à partir de horodatages source/ingestion/publication, cadence convenue et dépendances, produire diagnostic temporel et plan de reprise à faire exécuter par l'agent compétent puis vérifier le critère d'acceptation ci-dessus.

**Cas limite** : une preuve ou autorisation nécessaire manque ; livrer les éléments établis et indiquer précisément ce qui empêche la validation, sans substituer une valeur par défaut.

## Contraintes et références
- Référence officielle consultée le 2026-10-21 : [W3C Data Quality Vocabulary](https://www.w3.org/TR/vocab-dqv/). Synthèse originale, sans reproduction du texte source ; vérifier les versions et l'applicabilité au contexte.
- Migration : DEL-20261021-EXCLUSIVE-SKILLS-MIGRATION.

# Brief Assumption Ledger

## Objectif
Rendre explicites les hypothèses qui conditionnent un brief avant la décision de routage de l'agent de coordination.


## Quand l'utiliser (triggers)
- Demande portant sur « Brief Assumption Ledger » ou sur le livrable : registre hypothèse/preuve/impact/décision attendue.
- Besoin de vérifier ce résultat : aucune hypothèse bloquante ne figure comme fait acquis.

## Hors périmètre
- Ne pas remplacer les domaines des agents complémentaires : présenter les interfaces et transmettre les besoins à l'agent rattaché (voir table de routage).
- L'exécution système, les modifications de fichiers, les tests et les publications relèvent de l'agent rattaché (voir table de routage) ; cette skill n'accorde aucun outil supplémentaire.
- Ne pas confondre préparation d'un protocole, revue statique et résultat d'une exécution réelle.

## Inputs requis
- Brief, décisions attendues, faits établis, inconnues.
- Périmètre autorisé, version des artefacts, sources accessibles et décisions déjà validées.
- Critères d'acceptation et limites d'action ; marquer les éléments inconnus avant de conclure.

## Sorties attendues
- Registre hypothèse/preuve/impact/décision attendue.
- Preuves ou références par constat ; hypothèses, exceptions et vérifications non réalisées séparées.
- Brief des décisions ou actions nécessaires pour l'agent rattaché, sans les annoncer déjà exécutées.

## Workflow recommandé
1. Cadrer les inputs : brief, décisions attendues, faits établis, inconnues ; vérifier les préconditions et autorisations.
2. Extraire les prémisses non prouvées.
3. Relier chaque prémisse à la décision affectée.
4. Proposer la preuve ou clarification minimale nécessaire.
5. Vérifier le livrable par ce critère : aucune hypothèse bloquante ne figure comme fait acquis.
6. Restituer résultat, hypothèses, risques et prochaines actions ; signaler explicitement les blocages.

## Garde-fous
- Aucune hypothèse bloquante ne figure comme fait acquis.
- Ne pas inventer de mesure, d'accord, de preuve ou de source ; distinguer observé, inféré et non testé.
- Ne pas transmettre d'artefact privé ou de donnée personnelle à un service tiers ; minimiser les données sensibles.
- Privilégier les outils libres maintenus et vérifier les versions applicables sans introduire de dépendance EOL.
- Lire la référence dans son contexte : elle éclaire la méthode, elle ne certifie pas ce livrable et n'impose pas de seuil universel.

## Templates copier/coller
### Entrée
```text
Objet : Brief Assumption Ledger
Inputs : Brief, décisions attendues, faits établis, inconnues
Version / périmètre autorisé :
Résultat demandé : Registre hypothèse/preuve/impact/décision attendue
Contraintes et inconnues :
```

### Sortie
```text
Résultat : Registre hypothèse/preuve/impact/décision attendue
| Élément examiné | Preuve / source / version | Conclusion | Limite / action |
|---|---|---|---|
Hypothèses :
Risques :
Prochaines actions :
```

## Checklist QA interne
- [ ] Les inputs et les limites d'autorisation sont identifiés.
- [ ] Les trois analyses sont documentées : extraire les prémisses non prouvées ; relier chaque prémisse à la décision affectée ; proposer la preuve ou clarification minimale nécessaire.
- [ ] Le critère d'acceptation est vérifié ou explicitement marqué non vérifié.
- [ ] Aucun résultat d'exécution ou accord humain n'est inventé.

## KPI reliés
- Couverture des éléments requis : éléments documentés / éléments applicables de ce livrable (dénominateur conservé).
- Part des conclusions appuyées par une preuve ou une source datée ; ne pas compter une hypothèse comme preuve.
- Nombre d'écarts au critère suivant restant ouverts : aucune hypothèse bloquante ne figure comme fait acquis.

## Definition of done
- [ ] Registre hypothèse/preuve/impact/décision attendue livré dans le périmètre convenu.
- [ ] Aucune hypothèse bloquante ne figure comme fait acquis.
- [ ] Preuves, inconnues, exceptions et actions restantes sont lisibles ; aucune réussite globale en cas de vérification bloquante manquante.

## Exemples d'usage
**Cas nominal** : à partir de brief, décisions attendues, faits établis, inconnues, produire registre hypothèse/preuve/impact/décision attendue puis vérifier le critère d'acceptation ci-dessus.

**Cas limite** : une preuve ou autorisation nécessaire manque ; livrer les éléments établis et indiquer précisément ce qui empêche la validation, sans substituer une valeur par défaut.

## Contraintes et références
- Référence officielle consultée le 2026-10-21 : [W3C PROV Overview](https://www.w3.org/TR/prov-overview/). Synthèse originale, sans reproduction du texte source ; vérifier les versions et l'applicabilité au contexte.
- Migration : DEL-20261021-EXCLUSIVE-SKILLS-MIGRATION.

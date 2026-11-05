# Protected-Group Evaluation Protocol

## Objectif
Concevoir une évaluation de disparités respectueuse des personnes et des limites des données.


## Quand l'utiliser (triggers)
- Demande portant sur « Protected-Group Evaluation Protocol » ou sur le livrable : protocole de fairness avec limites statistiques et éthiques.
- Besoin de vérifier ce résultat : aucun attribut sensible n'est inféré pour compléter un groupe manquant.

## Hors périmètre
- Ne pas remplacer les domaines des agents complémentaires : présenter les interfaces et transmettre les besoins à l'agent rattaché (voir table de routage).
- L'exécution système, les modifications de fichiers, les tests et les publications relèvent de l'agent rattaché (voir table de routage) ; cette skill n'accorde aucun outil supplémentaire.
- Ne pas confondre préparation d'un protocole, revue statique et résultat d'une exécution réelle.

## Inputs requis
- Objectif d'évaluation, groupes autorisés, base de traitement confirmée et métriques.
- Périmètre autorisé, version des artefacts, sources accessibles et décisions déjà validées.
- Critères d'acceptation et limites d'action ; marquer les éléments inconnus avant de conclure.

## Sorties attendues
- Protocole de fairness avec limites statistiques et éthiques.
- Preuves ou références par constat ; hypothèses, exceptions et vérifications non réalisées séparées.
- Brief des décisions ou actions nécessaires pour l'agent rattaché, sans les annoncer déjà exécutées.

## Workflow recommandé
1. Cadrer les inputs : objectif d'évaluation, groupes autorisés, base de traitement confirmée et métriques ; vérifier les préconditions et autorisations.
2. Vérifier légitimité et minimisation des données.
3. Définir métriques, incertitude et tailles de groupe.
4. Prévoir interprétation contextualisée et escalade des résultats.
5. Vérifier le livrable par ce critère : aucun attribut sensible n'est inféré pour compléter un groupe manquant.
6. Restituer résultat, hypothèses, risques et prochaines actions ; signaler explicitement les blocages.

## Garde-fous
- Aucun attribut sensible n'est inféré pour compléter un groupe manquant.
- Ne pas inventer de mesure, d'accord, de preuve ou de source ; distinguer observé, inféré et non testé.
- Ne pas transmettre d'artefact privé ou de donnée personnelle à un service tiers ; minimiser les données sensibles.
- Privilégier les outils libres maintenus et vérifier les versions applicables sans introduire de dépendance EOL.
- Lire la référence dans son contexte : elle éclaire la méthode, elle ne certifie pas ce livrable et n'impose pas de seuil universel.

## Templates copier/coller
### Entrée
```text
Objet : Protected-Group Evaluation Protocol
Inputs : Objectif d'évaluation, groupes autorisés, base de traitement confirmée et métriques
Version / périmètre autorisé :
Résultat demandé : Protocole de fairness avec limites statistiques et éthiques
Contraintes et inconnues :
```

### Sortie
```text
Résultat : Protocole de fairness avec limites statistiques et éthiques
| Élément examiné | Preuve / source / version | Conclusion | Limite / action |
|---|---|---|---|
Hypothèses :
Risques :
Prochaines actions :
```

## Checklist QA interne
- [ ] Les inputs et les limites d'autorisation sont identifiés.
- [ ] Les trois analyses sont documentées : vérifier légitimité et minimisation des données ; définir métriques, incertitude et tailles de groupe ; prévoir interprétation contextualisée et escalade des résultats.
- [ ] Le critère d'acceptation est vérifié ou explicitement marqué non vérifié.
- [ ] Aucun résultat d'exécution ou accord humain n'est inventé.

## KPI reliés
- Couverture des éléments requis : éléments documentés / éléments applicables de ce livrable (dénominateur conservé).
- Part des conclusions appuyées par une preuve ou une source datée ; ne pas compter une hypothèse comme preuve.
- Nombre d'écarts au critère suivant restant ouverts : aucun attribut sensible n'est inféré pour compléter un groupe manquant.

## Definition of done
- [ ] Protocole de fairness avec limites statistiques et éthiques livré dans le périmètre convenu.
- [ ] Aucun attribut sensible n'est inféré pour compléter un groupe manquant.
- [ ] Preuves, inconnues, exceptions et actions restantes sont lisibles ; aucune réussite globale en cas de vérification bloquante manquante.

## Exemples d'usage
**Cas nominal** : à partir de objectif d'évaluation, groupes autorisés, base de traitement confirmée et métriques, produire protocole de fairness avec limites statistiques et éthiques puis vérifier le critère d'acceptation ci-dessus.

**Cas limite** : une preuve ou autorisation nécessaire manque ; livrer les éléments établis et indiquer précisément ce qui empêche la validation, sans substituer une valeur par défaut.

## Contraintes et références
- Référence officielle consultée le 2026-10-21 : [NIST AI Risk Management Framework](https://www.nist.gov/itl/ai-risk-management-framework). Synthèse originale, sans reproduction du texte source ; vérifier les versions et l'applicabilité au contexte.
- Migration : DEL-20261021-EXCLUSIVE-SKILLS-MIGRATION.

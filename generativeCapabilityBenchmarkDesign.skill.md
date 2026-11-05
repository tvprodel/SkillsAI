# Generative Capability Benchmark Design

## Objectif
Comparer des capacités de modèles génératifs sur des tâches représentatives du besoin.


## Quand l'utiliser (triggers)
- Demande portant sur « Generative Capability Benchmark Design » ou sur le livrable : benchmark de sélection avec cas, rubriques et limites.
- Besoin de vérifier ce résultat : les versions et conditions de mesure sont enregistrées et les résultats non exécutés restent planifiés.

## Hors périmètre
- Ne pas remplacer les domaines des agents complémentaires : présenter les interfaces et transmettre les besoins à l'agent rattaché (voir table de routage).
- L'exécution système, les modifications de fichiers, les tests et les publications relèvent de l'agent rattaché (voir table de routage) ; cette skill n'accorde aucun outil supplémentaire.
- Ne pas confondre préparation d'un protocole, revue statique et résultat d'une exécution réelle.

## Inputs requis
- Tâches, contraintes, modèles candidats et critères d'évaluation.
- Périmètre autorisé, version des artefacts, sources accessibles et décisions déjà validées.
- Critères d'acceptation et limites d'action ; marquer les éléments inconnus avant de conclure.

## Sorties attendues
- Benchmark de sélection avec cas, rubriques et limites.
- Preuves ou références par constat ; hypothèses, exceptions et vérifications non réalisées séparées.
- Brief des décisions ou actions nécessaires pour l'agent rattaché, sans les annoncer déjà exécutées.

## Workflow recommandé
1. Cadrer les inputs : tâches, contraintes, modèles candidats et critères d'évaluation ; vérifier les préconditions et autorisations.
2. Échantillonner des tâches réalistes sans données confidentielles.
3. Fixer protocole et paramètres comparables.
4. Analyser compromis capacité/robustesse/coût sans choisir sur un score isolé.
5. Vérifier le livrable par ce critère : les versions et conditions de mesure sont enregistrées et les résultats non exécutés restent planifiés.
6. Restituer résultat, hypothèses, risques et prochaines actions ; signaler explicitement les blocages.

## Garde-fous
- Les versions et conditions de mesure sont enregistrées et les résultats non exécutés restent planifiés.
- Ne pas inventer de mesure, d'accord, de preuve ou de source ; distinguer observé, inféré et non testé.
- Ne pas transmettre d'artefact privé ou de donnée personnelle à un service tiers ; minimiser les données sensibles.
- Privilégier les outils libres maintenus et vérifier les versions applicables sans introduire de dépendance EOL.
- Lire la référence dans son contexte : elle éclaire la méthode, elle ne certifie pas ce livrable et n'impose pas de seuil universel.

## Templates copier/coller
### Entrée
```text
Objet : Generative Capability Benchmark Design
Inputs : Tâches, contraintes, modèles candidats et critères d'évaluation
Version / périmètre autorisé :
Résultat demandé : Benchmark de sélection avec cas, rubriques et limites
Contraintes et inconnues :
```

### Sortie
```text
Résultat : Benchmark de sélection avec cas, rubriques et limites
| Élément examiné | Preuve / source / version | Conclusion | Limite / action |
|---|---|---|---|
Hypothèses :
Risques :
Prochaines actions :
```

## Checklist QA interne
- [ ] Les inputs et les limites d'autorisation sont identifiés.
- [ ] Les trois analyses sont documentées : échantillonner des tâches réalistes sans données confidentielles ; fixer protocole et paramètres comparables ; analyser compromis capacité/robustesse/coût sans choisir sur un score isolé.
- [ ] Le critère d'acceptation est vérifié ou explicitement marqué non vérifié.
- [ ] Aucun résultat d'exécution ou accord humain n'est inventé.

## KPI reliés
- Couverture des éléments requis : éléments documentés / éléments applicables de ce livrable (dénominateur conservé).
- Part des conclusions appuyées par une preuve ou une source datée ; ne pas compter une hypothèse comme preuve.
- Nombre d'écarts au critère suivant restant ouverts : les versions et conditions de mesure sont enregistrées et les résultats non exécutés restent planifiés.

## Definition of done
- [ ] Benchmark de sélection avec cas, rubriques et limites livré dans le périmètre convenu.
- [ ] Les versions et conditions de mesure sont enregistrées et les résultats non exécutés restent planifiés.
- [ ] Preuves, inconnues, exceptions et actions restantes sont lisibles ; aucune réussite globale en cas de vérification bloquante manquante.

## Exemples d'usage
**Cas nominal** : à partir de tâches, contraintes, modèles candidats et critères d'évaluation, produire benchmark de sélection avec cas, rubriques et limites puis vérifier le critère d'acceptation ci-dessus.

**Cas limite** : une preuve ou autorisation nécessaire manque ; livrer les éléments établis et indiquer précisément ce qui empêche la validation, sans substituer une valeur par défaut.

## Contraintes et références
- Référence officielle consultée le 2026-10-21 : [NIST AI Risk Management Framework](https://www.nist.gov/itl/ai-risk-management-framework). Synthèse originale, sans reproduction du texte source ; vérifier les versions et l'applicabilité au contexte.
- Migration : DEL-20261021-EXCLUSIVE-SKILLS-MIGRATION.

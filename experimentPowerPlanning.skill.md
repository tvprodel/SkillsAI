# Experiment Power Planning

## Objectif
Préparer le dimensionnement et la règle d'arrêt d'une expérience analytique.


## Quand l'utiliser (triggers)
- Demande portant sur « Experiment Power Planning » ou sur le livrable : plan de puissance avec hypothèses et scénarios de sensibilité.
- Besoin de vérifier ce résultat : aucune taille d'échantillon n'est garantie sans hypothèses et méthode explicites.

## Hors périmètre
- Ne pas remplacer les domaines des agents complémentaires : présenter les interfaces et transmettre les besoins à l'agent rattaché (voir table de routage).
- L'exécution système, les modifications de fichiers, les tests et les publications relèvent de l'agent rattaché (voir table de routage) ; cette skill n'accorde aucun outil supplémentaire.
- Ne pas confondre préparation d'un protocole, revue statique et résultat d'une exécution réelle.

## Inputs requis
- Effet minimal utile, variance estimée, allocation et coût d'erreur.
- Périmètre autorisé, version des artefacts, sources accessibles et décisions déjà validées.
- Critères d'acceptation et limites d'action ; marquer les éléments inconnus avant de conclure.

## Sorties attendues
- Plan de puissance avec hypothèses et scénarios de sensibilité.
- Preuves ou références par constat ; hypothèses, exceptions et vérifications non réalisées séparées.
- Brief des décisions ou actions nécessaires pour l'agent rattaché, sans les annoncer déjà exécutées.

## Workflow recommandé
1. Cadrer les inputs : effet minimal utile, variance estimée, allocation et coût d'erreur ; vérifier les préconditions et autorisations.
2. Justifier effet cible et risques d'erreur.
3. Estimer sensibilité aux hypothèses de variance.
4. Définir arrêt et analyse avant observation des résultats.
5. Vérifier le livrable par ce critère : aucune taille d'échantillon n'est garantie sans hypothèses et méthode explicites.
6. Restituer résultat, hypothèses, risques et prochaines actions ; signaler explicitement les blocages.

## Garde-fous
- Aucune taille d'échantillon n'est garantie sans hypothèses et méthode explicites.
- Ne pas inventer de mesure, d'accord, de preuve ou de source ; distinguer observé, inféré et non testé.
- Ne pas transmettre d'artefact privé ou de donnée personnelle à un service tiers ; minimiser les données sensibles.
- Privilégier les outils libres maintenus et vérifier les versions applicables sans introduire de dépendance EOL.
- Lire la référence dans son contexte : elle éclaire la méthode, elle ne certifie pas ce livrable et n'impose pas de seuil universel.

## Templates copier/coller
### Entrée
```text
Objet : Experiment Power Planning
Inputs : Effet minimal utile, variance estimée, allocation et coût d'erreur
Version / périmètre autorisé :
Résultat demandé : Plan de puissance avec hypothèses et scénarios de sensibilité
Contraintes et inconnues :
```

### Sortie
```text
Résultat : Plan de puissance avec hypothèses et scénarios de sensibilité
| Élément examiné | Preuve / source / version | Conclusion | Limite / action |
|---|---|---|---|
Hypothèses :
Risques :
Prochaines actions :
```

## Checklist QA interne
- [ ] Les inputs et les limites d'autorisation sont identifiés.
- [ ] Les trois analyses sont documentées : justifier effet cible et risques d'erreur ; estimer sensibilité aux hypothèses de variance ; définir arrêt et analyse avant observation des résultats.
- [ ] Le critère d'acceptation est vérifié ou explicitement marqué non vérifié.
- [ ] Aucun résultat d'exécution ou accord humain n'est inventé.

## KPI reliés
- Couverture des éléments requis : éléments documentés / éléments applicables de ce livrable (dénominateur conservé).
- Part des conclusions appuyées par une preuve ou une source datée ; ne pas compter une hypothèse comme preuve.
- Nombre d'écarts au critère suivant restant ouverts : aucune taille d'échantillon n'est garantie sans hypothèses et méthode explicites.

## Definition of done
- [ ] Plan de puissance avec hypothèses et scénarios de sensibilité livré dans le périmètre convenu.
- [ ] Aucune taille d'échantillon n'est garantie sans hypothèses et méthode explicites.
- [ ] Preuves, inconnues, exceptions et actions restantes sont lisibles ; aucune réussite globale en cas de vérification bloquante manquante.

## Exemples d'usage
**Cas nominal** : à partir de effet minimal utile, variance estimée, allocation et coût d'erreur, produire plan de puissance avec hypothèses et scénarios de sensibilité puis vérifier le critère d'acceptation ci-dessus.

**Cas limite** : une preuve ou autorisation nécessaire manque ; livrer les éléments établis et indiquer précisément ce qui empêche la validation, sans substituer une valeur par défaut.

## Contraintes et références
- Référence officielle consultée le 2026-10-21 : [scikit-learn - Model selection and evaluation](https://scikit-learn.org/stable/model_selection.html). Synthèse originale, sans reproduction du texte source ; vérifier les versions et l'applicabilité au contexte.
- Migration : DEL-20261021-EXCLUSIVE-SKILLS-MIGRATION.

# Statistical Inference Protocol

## Objectif
Choisir une analyse statistique compatible avec la question, l'échantillonnage et les hypothèses.


## Quand l'utiliser (triggers)
- Demande portant sur « Statistical Inference Protocol » ou sur le livrable : protocole d'inférence avec méthode et diagnostics attendus.
- Besoin de vérifier ce résultat : la significativité ne remplace ni taille d'effet ni examen des biais de sélection.

## Hors périmètre
- Ne pas remplacer les domaines des agents complémentaires : présenter les interfaces et transmettre les besoins à l'agent rattaché (voir table de routage).
- L'exécution système, les modifications de fichiers, les tests et les publications relèvent de l'agent rattaché (voir table de routage) ; cette skill n'accorde aucun outil supplémentaire.
- Ne pas confondre préparation d'un protocole, revue statique et résultat d'une exécution réelle.

## Inputs requis
- Question, variables, plan de collecte, dépendances et taille d'échantillon.
- Périmètre autorisé, version des artefacts, sources accessibles et décisions déjà validées.
- Critères d'acceptation et limites d'action ; marquer les éléments inconnus avant de conclure.

## Sorties attendues
- Protocole d'inférence avec méthode et diagnostics attendus.
- Preuves ou références par constat ; hypothèses, exceptions et vérifications non réalisées séparées.
- Brief des décisions ou actions nécessaires pour l'agent rattaché, sans les annoncer déjà exécutées.

## Workflow recommandé
1. Cadrer les inputs : question, variables, plan de collecte, dépendances et taille d'échantillon ; vérifier les préconditions et autorisations.
2. Définir estimand et hypothèse.
3. Vérifier conditions de la méthode et alternatives.
4. Rapporter incertitude, taille d'effet et limites causales.
5. Vérifier le livrable par ce critère : la significativité ne remplace ni taille d'effet ni examen des biais de sélection.
6. Restituer résultat, hypothèses, risques et prochaines actions ; signaler explicitement les blocages.

## Garde-fous
- La significativité ne remplace ni taille d'effet ni examen des biais de sélection.
- Ne pas inventer de mesure, d'accord, de preuve ou de source ; distinguer observé, inféré et non testé.
- Ne pas transmettre d'artefact privé ou de donnée personnelle à un service tiers ; minimiser les données sensibles.
- Privilégier les outils libres maintenus et vérifier les versions applicables sans introduire de dépendance EOL.
- Lire la référence dans son contexte : elle éclaire la méthode, elle ne certifie pas ce livrable et n'impose pas de seuil universel.

## Templates copier/coller
### Entrée
```text
Objet : Statistical Inference Protocol
Inputs : Question, variables, plan de collecte, dépendances et taille d'échantillon
Version / périmètre autorisé :
Résultat demandé : Protocole d'inférence avec méthode et diagnostics attendus
Contraintes et inconnues :
```

### Sortie
```text
Résultat : Protocole d'inférence avec méthode et diagnostics attendus
| Élément examiné | Preuve / source / version | Conclusion | Limite / action |
|---|---|---|---|
Hypothèses :
Risques :
Prochaines actions :
```

## Checklist QA interne
- [ ] Les inputs et les limites d'autorisation sont identifiés.
- [ ] Les trois analyses sont documentées : définir estimand et hypothèse ; vérifier conditions de la méthode et alternatives ; rapporter incertitude, taille d'effet et limites causales.
- [ ] Le critère d'acceptation est vérifié ou explicitement marqué non vérifié.
- [ ] Aucun résultat d'exécution ou accord humain n'est inventé.

## KPI reliés
- Couverture des éléments requis : éléments documentés / éléments applicables de ce livrable (dénominateur conservé).
- Part des conclusions appuyées par une preuve ou une source datée ; ne pas compter une hypothèse comme preuve.
- Nombre d'écarts au critère suivant restant ouverts : la significativité ne remplace ni taille d'effet ni examen des biais de sélection.

## Definition of done
- [ ] Protocole d'inférence avec méthode et diagnostics attendus livré dans le périmètre convenu.
- [ ] La significativité ne remplace ni taille d'effet ni examen des biais de sélection.
- [ ] Preuves, inconnues, exceptions et actions restantes sont lisibles ; aucune réussite globale en cas de vérification bloquante manquante.

## Exemples d'usage
**Cas nominal** : à partir de question, variables, plan de collecte, dépendances et taille d'échantillon, produire protocole d'inférence avec méthode et diagnostics attendus puis vérifier le critère d'acceptation ci-dessus.

**Cas limite** : une preuve ou autorisation nécessaire manque ; livrer les éléments établis et indiquer précisément ce qui empêche la validation, sans substituer une valeur par défaut.

## Contraintes et références
- Référence officielle consultée le 2026-10-21 : [scikit-learn - Model selection and evaluation](https://scikit-learn.org/stable/model_selection.html). Synthèse originale, sans reproduction du texte source ; vérifier les versions et l'applicabilité au contexte.
- Migration : DEL-20261021-EXCLUSIVE-SKILLS-MIGRATION.

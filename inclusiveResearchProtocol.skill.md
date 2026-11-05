# Inclusive Research Protocol

## Objectif
Concevoir une étude qualitative accessible pour examiner une hypothèse cognitive sans inférer de diagnostic.


## Quand l'utiliser (triggers)
- Demande portant sur « Inclusive Research Protocol » ou sur le livrable : protocole de séance avec adaptations et grille d'observation.
- Besoin de vérifier ce résultat : chaque hypothèse possède une observation attendue et un mode de recueil consenti.

## Hors périmètre
- Ne pas remplacer les domaines des agents complémentaires : présenter les interfaces et transmettre les besoins à l'agent rattaché (voir table de routage).
- L'exécution système, les modifications de fichiers, les tests et les publications relèvent de l'agent rattaché (voir table de routage) ; cette skill n'accorde aucun outil supplémentaire.
- Ne pas confondre préparation d'un protocole, revue statique et résultat d'une exécution réelle.

## Inputs requis
- Question UX, publics volontaires, modalités de consentement, contraintes sensorielles.
- Périmètre autorisé, version des artefacts, sources accessibles et décisions déjà validées.
- Critères d'acceptation et limites d'action ; marquer les éléments inconnus avant de conclure.

## Sorties attendues
- Protocole de séance avec adaptations et grille d'observation.
- Preuves ou références par constat ; hypothèses, exceptions et vérifications non réalisées séparées.
- Brief des décisions ou actions nécessaires pour l'agent rattaché, sans les annoncer déjà exécutées.

## Workflow recommandé
1. Cadrer les inputs : question ux, publics volontaires, modalités de consentement, contraintes sensorielles ; vérifier les préconditions et autorisations.
2. Formuler une hypothèse réfutable.
3. Adapter consignes et durée aux besoins déclarés.
4. Séparer observations, interprétations et limites de recrutement.
5. Vérifier le livrable par ce critère : chaque hypothèse possède une observation attendue et un mode de recueil consenti.
6. Restituer résultat, hypothèses, risques et prochaines actions ; signaler explicitement les blocages.

## Garde-fous
- Chaque hypothèse possède une observation attendue et un mode de recueil consenti.
- Ne pas inventer de mesure, d'accord, de preuve ou de source ; distinguer observé, inféré et non testé.
- Ne pas transmettre d'artefact privé ou de donnée personnelle à un service tiers ; minimiser les données sensibles.
- Privilégier les outils libres maintenus et vérifier les versions applicables sans introduire de dépendance EOL.
- Lire la référence dans son contexte : elle éclaire la méthode, elle ne certifie pas ce livrable et n'impose pas de seuil universel.

## Templates copier/coller
### Entrée
```text
Objet : Inclusive Research Protocol
Inputs : Question UX, publics volontaires, modalités de consentement, contraintes sensorielles
Version / périmètre autorisé :
Résultat demandé : Protocole de séance avec adaptations et grille d'observation
Contraintes et inconnues :
```

### Sortie
```text
Résultat : Protocole de séance avec adaptations et grille d'observation
| Élément examiné | Preuve / source / version | Conclusion | Limite / action |
|---|---|---|---|
Hypothèses :
Risques :
Prochaines actions :
```

## Checklist QA interne
- [ ] Les inputs et les limites d'autorisation sont identifiés.
- [ ] Les trois analyses sont documentées : formuler une hypothèse réfutable ; adapter consignes et durée aux besoins déclarés ; séparer observations, interprétations et limites de recrutement.
- [ ] Le critère d'acceptation est vérifié ou explicitement marqué non vérifié.
- [ ] Aucun résultat d'exécution ou accord humain n'est inventé.

## KPI reliés
- Couverture des éléments requis : éléments documentés / éléments applicables de ce livrable (dénominateur conservé).
- Part des conclusions appuyées par une preuve ou une source datée ; ne pas compter une hypothèse comme preuve.
- Nombre d'écarts au critère suivant restant ouverts : chaque hypothèse possède une observation attendue et un mode de recueil consenti.

## Definition of done
- [ ] Protocole de séance avec adaptations et grille d'observation livré dans le périmètre convenu.
- [ ] Chaque hypothèse possède une observation attendue et un mode de recueil consenti.
- [ ] Preuves, inconnues, exceptions et actions restantes sont lisibles ; aucune réussite globale en cas de vérification bloquante manquante.

## Exemples d'usage
**Cas nominal** : à partir de question ux, publics volontaires, modalités de consentement, contraintes sensorielles, produire protocole de séance avec adaptations et grille d'observation puis vérifier le critère d'acceptation ci-dessus.

**Cas limite** : une preuve ou autorisation nécessaire manque ; livrer les éléments établis et indiquer précisément ce qui empêche la validation, sans substituer une valeur par défaut.

## Contraintes et références
- Référence officielle consultée le 2026-10-21 : [W3C COGA - Making Content Usable](https://www.w3.org/TR/coga-usable/). Synthèse originale, sans reproduction du texte source ; vérifier les versions et l'applicabilité au contexte.
- Migration : DEL-20261021-EXCLUSIVE-SKILLS-MIGRATION.

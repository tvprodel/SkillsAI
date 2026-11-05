# Cookie Consent Evidence Review

## Objectif
Examiner si les choix et preuves de consentement reflètent le comportement réel d'un produit.


## Quand l'utiliser (triggers)
- Demande portant sur « Cookie Consent Evidence Review » ou sur le livrable : matrice choix/traceur/activation/preuve/écart.
- Besoin de vérifier ce résultat : l'affichage d'une bannière ne vaut pas preuve d'absence de traceur avant choix.

## Hors périmètre
- Ne pas remplacer les domaines des agents complémentaires : présenter les interfaces et transmettre les besoins à l'agent rattaché (voir table de routage).
- L'exécution système, les modifications de fichiers, les tests et les publications relèvent de l'agent rattaché (voir table de routage) ; cette skill n'accorde aucun outil supplémentaire.
- Ne pas confondre préparation d'un protocole, revue statique et résultat d'une exécution réelle.

## Inputs requis
- Inventaire traceurs, finalités, UI de choix et preuves techniques.
- Périmètre autorisé, version des artefacts, sources accessibles et décisions déjà validées.
- Critères d'acceptation et limites d'action ; marquer les éléments inconnus avant de conclure.

## Sorties attendues
- Matrice choix/traceur/activation/preuve/écart.
- Preuves ou références par constat ; hypothèses, exceptions et vérifications non réalisées séparées.
- Brief des décisions ou actions nécessaires pour l'agent rattaché, sans les annoncer déjà exécutées.

## Workflow recommandé
1. Cadrer les inputs : inventaire traceurs, finalités, ui de choix et preuves techniques ; vérifier les préconditions et autorisations.
2. Distinguer finalités et nécessité à confirmer.
3. Comparer choix accepté/refusé/retiré aux déclenchements observés.
4. Lister écarts et validations juridiques.
5. Vérifier le livrable par ce critère : l'affichage d'une bannière ne vaut pas preuve d'absence de traceur avant choix.
6. Restituer résultat, hypothèses, risques et prochaines actions ; signaler explicitement les blocages.

## Garde-fous
- L'affichage d'une bannière ne vaut pas preuve d'absence de traceur avant choix.
- Ne pas inventer de mesure, d'accord, de preuve ou de source ; distinguer observé, inféré et non testé.
- Ne pas transmettre d'artefact privé ou de donnée personnelle à un service tiers ; minimiser les données sensibles.
- Privilégier les outils libres maintenus et vérifier les versions applicables sans introduire de dépendance EOL.
- Lire la référence dans son contexte : elle éclaire la méthode, elle ne certifie pas ce livrable et n'impose pas de seuil universel.

## Templates copier/coller
### Entrée
```text
Objet : Cookie Consent Evidence Review
Inputs : Inventaire traceurs, finalités, UI de choix et preuves techniques
Version / périmètre autorisé :
Résultat demandé : Matrice choix/traceur/activation/preuve/écart
Contraintes et inconnues :
```

### Sortie
```text
Résultat : Matrice choix/traceur/activation/preuve/écart
| Élément examiné | Preuve / source / version | Conclusion | Limite / action |
|---|---|---|---|
Hypothèses :
Risques :
Prochaines actions :
```

## Checklist QA interne
- [ ] Les inputs et les limites d'autorisation sont identifiés.
- [ ] Les trois analyses sont documentées : distinguer finalités et nécessité à confirmer ; comparer choix accepté/refusé/retiré aux déclenchements observés ; lister écarts et validations juridiques.
- [ ] Le critère d'acceptation est vérifié ou explicitement marqué non vérifié.
- [ ] Aucun résultat d'exécution ou accord humain n'est inventé.

## KPI reliés
- Couverture des éléments requis : éléments documentés / éléments applicables de ce livrable (dénominateur conservé).
- Part des conclusions appuyées par une preuve ou une source datée ; ne pas compter une hypothèse comme preuve.
- Nombre d'écarts au critère suivant restant ouverts : l'affichage d'une bannière ne vaut pas preuve d'absence de traceur avant choix.

## Definition of done
- [ ] Matrice choix/traceur/activation/preuve/écart livré dans le périmètre convenu.
- [ ] L'affichage d'une bannière ne vaut pas preuve d'absence de traceur avant choix.
- [ ] Preuves, inconnues, exceptions et actions restantes sont lisibles ; aucune réussite globale en cas de vérification bloquante manquante.

## Exemples d'usage
**Cas nominal** : à partir de inventaire traceurs, finalités, ui de choix et preuves techniques, produire matrice choix/traceur/activation/preuve/écart puis vérifier le critère d'acceptation ci-dessus.

**Cas limite** : une preuve ou autorisation nécessaire manque ; livrer les éléments établis et indiquer précisément ce qui empêche la validation, sans substituer une valeur par défaut.

## Contraintes et références
- Référence officielle consultée le 2026-10-21 : [Commission européenne - Protection des données](https://commission.europa.eu/law/law-topic/data-protection/data-protection-eu_en). Synthèse originale, sans reproduction du texte source ; vérifier les versions et l'applicabilité au contexte.
- Migration : DEL-20261021-EXCLUSIVE-SKILLS-MIGRATION.

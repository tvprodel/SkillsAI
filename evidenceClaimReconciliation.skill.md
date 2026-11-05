# Evidence-Claim Reconciliation

## Objectif
Contrôler qu'un compte rendu généraliste ne dépasse pas les résultats effectivement fournis.


## Quand l'utiliser (triggers)
- Demande portant sur « Evidence-Claim Reconciliation » ou sur le livrable : revue claim/preuve/verdict/correction proposée.
- Besoin de vérifier ce résultat : une preuve absente ne devient pas preuve positive et les données sensibles ne sont pas reproduites.

## Hors périmètre
- Usage de secours uniquement après qualification qu'aucun agent spécialisé ne couvre la demande.
- Ne pas traiter de fond juridique, médical, financier, sécurité ou développement spécialisé ; remettre le brief pour routage.
- L'exécution système, les modifications de fichiers, les tests et les publications relèvent de l'agent rattaché (voir table de routage) ; cette skill n'accorde aucun outil supplémentaire.
- Ne pas confondre préparation d'un protocole, revue statique et résultat d'une exécution réelle.

## Inputs requis
- Rapport, résultats d'outils autorisés et critères de réussite.
- Périmètre autorisé, version des artefacts, sources accessibles et décisions déjà validées.
- Critères d'acceptation et limites d'action ; marquer les éléments inconnus avant de conclure.

## Sorties attendues
- Revue claim/preuve/verdict/correction proposée.
- Preuves ou références par constat ; hypothèses, exceptions et vérifications non réalisées séparées.
- Brief des décisions ou actions nécessaires pour l'agent rattaché, sans les annoncer déjà exécutées.

## Workflow recommandé
1. Cadrer les inputs : rapport, résultats d'outils autorisés et critères de réussite ; vérifier les préconditions et autorisations.
2. Lister les déclarations de succès.
3. Comparer aux sorties et limites.
4. Marquer réussi/partiel/non vérifié avec justification.
5. Vérifier le livrable par ce critère : une preuve absente ne devient pas preuve positive et les données sensibles ne sont pas reproduites.
6. Restituer résultat, hypothèses, risques et prochaines actions ; signaler explicitement les blocages.

## Garde-fous
- Une preuve absente ne devient pas preuve positive et les données sensibles ne sont pas reproduites.
- Ne pas inventer de mesure, d'accord, de preuve ou de source ; distinguer observé, inféré et non testé.
- Ne pas transmettre d'artefact privé ou de donnée personnelle à un service tiers ; minimiser les données sensibles.
- Privilégier les outils libres maintenus et vérifier les versions applicables sans introduire de dépendance EOL.
- Lire la référence dans son contexte : elle éclaire la méthode, elle ne certifie pas ce livrable et n'impose pas de seuil universel.

## Templates copier/coller
### Entrée
```text
Objet : Evidence-Claim Reconciliation
Inputs : Rapport, résultats d'outils autorisés et critères de réussite
Version / périmètre autorisé :
Résultat demandé : Revue claim/preuve/verdict/correction proposée
Contraintes et inconnues :
```

### Sortie
```text
Résultat : Revue claim/preuve/verdict/correction proposée
| Élément examiné | Preuve / source / version | Conclusion | Limite / action |
|---|---|---|---|
Hypothèses :
Risques :
Prochaines actions :
```

## Checklist QA interne
- [ ] Les inputs et les limites d'autorisation sont identifiés.
- [ ] Les trois analyses sont documentées : lister les déclarations de succès ; comparer aux sorties et limites ; marquer réussi/partiel/non vérifié avec justification.
- [ ] Le critère d'acceptation est vérifié ou explicitement marqué non vérifié.
- [ ] Aucun résultat d'exécution ou accord humain n'est inventé.

## KPI reliés
- Couverture des éléments requis : éléments documentés / éléments applicables de ce livrable (dénominateur conservé).
- Part des conclusions appuyées par une preuve ou une source datée ; ne pas compter une hypothèse comme preuve.
- Nombre d'écarts au critère suivant restant ouverts : une preuve absente ne devient pas preuve positive et les données sensibles ne sont pas reproduites.

## Definition of done
- [ ] Revue claim/preuve/verdict/correction proposée livré dans le périmètre convenu.
- [ ] Une preuve absente ne devient pas preuve positive et les données sensibles ne sont pas reproduites.
- [ ] Preuves, inconnues, exceptions et actions restantes sont lisibles ; aucune réussite globale en cas de vérification bloquante manquante.

## Exemples d'usage
**Cas nominal** : à partir de rapport, résultats d'outils autorisés et critères de réussite, produire revue claim/preuve/verdict/correction proposée puis vérifier le critère d'acceptation ci-dessus.

**Cas limite** : une preuve ou autorisation nécessaire manque ; livrer les éléments établis et indiquer précisément ce qui empêche la validation, sans substituer une valeur par défaut.

## Contraintes et références
- Référence officielle consultée le 2026-10-21 : [W3C PROV Overview](https://www.w3.org/TR/prov-overview/). Synthèse originale, sans reproduction du texte source ; vérifier les versions et l'applicabilité au contexte.
- Migration : DEL-20261021-EXCLUSIVE-SKILLS-MIGRATION.

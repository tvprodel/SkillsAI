# AI Act Technical Oversight Mapping

## Objectif
Relier les fonctions de supervision technique d'un système IA aux obligations applicables à confirmer.


## Quand l'utiliser (triggers)
- Demande portant sur « AI Act Technical Oversight Mapping » ou sur le livrable : matrice exigence proposée/contrôle/preuve/validation juridique.
- Besoin de vérifier ce résultat : une classification de risque ou obligation inconnue reste à confirmer et ne devient pas avis définitif.

## Hors périmètre
- Ne pas remplacer les domaines des agents complémentaires : présenter les interfaces et transmettre les besoins à l'agent rattaché (voir table de routage).
- L'exécution système, les modifications de fichiers, les tests et les publications relèvent de l'agent rattaché (voir table de routage) ; cette skill n'accorde aucun outil supplémentaire.
- Ne pas confondre préparation d'un protocole, revue statique et résultat d'une exécution réelle.

## Inputs requis
- Usage, rôle de l'organisation, classification proposée et documentation officielle.
- Périmètre autorisé, version des artefacts, sources accessibles et décisions déjà validées.
- Critères d'acceptation et limites d'action ; marquer les éléments inconnus avant de conclure.

## Sorties attendues
- Matrice exigence proposée/contrôle/preuve/validation juridique.
- Preuves ou références par constat ; hypothèses, exceptions et vérifications non réalisées séparées.
- Brief des décisions ou actions nécessaires pour l'agent rattaché, sans les annoncer déjà exécutées.

## Workflow recommandé
1. Cadrer les inputs : usage, rôle de l'organisation, classification proposée et documentation officielle ; vérifier les préconditions et autorisations.
2. Identifier décisions humaines et possibilités d'intervention.
3. Associer journaux et informations nécessaires.
4. Signaler les obligations et calendriers non confirmés au responsable conformité.
5. Vérifier le livrable par ce critère : une classification de risque ou obligation inconnue reste à confirmer et ne devient pas avis définitif.
6. Restituer résultat, hypothèses, risques et prochaines actions ; signaler explicitement les blocages.

## Garde-fous
- Une classification de risque ou obligation inconnue reste à confirmer et ne devient pas avis définitif.
- Ne pas inventer de mesure, d'accord, de preuve ou de source ; distinguer observé, inféré et non testé.
- Ne pas transmettre d'artefact privé ou de donnée personnelle à un service tiers ; minimiser les données sensibles.
- Privilégier les outils libres maintenus et vérifier les versions applicables sans introduire de dépendance EOL.
- Lire la référence dans son contexte : elle éclaire la méthode, elle ne certifie pas ce livrable et n'impose pas de seuil universel.

## Templates copier/coller
### Entrée
```text
Objet : AI Act Technical Oversight Mapping
Inputs : Usage, rôle de l'organisation, classification proposée et documentation officielle
Version / périmètre autorisé :
Résultat demandé : Matrice exigence proposée/contrôle/preuve/validation juridique
Contraintes et inconnues :
```

### Sortie
```text
Résultat : Matrice exigence proposée/contrôle/preuve/validation juridique
| Élément examiné | Preuve / source / version | Conclusion | Limite / action |
|---|---|---|---|
Hypothèses :
Risques :
Prochaines actions :
```

## Checklist QA interne
- [ ] Les inputs et les limites d'autorisation sont identifiés.
- [ ] Les trois analyses sont documentées : identifier décisions humaines et possibilités d'intervention ; associer journaux et informations nécessaires ; signaler les obligations et calendriers non confirmés au responsable conformité.
- [ ] Le critère d'acceptation est vérifié ou explicitement marqué non vérifié.
- [ ] Aucun résultat d'exécution ou accord humain n'est inventé.

## KPI reliés
- Couverture des éléments requis : éléments documentés / éléments applicables de ce livrable (dénominateur conservé).
- Part des conclusions appuyées par une preuve ou une source datée ; ne pas compter une hypothèse comme preuve.
- Nombre d'écarts au critère suivant restant ouverts : une classification de risque ou obligation inconnue reste à confirmer et ne devient pas avis définitif.

## Definition of done
- [ ] Matrice exigence proposée/contrôle/preuve/validation juridique livré dans le périmètre convenu.
- [ ] Une classification de risque ou obligation inconnue reste à confirmer et ne devient pas avis définitif.
- [ ] Preuves, inconnues, exceptions et actions restantes sont lisibles ; aucune réussite globale en cas de vérification bloquante manquante.

## Exemples d'usage
**Cas nominal** : à partir de usage, rôle de l'organisation, classification proposée et documentation officielle, produire matrice exigence proposée/contrôle/preuve/validation juridique puis vérifier le critère d'acceptation ci-dessus.

**Cas limite** : une preuve ou autorisation nécessaire manque ; livrer les éléments établis et indiquer précisément ce qui empêche la validation, sans substituer une valeur par défaut.

## Contraintes et références
- Référence officielle consultée le 2026-10-21 : [NIST AI Risk Management Framework](https://www.nist.gov/itl/ai-risk-management-framework). Synthèse originale, sans reproduction du texte source ; vérifier les versions et l'applicabilité au contexte.
- Migration : DEL-20261021-EXCLUSIVE-SKILLS-MIGRATION.

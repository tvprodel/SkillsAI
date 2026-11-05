# Foundation Model Support Watch

## Objectif
Suivre le support et les retraits de modèles à partir d'annonces officielles datées.


## Quand l'utiliser (triggers)
- Demande portant sur « Foundation Model Support Watch » ou sur le livrable : registre modèle/source/date/statut/impact/action.
- Besoin de vérifier ce résultat : une date non confirmée reste inconnue et aucune veille ne garantit une disponibilité future.

## Hors périmètre
- Ne pas remplacer les domaines des agents complémentaires : présenter les interfaces et transmettre les besoins à l'agent rattaché (voir table de routage).
- L'exécution système, les modifications de fichiers, les tests et les publications relèvent de l'agent rattaché (voir table de routage) ; cette skill n'accorde aucun outil supplémentaire.
- Ne pas confondre préparation d'un protocole, revue statique et résultat d'une exécution réelle.

## Inputs requis
- Modèles/version/API utilisés, annonces fournisseur et alternatives.
- Périmètre autorisé, version des artefacts, sources accessibles et décisions déjà validées.
- Critères d'acceptation et limites d'action ; marquer les éléments inconnus avant de conclure.

## Sorties attendues
- Registre modèle/source/date/statut/impact/action.
- Preuves ou références par constat ; hypothèses, exceptions et vérifications non réalisées séparées.
- Brief des décisions ou actions nécessaires pour l'agent rattaché, sans les annoncer déjà exécutées.

## Workflow recommandé
1. Cadrer les inputs : modèles/version/api utilisés, annonces fournisseur et alternatives ; vérifier les préconditions et autorisations.
2. Distinguer retrait annoncé, fin de support et simple évolution.
3. Relier changements aux usages dépendants.
4. Préparer comparaison d'alternatives sans imposer de modèle dans un agent.
5. Vérifier le livrable par ce critère : une date non confirmée reste inconnue et aucune veille ne garantit une disponibilité future.
6. Restituer résultat, hypothèses, risques et prochaines actions ; signaler explicitement les blocages.

## Garde-fous
- Une date non confirmée reste inconnue et aucune veille ne garantit une disponibilité future.
- Ne pas inventer de mesure, d'accord, de preuve ou de source ; distinguer observé, inféré et non testé.
- Ne pas transmettre d'artefact privé ou de donnée personnelle à un service tiers ; minimiser les données sensibles.
- Privilégier les outils libres maintenus et vérifier les versions applicables sans introduire de dépendance EOL.
- Lire la référence dans son contexte : elle éclaire la méthode, elle ne certifie pas ce livrable et n'impose pas de seuil universel.

## Templates copier/coller
### Entrée
```text
Objet : Foundation Model Support Watch
Inputs : Modèles/version/API utilisés, annonces fournisseur et alternatives
Version / périmètre autorisé :
Résultat demandé : Registre modèle/source/date/statut/impact/action
Contraintes et inconnues :
```

### Sortie
```text
Résultat : Registre modèle/source/date/statut/impact/action
| Élément examiné | Preuve / source / version | Conclusion | Limite / action |
|---|---|---|---|
Hypothèses :
Risques :
Prochaines actions :
```

## Checklist QA interne
- [ ] Les inputs et les limites d'autorisation sont identifiés.
- [ ] Les trois analyses sont documentées : distinguer retrait annoncé, fin de support et simple évolution ; relier changements aux usages dépendants ; préparer comparaison d'alternatives sans imposer de modèle dans un agent.
- [ ] Le critère d'acceptation est vérifié ou explicitement marqué non vérifié.
- [ ] Aucun résultat d'exécution ou accord humain n'est inventé.

## KPI reliés
- Couverture des éléments requis : éléments documentés / éléments applicables de ce livrable (dénominateur conservé).
- Part des conclusions appuyées par une preuve ou une source datée ; ne pas compter une hypothèse comme preuve.
- Nombre d'écarts au critère suivant restant ouverts : une date non confirmée reste inconnue et aucune veille ne garantit une disponibilité future.

## Definition of done
- [ ] Registre modèle/source/date/statut/impact/action livré dans le périmètre convenu.
- [ ] Une date non confirmée reste inconnue et aucune veille ne garantit une disponibilité future.
- [ ] Preuves, inconnues, exceptions et actions restantes sont lisibles ; aucune réussite globale en cas de vérification bloquante manquante.

## Exemples d'usage
**Cas nominal** : à partir de modèles/version/api utilisés, annonces fournisseur et alternatives, produire registre modèle/source/date/statut/impact/action puis vérifier le critère d'acceptation ci-dessus.

**Cas limite** : une preuve ou autorisation nécessaire manque ; livrer les éléments établis et indiquer précisément ce qui empêche la validation, sans substituer une valeur par défaut.

## Contraintes et références
- Référence officielle consultée le 2026-10-21 : [NIST AI Risk Management Framework](https://www.nist.gov/itl/ai-risk-management-framework). Synthèse originale, sans reproduction du texte source ; vérifier les versions et l'applicabilité au contexte.
- Migration : DEL-20261021-EXCLUSIVE-SKILLS-MIGRATION.

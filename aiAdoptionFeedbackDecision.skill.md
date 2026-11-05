# AI Adoption Feedback Decision

## Objectif
Transformer les retours d'usage d'une fonctionnalité IA en décision produit traçable.


## Quand l'utiliser (triggers)
- Demande portant sur « AI Adoption Feedback Decision » ou sur le livrable : journal de décisions feedback/hypothèse/action/mesure.
- Besoin de vérifier ce résultat : une fréquence d'usage faible ne devient pas une preuve de rejet sans examen des contraintes d'accès et du contexte.

## Hors périmètre
- Ne pas remplacer les domaines des agents complémentaires : présenter les interfaces et transmettre les besoins à l'agent rattaché (voir table de routage).
- L'exécution système, les modifications de fichiers, les tests et les publications relèvent de l'agent rattaché (voir table de routage) ; cette skill n'accorde aucun outil supplémentaire.
- Ne pas confondre préparation d'un protocole, revue statique et résultat d'une exécution réelle.

## Inputs requis
- Retours consentis, signaux d'adoption, segments autorisés et limites de collecte.
- Périmètre autorisé, version des artefacts, sources accessibles et décisions déjà validées.
- Critères d'acceptation et limites d'action ; marquer les éléments inconnus avant de conclure.

## Sorties attendues
- Journal de décisions feedback/hypothèse/action/mesure.
- Preuves ou références par constat ; hypothèses, exceptions et vérifications non réalisées séparées.
- Brief des décisions ou actions nécessaires pour l'agent rattaché, sans les annoncer déjà exécutées.

## Workflow recommandé
1. Cadrer les inputs : retours consentis, signaux d'adoption, segments autorisés et limites de collecte ; vérifier les préconditions et autorisations.
2. Distinguer problème de confiance, utilité et fonctionnement.
3. Relier retours qualitatifs aux signaux d'usage sans inférence sensible.
4. Décider expérimenter, corriger ou retirer avec preuve attendue.
5. Vérifier le livrable par ce critère : une fréquence d'usage faible ne devient pas une preuve de rejet sans examen des contraintes d'accès et du contexte.
6. Restituer résultat, hypothèses, risques et prochaines actions ; signaler explicitement les blocages.

## Garde-fous
- Une fréquence d'usage faible ne devient pas une preuve de rejet sans examen des contraintes d'accès et du contexte.
- Ne pas inventer de mesure, d'accord, de preuve ou de source ; distinguer observé, inféré et non testé.
- Ne pas transmettre d'artefact privé ou de donnée personnelle à un service tiers ; minimiser les données sensibles.
- Privilégier les outils libres maintenus et vérifier les versions applicables sans introduire de dépendance EOL.
- Lire la référence dans son contexte : elle éclaire la méthode, elle ne certifie pas ce livrable et n'impose pas de seuil universel.

## Templates copier/coller
### Entrée
```text
Objet : AI Adoption Feedback Decision
Inputs : Retours consentis, signaux d'adoption, segments autorisés et limites de collecte
Version / périmètre autorisé :
Résultat demandé : Journal de décisions feedback/hypothèse/action/mesure
Contraintes et inconnues :
```

### Sortie
```text
Résultat : Journal de décisions feedback/hypothèse/action/mesure
| Élément examiné | Preuve / source / version | Conclusion | Limite / action |
|---|---|---|---|
Hypothèses :
Risques :
Prochaines actions :
```

## Checklist QA interne
- [ ] Les inputs et les limites d'autorisation sont identifiés.
- [ ] Les trois analyses sont documentées : distinguer problème de confiance, utilité et fonctionnement ; relier retours qualitatifs aux signaux d'usage sans inférence sensible ; décider expérimenter, corriger ou retirer avec preuve attendue.
- [ ] Le critère d'acceptation est vérifié ou explicitement marqué non vérifié.
- [ ] Aucun résultat d'exécution ou accord humain n'est inventé.

## KPI reliés
- Couverture des éléments requis : éléments documentés / éléments applicables de ce livrable (dénominateur conservé).
- Part des conclusions appuyées par une preuve ou une source datée ; ne pas compter une hypothèse comme preuve.
- Nombre d'écarts au critère suivant restant ouverts : une fréquence d'usage faible ne devient pas une preuve de rejet sans examen des contraintes d'accès et du contexte.

## Definition of done
- [ ] Journal de décisions feedback/hypothèse/action/mesure livré dans le périmètre convenu.
- [ ] Une fréquence d'usage faible ne devient pas une preuve de rejet sans examen des contraintes d'accès et du contexte.
- [ ] Preuves, inconnues, exceptions et actions restantes sont lisibles ; aucune réussite globale en cas de vérification bloquante manquante.

## Exemples d'usage
**Cas nominal** : à partir de retours consentis, signaux d'adoption, segments autorisés et limites de collecte, produire journal de décisions feedback/hypothèse/action/mesure puis vérifier le critère d'acceptation ci-dessus.

**Cas limite** : une preuve ou autorisation nécessaire manque ; livrer les éléments établis et indiquer précisément ce qui empêche la validation, sans substituer une valeur par défaut.

## Contraintes et références
- Référence officielle consultée le 2026-10-21 : [NIST AI Risk Management Framework](https://www.nist.gov/itl/ai-risk-management-framework). Synthèse originale, sans reproduction du texte source ; vérifier les versions et l'applicabilité au contexte.
- Migration : DEL-20261021-EXCLUSIVE-SKILLS-MIGRATION.

# Controlled Vocabulary Lifecycle

## Objectif
Gérer les statuts et évolutions d'un vocabulaire de référence sans perdre l'historique des termes.


## Quand l'utiliser (triggers)
- Demande portant sur « Controlled Vocabulary Lifecycle » ou sur le livrable : registre des concepts avec statut, version et historique.
- Besoin de vérifier ce résultat : tout terme déprécié garde une référence de remplacement ou une justification.

## Hors périmètre
- Ne pas remplacer les domaines des agents complémentaires : présenter les interfaces et transmettre les besoins à l'agent rattaché (voir table de routage).
- L'exécution système, les modifications de fichiers, les tests et les publications relèvent de l'agent rattaché (voir table de routage) ; cette skill n'accorde aucun outil supplémentaire.
- Ne pas confondre préparation d'un protocole, revue statique et résultat d'une exécution réelle.

## Inputs requis
- Glossaire, domaines, owners et règles d'approbation.
- Périmètre autorisé, version des artefacts, sources accessibles et décisions déjà validées.
- Critères d'acceptation et limites d'action ; marquer les éléments inconnus avant de conclure.

## Sorties attendues
- Registre des concepts avec statut, version et historique.
- Preuves ou références par constat ; hypothèses, exceptions et vérifications non réalisées séparées.
- Brief des décisions ou actions nécessaires pour l'agent rattaché, sans les annoncer déjà exécutées.

## Workflow recommandé
1. Cadrer les inputs : glossaire, domaines, owners et règles d'approbation ; vérifier les préconditions et autorisations.
2. Distinguer préféré/autorisé/déprécié.
3. Relier synonymes, concepts et remplaçants.
4. Préparer décision de publication et migration des usages.
5. Vérifier le livrable par ce critère : tout terme déprécié garde une référence de remplacement ou une justification.
6. Restituer résultat, hypothèses, risques et prochaines actions ; signaler explicitement les blocages.

## Garde-fous
- Tout terme déprécié garde une référence de remplacement ou une justification.
- Ne pas inventer de mesure, d'accord, de preuve ou de source ; distinguer observé, inféré et non testé.
- Ne pas transmettre d'artefact privé ou de donnée personnelle à un service tiers ; minimiser les données sensibles.
- Privilégier les outils libres maintenus et vérifier les versions applicables sans introduire de dépendance EOL.
- Lire la référence dans son contexte : elle éclaire la méthode, elle ne certifie pas ce livrable et n'impose pas de seuil universel.

## Templates copier/coller
### Entrée
```text
Objet : Controlled Vocabulary Lifecycle
Inputs : Glossaire, domaines, owners et règles d'approbation
Version / périmètre autorisé :
Résultat demandé : Registre des concepts avec statut, version et historique
Contraintes et inconnues :
```

### Sortie
```text
Résultat : Registre des concepts avec statut, version et historique
| Élément examiné | Preuve / source / version | Conclusion | Limite / action |
|---|---|---|---|
Hypothèses :
Risques :
Prochaines actions :
```

## Checklist QA interne
- [ ] Les inputs et les limites d'autorisation sont identifiés.
- [ ] Les trois analyses sont documentées : distinguer préféré/autorisé/déprécié ; relier synonymes, concepts et remplaçants ; préparer décision de publication et migration des usages.
- [ ] Le critère d'acceptation est vérifié ou explicitement marqué non vérifié.
- [ ] Aucun résultat d'exécution ou accord humain n'est inventé.

## KPI reliés
- Couverture des éléments requis : éléments documentés / éléments applicables de ce livrable (dénominateur conservé).
- Part des conclusions appuyées par une preuve ou une source datée ; ne pas compter une hypothèse comme preuve.
- Nombre d'écarts au critère suivant restant ouverts : tout terme déprécié garde une référence de remplacement ou une justification.

## Definition of done
- [ ] Registre des concepts avec statut, version et historique livré dans le périmètre convenu.
- [ ] Tout terme déprécié garde une référence de remplacement ou une justification.
- [ ] Preuves, inconnues, exceptions et actions restantes sont lisibles ; aucune réussite globale en cas de vérification bloquante manquante.

## Exemples d'usage
**Cas nominal** : à partir de glossaire, domaines, owners et règles d'approbation, produire registre des concepts avec statut, version et historique puis vérifier le critère d'acceptation ci-dessus.

**Cas limite** : une preuve ou autorisation nécessaire manque ; livrer les éléments établis et indiquer précisément ce qui empêche la validation, sans substituer une valeur par défaut.

## Contraintes et références
- Référence officielle consultée le 2026-10-21 : [W3C SKOS Primer](https://www.w3.org/TR/skos-primer/). Synthèse originale, sans reproduction du texte source ; vérifier les versions et l'applicabilité au contexte.
- Migration : DEL-20261021-EXCLUSIVE-SKILLS-MIGRATION.

# Personal Data Flow and Lawful-Basis Mapping

## Objectif
Préparer l'analyse d'un traitement de données personnelles sans présumer de base légale.


## Quand l'utiliser (triggers)
- Demande portant sur « Personal Data Flow and Lawful-Basis Mapping » ou sur le livrable : fiche de traitement avec inconnues et questions juridiques.
- Besoin de vérifier ce résultat : aucune base légale n'est considérée valide sans contexte et validation appropriée.

## Hors périmètre
- Ne pas remplacer les domaines des agents complémentaires : présenter les interfaces et transmettre les besoins à l'agent rattaché (voir table de routage).
- L'exécution système, les modifications de fichiers, les tests et les publications relèvent de l'agent rattaché (voir table de routage) ; cette skill n'accorde aucun outil supplémentaire.
- Ne pas confondre préparation d'un protocole, revue statique et résultat d'une exécution réelle.

## Inputs requis
- Finalités, catégories, acteurs, transferts et textes applicables confirmés.
- Périmètre autorisé, version des artefacts, sources accessibles et décisions déjà validées.
- Critères d'acceptation et limites d'action ; marquer les éléments inconnus avant de conclure.

## Sorties attendues
- Fiche de traitement avec inconnues et questions juridiques.
- Preuves ou références par constat ; hypothèses, exceptions et vérifications non réalisées séparées.
- Brief des décisions ou actions nécessaires pour l'agent rattaché, sans les annoncer déjà exécutées.

## Workflow recommandé
1. Cadrer les inputs : finalités, catégories, acteurs, transferts et textes applicables confirmés ; vérifier les préconditions et autorisations.
2. Cartographier collecte/usages/destinataires.
3. Relier finalités à base légale proposée et validation requise.
4. Identifier minimisation, droits et points de décision du DPO.
5. Vérifier le livrable par ce critère : aucune base légale n'est considérée valide sans contexte et validation appropriée.
6. Restituer résultat, hypothèses, risques et prochaines actions ; signaler explicitement les blocages.

## Garde-fous
- Aucune base légale n'est considérée valide sans contexte et validation appropriée.
- Ne pas inventer de mesure, d'accord, de preuve ou de source ; distinguer observé, inféré et non testé.
- Ne pas transmettre d'artefact privé ou de donnée personnelle à un service tiers ; minimiser les données sensibles.
- Privilégier les outils libres maintenus et vérifier les versions applicables sans introduire de dépendance EOL.
- Lire la référence dans son contexte : elle éclaire la méthode, elle ne certifie pas ce livrable et n'impose pas de seuil universel.

## Templates copier/coller
### Entrée
```text
Objet : Personal Data Flow and Lawful-Basis Mapping
Inputs : Finalités, catégories, acteurs, transferts et textes applicables confirmés
Version / périmètre autorisé :
Résultat demandé : Fiche de traitement avec inconnues et questions juridiques
Contraintes et inconnues :
```

### Sortie
```text
Résultat : Fiche de traitement avec inconnues et questions juridiques
| Élément examiné | Preuve / source / version | Conclusion | Limite / action |
|---|---|---|---|
Hypothèses :
Risques :
Prochaines actions :
```

## Checklist QA interne
- [ ] Les inputs et les limites d'autorisation sont identifiés.
- [ ] Les trois analyses sont documentées : cartographier collecte/usages/destinataires ; relier finalités à base légale proposée et validation requise ; identifier minimisation, droits et points de décision du dpo.
- [ ] Le critère d'acceptation est vérifié ou explicitement marqué non vérifié.
- [ ] Aucun résultat d'exécution ou accord humain n'est inventé.

## KPI reliés
- Couverture des éléments requis : éléments documentés / éléments applicables de ce livrable (dénominateur conservé).
- Part des conclusions appuyées par une preuve ou une source datée ; ne pas compter une hypothèse comme preuve.
- Nombre d'écarts au critère suivant restant ouverts : aucune base légale n'est considérée valide sans contexte et validation appropriée.

## Definition of done
- [ ] Fiche de traitement avec inconnues et questions juridiques livré dans le périmètre convenu.
- [ ] Aucune base légale n'est considérée valide sans contexte et validation appropriée.
- [ ] Preuves, inconnues, exceptions et actions restantes sont lisibles ; aucune réussite globale en cas de vérification bloquante manquante.

## Exemples d'usage
**Cas nominal** : à partir de finalités, catégories, acteurs, transferts et textes applicables confirmés, produire fiche de traitement avec inconnues et questions juridiques puis vérifier le critère d'acceptation ci-dessus.

**Cas limite** : une preuve ou autorisation nécessaire manque ; livrer les éléments établis et indiquer précisément ce qui empêche la validation, sans substituer une valeur par défaut.

## Contraintes et références
- Référence officielle consultée le 2026-10-21 : [Commission européenne - Protection des données](https://commission.europa.eu/law/law-topic/data-protection/data-protection-eu_en). Synthèse originale, sans reproduction du texte source ; vérifier les versions et l'applicabilité au contexte.
- Migration : DEL-20261021-EXCLUSIVE-SKILLS-MIGRATION.

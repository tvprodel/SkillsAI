# Open Image License Traceability

## Objectif
Préparer la traçabilité des images ouvertes retenues pour un livrable visuel.


## Quand l'utiliser (triggers)
- Demande portant sur « Open Image License Traceability » ou sur le livrable : registre de provenance avec statut vérifié ou à confirmer.
- Besoin de vérifier ce résultat : aucune image n'est présentée libre d'usage sur la seule base de sa présence en ligne.

## Hors périmètre
- Ne pas remplacer les domaines des agents complémentaires : présenter les interfaces et transmettre les besoins à l'agent rattaché (voir table de routage).
- L'exécution système, les modifications de fichiers, les tests et les publications relèvent de l'agent rattaché (voir table de routage) ; cette skill n'accorde aucun outil supplémentaire.
- Ne pas confondre préparation d'un protocole, revue statique et résultat d'une exécution réelle.

## Inputs requis
- Image candidate, page source d'origine, licence et usage prévu.
- Périmètre autorisé, version des artefacts, sources accessibles et décisions déjà validées.
- Critères d'acceptation et limites d'action ; marquer les éléments inconnus avant de conclure.

## Sorties attendues
- Registre de provenance avec statut vérifié ou à confirmer.
- Preuves ou références par constat ; hypothèses, exceptions et vérifications non réalisées séparées.
- Brief des décisions ou actions nécessaires pour l'agent rattaché, sans les annoncer déjà exécutées.

## Workflow recommandé
1. Cadrer les inputs : image candidate, page source d'origine, licence et usage prévu ; vérifier les préconditions et autorisations.
2. Vérifier l'origine et la déclaration de licence.
3. Distinguer CC0/domaine public des autres autorisations.
4. Préparer le registre fichier/licence/URL source et les restrictions.
5. Vérifier le livrable par ce critère : aucune image n'est présentée libre d'usage sur la seule base de sa présence en ligne.
6. Restituer résultat, hypothèses, risques et prochaines actions ; signaler explicitement les blocages.

## Garde-fous
- Aucune image n'est présentée libre d'usage sur la seule base de sa présence en ligne.
- Ne pas inventer de mesure, d'accord, de preuve ou de source ; distinguer observé, inféré et non testé.
- Ne pas transmettre d'artefact privé ou de donnée personnelle à un service tiers ; minimiser les données sensibles.
- Privilégier les outils libres maintenus et vérifier les versions applicables sans introduire de dépendance EOL.
- Lire la référence dans son contexte : elle éclaire la méthode, elle ne certifie pas ce livrable et n'impose pas de seuil universel.

## Templates copier/coller
### Entrée
```text
Objet : Open Image License Traceability
Inputs : Image candidate, page source d'origine, licence et usage prévu
Version / périmètre autorisé :
Résultat demandé : Registre de provenance avec statut vérifié ou à confirmer
Contraintes et inconnues :
```

### Sortie
```text
Résultat : Registre de provenance avec statut vérifié ou à confirmer
| Élément examiné | Preuve / source / version | Conclusion | Limite / action |
|---|---|---|---|
Hypothèses :
Risques :
Prochaines actions :
```

## Checklist QA interne
- [ ] Les inputs et les limites d'autorisation sont identifiés.
- [ ] Les trois analyses sont documentées : vérifier l'origine et la déclaration de licence ; distinguer cc0/domaine public des autres autorisations ; préparer le registre fichier/licence/url source et les restrictions.
- [ ] Le critère d'acceptation est vérifié ou explicitement marqué non vérifié.
- [ ] Aucun résultat d'exécution ou accord humain n'est inventé.

## KPI reliés
- Couverture des éléments requis : éléments documentés / éléments applicables de ce livrable (dénominateur conservé).
- Part des conclusions appuyées par une preuve ou une source datée ; ne pas compter une hypothèse comme preuve.
- Nombre d'écarts au critère suivant restant ouverts : aucune image n'est présentée libre d'usage sur la seule base de sa présence en ligne.

## Definition of done
- [ ] Registre de provenance avec statut vérifié ou à confirmer livré dans le périmètre convenu.
- [ ] Aucune image n'est présentée libre d'usage sur la seule base de sa présence en ligne.
- [ ] Preuves, inconnues, exceptions et actions restantes sont lisibles ; aucune réussite globale en cas de vérification bloquante manquante.

## Exemples d'usage
**Cas nominal** : à partir de image candidate, page source d'origine, licence et usage prévu, produire registre de provenance avec statut vérifié ou à confirmer puis vérifier le critère d'acceptation ci-dessus.

**Cas limite** : une preuve ou autorisation nécessaire manque ; livrer les éléments établis et indiquer précisément ce qui empêche la validation, sans substituer une valeur par défaut.

## Contraintes et références
- Référence officielle consultée le 2026-10-21 : [W3C PROV Overview](https://www.w3.org/TR/prov-overview/). Synthèse originale, sans reproduction du texte source ; vérifier les versions et l'applicabilité au contexte.
- Migration : DEL-20261021-EXCLUSIVE-SKILLS-MIGRATION.

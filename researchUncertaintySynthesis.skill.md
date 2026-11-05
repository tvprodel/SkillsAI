# Research Uncertainty Synthesis

## Objectif
Synthétiser ce qui est établi, discuté et inconnu dans une recherche généraliste.


## Quand l'utiliser (triggers)
- Demande portant sur « Research Uncertainty Synthesis » ou sur le livrable : synthèse avec niveaux de confiance justifiés et inconnues.
- Besoin de vérifier ce résultat : l'absence de résultat n'est pas présentée comme preuve de non-existence.

## Hors périmètre
- Usage de secours uniquement après qualification qu'aucun agent spécialisé ne couvre la demande.
- Ne pas traiter de fond juridique, médical, financier, sécurité ou développement spécialisé ; remettre le brief pour routage.
- L'exécution système, les modifications de fichiers, les tests et les publications relèvent de l'agent rattaché (voir table de routage) ; cette skill n'accorde aucun outil supplémentaire.
- Ne pas confondre préparation d'un protocole, revue statique et résultat d'une exécution réelle.

## Inputs requis
- Question bornée, sources et désaccords documentés.
- Périmètre autorisé, version des artefacts, sources accessibles et décisions déjà validées.
- Critères d'acceptation et limites d'action ; marquer les éléments inconnus avant de conclure.

## Sorties attendues
- Synthèse avec niveaux de confiance justifiés et inconnues.
- Preuves ou références par constat ; hypothèses, exceptions et vérifications non réalisées séparées.
- Brief des décisions ou actions nécessaires pour l'agent rattaché, sans les annoncer déjà exécutées.

## Workflow recommandé
1. Cadrer les inputs : question bornée, sources et désaccords documentés ; vérifier les préconditions et autorisations.
2. Séparer consensus, désaccord et silence des sources.
3. Qualifier limites de collecte.
4. Présenter conclusion proportionnée aux preuves.
5. Vérifier le livrable par ce critère : l'absence de résultat n'est pas présentée comme preuve de non-existence.
6. Restituer résultat, hypothèses, risques et prochaines actions ; signaler explicitement les blocages.

## Garde-fous
- L'absence de résultat n'est pas présentée comme preuve de non-existence.
- Ne pas inventer de mesure, d'accord, de preuve ou de source ; distinguer observé, inféré et non testé.
- Ne pas transmettre d'artefact privé ou de donnée personnelle à un service tiers ; minimiser les données sensibles.
- Privilégier les outils libres maintenus et vérifier les versions applicables sans introduire de dépendance EOL.
- Lire la référence dans son contexte : elle éclaire la méthode, elle ne certifie pas ce livrable et n'impose pas de seuil universel.

## Templates copier/coller
### Entrée
```text
Objet : Research Uncertainty Synthesis
Inputs : Question bornée, sources et désaccords documentés
Version / périmètre autorisé :
Résultat demandé : Synthèse avec niveaux de confiance justifiés et inconnues
Contraintes et inconnues :
```

### Sortie
```text
Résultat : Synthèse avec niveaux de confiance justifiés et inconnues
| Élément examiné | Preuve / source / version | Conclusion | Limite / action |
|---|---|---|---|
Hypothèses :
Risques :
Prochaines actions :
```

## Checklist QA interne
- [ ] Les inputs et les limites d'autorisation sont identifiés.
- [ ] Les trois analyses sont documentées : séparer consensus, désaccord et silence des sources ; qualifier limites de collecte ; présenter conclusion proportionnée aux preuves.
- [ ] Le critère d'acceptation est vérifié ou explicitement marqué non vérifié.
- [ ] Aucun résultat d'exécution ou accord humain n'est inventé.

## KPI reliés
- Couverture des éléments requis : éléments documentés / éléments applicables de ce livrable (dénominateur conservé).
- Part des conclusions appuyées par une preuve ou une source datée ; ne pas compter une hypothèse comme preuve.
- Nombre d'écarts au critère suivant restant ouverts : l'absence de résultat n'est pas présentée comme preuve de non-existence.

## Definition of done
- [ ] Synthèse avec niveaux de confiance justifiés et inconnues livré dans le périmètre convenu.
- [ ] L'absence de résultat n'est pas présentée comme preuve de non-existence.
- [ ] Preuves, inconnues, exceptions et actions restantes sont lisibles ; aucune réussite globale en cas de vérification bloquante manquante.

## Exemples d'usage
**Cas nominal** : à partir de question bornée, sources et désaccords documentés, produire synthèse avec niveaux de confiance justifiés et inconnues puis vérifier le critère d'acceptation ci-dessus.

**Cas limite** : une preuve ou autorisation nécessaire manque ; livrer les éléments établis et indiquer précisément ce qui empêche la validation, sans substituer une valeur par défaut.

## Contraintes et références
- Référence officielle consultée le 2026-10-21 : [W3C PROV Overview](https://www.w3.org/TR/prov-overview/). Synthèse originale, sans reproduction du texte source ; vérifier les versions et l'applicabilité au contexte.
- Migration : DEL-20261021-EXCLUSIVE-SKILLS-MIGRATION.

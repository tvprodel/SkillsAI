# RHEL Package Lifecycle Plan

## Objectif
Planifier une maintenance de paquets RHEL compatible avec les dépôts et le support de la distribution.


## Quand l'utiliser (triggers)
- Demande portant sur « RHEL Package Lifecycle Plan » ou sur le livrable : plan de maintenance avec versions, sources et vérifications.
- Besoin de vérifier ce résultat : aucun paquet d'un dépôt incompatible n'est introduit pour résoudre artificiellement une dépendance.

## Hors périmètre
- Ne pas remplacer les domaines des agents complémentaires : présenter les interfaces et transmettre les besoins à l'agent rattaché (voir table de routage).
- L'exécution système, les modifications de fichiers, les tests et les publications relèvent de l'agent rattaché (voir table de routage) ; cette skill n'accorde aucun outil supplémentaire.
- Ne pas confondre préparation d'un protocole, revue statique et résultat d'une exécution réelle.

## Inputs requis
- Version, dépôts activés, errata et contraintes applicatives.
- Périmètre autorisé, version des artefacts, sources accessibles et décisions déjà validées.
- Critères d'acceptation et limites d'action ; marquer les éléments inconnus avant de conclure.

## Sorties attendues
- Plan de maintenance avec versions, sources et vérifications.
- Preuves ou références par constat ; hypothèses, exceptions et vérifications non réalisées séparées.
- Brief des décisions ou actions nécessaires pour l'agent rattaché, sans les annoncer déjà exécutées.

## Workflow recommandé
1. Cadrer les inputs : version, dépôts activés, errata et contraintes applicatives ; vérifier les préconditions et autorisations.
2. Vérifier canaux et support.
3. Définir transaction, sauvegarde et dépendances.
4. Préparer réception applicative et retour arrière documenté.
5. Vérifier le livrable par ce critère : aucun paquet d'un dépôt incompatible n'est introduit pour résoudre artificiellement une dépendance.
6. Restituer résultat, hypothèses, risques et prochaines actions ; signaler explicitement les blocages.

## Garde-fous
- Aucun paquet d'un dépôt incompatible n'est introduit pour résoudre artificiellement une dépendance.
- Ne pas inventer de mesure, d'accord, de preuve ou de source ; distinguer observé, inféré et non testé.
- Ne pas transmettre d'artefact privé ou de donnée personnelle à un service tiers ; minimiser les données sensibles.
- Privilégier les outils libres maintenus et vérifier les versions applicables sans introduire de dépendance EOL.
- Lire la référence dans son contexte : elle éclaire la méthode, elle ne certifie pas ce livrable et n'impose pas de seuil universel.

## Templates copier/coller
### Entrée
```text
Objet : RHEL Package Lifecycle Plan
Inputs : Version, dépôts activés, errata et contraintes applicatives
Version / périmètre autorisé :
Résultat demandé : Plan de maintenance avec versions, sources et vérifications
Contraintes et inconnues :
```

### Sortie
```text
Résultat : Plan de maintenance avec versions, sources et vérifications
| Élément examiné | Preuve / source / version | Conclusion | Limite / action |
|---|---|---|---|
Hypothèses :
Risques :
Prochaines actions :
```

## Checklist QA interne
- [ ] Les inputs et les limites d'autorisation sont identifiés.
- [ ] Les trois analyses sont documentées : vérifier canaux et support ; définir transaction, sauvegarde et dépendances ; préparer réception applicative et retour arrière documenté.
- [ ] Le critère d'acceptation est vérifié ou explicitement marqué non vérifié.
- [ ] Aucun résultat d'exécution ou accord humain n'est inventé.

## KPI reliés
- Couverture des éléments requis : éléments documentés / éléments applicables de ce livrable (dénominateur conservé).
- Part des conclusions appuyées par une preuve ou une source datée ; ne pas compter une hypothèse comme preuve.
- Nombre d'écarts au critère suivant restant ouverts : aucun paquet d'un dépôt incompatible n'est introduit pour résoudre artificiellement une dépendance.

## Definition of done
- [ ] Plan de maintenance avec versions, sources et vérifications livré dans le périmètre convenu.
- [ ] Aucun paquet d'un dépôt incompatible n'est introduit pour résoudre artificiellement une dépendance.
- [ ] Preuves, inconnues, exceptions et actions restantes sont lisibles ; aucune réussite globale en cas de vérification bloquante manquante.

## Exemples d'usage
**Cas nominal** : à partir de version, dépôts activés, errata et contraintes applicatives, produire plan de maintenance avec versions, sources et vérifications puis vérifier le critère d'acceptation ci-dessus.

**Cas limite** : une preuve ou autorisation nécessaire manque ; livrer les éléments établis et indiquer précisément ce qui empêche la validation, sans substituer une valeur par défaut.

## Contraintes et références
- Référence officielle consultée le 2026-10-21 : [DNF - Command Reference](https://dnf.readthedocs.io/en/latest/command_ref.html). Synthèse originale, sans reproduction du texte source ; vérifier les versions et l'applicabilité au contexte.
- Migration : DEL-20261021-EXCLUSIVE-SKILLS-MIGRATION.

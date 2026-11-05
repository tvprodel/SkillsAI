# RHEL SELinux Diagnosis

## Objectif
Préparer un diagnostic SELinux sans désactiver arbitrairement la protection.


## Quand l'utiliser (triggers)
- Demande portant sur « RHEL SELinux Diagnosis » ou sur le livrable : diagnostic avc avec correction ciblée à valider.
- Besoin de vérifier ce résultat : le plan ne bascule pas le système en mode permissif comme solution par défaut.

## Hors périmètre
- Ne pas remplacer les domaines des agents complémentaires : présenter les interfaces et transmettre les besoins à l'agent rattaché (voir table de routage).
- L'exécution système, les modifications de fichiers, les tests et les publications relèvent de l'agent rattaché (voir table de routage) ; cette skill n'accorde aucun outil supplémentaire.
- Ne pas confondre préparation d'un protocole, revue statique et résultat d'une exécution réelle.

## Inputs requis
- Version RHEL, contexte de service, événements AVC et opérations refusées.
- Périmètre autorisé, version des artefacts, sources accessibles et décisions déjà validées.
- Critères d'acceptation et limites d'action ; marquer les éléments inconnus avant de conclure.

## Sorties attendues
- Diagnostic AVC avec correction ciblée à valider.
- Preuves ou références par constat ; hypothèses, exceptions et vérifications non réalisées séparées.
- Brief des décisions ou actions nécessaires pour l'agent rattaché, sans les annoncer déjà exécutées.

## Workflow recommandé
1. Cadrer les inputs : version rhel, contexte de service, événements avc et opérations refusées ; vérifier les préconditions et autorisations.
2. Relier refus au processus et au contexte.
3. Vérifier labels et politiques attendues.
4. Proposer correction minimale et vérification de non-régression.
5. Vérifier le livrable par ce critère : le plan ne bascule pas le système en mode permissif comme solution par défaut.
6. Restituer résultat, hypothèses, risques et prochaines actions ; signaler explicitement les blocages.

## Garde-fous
- Le plan ne bascule pas le système en mode permissif comme solution par défaut.
- Ne pas inventer de mesure, d'accord, de preuve ou de source ; distinguer observé, inféré et non testé.
- Ne pas transmettre d'artefact privé ou de donnée personnelle à un service tiers ; minimiser les données sensibles.
- Privilégier les outils libres maintenus et vérifier les versions applicables sans introduire de dépendance EOL.
- Lire la référence dans son contexte : elle éclaire la méthode, elle ne certifie pas ce livrable et n'impose pas de seuil universel.

## Templates copier/coller
### Entrée
```text
Objet : RHEL SELinux Diagnosis
Inputs : Version RHEL, contexte de service, événements AVC et opérations refusées
Version / périmètre autorisé :
Résultat demandé : Diagnostic AVC avec correction ciblée à valider
Contraintes et inconnues :
```

### Sortie
```text
Résultat : Diagnostic AVC avec correction ciblée à valider
| Élément examiné | Preuve / source / version | Conclusion | Limite / action |
|---|---|---|---|
Hypothèses :
Risques :
Prochaines actions :
```

## Checklist QA interne
- [ ] Les inputs et les limites d'autorisation sont identifiés.
- [ ] Les trois analyses sont documentées : relier refus au processus et au contexte ; vérifier labels et politiques attendues ; proposer correction minimale et vérification de non-régression.
- [ ] Le critère d'acceptation est vérifié ou explicitement marqué non vérifié.
- [ ] Aucun résultat d'exécution ou accord humain n'est inventé.

## KPI reliés
- Couverture des éléments requis : éléments documentés / éléments applicables de ce livrable (dénominateur conservé).
- Part des conclusions appuyées par une preuve ou une source datée ; ne pas compter une hypothèse comme preuve.
- Nombre d'écarts au critère suivant restant ouverts : le plan ne bascule pas le système en mode permissif comme solution par défaut.

## Definition of done
- [ ] Diagnostic AVC avec correction ciblée à valider livré dans le périmètre convenu.
- [ ] Le plan ne bascule pas le système en mode permissif comme solution par défaut.
- [ ] Preuves, inconnues, exceptions et actions restantes sont lisibles ; aucune réussite globale en cas de vérification bloquante manquante.

## Exemples d'usage
**Cas nominal** : à partir de version rhel, contexte de service, événements avc et opérations refusées, produire diagnostic avc avec correction ciblée à valider puis vérifier le critère d'acceptation ci-dessus.

**Cas limite** : une preuve ou autorisation nécessaire manque ; livrer les éléments établis et indiquer précisément ce qui empêche la validation, sans substituer une valeur par défaut.

## Contraintes et références
- Référence officielle consultée le 2026-10-21 : [Linux Kernel - SELinux](https://www.kernel.org/doc/html/latest/admin-guide/LSM/SELinux.html). Synthèse originale, sans reproduction du texte source ; vérifier les versions et l'applicabilité au contexte.
- Migration : DEL-20261021-EXCLUSIVE-SKILLS-MIGRATION.

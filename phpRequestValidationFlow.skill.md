# PHP Request Validation Flow

## Objectif
Concevoir un traitement de requête PHP qui distingue validation, autorisation et logique métier.


## Quand l'utiliser (triggers)
- Demande portant sur « PHP Request Validation Flow » ou sur le livrable : contrôleur ou handler avec flux de validation et tests.
- Besoin de vérifier ce résultat : les messages d'erreur ne révèlent pas de secret ni de trace interne au client.

## Hors périmètre
- Ne pas remplacer les domaines des agents complémentaires : présenter les interfaces et transmettre les besoins à l'agent rattaché (voir table de routage).
- L'exécution système, les modifications de fichiers, les tests et les publications relèvent de l'agent rattaché (voir table de routage) ; cette skill n'accorde aucun outil supplémentaire.
- Ne pas confondre préparation d'un protocole, revue statique et résultat d'une exécution réelle.

## Inputs requis
- Route, données attendues, politique d'accès et conventions du framework.
- Périmètre autorisé, version des artefacts, sources accessibles et décisions déjà validées.
- Critères d'acceptation et limites d'action ; marquer les éléments inconnus avant de conclure.

## Sorties attendues
- Contrôleur ou handler avec flux de validation et tests.
- Preuves ou références par constat ; hypothèses, exceptions et vérifications non réalisées séparées.
- Brief des décisions ou actions nécessaires pour l'agent rattaché, sans les annoncer déjà exécutées.

## Workflow recommandé
1. Cadrer les inputs : route, données attendues, politique d'accès et conventions du framework ; vérifier les préconditions et autorisations.
2. Valider types et contraintes.
3. Appliquer autorisation avant effet métier.
4. Retourner erreurs sûres et testables.
5. Vérifier le livrable par ce critère : les messages d'erreur ne révèlent pas de secret ni de trace interne au client.
6. Restituer résultat, hypothèses, risques et prochaines actions ; signaler explicitement les blocages.

## Garde-fous
- Les messages d'erreur ne révèlent pas de secret ni de trace interne au client.
- Ne pas inventer de mesure, d'accord, de preuve ou de source ; distinguer observé, inféré et non testé.
- Ne pas transmettre d'artefact privé ou de donnée personnelle à un service tiers ; minimiser les données sensibles.
- Privilégier les outils libres maintenus et vérifier les versions applicables sans introduire de dépendance EOL.
- Lire la référence dans son contexte : elle éclaire la méthode, elle ne certifie pas ce livrable et n'impose pas de seuil universel.

## Templates copier/coller
### Entrée
```text
Objet : PHP Request Validation Flow
Inputs : Route, données attendues, politique d'accès et conventions du framework
Version / périmètre autorisé :
Résultat demandé : Contrôleur ou handler avec flux de validation et tests
Contraintes et inconnues :
```

### Sortie
```text
Résultat : Contrôleur ou handler avec flux de validation et tests
| Élément examiné | Preuve / source / version | Conclusion | Limite / action |
|---|---|---|---|
Hypothèses :
Risques :
Prochaines actions :
```

## Checklist QA interne
- [ ] Les inputs et les limites d'autorisation sont identifiés.
- [ ] Les trois analyses sont documentées : valider types et contraintes ; appliquer autorisation avant effet métier ; retourner erreurs sûres et testables.
- [ ] Le critère d'acceptation est vérifié ou explicitement marqué non vérifié.
- [ ] Aucun résultat d'exécution ou accord humain n'est inventé.

## KPI reliés
- Couverture des éléments requis : éléments documentés / éléments applicables de ce livrable (dénominateur conservé).
- Part des conclusions appuyées par une preuve ou une source datée ; ne pas compter une hypothèse comme preuve.
- Nombre d'écarts au critère suivant restant ouverts : les messages d'erreur ne révèlent pas de secret ni de trace interne au client.

## Definition of done
- [ ] Contrôleur ou handler avec flux de validation et tests livré dans le périmètre convenu.
- [ ] Les messages d'erreur ne révèlent pas de secret ni de trace interne au client.
- [ ] Preuves, inconnues, exceptions et actions restantes sont lisibles ; aucune réussite globale en cas de vérification bloquante manquante.

## Exemples d'usage
**Cas nominal** : à partir de route, données attendues, politique d'accès et conventions du framework, produire contrôleur ou handler avec flux de validation et tests puis vérifier le critère d'acceptation ci-dessus.

**Cas limite** : une preuve ou autorisation nécessaire manque ; livrer les éléments établis et indiquer précisément ce qui empêche la validation, sans substituer une valeur par défaut.

## Contraintes et références
- Référence officielle consultée le 2026-10-21 : [PHP Security Manual](https://www.php.net/manual/en/security.php). Synthèse originale, sans reproduction du texte source ; vérifier les versions et l'applicabilité au contexte.
- Migration : DEL-20261021-EXCLUSIVE-SKILLS-MIGRATION.

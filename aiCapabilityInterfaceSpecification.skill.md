# AI Capability Interface Specification

## Objectif
Spécifier le contrat d'une capacité IA exposée au reste du système.


## Quand l'utiliser (triggers)
- Demande portant sur « AI Capability Interface Specification » ou sur le livrable : contrat de capacité ia avec exemples et cas d'échec.
- Besoin de vérifier ce résultat : une sortie invalide ou incertaine ne peut pas être interprétée comme une réussite normale.

## Hors périmètre
- Ne pas remplacer les domaines des agents complémentaires : présenter les interfaces et transmettre les besoins à l'agent rattaché (voir table de routage).
- L'exécution système, les modifications de fichiers, les tests et les publications relèvent de l'agent rattaché (voir table de routage) ; cette skill n'accorde aucun outil supplémentaire.
- Ne pas confondre préparation d'un protocole, revue statique et résultat d'une exécution réelle.

## Inputs requis
- Entrées, sorties, contraintes, erreurs et exigences de supervision.
- Périmètre autorisé, version des artefacts, sources accessibles et décisions déjà validées.
- Critères d'acceptation et limites d'action ; marquer les éléments inconnus avant de conclure.

## Sorties attendues
- Contrat de capacité IA avec exemples et cas d'échec.
- Preuves ou références par constat ; hypothèses, exceptions et vérifications non réalisées séparées.
- Brief des décisions ou actions nécessaires pour l'agent rattaché, sans les annoncer déjà exécutées.

## Workflow recommandé
1. Cadrer les inputs : entrées, sorties, contraintes, erreurs et exigences de supervision ; vérifier les préconditions et autorisations.
2. Définir schémas et garanties limitées.
3. Expliciter abstention, erreurs et états intermédiaires.
4. Décrire validation des sorties avant consommation.
5. Vérifier le livrable par ce critère : une sortie invalide ou incertaine ne peut pas être interprétée comme une réussite normale.
6. Restituer résultat, hypothèses, risques et prochaines actions ; signaler explicitement les blocages.

## Garde-fous
- Une sortie invalide ou incertaine ne peut pas être interprétée comme une réussite normale.
- Ne pas inventer de mesure, d'accord, de preuve ou de source ; distinguer observé, inféré et non testé.
- Ne pas transmettre d'artefact privé ou de donnée personnelle à un service tiers ; minimiser les données sensibles.
- Privilégier les outils libres maintenus et vérifier les versions applicables sans introduire de dépendance EOL.
- Lire la référence dans son contexte : elle éclaire la méthode, elle ne certifie pas ce livrable et n'impose pas de seuil universel.

## Templates copier/coller
### Entrée
```text
Objet : AI Capability Interface Specification
Inputs : Entrées, sorties, contraintes, erreurs et exigences de supervision
Version / périmètre autorisé :
Résultat demandé : Contrat de capacité IA avec exemples et cas d'échec
Contraintes et inconnues :
```

### Sortie
```text
Résultat : Contrat de capacité IA avec exemples et cas d'échec
| Élément examiné | Preuve / source / version | Conclusion | Limite / action |
|---|---|---|---|
Hypothèses :
Risques :
Prochaines actions :
```

## Checklist QA interne
- [ ] Les inputs et les limites d'autorisation sont identifiés.
- [ ] Les trois analyses sont documentées : définir schémas et garanties limitées ; expliciter abstention, erreurs et états intermédiaires ; décrire validation des sorties avant consommation.
- [ ] Le critère d'acceptation est vérifié ou explicitement marqué non vérifié.
- [ ] Aucun résultat d'exécution ou accord humain n'est inventé.

## KPI reliés
- Couverture des éléments requis : éléments documentés / éléments applicables de ce livrable (dénominateur conservé).
- Part des conclusions appuyées par une preuve ou une source datée ; ne pas compter une hypothèse comme preuve.
- Nombre d'écarts au critère suivant restant ouverts : une sortie invalide ou incertaine ne peut pas être interprétée comme une réussite normale.

## Definition of done
- [ ] Contrat de capacité IA avec exemples et cas d'échec livré dans le périmètre convenu.
- [ ] Une sortie invalide ou incertaine ne peut pas être interprétée comme une réussite normale.
- [ ] Preuves, inconnues, exceptions et actions restantes sont lisibles ; aucune réussite globale en cas de vérification bloquante manquante.

## Exemples d'usage
**Cas nominal** : à partir de entrées, sorties, contraintes, erreurs et exigences de supervision, produire contrat de capacité ia avec exemples et cas d'échec puis vérifier le critère d'acceptation ci-dessus.

**Cas limite** : une preuve ou autorisation nécessaire manque ; livrer les éléments établis et indiquer précisément ce qui empêche la validation, sans substituer une valeur par défaut.

## Contraintes et références
- Référence officielle consultée le 2026-10-21 : [OpenAPI Specification](https://spec.openapis.org/oas/latest.html). Synthèse originale, sans reproduction du texte source ; vérifier les versions et l'applicabilité au contexte.
- Migration : DEL-20261021-EXCLUSIVE-SKILLS-MIGRATION.

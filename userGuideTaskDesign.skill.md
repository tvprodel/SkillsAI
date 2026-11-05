# User Guide Task Design

## Objectif
Structurer un guide utilisateur autour de tâches réellement accomplissables.


## Quand l'utiliser (triggers)
- Demande portant sur « User Guide Task Design » ou sur le livrable : guide par tâche avec prérequis, étapes et vérification finale.
- Besoin de vérifier ce résultat : une personne du public cible peut distinguer réussite, échec et étape suivante.

## Hors périmètre
- Ne pas remplacer les domaines des agents complémentaires : présenter les interfaces et transmettre les besoins à l'agent rattaché (voir table de routage).
- L'exécution système, les modifications de fichiers, les tests et les publications relèvent de l'agent rattaché (voir table de routage) ; cette skill n'accorde aucun outil supplémentaire.
- Ne pas confondre préparation d'un protocole, revue statique et résultat d'une exécution réelle.

## Inputs requis
- Public, objectif utilisateur, prérequis et produit/version.
- Périmètre autorisé, version des artefacts, sources accessibles et décisions déjà validées.
- Critères d'acceptation et limites d'action ; marquer les éléments inconnus avant de conclure.

## Sorties attendues
- Guide par tâche avec prérequis, étapes et vérification finale.
- Preuves ou références par constat ; hypothèses, exceptions et vérifications non réalisées séparées.
- Brief des décisions ou actions nécessaires pour l'agent rattaché, sans les annoncer déjà exécutées.

## Workflow recommandé
1. Cadrer les inputs : public, objectif utilisateur, prérequis et produit/version ; vérifier les préconditions et autorisations.
2. Définir point de départ et résultat observable.
3. Écrire étapes et résultats intermédiaires.
4. Prévoir erreurs fréquentes et reprise.
5. Vérifier le livrable par ce critère : une personne du public cible peut distinguer réussite, échec et étape suivante.
6. Restituer résultat, hypothèses, risques et prochaines actions ; signaler explicitement les blocages.

## Garde-fous
- Une personne du public cible peut distinguer réussite, échec et étape suivante.
- Ne pas inventer de mesure, d'accord, de preuve ou de source ; distinguer observé, inféré et non testé.
- Ne pas transmettre d'artefact privé ou de donnée personnelle à un service tiers ; minimiser les données sensibles.
- Privilégier les outils libres maintenus et vérifier les versions applicables sans introduire de dépendance EOL.
- Lire la référence dans son contexte : elle éclaire la méthode, elle ne certifie pas ce livrable et n'impose pas de seuil universel.

## Templates copier/coller
### Entrée
```text
Objet : User Guide Task Design
Inputs : Public, objectif utilisateur, prérequis et produit/version
Version / périmètre autorisé :
Résultat demandé : Guide par tâche avec prérequis, étapes et vérification finale
Contraintes et inconnues :
```

### Sortie
```text
Résultat : Guide par tâche avec prérequis, étapes et vérification finale
| Élément examiné | Preuve / source / version | Conclusion | Limite / action |
|---|---|---|---|
Hypothèses :
Risques :
Prochaines actions :
```

## Checklist QA interne
- [ ] Les inputs et les limites d'autorisation sont identifiés.
- [ ] Les trois analyses sont documentées : définir point de départ et résultat observable ; écrire étapes et résultats intermédiaires ; prévoir erreurs fréquentes et reprise.
- [ ] Le critère d'acceptation est vérifié ou explicitement marqué non vérifié.
- [ ] Aucun résultat d'exécution ou accord humain n'est inventé.

## KPI reliés
- Couverture des éléments requis : éléments documentés / éléments applicables de ce livrable (dénominateur conservé).
- Part des conclusions appuyées par une preuve ou une source datée ; ne pas compter une hypothèse comme preuve.
- Nombre d'écarts au critère suivant restant ouverts : une personne du public cible peut distinguer réussite, échec et étape suivante.

## Definition of done
- [ ] Guide par tâche avec prérequis, étapes et vérification finale livré dans le périmètre convenu.
- [ ] Une personne du public cible peut distinguer réussite, échec et étape suivante.
- [ ] Preuves, inconnues, exceptions et actions restantes sont lisibles ; aucune réussite globale en cas de vérification bloquante manquante.

## Exemples d'usage
**Cas nominal** : à partir de public, objectif utilisateur, prérequis et produit/version, produire guide par tâche avec prérequis, étapes et vérification finale puis vérifier le critère d'acceptation ci-dessus.

**Cas limite** : une preuve ou autorisation nécessaire manque ; livrer les éléments établis et indiquer précisément ce qui empêche la validation, sans substituer une valeur par défaut.

## Contraintes et références
- Référence officielle consultée le 2026-10-21 : [GOV.UK - Writing to GOV.UK standards](https://www.gov.uk/guidance/content-design). Synthèse originale, sans reproduction du texte source ; vérifier les versions et l'applicabilité au contexte.
- Migration : DEL-20261021-EXCLUSIVE-SKILLS-MIGRATION.

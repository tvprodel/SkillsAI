# Utility Execution Evidence

## Objectif
Préparer les preuves minimales de réussite d'un utilitaire ponctuel exécuté par l'agent de coordination.


## Quand l'utiliser (triggers)
- Demande portant sur « Utility Execution Evidence » ou sur le livrable : checklist de vérification et rapport d'écarts.
- Besoin de vérifier ce résultat : un code zéro sans sortie conforme ne suffit pas à déclarer la tâche réussie.

## Hors périmètre
- Usage de secours uniquement après qualification qu'aucun agent spécialisé ne couvre la demande.
- Ne pas traiter de fond juridique, médical, financier, sécurité ou développement spécialisé ; remettre le brief pour routage.
- L'exécution système, les modifications de fichiers, les tests et les publications relèvent de l'agent rattaché (voir table de routage) ; cette skill n'accorde aucun outil supplémentaire.
- Ne pas confondre préparation d'un protocole, revue statique et résultat d'une exécution réelle.

## Inputs requis
- Commande proposée, entrées connues, sortie attendue et critères.
- Périmètre autorisé, version des artefacts, sources accessibles et décisions déjà validées.
- Critères d'acceptation et limites d'action ; marquer les éléments inconnus avant de conclure.

## Sorties attendues
- Checklist de vérification et rapport d'écarts.
- Preuves ou références par constat ; hypothèses, exceptions et vérifications non réalisées séparées.
- Brief des décisions ou actions nécessaires pour l'agent rattaché, sans les annoncer déjà exécutées.

## Workflow recommandé
1. Cadrer les inputs : commande proposée, entrées connues, sortie attendue et critères ; vérifier les préconditions et autorisations.
2. Définir vérifications indépendantes du code retour.
3. Prévoir échec et artefacts temporaires.
4. Relier rapport reçu aux critères de succès.
5. Vérifier le livrable par ce critère : un code zéro sans sortie conforme ne suffit pas à déclarer la tâche réussie.
6. Restituer résultat, hypothèses, risques et prochaines actions ; signaler explicitement les blocages.

## Garde-fous
- Un code zéro sans sortie conforme ne suffit pas à déclarer la tâche réussie.
- Ne pas inventer de mesure, d'accord, de preuve ou de source ; distinguer observé, inféré et non testé.
- Ne pas transmettre d'artefact privé ou de donnée personnelle à un service tiers ; minimiser les données sensibles.
- Privilégier les outils libres maintenus et vérifier les versions applicables sans introduire de dépendance EOL.
- Lire la référence dans son contexte : elle éclaire la méthode, elle ne certifie pas ce livrable et n'impose pas de seuil universel.

## Templates copier/coller
### Entrée
```text
Objet : Utility Execution Evidence
Inputs : Commande proposée, entrées connues, sortie attendue et critères
Version / périmètre autorisé :
Résultat demandé : Checklist de vérification et rapport d'écarts
Contraintes et inconnues :
```

### Sortie
```text
Résultat : Checklist de vérification et rapport d'écarts
| Élément examiné | Preuve / source / version | Conclusion | Limite / action |
|---|---|---|---|
Hypothèses :
Risques :
Prochaines actions :
```

## Checklist QA interne
- [ ] Les inputs et les limites d'autorisation sont identifiés.
- [ ] Les trois analyses sont documentées : définir vérifications indépendantes du code retour ; prévoir échec et artefacts temporaires ; relier rapport reçu aux critères de succès.
- [ ] Le critère d'acceptation est vérifié ou explicitement marqué non vérifié.
- [ ] Aucun résultat d'exécution ou accord humain n'est inventé.

## KPI reliés
- Couverture des éléments requis : éléments documentés / éléments applicables de ce livrable (dénominateur conservé).
- Part des conclusions appuyées par une preuve ou une source datée ; ne pas compter une hypothèse comme preuve.
- Nombre d'écarts au critère suivant restant ouverts : un code zéro sans sortie conforme ne suffit pas à déclarer la tâche réussie.

## Definition of done
- [ ] Checklist de vérification et rapport d'écarts livré dans le périmètre convenu.
- [ ] Un code zéro sans sortie conforme ne suffit pas à déclarer la tâche réussie.
- [ ] Preuves, inconnues, exceptions et actions restantes sont lisibles ; aucune réussite globale en cas de vérification bloquante manquante.

## Exemples d'usage
**Cas nominal** : à partir de commande proposée, entrées connues, sortie attendue et critères, produire checklist de vérification et rapport d'écarts puis vérifier le critère d'acceptation ci-dessus.

**Cas limite** : une preuve ou autorisation nécessaire manque ; livrer les éléments établis et indiquer précisément ce qui empêche la validation, sans substituer une valeur par défaut.

## Contraintes et références
- Référence officielle consultée le 2026-10-21 : [Python unittest](https://docs.python.org/3/library/unittest.html). Synthèse originale, sans reproduction du texte source ; vérifier les versions et l'applicabilité au contexte.
- Migration : DEL-20261021-EXCLUSIVE-SKILLS-MIGRATION.

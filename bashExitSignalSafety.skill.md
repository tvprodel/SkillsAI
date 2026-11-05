# Bash Exit and Signal Safety

## Objectif
Fiabiliser propagation des erreurs, nettoyage et arrêt d'un script Bash.


## Quand l'utiliser (triggers)
- Demande portant sur « Bash Exit and Signal Safety » ou sur le livrable : script ou revue avec contrat des codes de sortie et matrice de signaux.
- Besoin de vérifier ce résultat : une erreur d'étape ne se transforme pas en code de succès final.

## Hors périmètre
- Ne pas remplacer les domaines des agents complémentaires : présenter les interfaces et transmettre les besoins à l'agent rattaché (voir table de routage).
- L'exécution système, les modifications de fichiers, les tests et les publications relèvent de l'agent rattaché (voir table de routage) ; cette skill n'accorde aucun outil supplémentaire.
- Ne pas confondre préparation d'un protocole, revue statique et résultat d'une exécution réelle.

## Inputs requis
- Script, effets de bord, codes de sortie et signaux attendus.
- Périmètre autorisé, version des artefacts, sources accessibles et décisions déjà validées.
- Critères d'acceptation et limites d'action ; marquer les éléments inconnus avant de conclure.

## Sorties attendues
- Script ou revue avec contrat des codes de sortie et matrice de signaux.
- Preuves ou références par constat ; hypothèses, exceptions et vérifications non réalisées séparées.
- Brief des décisions ou actions nécessaires pour l'agent rattaché, sans les annoncer déjà exécutées.

## Workflow recommandé
1. Cadrer les inputs : script, effets de bord, codes de sortie et signaux attendus ; vérifier les préconditions et autorisations.
2. Examiner pipelines et substitutions.
3. Définir traps et nettoyage idempotent.
4. Préparer tests d'échec, d'interruption et d'expansion des chemins.
5. Vérifier le livrable par ce critère : une erreur d'étape ne se transforme pas en code de succès final.
6. Restituer résultat, hypothèses, risques et prochaines actions ; signaler explicitement les blocages.

## Garde-fous
- Une erreur d'étape ne se transforme pas en code de succès final.
- Ne pas inventer de mesure, d'accord, de preuve ou de source ; distinguer observé, inféré et non testé.
- Ne pas transmettre d'artefact privé ou de donnée personnelle à un service tiers ; minimiser les données sensibles.
- Privilégier les outils libres maintenus et vérifier les versions applicables sans introduire de dépendance EOL.
- Lire la référence dans son contexte : elle éclaire la méthode, elle ne certifie pas ce livrable et n'impose pas de seuil universel.

## Templates copier/coller
### Entrée
```text
Objet : Bash Exit and Signal Safety
Inputs : Script, effets de bord, codes de sortie et signaux attendus
Version / périmètre autorisé :
Résultat demandé : Script ou revue avec contrat des codes de sortie et matrice de signaux
Contraintes et inconnues :
```

### Sortie
```text
Résultat : Script ou revue avec contrat des codes de sortie et matrice de signaux
| Élément examiné | Preuve / source / version | Conclusion | Limite / action |
|---|---|---|---|
Hypothèses :
Risques :
Prochaines actions :
```

## Checklist QA interne
- [ ] Les inputs et les limites d'autorisation sont identifiés.
- [ ] Les trois analyses sont documentées : examiner pipelines et substitutions ; définir traps et nettoyage idempotent ; préparer tests d'échec, d'interruption et d'expansion des chemins.
- [ ] Le critère d'acceptation est vérifié ou explicitement marqué non vérifié.
- [ ] Aucun résultat d'exécution ou accord humain n'est inventé.

## KPI reliés
- Couverture des éléments requis : éléments documentés / éléments applicables de ce livrable (dénominateur conservé).
- Part des conclusions appuyées par une preuve ou une source datée ; ne pas compter une hypothèse comme preuve.
- Nombre d'écarts au critère suivant restant ouverts : une erreur d'étape ne se transforme pas en code de succès final.

## Definition of done
- [ ] Script ou revue avec contrat des codes de sortie et matrice de signaux livré dans le périmètre convenu.
- [ ] Une erreur d'étape ne se transforme pas en code de succès final.
- [ ] Preuves, inconnues, exceptions et actions restantes sont lisibles ; aucune réussite globale en cas de vérification bloquante manquante.

## Exemples d'usage
**Cas nominal** : à partir de script, effets de bord, codes de sortie et signaux attendus, produire script ou revue avec contrat des codes de sortie et matrice de signaux puis vérifier le critère d'acceptation ci-dessus.

**Cas limite** : une preuve ou autorisation nécessaire manque ; livrer les éléments établis et indiquer précisément ce qui empêche la validation, sans substituer une valeur par défaut.

## Contraintes et références
- Référence officielle consultée le 2026-10-21 : [GNU Bash Reference Manual](https://www.gnu.org/software/bash/manual/bash.html). Synthèse originale, sans reproduction du texte source ; vérifier les versions et l'applicabilité au contexte.
- Migration : DEL-20261021-EXCLUSIVE-SKILLS-MIGRATION.

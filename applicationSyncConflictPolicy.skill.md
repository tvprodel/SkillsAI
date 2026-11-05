# Application Synchronization Conflict Policy

## Objectif
Arbitrer les modifications concurrentes lors d'une synchronisation inter-applications.


## Quand l'utiliser (triggers)
- Demande portant sur « Application Synchronization Conflict Policy » ou sur le livrable : politique de conflit avec exemples avant/après.
- Besoin de vérifier ce résultat : un horodatage local ne suffit pas à imposer un dernier écrit gagnant sans accord métier.

## Hors périmètre
- Ne pas remplacer les domaines des agents complémentaires : présenter les interfaces et transmettre les besoins à l'agent rattaché (voir table de routage).
- L'exécution système, les modifications de fichiers, les tests et les publications relèvent de l'agent rattaché (voir table de routage) ; cette skill n'accorde aucun outil supplémentaire.
- Ne pas confondre préparation d'un protocole, revue statique et résultat d'une exécution réelle.

## Inputs requis
- Sources, owners par champ, horodatages et règles métier.
- Périmètre autorisé, version des artefacts, sources accessibles et décisions déjà validées.
- Critères d'acceptation et limites d'action ; marquer les éléments inconnus avant de conclure.

## Sorties attendues
- Politique de conflit avec exemples avant/après.
- Preuves ou références par constat ; hypothèses, exceptions et vérifications non réalisées séparées.
- Brief des décisions ou actions nécessaires pour l'agent rattaché, sans les annoncer déjà exécutées.

## Workflow recommandé
1. Cadrer les inputs : sources, owners par champ, horodatages et règles métier ; vérifier les préconditions et autorisations.
2. Définir autorité par donnée.
3. Détecter divergence et suppression.
4. Choisir résolution, escalade et journal d'audit.
5. Vérifier le livrable par ce critère : un horodatage local ne suffit pas à imposer un dernier écrit gagnant sans accord métier.
6. Restituer résultat, hypothèses, risques et prochaines actions ; signaler explicitement les blocages.

## Garde-fous
- Un horodatage local ne suffit pas à imposer un dernier écrit gagnant sans accord métier.
- Ne pas inventer de mesure, d'accord, de preuve ou de source ; distinguer observé, inféré et non testé.
- Ne pas transmettre d'artefact privé ou de donnée personnelle à un service tiers ; minimiser les données sensibles.
- Privilégier les outils libres maintenus et vérifier les versions applicables sans introduire de dépendance EOL.
- Lire la référence dans son contexte : elle éclaire la méthode, elle ne certifie pas ce livrable et n'impose pas de seuil universel.

## Templates copier/coller
### Entrée
```text
Objet : Application Synchronization Conflict Policy
Inputs : Sources, owners par champ, horodatages et règles métier
Version / périmètre autorisé :
Résultat demandé : Politique de conflit avec exemples avant/après
Contraintes et inconnues :
```

### Sortie
```text
Résultat : Politique de conflit avec exemples avant/après
| Élément examiné | Preuve / source / version | Conclusion | Limite / action |
|---|---|---|---|
Hypothèses :
Risques :
Prochaines actions :
```

## Checklist QA interne
- [ ] Les inputs et les limites d'autorisation sont identifiés.
- [ ] Les trois analyses sont documentées : définir autorité par donnée ; détecter divergence et suppression ; choisir résolution, escalade et journal d'audit.
- [ ] Le critère d'acceptation est vérifié ou explicitement marqué non vérifié.
- [ ] Aucun résultat d'exécution ou accord humain n'est inventé.

## KPI reliés
- Couverture des éléments requis : éléments documentés / éléments applicables de ce livrable (dénominateur conservé).
- Part des conclusions appuyées par une preuve ou une source datée ; ne pas compter une hypothèse comme preuve.
- Nombre d'écarts au critère suivant restant ouverts : un horodatage local ne suffit pas à imposer un dernier écrit gagnant sans accord métier.

## Definition of done
- [ ] Politique de conflit avec exemples avant/après livré dans le périmètre convenu.
- [ ] Un horodatage local ne suffit pas à imposer un dernier écrit gagnant sans accord métier.
- [ ] Preuves, inconnues, exceptions et actions restantes sont lisibles ; aucune réussite globale en cas de vérification bloquante manquante.

## Exemples d'usage
**Cas nominal** : à partir de sources, owners par champ, horodatages et règles métier, produire politique de conflit avec exemples avant/après puis vérifier le critère d'acceptation ci-dessus.

**Cas limite** : une preuve ou autorisation nécessaire manque ; livrer les éléments établis et indiquer précisément ce qui empêche la validation, sans substituer une valeur par défaut.

## Contraintes et références
- Référence officielle consultée le 2026-10-21 : [W3C PROV Overview](https://www.w3.org/TR/prov-overview/). Synthèse originale, sans reproduction du texte source ; vérifier les versions et l'applicabilité au contexte.
- Migration : DEL-20261021-EXCLUSIVE-SKILLS-MIGRATION.

# AI System Failure Recovery Design

## Objectif
Concevoir les chemins d'échec et de reprise d'un système IA orchestré.


## Quand l'utiliser (triggers)
- Demande portant sur « AI System Failure Recovery Design » ou sur le livrable : matrice panne/reprise/état/compensation/condition d'arrêt.
- Besoin de vérifier ce résultat : une relance ne répète pas un effet de bord irréversible sans contrôle.

## Hors périmètre
- Ne pas remplacer les domaines des agents complémentaires : présenter les interfaces et transmettre les besoins à l'agent rattaché (voir table de routage).
- L'exécution système, les modifications de fichiers, les tests et les publications relèvent de l'agent rattaché (voir table de routage) ; cette skill n'accorde aucun outil supplémentaire.
- Ne pas confondre préparation d'un protocole, revue statique et résultat d'une exécution réelle.

## Inputs requis
- Composants IA, appels outils, délais, effets de bord et états persistés.
- Périmètre autorisé, version des artefacts, sources accessibles et décisions déjà validées.
- Critères d'acceptation et limites d'action ; marquer les éléments inconnus avant de conclure.

## Sorties attendues
- Matrice panne/reprise/état/compensation/condition d'arrêt.
- Preuves ou références par constat ; hypothèses, exceptions et vérifications non réalisées séparées.
- Brief des décisions ou actions nécessaires pour l'agent rattaché, sans les annoncer déjà exécutées.

## Workflow recommandé
1. Cadrer les inputs : composants ia, appels outils, délais, effets de bord et états persistés ; vérifier les préconditions et autorisations.
2. Classifier échecs récupérables et définitifs.
3. Définir budgets de retry et idempotence.
4. Prévoir reprise humaine et compensation explicite.
5. Vérifier le livrable par ce critère : une relance ne répète pas un effet de bord irréversible sans contrôle.
6. Restituer résultat, hypothèses, risques et prochaines actions ; signaler explicitement les blocages.

## Garde-fous
- Une relance ne répète pas un effet de bord irréversible sans contrôle.
- Ne pas inventer de mesure, d'accord, de preuve ou de source ; distinguer observé, inféré et non testé.
- Ne pas transmettre d'artefact privé ou de donnée personnelle à un service tiers ; minimiser les données sensibles.
- Privilégier les outils libres maintenus et vérifier les versions applicables sans introduire de dépendance EOL.
- Lire la référence dans son contexte : elle éclaire la méthode, elle ne certifie pas ce livrable et n'impose pas de seuil universel.

## Templates copier/coller
### Entrée
```text
Objet : AI System Failure Recovery Design
Inputs : Composants IA, appels outils, délais, effets de bord et états persistés
Version / périmètre autorisé :
Résultat demandé : Matrice panne/reprise/état/compensation/condition d'arrêt
Contraintes et inconnues :
```

### Sortie
```text
Résultat : Matrice panne/reprise/état/compensation/condition d'arrêt
| Élément examiné | Preuve / source / version | Conclusion | Limite / action |
|---|---|---|---|
Hypothèses :
Risques :
Prochaines actions :
```

## Checklist QA interne
- [ ] Les inputs et les limites d'autorisation sont identifiés.
- [ ] Les trois analyses sont documentées : classifier échecs récupérables et définitifs ; définir budgets de retry et idempotence ; prévoir reprise humaine et compensation explicite.
- [ ] Le critère d'acceptation est vérifié ou explicitement marqué non vérifié.
- [ ] Aucun résultat d'exécution ou accord humain n'est inventé.

## KPI reliés
- Couverture des éléments requis : éléments documentés / éléments applicables de ce livrable (dénominateur conservé).
- Part des conclusions appuyées par une preuve ou une source datée ; ne pas compter une hypothèse comme preuve.
- Nombre d'écarts au critère suivant restant ouverts : une relance ne répète pas un effet de bord irréversible sans contrôle.

## Definition of done
- [ ] Matrice panne/reprise/état/compensation/condition d'arrêt livré dans le périmètre convenu.
- [ ] Une relance ne répète pas un effet de bord irréversible sans contrôle.
- [ ] Preuves, inconnues, exceptions et actions restantes sont lisibles ; aucune réussite globale en cas de vérification bloquante manquante.

## Exemples d'usage
**Cas nominal** : à partir de composants ia, appels outils, délais, effets de bord et états persistés, produire matrice panne/reprise/état/compensation/condition d'arrêt puis vérifier le critère d'acceptation ci-dessus.

**Cas limite** : une preuve ou autorisation nécessaire manque ; livrer les éléments établis et indiquer précisément ce qui empêche la validation, sans substituer une valeur par défaut.

## Contraintes et références
- Référence officielle consultée le 2026-10-21 : [Google SRE Workbook](https://sre.google/workbook/table-of-contents/). Synthèse originale, sans reproduction du texte source ; vérifier les versions et l'applicabilité au contexte.
- Migration : DEL-20261021-EXCLUSIVE-SKILLS-MIGRATION.

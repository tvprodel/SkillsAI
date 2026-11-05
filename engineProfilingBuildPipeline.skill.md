# Engine Profiling & Build Pipeline

## Objectif
Produire un livrable maîtrisé : rapport de profiling natif (CPU, GPU, mémoire) du moteur ou d'une extension, et pipeline de build/CI multi-plateformes reproductible avec tests et benchmarks.


## Quand l'utiliser (triggers)
- Demande portant sur « Engine Profiling & Build Pipeline » ou sur le livrable : rapport de profiling natif et pipeline de build/CI du moteur ou des extensions.
- Besoin de vérifier ce résultat : le pipeline reconstruit les artefacts de façon reproductible sur chaque plateforme déclarée et les benchmarks de référence sont rejouables avec une dispersion documentée.

## Hors périmètre
- Ne pas remplacer les domaines des agents complémentaires : présenter les interfaces et transmettre les besoins à l'agent rattaché (voir table de routage).
- L'exécution système, les modifications de fichiers, les builds, les benchmarks et les publications relèvent de l'agent rattaché (voir table de routage) ; cette skill n'accorde aucun outil supplémentaire.
- Ne pas confondre plan de profiling, revue statique et mesures réellement exécutées.
- Ne pas traiter la CI générique ni la conteneurisation non liées au moteur (relèvent de l'agent de conteneurisation via l'agent de coordination) ni les effets visuels artistiques (relèvent de l'agent d'effets visuels (VFX)).

## Inputs requis
- Moteur ou extension ciblé, version, plateformes et architectures, compilateurs et options de build.
- Scénarios de charge de référence, métriques à suivre (temps de frame, mémoire, temps de build) et matériel de mesure.
- Outils de profiling autorisés (par exemple Tracy, perf, RenderDoc, Valgrind) et leurs licences, système de CI disponible.
- Critères d'acceptation et limites d'action ; marquer les éléments inconnus avant de conclure.

## Sorties attendues
- Rapport de profiling : méthode, outils et versions, goulots d'étranglement classés par impact, recommandations chiffrées avec leur niveau de preuve.
- Définition du pipeline de build/CI : matrice plateformes, cache, signature des artefacts, étapes de tests et de benchmarks.
- Protocole de benchmark reproductible et seuils de régression proposés.
- Preuves ou références par constat ; hypothèses, exceptions et vérifications non réalisées séparées.
- Brief des décisions ou actions nécessaires pour l'agent rattaché, sans les annoncer déjà exécutées.

## Workflow recommandé
1. Cadrer les inputs : cible, plateformes, scénarios de charge, métriques et outils autorisés.
2. Établir une mesure de base reproductible (build release avec symboles, machine et charge fixées, plusieurs exécutions).
3. Profiler CPU, GPU et mémoire, classer les goulots d'étranglement et formuler des hypothèses vérifiables.
4. Définir le pipeline de build/CI : matrice de plateformes, builds déterministes autant que possible, cache, tests et benchmarks automatisés.
5. Vérifier le livrable par ce critère : le pipeline reconstruit les artefacts de façon reproductible sur chaque plateforme déclarée et les benchmarks de référence sont rejouables avec une dispersion documentée.
6. Restituer rapport, pipeline, hypothèses, risques et prochaines actions ; signaler explicitement les blocages et les mesures non réalisées.

## Garde-fous
- Le pipeline reconstruit les artefacts de façon reproductible sur chaque plateforme déclarée et les benchmarks de référence sont rejouables avec une dispersion documentée.
- Ne jamais comparer des mesures issues de builds, machines ou charges différents sans le signaler.
- Ne pas inventer de mesure ni de gain ; distinguer observé, inféré et non testé.
- Aucun secret en dur dans les fichiers de CI : variables d'environnement ou coffre de secrets de la plateforme.
- Épingler les versions des compilateurs et des actions de CI ; ne pas utiliser de version EOL ni de version préliminaire en production sans justification tracée.
- Vérifier les licences des outils et dépendances (MIT, Apache, GPL) ; privilégier les outils libres.
- Ne pas transmettre de traces de profiling ou de binaires privés à un service tiers.
- Lire la référence dans son contexte : elle éclaire la méthode, elle ne certifie pas ce livrable et n'impose pas de seuil universel.

## Templates copier/coller
### Entrée
```text
Objet : Engine Profiling & Build Pipeline
Inputs : cible et version, plateformes, compilateurs, scénarios de charge, métriques, outils de profiling, CI disponible
Version / périmètre autorisé :
Résultat demandé : rapport de profiling natif et pipeline de build/CI reproductible avec benchmarks
Contraintes et inconnues :
```

### Sortie
```text
Résultat : rapport de profiling et pipeline de build/CI
| Goulot / étape | Preuve (outil, version, trace) | Impact estimé | Action / limite |
|---|---|---|---|
Mesure de base (machine, build, charge, nombre d'exécutions, dispersion) :
Matrice de plateformes du pipeline :
Hypothèses :
Risques :
Prochaines actions :
```

## Checklist QA interne
- [ ] Les inputs et les limites d'autorisation sont identifiés.
- [ ] Les trois analyses sont documentées : mesure de base reproductible ; classement des goulots CPU, GPU et mémoire ; matrice de build/CI avec tests et benchmarks.
- [ ] Les versions des compilateurs, outils et actions de CI sont épinglées et non EOL.
- [ ] Le critère d'acceptation est vérifié ou explicitement marqué non vérifié.
- [ ] Aucun résultat de mesure ou de build n'est inventé.

## KPI reliés
- Plateformes déclarées reconstruites de façon reproductible / plateformes déclarées (dénominateur conservé).
- Dispersion (écart relatif entre exécutions) des benchmarks de référence, comparée au seuil déclaré.
- Nombre de goulots classés « élevé » sans preuve de mesure restant ouverts au critère : benchmarks rejouables avec dispersion documentée.

## Definition of done
- [ ] Rapport de profiling et définition du pipeline de build/CI livrés dans le périmètre convenu.
- [ ] Le pipeline reconstruit les artefacts de façon reproductible sur chaque plateforme déclarée et les benchmarks de référence sont rejouables avec une dispersion documentée.
- [ ] Preuves, inconnues, exceptions et actions restantes sont lisibles ; aucune réussite globale en cas de vérification bloquante manquante.

## Exemples d'usage
**Cas nominal** : à partir d'une extension GDExtension C++ ralentissant la frame sur Linux et Windows, produire le rapport de profiling et un pipeline de build/CI avec benchmarks, puis vérifier le critère d'acceptation ci-dessus.

**Cas limite** : le matériel de mesure ou une plateforme de CI manque ; livrer les mesures et le pipeline établis, indiquer ce qui reste non vérifié, sans extrapoler de gain de performance.

## Contraintes et références
- Référence officielle : [Tracy Profiler](https://github.com/wolfpld/tracy). Synthèse originale, sans reproduction du texte source ; page non consultée en détail lors de la création, vérifier les versions et l'applicabilité au contexte.
- Création : DEL-20261026-GAMEDEV-CREA-AGENTS.

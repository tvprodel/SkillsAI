# FX Performance Budget Optimization

## Objectif
Produire un livrable maîtrisé : budget de performance des effets visuels (particules, overdraw, shaders, post-traitement) avec mesures avant/après et plan d'optimisation priorisé.


## Quand l'utiliser (triggers)
- Demande portant sur « FX Performance Budget Optimization » ou sur le livrable : budget de performance des effets visuels (particules, overdraw, shaders, post-traitement) avec mesures avant/après et plan d'optimisation priorisé.
- Besoin de vérifier ce résultat : chaque effet respecte son budget déclaré (particules simultanées, couches transparentes, coût GPU en ms) sur la machine de référence, mesures à l'appui.

## Hors périmètre
- Ne pas remplacer les domaines des agents complémentaires : présenter les interfaces et transmettre les besoins à l'agent rattaché (voir table de routage).
- L'exécution système, les modifications de fichiers, les tests et les publications relèvent de l'agent rattaché (voir table de routage) ; cette skill n'accorde aucun outil supplémentaire.
- Ne pas confondre préparation d'un protocole, revue statique et résultat d'une exécution réelle dans le logiciel.
- L'optimisation du moteur ou du rendu bas niveau et du code de gameplay reste hors périmètre ; la transmettre à l'agent de coordination pour l'agent de développement moteur ou l'agent de développement Godot.

## Inputs requis
- Machine et plateforme de référence (CPU, GPU, résolution cible, framerate visé), version de Godot et moteur de rendu.
- Liste des effets concernés avec leur usage en jeu (nombre d'instances simultanées au pire cas) et scène de mesure représentative.
- Mesures disponibles (moniteur de performance, profileur du moteur) ; si absentes, marquer l'état comme non mesuré.
- Périmètre autorisé et décisions déjà validées ; marquer les éléments inconnus avant de conclure.

## Sorties attendues
- Tableau de budget par effet : particules maximales, couches transparentes superposées, coût GPU estimé ou mesuré, mémoire des textures.
- Mesures avant/après pour chaque optimisation, avec conditions de mesure décrites ; plan priorisé par gain attendu et effort.
- Preuves ou références par constat ; hypothèses, exceptions et vérifications non réalisées séparées.
- Brief des décisions ou actions nécessaires pour l'agent rattaché, sans les annoncer déjà exécutées.

## Workflow recommandé
1. Cadrer la référence : machine, résolution, framerate visé, moteur de rendu et pire cas d'usage en jeu ; vérifier les autorisations.
2. Établir le budget global puis le répartir par effet (particules, overdraw, shaders, post-traitement) selon leur importance visuelle.
3. Mesurer l'état initial dans une scène de pire cas ; noter les conditions pour que la mesure soit reproductible.
4. Appliquer les leviers par ordre de gain : réduction du nombre de particules, taille et surface des quads, atlas et flipbooks, fusion simplifiée, LOD d'effets, désactivation hors champ, simplification des shaders.
5. Vérifier le critère : chaque effet respecte son budget déclaré (particules simultanées, couches transparentes, coût GPU en ms) sur la machine de référence, mesures à l'appui, sans perte de lisibilité jugée bloquante.
6. Restituer budget, mesures avant/après, hypothèses, risques et prochaines actions ; signaler explicitement les blocages et les mesures non réalisées.

## Garde-fous
- Chaque effet porte un budget explicite ; aucun gain n'est annoncé sans mesure avant/après dans des conditions comparables.
- Ne pas imposer de seuil universel : les budgets dépendent de la machine de référence et du pire cas déclarés.
- Ne pas dégrader la lisibilité ni l'accessibilité pour gagner en performance : conserver les repères visuels de gameplay et la variante à flashs limités (photosensibilité).
- Ne pas inventer de mesure, d'accord, de preuve ou de source ; distinguer observé, inféré et non testé.
- Ne pas transmettre d'artefact privé ou de donnée personnelle à un service tiers ; minimiser les données sensibles.
- Privilégier les outils libres maintenus et vérifier les versions applicables sans introduire de dépendance EOL.
- Utiliser uniquement des ressources originales, du Domaine Public ou CC0 ; tracer chaque source externe dans `docs/imageLicencesSources.md` (format `Nomdefichier | licence | url source`).
- Lire la référence dans son contexte : elle éclaire la méthode, elle ne certifie pas ce livrable et n'impose pas de seuil universel.

## Templates copier/coller
### Entrée
```text
Objet : FX Performance Budget Optimization
Inputs : machine et plateforme de référence, framerate visé, version de Godot et moteur de rendu, liste des effets et pire cas, mesures existantes
Version / périmètre autorisé :
Résultat demandé : budget par effet avec mesures avant/après et plan d'optimisation priorisé
Contraintes et inconnues :
```

### Sortie
```text
Résultat : budget de performance des effets visuels (budget, mesures, plan)
| Effet | Budget (particules / couches / ms GPU) | Mesure avant → après | Limite / action |
|---|---|---|---|
Conditions de mesure (machine, résolution, scène) :
Hypothèses :
Risques :
Prochaines actions :
```

## Checklist QA interne
- [ ] Les inputs, la machine de référence et les limites d'autorisation sont identifiés.
- [ ] Les trois analyses sont documentées : répartition du budget par effet ; mesure initiale reproductible en pire cas ; leviers appliqués par ordre de gain avec mesure après.
- [ ] Le critère d'acceptation est vérifié ou explicitement marqué non vérifié.
- [ ] Les effets non mesurés sont signalés comme tels et non comptés comme conformes.
- [ ] Aucun résultat d'exécution ou accord humain n'est inventé.

## KPI reliés
- Part des effets avec budget déclaré et mesuré : effets mesurés / effets applicables (dénominateur conservé).
- Écart de coût GPU mesuré avant/après optimisation, en ms, dans des conditions comparables.
- Nombre d'effets dépassant encore leur budget déclaré dans la scène de pire cas.

## Definition of done
- [ ] Budget par effet, mesures avant/après et plan priorisé livrés dans le périmètre convenu.
- [ ] Chaque effet respecte son budget déclaré sur la machine de référence, mesures à l'appui, ou l'écart est explicitement listé.
- [ ] Preuves, inconnues, exceptions et actions restantes sont lisibles ; aucune réussite globale en cas de vérification bloquante manquante.

## Exemples d'usage
**Cas nominal** : à partir d'une scène de combat avec 12 effets d'impact simultanés, d'une machine de référence et de Godot 4.x, produire un budget par effet et un plan d'optimisation mesuré, puis vérifier le critère d'acceptation ci-dessus.

**Cas limite** : une preuve ou autorisation nécessaire manque (par exemple aucune machine de référence fournie) ; livrer le budget en hypothèses marquées non mesurées et indiquer précisément ce qui empêche la validation, sans substituer une valeur par défaut.

## Contraintes et références
- Référence officielle : [Godot - Performance](https://docs.godotengine.org/en/stable/tutorials/performance/index.html). Synthèse originale, sans reproduction du texte source ; page non consultée en détail lors de la création, vérifier les versions et l'applicabilité au contexte.
- Création : DEL-20261026-GAMEDEV-CREA-AGENTS.

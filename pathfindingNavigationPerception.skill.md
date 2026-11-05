# Pathfinding, Navigation & Perception

## Objectif
Produire un livrable maîtrisé : spécification de la navigation et de la perception d'agents de jeu (pathfinding A* ou navmesh, steering, évitement, vision, ouïe, mémoire) avec paramètres, cas de test et budget de performance.


## Quand l'utiliser (triggers)
- Demande portant sur « Pathfinding, Navigation & Perception » ou sur le livrable : spécification de la navigation (A*, navmesh, steering, évitement) et de la perception (vision, ouïe, mémoire) d'agents de jeu.
- Besoin de décider comment un agent se déplace, évite les obstacles et les autres agents, ou détecte et mémorise le joueur.
- Besoin de vérifier ce résultat : sur les cartes de test, les agents atteignent leur but, ne restent pas bloqués et respectent le budget de recherche de chemin et de perception.

## Hors périmètre
- Ne pas implémenter les nœuds de navigation, les scripts ni les scènes Godot : transmettre la spécification à l'agent de développement Godot via l'agent de coordination.
- Ne pas concevoir de moteur de navigation natif ni d'optimisation bas niveau (C++/Rust, GDExtension) : demander l'orientation à l'agent de coordination (l'agent de développement moteur).
- Ne pas concevoir de modèle d'apprentissage automatique ni d'agent conversationnel, ni les animations de déplacement.
- L'exécution système, les modifications de fichiers, les tests et les publications relèvent de l'agent rattaché (voir table de routage) ; cette skill n'accorde aucun outil supplémentaire.
- Ne pas confondre spécification, revue statique et résultat d'une exécution réelle dans le moteur.

## Inputs requis
- Type de monde (2D grille, 2D libre, 3D), taille des cartes, terrains et coûts, obstacles statiques et dynamiques.
- Types d'agents (rayon, vitesse, capacités de saut ou d'escalade), nombre maximal d'agents simultanés, comportement attendu en foule ou en escouade.
- Règles de perception : champ de vision, portée, occlusion, bruits, durée de mémoire, alertes partagées.
- Version de Godot visée, budget CPU alloué à la navigation et à la perception, plateforme cible ; marquer les éléments inconnus.

## Sorties attendues
- Choix justifié de la représentation spatiale (grille, graphe de waypoints, navmesh) et de l'algorithme de recherche, avec heuristique et coûts de terrain.
- Spécification du suivi de chemin : steering, lissage, évitement local, gestion des chemins invalidés ou bloqués, replanification avec délai minimal.
- Modèle de perception : vision (cône, portée, occlusion), ouïe (événements sonores, atténuation), mémoire (dernière position connue, oubli), fréquence de mise à jour.
- Cartes et cas de test (couloir étroit, goulot, obstacle mobile, foule, cible inaccessible) avec résultats attendus et budget de performance par agent.
- Brief des décisions ou actions nécessaires pour l'agent rattaché, sans les annoncer déjà exécutées.

## Workflow recommandé
1. Cadrer les inputs : monde, agents, perception voulue, budget CPU, plateforme ; vérifier les préconditions et le périmètre.
2. Choisir la représentation spatiale et l'algorithme de recherche, avec coûts de terrain et gestion des cibles inaccessibles ; justifier par un comparatif court.
3. Spécifier le suivi de chemin, l'évitement local et la replanification (fréquence, déclencheurs, délais minimaux) pour éviter les blocages et les oscillations.
4. Spécifier la perception : vision, ouïe, mémoire, partage d'alertes, et fréquence d'échantillonnage échelonnée entre agents.
5. Définir les cartes de test et le budget de performance (temps de calcul par agent et par image, nombre maximal de requêtes par image) ; vérifier le critère d'acceptation ci-dessous.
6. Restituer résultat, hypothèses, risques et prochaines actions ; transmettre l'implémentation à l'agent de développement Godot via l'agent de coordination.

## Garde-fous
- Sur les cartes de test, les agents atteignent leur but ou concluent proprement à l'inaccessibilité, ne restent pas bloqués et respectent le budget de calcul par agent et par image défini avant la conception.
- Ne pas inventer de fonctionnalité Godot ni d'algorithme : en cas d'incertitude sur une API de navigation, l'indiquer et proposer une vérification dans la documentation officielle.
- Ne pas inventer de mesure de performance : un budget est une cible à mesurer dans le moteur, jamais un résultat supposé.
- Échelonner les mises à jour de perception et de recherche de chemin entre les agents plutôt que de tout recalculer à chaque image.
- Privilégier les outils libres maintenus et vérifier les versions applicables sans introduire de dépendance EOL ; aucun secret en dur.
- Lire la référence dans son contexte : elle éclaire la méthode, elle ne certifie pas ce livrable et n'impose pas de seuil universel.

## Templates copier/coller
### Entrée
```text
Objet : Pathfinding, Navigation & Perception
Inputs : type de monde, taille des cartes, types d'agents, nombre d'agents, règles de perception, budget CPU, plateforme
Version / périmètre autorisé :
Résultat demandé : spécification de navigation et de perception (représentation, algorithme, suivi de chemin, perception, cas de test, budget)
Contraintes et inconnues :
```

### Sortie
```text
Résultat : spécification de navigation et de perception (représentation spatiale, algorithme, évitement, perception, cas de test, budget)
| Élément (carte, agent, capteur) | Paramètres / source / version | Cas de test et résultat attendu | Budget CPU cible | Limite / action |
|---|---|---|---|---|
Hypothèses :
Risques :
Prochaines actions :
```

## Checklist QA interne
- [ ] Les inputs, le budget CPU et les limites d'autorisation sont identifiés.
- [ ] Les trois analyses sont documentées : représentation spatiale et algorithme ; suivi de chemin, évitement et replanification ; modèle de perception et fréquences de mise à jour.
- [ ] Les cas de blocage (couloir étroit, goulot, cible inaccessible, obstacle mobile) ont chacun un résultat attendu.
- [ ] Le critère d'acceptation est vérifié ou explicitement marqué non vérifié.
- [ ] Aucun résultat d'exécution ou accord humain n'est inventé.

## KPI reliés
- Taux de réussite de navigation sur les cartes de test : parcours atteignant le but ou concluant proprement à l'inaccessibilité / parcours testés (dénominateur conservé).
- Temps de calcul par agent et par image, et nombre de requêtes de chemin par image, comparés au budget cible une fois mesurés dans le moteur.
- Nombre de blocages ou d'oscillations restant ouverts après les cas de test.
- Part des conclusions appuyées par une preuve ou une source datée ; ne pas compter une hypothèse comme preuve.

## Definition of done
- [ ] Spécification de navigation et de perception livrée dans le périmètre convenu (représentation, algorithme, évitement, perception, cas de test, budget).
- [ ] Les agents atteignent leur but ou concluent à l'inaccessibilité sur les cartes de test, sans blocage, dans le budget défini ; sinon l'écart est documenté.
- [ ] Preuves, inconnues, exceptions et actions restantes sont lisibles ; aucune réussite globale en cas de vérification bloquante manquante.

## Exemples d'usage
**Cas nominal** : à partir d'une carte 3D de donjon, de trente ennemis simultanés et d'un budget CPU, produire la spécification navmesh avec évitement local, un modèle de vision et d'ouïe, et cinq cartes de test, puis vérifier le critère d'acceptation ci-dessus.

**Cas limite** : la taille des cartes ou le nombre d'agents n'est pas connu ; livrer les choix indépendants de l'échelle, indiquer précisément ce qui empêche la validation du budget, sans substituer une valeur par défaut.

## Contraintes et références
- Référence officielle : [Godot - Using navigation](https://docs.godotengine.org/en/stable/tutorials/navigation/index.html). Synthèse originale, sans reproduction du texte source ; page non consultée en détail lors de la création, vérifier les versions et l'applicabilité au contexte.
- Création : DEL-20261026-GAMEDEV-CREA-AGENTS.

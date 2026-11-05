# NPC Behavior Trees & State Machines

## Objectif
Produire un livrable maîtrisé : spécification du comportement d'un PNJ, ennemi ou allié (machine à états FSM/HFSM, behavior tree, utility AI ou GOAP) avec diagramme, tables d'états et de transitions, données paramétrables et scénarios de test déterministes.


## Quand l'utiliser (triggers)
- Demande portant sur « NPC Behavior Trees & State Machines » ou sur le livrable : spécification du comportement d'un PNJ (FSM/HFSM, behavior tree, utility AI, GOAP) avec diagramme, tables et scénarios de test.
- Besoin de choisir ou de justifier une architecture de décision (FSM, behavior tree, utility AI, GOAP) pour un type d'ennemi, d'allié ou de PNJ.
- Besoin de vérifier ce résultat : chaque scénario de test produit la même séquence d'états ou d'actions à seed identique, sans état inatteignable ni transition ambiguë.

## Hors périmètre
- Ne pas implémenter le code GDScript, les scènes ou les nœuds Godot : transmettre la spécification à l'agent de développement Godot via l'agent de coordination.
- Ne pas concevoir de modèle d'apprentissage automatique ni d'agent conversationnel : demander l'orientation à l'agent de coordination (l'agent de machine learning ou l'agent spécialiste en IA générative).
- Ne pas écrire les dialogues ou quêtes, ni l'économie du jeu, ni les animations.
- L'exécution système, les modifications de fichiers, les tests et les publications relèvent de l'agent rattaché (voir table de routage) ; cette skill n'accorde aucun outil supplémentaire.
- Ne pas confondre spécification, revue statique d'une logique et résultat d'une exécution réelle dans le moteur.

## Inputs requis
- Fiche du personnage (rôle, capacités, ressources, ennemis ou alliés visés), fantasme de jeu voulu, difficulté cible.
- Liste des actions disponibles, des capteurs ou informations accessibles (perception, blackboard) et des contraintes de design.
- Version de Godot visée, budget CPU alloué à l'IA, nombre maximal d'agents simultanés.
- Décisions déjà validées, périmètre autorisé et critères d'acceptation ; marquer les éléments inconnus avant de conclure.

## Sorties attendues
- Choix d'architecture de décision justifié (comparatif court FSM / HFSM / behavior tree / utility AI / GOAP) avec critères.
- Diagramme (Mermaid ou équivalent texte) et tables : états, transitions, conditions, priorités, interruptions, valeurs par défaut.
- Pseudo-code des nœuds ou des scores, schéma de données paramétrables (ressource, JSON ou tableau) séparant logique et réglages.
- Scénarios de test déterministes (seed, situation initiale, séquence attendue) à transmettre à l'agent qualité.
- Brief des décisions ou actions nécessaires pour l'agent rattaché, sans les annoncer déjà exécutées.

## Workflow recommandé
1. Cadrer les inputs : fiche du personnage, actions, informations accessibles, budget CPU, nombre d'agents ; vérifier les préconditions et le périmètre.
2. Lister les comportements voulus (patrouille, poursuite, fuite, attaque, soutien, retour) et leurs conditions d'entrée et de sortie.
3. Choisir l'architecture : FSM/HFSM pour des modes clairs, behavior tree pour la composition et la priorité, utility AI pour les arbitrages graduels, GOAP pour les plans dynamiques ; justifier par un comparatif court.
4. Spécifier états, nœuds ou actions, transitions et interruptions ; traiter explicitement les conflits, les oscillations (hystérésis, délai minimal) et les cas d'échec d'action.
5. Définir les données paramétrables et les scénarios de test déterministes (seed, situation, séquence attendue) ; vérifier le critère d'acceptation ci-dessous.
6. Restituer résultat, hypothèses, risques et prochaines actions ; transmettre l'implémentation à l'agent de développement Godot via l'agent de coordination.

## Garde-fous
- Chaque scénario de test produit la même séquence d'états ou d'actions à seed identique ; aucun état n'est inatteignable et aucune paire de transitions n'est ambiguë.
- Ne pas inventer de fonctionnalité Godot ni d'algorithme : en cas d'incertitude, l'indiquer et proposer une vérification dans la documentation officielle.
- Ne pas inventer de mesure, d'accord, de preuve ou de source ; distinguer observé, inféré et non testé.
- Séparer la logique de décision des paramètres de réglage pour permettre l'équilibrage sans modifier la structure.
- Privilégier les outils libres maintenus et vérifier les versions applicables sans introduire de dépendance EOL ; aucun secret en dur.
- Lire la référence dans son contexte : elle éclaire la méthode, elle ne certifie pas ce livrable et n'impose pas de seuil universel.

## Templates copier/coller
### Entrée
```text
Objet : NPC Behavior Trees & State Machines
Inputs : fiche du personnage, actions disponibles, informations accessibles, difficulté cible, budget CPU, nombre d'agents
Version / périmètre autorisé :
Résultat demandé : spécification du comportement (architecture, diagramme, transitions, données, scénarios de test)
Contraintes et inconnues :
```

### Sortie
```text
Résultat : spécification du comportement du PNJ (architecture choisie, diagramme, tables d'états et de transitions, données, scénarios de test)
| Comportement / état | Conditions d'entrée et de sortie | Priorité / interruption | Scénario de test (seed) | Limite / action |
|---|---|---|---|---|
Hypothèses :
Risques :
Prochaines actions :
```

## Checklist QA interne
- [ ] Les inputs, le budget CPU et les limites d'autorisation sont identifiés.
- [ ] Les trois analyses sont documentées : comparatif et choix d'architecture ; états, transitions et interruptions ; données paramétrables et scénarios de test déterministes.
- [ ] Les oscillations et les cas d'échec d'action sont traités explicitement.
- [ ] Le critère d'acceptation est vérifié ou explicitement marqué non vérifié.
- [ ] Aucun résultat d'exécution ou accord humain n'est inventé.

## KPI reliés
- Couverture des comportements : comportements voulus couverts par au moins un scénario de test / comportements voulus (dénominateur conservé).
- Part des états et transitions atteints par au moins un scénario ; nombre d'états inatteignables restant ouverts.
- Nombre de transitions ambiguës ou oscillantes restant ouvertes après revue.
- Part des conclusions appuyées par une preuve ou une source datée ; ne pas compter une hypothèse comme preuve.

## Definition of done
- [ ] Spécification du comportement du PNJ livrée dans le périmètre convenu (architecture, diagramme, tables, données, scénarios).
- [ ] Chaque scénario de test produit la même séquence à seed identique, sans état inatteignable ni transition ambiguë.
- [ ] Preuves, inconnues, exceptions et actions restantes sont lisibles ; aucune réussite globale en cas de vérification bloquante manquante.

## Exemples d'usage
**Cas nominal** : à partir de la fiche d'un garde de forteresse (patrouille, alerte, poursuite, retour), de ses capteurs et d'un budget CPU, produire un behavior tree documenté avec table de transitions et trois scénarios de test à seed fixe, puis vérifier le critère d'acceptation ci-dessus.

**Cas limite** : le budget CPU ou la liste des informations accessibles manque ; livrer l'architecture et les états établis, indiquer précisément ce qui empêche la validation, sans substituer une valeur par défaut.

## Contraintes et références
- Référence officielle : [Godot - Documentation (stable)](https://docs.godotengine.org/en/stable/). Synthèse originale, sans reproduction du texte source ; page non consultée en détail lors de la création, vérifier les versions et l'applicabilité au contexte.
- Création : DEL-20261026-GAMEDEV-CREA-AGENTS.

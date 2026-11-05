# Progression & Loot Table Balancing

## Objectif
Produire un livrable maîtrisé : courbes d'XP et de niveaux, tables de loot avec taux de drop, prix des objets et recettes de crafting, équilibrés et vérifiés par simulation.


## Quand l'utiliser (triggers)
- Demande portant sur « Progression & Loot Table Balancing » ou sur le livrable : courbes d'XP et de niveaux, tables de loot avec taux de drop, prix des objets et recettes de crafting, équilibrés et vérifiés par simulation.
- Besoin de vérifier ce résultat : la simulation de milliers de parcours atteint les temps de progression cibles et les fréquences de drop déclarées, dans la tolérance fixée.

## Hors périmètre
- Ne pas remplacer les domaines des agents complémentaires : présenter les interfaces et transmettre les besoins à l'agent de coordination (code Godot, analyse statistique avancée, A/B test, narration, IA de PNJ).
- L'exécution système, les modifications de fichiers, les tests et les publications relèvent de l'agent rattaché (voir table de routage) ; cette skill n'accorde aucun outil supplémentaire.
- Ne pas concevoir de mécanisme de drop payant ou à rareté artificielle ciblant les mineurs : ce volet relève de la skill de monétisation éthique et des agents compétents.

## Inputs requis
- Durée de progression visée par palier (ex. heures de jeu du niveau 1 au niveau maximal), rythme des sessions, sources d'XP et de loot connues.
- Catalogue d'objets avec rareté souhaitée, valeur d'usage, rôle dans le crafting et prix d'ancrage issus du modèle sources/sinks.
- Seed, version des tables, tolérance admise sur les taux ; marquer les valeurs inconnues avant de conclure.

## Sorties attendues
- Courbe d'XP (formule, paramètres, plages) et table des niveaux avec temps cumulé estimé.
- Tables de loot : poids ou probabilités par rareté, taux de drop effectifs, mécanisme de pitié ou de borne éventuel, avec leurs hypothèses.
- Grille de prix et recettes de crafting cohérentes avec les sinks du modèle économique.
- Fichiers de données (CSV ou tableur) prêts à être importés par l'agent technique du moteur de jeu, et brief des décisions pour l'agent de coordination.

## Workflow recommandé
1. Cadrer les inputs : durée visée, rythme de jeu, catalogue d'objets, prix d'ancrage ; vérifier le statut (observé, simulé, supposé) de chaque paramètre.
2. Choisir la forme de la courbe d'XP (linéaire, polynomiale, exponentielle amortie), la calibrer sur les temps cibles par palier et documenter la plage admise de chaque paramètre.
3. Définir les tables de loot (poids par rareté, tirages indépendants ou avec borne) et dériver les taux effectifs ; relier prix et recettes au coût de production des ressources.
4. Simuler des milliers de parcours (Python/NumPy ou tableur) avec seed et version fixées, y compris des joueurs plus chanceux ou plus rapides que la moyenne.
5. Vérifier le livrable par ce critère : la simulation atteint les temps de progression cibles et les fréquences de drop déclarées, dans la tolérance fixée, et un résultat reproduit avec la même seed.
6. Restituer résultat, hypothèses, risques et prochaines actions ; transmettre les tables à l'agent technique du moteur de jeu et signaler explicitement les blocages.

## Garde-fous
- La simulation atteint les temps de progression cibles et les fréquences de drop déclarées dans la tolérance fixée.
- Publier les taux de drop effectifs tels que simulés ; ne jamais annoncer un taux différent de celui implémenté.
- Ne pas inventer de mesure ni de source ; distinguer observé, simulé et supposé, et ne pas compter une hypothèse comme preuve.
- Aucune donnée personnelle de joueur ; n'utiliser que des agrégats anonymisés ; aucun secret en dur.
- Privilégier les outils libres maintenus (LibreOffice Calc, Python/NumPy) sans dépendance EOL.
- Lire la référence dans son contexte : elle éclaire la méthode, elle ne certifie pas ce livrable et n'impose pas de seuil universel.

## Templates copier/coller
### Entrée
```text
Objet : Progression & Loot Table Balancing
Inputs : durée de progression visée, rythme de sessions, catalogue d'objets, raretés, prix d'ancrage, seed, tolérance
Version des tables / périmètre autorisé :
Résultat demandé : courbe XP, tables de loot, prix et recettes équilibrés par simulation
Contraintes et inconnues :
```

### Sortie
```text
Résultat : courbe XP, tables de loot, prix et recettes, avec simulation reproductible
| Élément | Paramètre / plage | Valeur simulée vs cible | Écart / tolérance | Statut (observé / simulé / supposé) |
|---|---|---|---|---|
Seed / version / nombre de parcours simulés :
Hypothèses :
Risques :
Prochaines actions :
```

## Checklist QA interne
- [ ] Les inputs, tolérances et limites d'autorisation sont identifiés.
- [ ] Les trois analyses sont documentées : calibrage de la courbe d'XP sur les temps cibles ; dérivation des taux de drop effectifs ; cohérence prix, recettes et sinks.
- [ ] Le critère d'acceptation est vérifié ou explicitement marqué non vérifié.
- [ ] Aucun résultat de simulation n'est inventé ; seed et version sont notées.

## KPI reliés
- Écart entre temps de progression simulé et cible, par palier, en pourcentage (dénominateur : paliers applicables).
- Écart entre taux de drop simulé et déclaré, par rareté, rapporté à la tolérance fixée.
- Nombre de paliers ou de raretés hors tolérance restant ouverts : la simulation atteint les temps de progression cibles et les fréquences de drop déclarées.

## Definition of done
- [ ] Courbes, tables de loot, prix et recettes livrés dans le périmètre convenu, en fichiers de données importables.
- [ ] La simulation atteint les temps de progression cibles et les fréquences de drop déclarées dans la tolérance fixée.
- [ ] Preuves, inconnues, exceptions et actions restantes sont lisibles ; aucune réussite globale en cas de vérification bloquante manquante.

## Exemples d'usage
**Cas nominal** : à partir d'un RPG visant 40 heures jusqu'au niveau maximal et de cinq raretés d'objets, calibrer la courbe d'XP, fixer les poids de loot, simuler 10 000 parcours avec seed fixée, puis vérifier le critère d'acceptation ci-dessus.

**Cas limite** : le catalogue d'objets est incomplet ; livrer la courbe d'XP et un gabarit de table de loot avec les raretés connues, indiquer les objets manquants qui empêchent la validation des prix, sans inventer de valeurs.

## Contraintes et références
- Référence officielle : [NumPy - Random Generator](https://numpy.org/doc/stable/reference/random/generator.html). Synthèse originale, sans reproduction du texte source ; page non consultée en détail lors de la création, vérifier les versions et l'applicabilité au contexte.
- Création : DEL-20261026-GAMEDEV-CREA-AGENTS.

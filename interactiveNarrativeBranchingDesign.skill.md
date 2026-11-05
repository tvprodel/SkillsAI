# Interactive Narrative & Branching Design

## Objectif
Produire un livrable maîtrisé : structure narrative interactive d'un jeu (arcs, nœuds de choix, branches, convergences, variables d'état du monde) sous forme de carte de narration vérifiable.


## Quand l'utiliser (triggers)
- Demande portant sur « Interactive Narrative & Branching Design » ou sur le livrable : carte de narration avec arcs, branches, points de convergence et table des variables d'état.
- Besoin de vérifier ce résultat : chaque chemin du graphe mène à une fin déclarée, aucune branche n'est orpheline, et chaque variable de narration a une origine, une condition de lecture et une valeur par défaut.

## Hors périmètre
- Ne pas remplacer les domaines des agents complémentaires : présenter les interfaces et transmettre les besoins à l'agent rattaché (voir table de routage).
- L'implémentation du système de dialogue ou de quêtes en GDScript relève de l'agent de développement Godot ; le comportement des PNJ, de l'agent d'IA de jeu ; l'économie chiffrée, de l'agent de conception économique de jeu.
- L'exécution système, les modifications de fichiers, les tests et les publications relèvent de l'agent rattaché (voir table de routage) ; cette skill n'accorde aucun outil supplémentaire.
- Ne pas confondre préparation d'un protocole, revue statique d'un graphe et résultat d'une exécution réelle dans le moteur de jeu.

## Inputs requis
- Pitch ou résumé du jeu, genre, durée visée, nombre de fins souhaité, degré de non-linéarité accepté et contraintes de production (budget de contenu, nombre de personnages).
- Format cible d'écriture (Ink, Yarn Spinner, Twine, tableur) et version de l'outil ; moteur cible.
- Canon existant (bible de monde), décisions déjà validées, sujets sensibles à traiter avec précaution.
- Critères d'acceptation et limites d'action ; marquer les éléments inconnus avant de conclure.

## Sorties attendues
- Carte de narration (arcs, actes, nœuds, choix, convergences) et table des variables d'état (nom, type, valeur par défaut, écrivains, lecteurs).
- Matrice choix → conséquences (immédiates, différées) et inventaire des fins.
- Preuves ou références par constat ; hypothèses, exceptions et vérifications non réalisées séparées.
- Brief des décisions ou actions nécessaires pour l'agent de coordination et pour l'agent de développement Godot, sans les annoncer déjà exécutées.

## Workflow recommandé
1. Cadrer les inputs : pitch, durée, fins visées, format d'écriture, canon et contraintes de contenu ; vérifier les préconditions et autorisations.
2. Définir la structure globale (arcs, actes, piliers) et choisir le modèle de branchement (parallèle, bouteille, convergent, hub, qualité d'état) selon le budget de contenu.
3. Modéliser l'état du monde : variables et drapeaux de narration, conventions de nommage stables, valeurs par défaut, règles d'écriture et de lecture.
4. Dessiner le graphe nœud par nœud : choix, conditions, conséquences et points de convergence ; consigner les avertissements de contenu des passages sensibles.
5. Vérifier le graphe par ce critère : chaque chemin mène à une fin déclarée, aucune branche n'est orpheline ni impossible à atteindre, et chaque variable est initialisée et lue au moins une fois.
6. Restituer résultat, hypothèses, risques et prochaines actions ; transmettre le graphe et la table des variables à l'agent de développement Godot ; signaler explicitement les blocages.

## Garde-fous
- Chaque chemin du graphe mène à une fin déclarée ; aucune branche orpheline, aucune variable lue sans valeur par défaut.
- Contenu original uniquement : ne pas reproduire d'œuvre protégée ni de personnages ou d'univers sous copyright.
- Signaler les sujets sensibles (violence, discrimination, mineurs) et proposer des avertissements de contenu ; ne pas les banaliser.
- Ne pas inventer de mesure, d'accord, de preuve ou de source ; distinguer observé, inféré et non testé.
- Ne pas transmettre de document de conception privé ou de donnée personnelle à un service tiers ; minimiser les données sensibles.
- Privilégier les outils libres maintenus (Ink, Yarn Spinner, Twine, Godot) en vérifiant licence et version applicables, sans dépendance EOL.
- Lire la référence dans son contexte : elle éclaire la méthode, elle ne certifie pas ce livrable et n'impose pas de seuil universel.

## Templates copier/coller
### Entrée
```text
Objet : Interactive Narrative & Branching Design
Inputs : pitch du jeu, genre, durée, nombre de fins, format d'écriture et version, canon, contraintes de contenu
Version / périmètre autorisé :
Résultat demandé : carte de narration, table des variables d'état, matrice choix → conséquences, inventaire des fins
Contraintes et inconnues :
```

### Sortie
```text
Résultat : carte de narration et table des variables d'état
| Nœud / variable | Rôle (choix, hub, fin, drapeau) | Condition / valeur par défaut | Conséquence ou lecteur | Limite / action |
|---|---|---|---|---|
Hypothèses :
Risques :
Prochaines actions :
```

## Checklist QA interne
- [ ] Les inputs et les limites d'autorisation sont identifiés.
- [ ] Les trois analyses sont documentées : choix du modèle de branchement selon le budget de contenu ; modélisation de l'état du monde et conventions de nommage ; graphe nœud par nœud avec convergences et avertissements de contenu.
- [ ] Le critère d'acceptation est vérifié ou explicitement marqué non vérifié.
- [ ] Aucun résultat d'exécution ou accord humain n'est inventé.

## KPI reliés
- Couverture des éléments requis : nœuds et variables documentés / nœuds et variables applicables (dénominateur conservé).
- Part des chemins du graphe aboutissant à une fin déclarée ; nombre de branches orphelines et de variables sans valeur par défaut restant ouvertes.
- Ratio contenu écrit / contenu joué par chemin le plus court, pour piloter le budget de branchement ; ne pas compter une hypothèse comme preuve.

## Definition of done
- [ ] Carte de narration, table des variables et inventaire des fins livrés dans le périmètre convenu.
- [ ] Chaque chemin mène à une fin déclarée, sans branche orpheline ni variable sans valeur par défaut.
- [ ] Preuves, inconnues, exceptions et actions restantes sont lisibles ; aucune réussite globale en cas de vérification bloquante manquante.

## Exemples d'usage
**Cas nominal** : à partir d'un pitch de jeu d'aventure de 6 heures avec 3 fins et un canon validé, produire la carte de narration en modèle « hub et convergence », la table des variables d'état et l'inventaire des fins, puis vérifier le critère d'acceptation ci-dessus.

**Cas limite** : le nombre de fins ou le budget de contenu n'est pas arrêté ; livrer la structure par actes et les options de branchement comparées, et indiquer précisément ce qui empêche la validation, sans substituer une valeur par défaut.

## Contraintes et références
- Référence officielle : [Ink - Writing with Ink (inkle)](https://github.com/inkle/ink/blob/master/Documentation/WritingWithInk.md). Synthèse originale, sans reproduction du texte source ; page non consultée en détail lors de la création, vérifier les versions, la licence et l'applicabilité au contexte.
- Création : DEL-20261026-GAMEDEV-CREA-AGENTS.

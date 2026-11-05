# Game AI Difficulty & Director Tuning

## Objectif
Produire un livrable maîtrisé : conception et plan de réglage d'un directeur d'IA et de l'adaptation de difficulté (rythme, intensité, apparition d'ennemis, coordination d'escouade) avec outils de debug visuel et protocole de mesure reproductible.


## Quand l'utiliser (triggers)
- Demande portant sur « Game AI Difficulty & Director Tuning » ou sur le livrable : conception d'un directeur d'IA, d'une adaptation de difficulté ou d'une IA d'escouade, avec plan de réglage et debug visuel.
- Besoin de régler la difficulté ou le rythme d'un jeu à partir de métriques de jeu observables plutôt que d'intuitions.
- Besoin de vérifier ce résultat : sur les profils de joueur simulés ou testés, les métriques de difficulté restent dans la plage cible et le comportement du directeur est reproductible à seed identique.

## Hors périmètre
- Ne pas implémenter le directeur, les outils de debug ni les scènes dans Godot : transmettre la spécification à l'agent de développement Godot via l'agent de coordination.
- Ne pas concevoir l'économie du jeu, la progression ni les récompenses : demander l'orientation à l'agent de coordination (l'agent de conception économique de jeu).
- Ne pas concevoir de modèle d'apprentissage automatique ni d'apprentissage par renforcement : demander l'orientation à l'agent de coordination (l'agent de machine learning).
- L'exécution système, les modifications de fichiers, les tests et les publications relèvent de l'agent rattaché (voir table de routage) ; cette skill n'accorde aucun outil supplémentaire.
- Ne pas confondre plan de réglage, simulation théorique et résultat de sessions de jeu réelles.

## Inputs requis
- Intention de design : expérience voulue (tension, répit, montée en puissance), public visé, modes de difficulté existants.
- Métriques de jeu disponibles : dégâts reçus, morts, temps par rencontre, précision, ressources restantes, taux d'abandon.
- Leviers modifiables : nombre et type d'ennemis, agressivité, précision, vitesse de réaction, apparition de ressources.
- Contraintes : transparence envers le joueur, équité perçue, budget CPU de l'IA, nombre maximal d'agents, vie privée des données de jeu.

## Sorties attendues
- Modèle de directeur : états de rythme (montée, pic, répit), signaux d'entrée, règles ou courbes d'intensité, limites de variation et délais de stabilisation.
- Règles d'adaptation de difficulté : métriques, fenêtres de mesure, leviers autorisés, bornes minimales et maximales, garde-fous contre les boucles de rétroaction et la sensation de triche.
- Spécification de l'IA d'escouade : rôles, jetons d'attaque, communication d'alertes, limites d'agressivité simultanée.
- Outils de debug visuel de l'IA : état courant, cible, chemin, cône de vision, scores d'utilité, journal des décisions, rejeu par seed.
- Protocole de réglage : profils de joueur, scénarios, métriques cibles, grille de paramètres, seuils d'arrêt.
- Brief des décisions ou actions nécessaires pour l'agent rattaché, sans les annoncer déjà exécutées.

## Workflow recommandé
1. Cadrer les inputs : intention de design, métriques, leviers, contraintes ; vérifier les préconditions et le périmètre.
2. Définir les métriques cibles et les plages acceptables par rencontre et par session, avec fenêtres de mesure explicites.
3. Spécifier le directeur : états de rythme, signaux, leviers, bornes, délais de stabilisation, et mécanisme d'adaptation évitant les oscillations.
4. Spécifier l'IA d'escouade (rôles, jetons d'attaque, alertes partagées) et les outils de debug visuel permettant de voir pourquoi l'IA décide.
5. Définir le protocole de réglage : profils de joueur, seeds, scénarios, grille de paramètres, critères d'arrêt ; vérifier le critère d'acceptation ci-dessous.
6. Restituer résultat, hypothèses, risques et prochaines actions ; transmettre l'implémentation à l'agent de développement Godot via l'agent de coordination.

## Garde-fous
- Sur les profils de joueur simulés ou testés, les métriques de difficulté restent dans la plage cible et le directeur se comporte de façon reproductible à seed identique ; tout écart est documenté.
- Ne pas inventer de fonctionnalité Godot ni d'algorithme ; ne pas présenter une plage cible comme un résultat mesuré.
- Borner chaque levier d'adaptation et limiter la vitesse de variation pour éviter les boucles de rétroaction et la sensation d'injustice.
- Distinguer observé en session, simulé et supposé ; ne pas conclure sur un échantillon de sessions trop réduit pour la métrique.
- Ne pas transmettre de données de jeu personnelles à un service tiers ; minimiser et anonymiser les données de télémétrie.
- Privilégier les outils libres maintenus et vérifier les versions applicables sans introduire de dépendance EOL ; aucun secret en dur.
- Lire la référence dans son contexte : elle éclaire la méthode, elle ne certifie pas ce livrable et n'impose pas de seuil universel.

## Templates copier/coller
### Entrée
```text
Objet : Game AI Difficulty & Director Tuning
Inputs : intention de design, métriques disponibles, leviers modifiables, contraintes d'équité, budget CPU, nombre d'agents
Version / périmètre autorisé :
Résultat demandé : modèle de directeur, règles d'adaptation, IA d'escouade, outils de debug visuel, protocole de réglage
Contraintes et inconnues :
```

### Sortie
```text
Résultat : conception du directeur et de l'adaptation de difficulté (modèle, règles, escouade, debug visuel, protocole de réglage)
| Métrique / levier | Plage cible et bornes | Fenêtre de mesure / seed | Preuve ou source | Limite / action |
|---|---|---|---|---|
Hypothèses :
Risques :
Prochaines actions :
```

## Checklist QA interne
- [ ] Les inputs, les leviers et les limites d'autorisation sont identifiés.
- [ ] Les trois analyses sont documentées : métriques cibles et fenêtres de mesure ; modèle de directeur, bornes et délais de stabilisation ; protocole de réglage et outils de debug visuel.
- [ ] Les risques de boucle de rétroaction et de sensation de triche sont traités explicitement.
- [ ] Le critère d'acceptation est vérifié ou explicitement marqué non vérifié.
- [ ] Aucun résultat d'exécution ou accord humain n'est inventé.

## KPI reliés
- Part des sessions ou simulations dont les métriques de difficulté restent dans la plage cible : sessions dans la plage / sessions évaluées (dénominateur conservé).
- Amplitude maximale de variation d'un levier d'adaptation par fenêtre de mesure, comparée à la borne définie.
- Part des décisions de l'IA reproductibles à seed identique parmi les scénarios rejoués.
- Part des conclusions appuyées par une preuve ou une source datée ; ne pas compter une hypothèse comme preuve.

## Definition of done
- [ ] Conception du directeur et de l'adaptation de difficulté livrée dans le périmètre convenu (modèle, règles, escouade, debug visuel, protocole).
- [ ] Les métriques restent dans la plage cible sur les profils évalués et le directeur est reproductible à seed identique ; sinon l'écart est documenté.
- [ ] Preuves, inconnues, exceptions et actions restantes sont lisibles ; aucune réussite globale en cas de vérification bloquante manquante.

## Exemples d'usage
**Cas nominal** : à partir d'un jeu d'action en salles, de métriques de dégâts reçus et de temps par rencontre, produire un directeur à trois états de rythme avec leviers bornés, un jeton d'attaque d'escouade et un protocole de réglage sur trois profils de joueur, puis vérifier le critère d'acceptation ci-dessus.

**Cas limite** : aucune métrique de jeu n'est encore disponible ; livrer le modèle de directeur et la liste des métriques à instrumenter, indiquer précisément ce qui empêche la validation, sans substituer une valeur par défaut.

## Contraintes et références
- Référence officielle : [Godot - Debugging tools](https://docs.godotengine.org/en/stable/tutorials/scripting/debug/index.html). Synthèse originale, sans reproduction du texte source ; page non consultée en détail lors de la création, vérifier les versions et l'applicabilité au contexte.
- Création : DEL-20261026-GAMEDEV-CREA-AGENTS.

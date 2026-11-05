# Game Economy Sources & Sinks Modeling

## Objectif
Produire un livrable maîtrisé : modèle de l'économie interne d'un jeu (monnaies, ressources, sources, sinks, flux, prix) avec simulation reproductible et télémétrie économique à suivre.


## Quand l'utiliser (triggers)
- Demande portant sur « Game Economy Sources & Sinks Modeling » ou sur le livrable : modèle de l'économie interne d'un jeu (monnaies, ressources, sources, sinks, flux, prix) avec simulation reproductible et télémétrie économique à suivre.
- Besoin de vérifier ce résultat : sur la durée simulée, aucune monnaie ou ressource ne diverge (inflation ou pénurie) hors de la plage cible déclarée.

## Hors périmètre
- Ne pas remplacer les domaines des agents complémentaires : présenter les interfaces et transmettre les besoins à l'agent de coordination (implémentation Godot, stratégie produit, avis juridique, paiements réels, comptabilité).
- L'exécution système, les modifications de fichiers, les tests et les publications relèvent de l'agent rattaché (voir table de routage) ; cette skill n'accorde aucun outil supplémentaire.
- Ne pas confondre valeur observée en production, valeur simulée et valeur supposée : chaque paramètre porte son statut.

## Inputs requis
- Design du jeu (boucle principale, durée de session, profils de joueurs visés), liste des monnaies et ressources, actions qui créent ou détruisent de la valeur.
- Version du modèle, outil de simulation prévu (LibreOffice Calc ou Python/NumPy), seed, horizon simulé et plages de valeurs admises.
- Données observées éventuelles (anonymisées et agrégées) ; marquer les paramètres inconnus avant de conclure.

## Sorties attendues
- Modèle de l'économie interne : inventaire des monnaies et ressources, tableau sources/sinks avec taux, graphe des flux, hypothèses datées.
- Simulation reproductible (seed, version, paramètres) et courbes de stock par monnaie sur l'horizon retenu.
- Liste des métriques de télémétrie économique à suivre (stock en circulation, flux entrants et sortants, vitesse de circulation, répartition de richesse) sans donnée personnelle.
- Brief des décisions ou actions nécessaires pour l'agent de coordination et pour l'agent technique du moteur de jeu, sans les annoncer déjà exécutées.

## Workflow recommandé
1. Cadrer les inputs : design du jeu, monnaies et ressources, profils de joueurs, plages de valeurs ; vérifier les préconditions et le statut (observé, simulé, supposé) de chaque paramètre.
2. Inventorier chaque monnaie et ressource, puis lister ses sources (gains, récompenses, drops) et ses sinks (achats, réparations, taxes, consommation) avec un taux par unité de temps de jeu.
3. Construire le bilan par profil de joueur (casual, régulier, intensif) et le graphe des flux, y compris les échanges entre joueurs s'il y a un marché.
4. Simuler (tableur ou Python/NumPy) avec seed et version fixées ; tester au moins un scénario de stress (exploit de farm, afflux de joueurs, arrêt d'un sink).
5. Vérifier le livrable par ce critère : sur la durée simulée, aucune monnaie ou ressource ne diverge hors de la plage cible déclarée, et la même seed redonne les mêmes résultats.
6. Restituer résultat, hypothèses, risques et prochaines actions ; fournir les tables de données à l'agent technique du moteur de jeu et signaler explicitement les blocages.

## Garde-fous
- Sur la durée simulée, aucune monnaie ou ressource ne diverge hors de la plage cible déclarée.
- Ne pas inventer de mesure, de taux, de preuve ou de source ; distinguer observé, simulé et supposé.
- Aucune donnée personnelle de joueur dans les livrables ; n'utiliser que des agrégats anonymisés ; aucun secret en dur.
- Ne pas promettre de revenus ni de rétention : le modèle décrit l'équilibre interne, pas un résultat commercial.
- Privilégier les outils libres maintenus (LibreOffice Calc, Python/NumPy) et vérifier les versions sans introduire de dépendance EOL.
- Lire la référence dans son contexte : elle éclaire la méthode, elle ne certifie pas ce livrable et n'impose pas de seuil universel.

## Templates copier/coller
### Entrée
```text
Objet : Game Economy Sources & Sinks Modeling
Inputs : design du jeu, monnaies et ressources, profils de joueurs, plages de valeurs, seed, horizon simulé
Version du modèle / périmètre autorisé :
Résultat demandé : modèle sources/sinks avec simulation reproductible et télémétrie à suivre
Contraintes et inconnues :
```

### Sortie
```text
Résultat : modèle économique sources/sinks, simulation reproductible, télémétrie à suivre
| Monnaie / ressource | Sources (taux) | Sinks (taux) | Plage cible | Statut (observé / simulé / supposé) |
|---|---|---|---|---|
Seed / version / horizon simulé :
Hypothèses :
Risques :
Prochaines actions :
```

## Checklist QA interne
- [ ] Les inputs, plages de valeurs et limites d'autorisation sont identifiés.
- [ ] Les trois analyses sont documentées : inventaire des sources et sinks par monnaie ; bilan par profil de joueur ; simulation avec scénario de stress.
- [ ] Le critère d'acceptation est vérifié ou explicitement marqué non vérifié.
- [ ] Aucun résultat de simulation ou accord humain n'est inventé ; seed et version sont notées.

## KPI reliés
- Couverture des monnaies et ressources modélisées : éléments documentés / éléments applicables (dénominateur conservé).
- Part des paramètres dont le statut (observé, simulé, supposé) est renseigné.
- Nombre de scénarios simulés où une monnaie sort de sa plage cible et reste ouvert : sur la durée simulée, aucune monnaie ou ressource ne diverge hors de la plage cible déclarée.

## Definition of done
- [ ] Modèle de l'économie interne livré dans le périmètre convenu, avec tables de données exploitables par l'implémentation.
- [ ] Sur la durée simulée, aucune monnaie ou ressource ne diverge hors de la plage cible déclarée ; la simulation est reproductible.
- [ ] Preuves, inconnues, exceptions et actions restantes sont lisibles ; aucune réussite globale en cas de vérification bloquante manquante.

## Exemples d'usage
**Cas nominal** : à partir d'un jeu de survie avec deux monnaies et une boucle de récolte, produire le tableau sources/sinks, simuler 30 jours de jeu pour trois profils avec seed fixée, puis vérifier le critère d'acceptation ci-dessus.

**Cas limite** : aucune donnée observée n'existe et les taux sont supposés ; livrer le modèle avec chaque taux marqué « supposé » et la liste des mesures de télémétrie à collecter pour les remplacer, sans présenter la simulation comme une prévision.

## Contraintes et références
- Référence officielle : [Wikipedia - Virtual economy](https://en.wikipedia.org/wiki/Virtual_economy). Synthèse originale, sans reproduction du texte source ; page non consultée en détail lors de la création, vérifier les versions et l'applicabilité au contexte.
- Création : DEL-20261026-GAMEDEV-CREA-AGENTS.

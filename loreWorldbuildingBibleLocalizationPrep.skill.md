# Lore, Worldbuilding Bible & Localization Prep

## Objectif
Produire un livrable maîtrisé : bible de monde versionnée (lore, chronologie, personnages, lexique, règles de ton) et dossier de préparation à la localisation (clés de texte, contexte pour traducteurs, glossaire).


## Quand l'utiliser (triggers)
- Demande portant sur « Lore, Worldbuilding Bible & Localization Prep » ou sur le livrable : bible de monde versionnée et dossier de préparation à la localisation.
- Besoin de vérifier ce résultat : aucune contradiction de canon non résolue, chaque terme propre du monde figure au glossaire avec sa définition, et chaque chaîne exportée porte une clé stable et un contexte.

## Hors périmètre
- Ne pas remplacer les domaines des agents complémentaires : présenter les interfaces et transmettre les besoins à l'agent rattaché (voir table de routage).
- La traduction et la localisation finales relèvent de l'agent de traduction et localisation ; la gouvernance terminologique multilingue de fond, de l'agent de gouvernance terminologique ; la microcopie d'interface, de l'agent UX writing.
- La direction artistique des personnages relève de l'agent de direction artistique ; le copywriting de trailers et de marketing, de l'agent de copywriting.
- L'exécution système, les modifications de fichiers, les tests et les publications relèvent de l'agent rattaché (voir table de routage) ; cette skill n'accorde aucun outil supplémentaire.
- Ne pas confondre préparation de la localisation et traduction effective : aucun texte traduit n'est produit ici comme version finale.

## Inputs requis
- Pitch, thèmes, public visé et classification d'âge envisagée ; éléments de lore déjà validés (canon).
- Liste des langues cibles et format d'export des textes (CSV, PO, tableur, fichiers Ink ou Yarn) ; moteur et version.
- Scripts existants à indexer, personnages et lieux déjà nommés, contraintes de longueur de chaîne.
- Sujets sensibles à traiter avec précaution et limites d'action ; marquer les éléments inconnus avant de conclure.

## Sorties attendues
- Bible de monde versionnée : cosmologie ou contexte, chronologie, factions, lieux, personnages (voix, arcs), règles de ton, points de canon ouverts.
- Glossaire des termes propres (définition, genre grammatical si pertinent, à ne pas traduire / à adapter) et journal des décisions de canon.
- Dossier de localisation : convention de clés stables, contexte et notes pour traducteurs, contraintes de longueur, variables et pluriels signalés.
- Brief pour l'agent de traduction et localisation et l'agent de coordination, sans annoncer déjà exécutée une traduction ou une intégration.

## Workflow recommandé
1. Cadrer les inputs : pitch, canon validé, langues cibles, format d'export, sujets sensibles ; vérifier les préconditions et autorisations.
2. Structurer la bible (monde, chronologie, factions, lieux, personnages) avec un numéro de version et un journal des changements de canon.
3. Construire le glossaire et la liste des points de canon ouverts ; recouper les scripts existants pour détecter les contradictions.
4. Préparer la localisation : clés de texte stables, contexte et captures ou descriptions de scène, indication des variables, genres, pluriels et jeux de mots à adapter.
5. Vérifier le livrable par ce critère : 0 contradiction de canon non résolue, 100 % des termes propres au glossaire, et 100 % des chaînes exportées avec clé stable et contexte renseigné.
6. Restituer résultat, hypothèses, risques et prochaines actions ; transmettre le dossier de localisation à l'agent de traduction et localisation ; signaler explicitement les blocages.

## Garde-fous
- Aucune contradiction de canon non résolue : toute évolution est consignée dans le journal, avec incrément de version de la bible.
- Contenu original uniquement : ne pas reproduire d'œuvre protégée ni de personnages ou d'univers sous copyright ; vérifier les noms propres pour éviter les collisions de marque.
- Les clés de texte sont stables et indépendantes du libellé : ne jamais utiliser le texte source comme clé.
- Signaler les sujets sensibles (violence, discrimination, mineurs), les stéréotypes culturels et les risques de réception selon les marchés ; proposer des avertissements de contenu.
- Ne pas transmettre de bible ou de texte non publié, ni de donnée personnelle, à un service de traduction tiers sans accord explicite ; aucun secret en dur.
- Privilégier les outils libres maintenus (Godot, Ink, Yarn Spinner, LibreOffice) en vérifiant licence et version applicables, sans dépendance EOL.
- Lire la référence dans son contexte : elle éclaire la méthode, elle ne certifie pas ce livrable et n'impose pas de seuil universel.

## Templates copier/coller
### Entrée
```text
Objet : Lore, Worldbuilding Bible & Localization Prep
Inputs : pitch et thèmes, canon validé, langues cibles, format d'export, scripts existants, sujets sensibles
Version / périmètre autorisé :
Résultat demandé : bible de monde versionnée, glossaire, dossier de préparation à la localisation
Contraintes et inconnues :
```

### Sortie
```text
Résultat : bible de monde versionnée et dossier de localisation
| Élément (terme, entrée de canon, clé) | Source / version de la bible | Statut (validé, ouvert, contradictoire) | Contexte pour traducteur | Limite / action |
|---|---|---|---|---|
Hypothèses :
Risques :
Prochaines actions :
```

## Checklist QA interne
- [ ] Les inputs et les limites d'autorisation sont identifiés.
- [ ] Les trois analyses sont documentées : structuration et versionnement de la bible ; glossaire et détection des contradictions de canon ; clés stables, contexte et contraintes pour la localisation.
- [ ] Le critère d'acceptation est vérifié ou explicitement marqué non vérifié.
- [ ] Aucun résultat d'exécution ou accord humain n'est inventé.

## KPI reliés
- Couverture des éléments requis : entrées de canon, termes et chaînes documentés / éléments applicables (dénominateur conservé).
- Nombre de contradictions de canon restant ouvertes ; part des chaînes exportées avec clé stable et contexte renseigné.
- Taux de clés modifiées après la première livraison aux traducteurs (indicateur d'instabilité) ; ne pas compter une hypothèse comme preuve.

## Definition of done
- [ ] Bible de monde versionnée, glossaire et dossier de localisation livrés dans le périmètre convenu.
- [ ] 0 contradiction de canon non résolue, glossaire complet et chaînes exportées avec clé stable et contexte.
- [ ] Preuves, inconnues, exceptions et actions restantes sont lisibles ; aucune réussite globale en cas de vérification bloquante manquante.

## Exemples d'usage
**Cas nominal** : à partir d'un pitch de jeu de rôle et de scripts Ink existants, produire la bible v1.0, un glossaire de 40 termes propres et un export CSV de clés avec contexte pour la traduction en anglais et en néerlandais, puis vérifier le critère d'acceptation ci-dessus.

**Cas limite** : deux scripts contredisent la chronologie et le canon n'est pas arbitré ; livrer la bible avec le point de canon ouvert signalé, et indiquer précisément la décision humaine requise, sans trancher par défaut.

## Contraintes et références
- Référence officielle : [Godot - Internationalizing games](https://docs.godotengine.org/en/stable/tutorials/i18n/internationalizing_games.html). Synthèse originale, sans reproduction du texte source ; page non consultée en détail lors de la création, vérifier les versions et l'applicabilité au contexte.
- Création : DEL-20261026-GAMEDEV-CREA-AGENTS.

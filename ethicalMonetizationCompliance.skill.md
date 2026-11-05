# Ethical Monetization & Compliance Watch

## Objectif
Produire un livrable maîtrisé : revue de monétisation éthique d'une économie de jeu (absence de dark patterns, protection des mineurs) avec registre des points de vigilance réglementaires à faire valider par les agents juridiques.


## Quand l'utiliser (triggers)
- Demande portant sur « Ethical Monetization & Compliance Watch » ou sur le livrable : revue de monétisation éthique d'une économie de jeu avec registre des points de vigilance réglementaires.
- Besoin de vérifier ce résultat : chaque mécanisme monétisé est classé (acceptable, à risque, à retirer) et chaque point de vigilance a une orientation vers un agent ou un professionnel compétent.

## Hors périmètre
- Ne pas émettre d'avis juridique : signaler les points de vigilance et orienter vers l'agent de conseil juridique ou l'agent de conformité RGPD, via l'agent de coordination.
- Ne pas traiter la stratégie de monétisation d'entreprise (l'agent produit), les paiements réels (l'agent FinTech) ni la comptabilité ou la TVA (l'agent comptable) ; transmettre à l'agent de coordination.
- L'exécution système, les modifications de fichiers, les tests et les publications relèvent de l'agent rattaché (voir table de routage) ; cette skill n'accorde aucun outil supplémentaire.

## Inputs requis
- Liste des mécanismes monétisés ou assimilés (boutiques, monnaies premium, loot boxes ou coffres, passes, offres limitées dans le temps), avec prix et taux de drop publiés.
- Public cible déclaré (âge), marchés visés (dont la Belgique), plateformes de distribution et leurs règles connues.
- Version du design évalué ; marquer les éléments inconnus avant de conclure.

## Sorties attendues
- Grille d'évaluation par mécanisme : contenu aléatoire payant, pression temporelle, obscurcissement du prix réel, récompenses de connexion punitives, ciblage de joueurs vulnérables, classement acceptable, à risque ou à retirer.
- Registre des points de vigilance réglementaires (jeux de hasard, protection des mineurs et des consommateurs, transparence des probabilités, données personnelles) avec agent d'orientation et statut de validation.
- Alternatives éthiques proposées (achat direct d'un objet connu, cosmétiques déterministes, plafonds de dépense, information claire sur les prix).
- Brief pour l'agent de coordination, sans présenter d'avis comme validé ni comme juridique.

## Workflow recommandé
1. Cadrer les inputs : mécanismes monétisés, public, marchés, plateformes ; vérifier les préconditions et ce qui est déjà validé.
2. Classer chaque mécanisme selon la grille : le joueur sait-il ce qu'il obtient pour son argent, peut-il plafonner sa dépense, existe-t-il une pression artificielle ou un hasard payant ?
3. Signaler les points de vigilance : par exemple, en Belgique la Commission des jeux de hasard a considéré certaines loot boxes comme des jeux de hasard ; la protection des mineurs impose une prudence particulière. Vérifier la position à jour auprès de la source officielle.
4. Proposer des alternatives éthiques et leur effet sur l'économie interne (impact sur sources et sinks, à simuler avec la skill de modélisation).
5. Vérifier le livrable par ce critère : chaque mécanisme monétisé est classé, chaque point de vigilance a un agent d'orientation et un statut, et aucun mécanisme manipulateur ciblant les mineurs ou l'addiction n'est conservé.
6. Restituer résultat, hypothèses, risques et prochaines actions ; orienter via l'agent de coordination vers l'agent juridique, l'agent de conformité RGPD ou l'agent d'éthique des données, et signaler explicitement les blocages.

## Garde-fous
- Aucun avis juridique : toute conclusion réglementaire est un signalement à faire valider par un agent ou un professionnel qualifié.
- Aucun mécanisme manipulateur ciblant les mineurs ou l'addiction n'est conçu ni recommandé ; les dark patterns relevés sont proposés au retrait.
- Aucune garantie de revenus, de conversion ou de conformité.
- Ne pas inventer de texte de loi, de décision ni de source ; dater et sourcer chaque référence réglementaire, ou la marquer « à vérifier ».
- Aucune donnée personnelle de joueur dans les livrables ; aucun secret en dur.
- Lire la référence dans son contexte : elle éclaire la méthode, elle ne certifie pas ce livrable et n'impose pas de seuil universel.

## Templates copier/coller
### Entrée
```text
Objet : Ethical Monetization & Compliance Watch
Inputs : mécanismes monétisés, prix et taux publiés, public cible, marchés visés, plateformes
Version du design / périmètre autorisé :
Résultat demandé : grille d'évaluation éthique et registre des points de vigilance réglementaires
Contraintes et inconnues :
```

### Sortie
```text
Résultat : grille d'évaluation éthique et registre des points de vigilance
| Mécanisme | Constat (hasard payant, pression, prix opaque, mineurs) | Classement (acceptable / à risque / à retirer) | Orientation (agent) | Statut de validation |
|---|---|---|---|---|
Hypothèses :
Risques :
Prochaines actions :
```

## Checklist QA interne
- [ ] Les inputs, marchés et limites d'autorisation sont identifiés.
- [ ] Les trois analyses sont documentées : classement par mécanisme ; points de vigilance réglementaires avec source datée ; alternatives éthiques et impact économique.
- [ ] Le critère d'acceptation est vérifié ou explicitement marqué non vérifié.
- [ ] Aucun avis juridique ni accord humain n'est inventé ; chaque orientation nomme un agent.

## KPI reliés
- Part des mécanismes monétisés classés : mécanismes classés / mécanismes recensés (dénominateur conservé).
- Part des points de vigilance avec orientation nommée et statut de validation renseigné.
- Nombre de mécanismes « à retirer » ou « à risque » restant ouverts : chaque mécanisme est traité ou transmis pour décision à l'agent de coordination.

## Definition of done
- [ ] Grille d'évaluation et registre de vigilance livrés dans le périmètre convenu, avec alternatives éthiques.
- [ ] Chaque mécanisme est classé, chaque point de vigilance est orienté vers un agent ou un professionnel compétent, aucun avis juridique n'est présenté comme tel.
- [ ] Preuves, inconnues, exceptions et actions restantes sont lisibles ; aucune réussite globale en cas de vérification bloquante manquante.

## Exemples d'usage
**Cas nominal** : à partir d'un jeu mobile proposant des coffres payants à contenu aléatoire et une monnaie premium, classer chaque mécanisme, signaler le point loot boxes pour la Belgique, proposer une boutique à contenu connu, puis vérifier le critère d'acceptation ci-dessus.

**Cas limite** : le public cible ou le marché n'est pas défini ; livrer la grille avec l'hypothèse la plus prudente (présence de mineurs, marché belge inclus), marquer ce choix comme supposé et demander la confirmation via l'agent de coordination.

## Contraintes et références
- Référence officielle : [Commission des jeux de hasard (Belgique)](https://www.gamingcommission.be/). Synthèse originale, sans reproduction du texte source ; page non consultée en détail lors de la création, vérifier les versions et l'applicabilité au contexte.
- Création : DEL-20261026-GAMEDEV-CREA-AGENTS.

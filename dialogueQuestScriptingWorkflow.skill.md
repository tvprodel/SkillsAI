# Dialogue & Quest Scripting Workflow

## Objectif
Produire un livrable maîtrisé : scripts de dialogues, de barks et de quêtes dans un format structuré (Ink, Yarn Spinner, Dialogic ou tableur), avec clés de texte stables, prêts à être intégrés par l'équipe moteur.


## Quand l'utiliser (triggers)
- Demande portant sur « Dialogue & Quest Scripting Workflow » ou sur le livrable : fichiers de dialogues et de quêtes structurés, avec fiche de voix des personnages et index des clés.
- Besoin de vérifier ce résultat : le script se compile ou s'importe sans erreur dans l'outil choisi, chaque ligne a une clé unique et chaque quête a un objectif, un état de départ et d'achèvement testables.

## Hors périmètre
- Ne pas remplacer les domaines des agents complémentaires : présenter les interfaces et transmettre les besoins à l'agent rattaché (voir table de routage).
- L'implémentation du lecteur de dialogues ou du suivi de quêtes en GDScript relève de l'agent de développement Godot ; la microcopie d'interface, de l'agent UX writing ; la correction finale, de l'agent de relecture linguistique.
- Les récompenses chiffrées relèvent de l'agent de conception économique de jeu ; l'enregistrement de voix et la musique, de l'agent de sound design et l'agent de composition musicale.
- L'exécution système, les modifications de fichiers, les tests et les publications relèvent de l'agent rattaché (voir table de routage) ; cette skill n'accorde aucun outil supplémentaire.
- Ne pas confondre relecture statique d'un script et compilation ou lecture réelle dans l'outil.

## Inputs requis
- Graphe ou carte de narration validé, liste des personnages avec fiches de voix, ton et registre visés.
- Format de script retenu et version de l'outil (Ink, Yarn Spinner, Dialogic, tableur) ; convention de nommage des clés de texte.
- Liste des quêtes ou missions : objectif, déclencheur, étapes, récompense narrative, conditions d'échec éventuelles.
- Contraintes de longueur de ligne (boîtes de dialogue), avertissements de contenu et limites d'action ; marquer les éléments inconnus avant de conclure.

## Sorties attendues
- Scripts de dialogues et de barks au format retenu, avec identifiants de ligne stables et notes de contexte pour chaque ligne ambiguë.
- Fiches de quête (objectif, étapes, déclencheur, états, récompense narrative, dialogues liés) et index des clés de texte.
- Preuves ou références par constat ; hypothèses, exceptions et vérifications non réalisées séparées.
- Brief d'intégration pour l'agent de développement Godot et pour l'agent de coordination, sans l'annoncer déjà exécuté.

## Workflow recommandé
1. Cadrer les inputs : graphe validé, personnages et voix, format et version de l'outil, convention de clés ; vérifier les préconditions et autorisations.
2. Rédiger les fiches de voix (vocabulaire, rythme, tics, ce que le personnage ne dit jamais) et la structure de chaque quête (objectif, étapes, états).
3. Écrire les dialogues et les barks dans le format choisi, avec une clé unique par ligne, des conditions explicites et le contexte du locuteur.
4. Relire pour la cohérence de ton et de canon, la longueur des lignes et les avertissements de contenu ; transmettre la correction orthographique finale à l'agent de relecture linguistique si besoin.
5. Vérifier le livrable par ce critère : le script se compile ou s'importe sans erreur dans l'outil choisi, 100 % des lignes ont une clé unique, et chaque quête possède un état de départ et un état d'achèvement atteignables.
6. Restituer résultat, hypothèses, risques et prochaines actions ; transmettre les scripts à l'agent de développement Godot ; signaler explicitement les blocages et ce qui n'a pas pu être compilé.

## Garde-fous
- Le script se compile ou s'importe sans erreur ; chaque ligne a une clé unique et stable, qui ne change pas lors d'une réécriture du texte.
- Contenu original uniquement : ne pas citer ni imiter longuement une œuvre protégée ; ne pas utiliser de personnages ou d'univers sous copyright.
- Signaler les sujets sensibles (violence, discrimination, mineurs) et les avertissements de contenu ; ne pas écrire de contenu haineux ou destiné à nuire.
- Ne pas inventer de syntaxe ni de fonctionnalité d'outil : en cas d'incertitude, indiquer la vérification à faire dans la documentation officielle.
- Ne pas transmettre de script privé ou de donnée personnelle à un service tiers ; aucun secret en dur, aucun nom de personne réelle sans accord.
- Privilégier les outils libres maintenus et vérifier licence et version applicables, sans dépendance EOL.
- Lire la référence dans son contexte : elle éclaire la méthode, elle ne certifie pas ce livrable et n'impose pas de seuil universel.

## Templates copier/coller
### Entrée
```text
Objet : Dialogue & Quest Scripting Workflow
Inputs : graphe de narration validé, personnages et voix, format et version de l'outil, convention de clés, liste de quêtes
Version / périmètre autorisé :
Résultat demandé : scripts de dialogues et barks, fiches de quête, index des clés de texte
Contraintes et inconnues :
```

### Sortie
```text
Résultat : scripts de dialogues, fiches de quête et index des clés
| Clé de texte | Locuteur / quête | Contexte pour traducteur | Statut de vérification | Limite / action |
|---|---|---|---|---|
Hypothèses :
Risques :
Prochaines actions :
```

## Checklist QA interne
- [ ] Les inputs et les limites d'autorisation sont identifiés.
- [ ] Les trois analyses sont documentées : fiches de voix et structure des quêtes ; écriture des dialogues et barks avec clés uniques ; relecture de ton, de canon, de longueur et de contenu sensible.
- [ ] Le critère d'acceptation est vérifié ou explicitement marqué non vérifié.
- [ ] Aucun résultat d'exécution ou accord humain n'est inventé.

## KPI reliés
- Couverture des éléments requis : lignes et quêtes documentées / lignes et quêtes applicables (dénominateur conservé).
- Part des lignes avec clé unique et contexte renseigné ; nombre d'erreurs de compilation ou d'import restant ouvertes.
- Nombre de quêtes dont l'état d'achèvement n'est pas atteignable restant ouvertes ; ne pas compter une hypothèse comme preuve.

## Definition of done
- [ ] Scripts, fiches de quête et index des clés livrés dans le périmètre convenu.
- [ ] Le script se compile ou s'importe sans erreur et toutes les lignes ont une clé unique.
- [ ] Preuves, inconnues, exceptions et actions restantes sont lisibles ; aucune réussite globale en cas de vérification bloquante manquante.

## Exemples d'usage
**Cas nominal** : à partir d'un graphe validé et de trois fiches de voix, écrire en Ink les dialogues d'une quête de livraison avec dix barks de PNJ, un index de clés et des notes de contexte, puis vérifier le critère d'acceptation ci-dessus.

**Cas limite** : l'outil ou sa version n'est pas disponible pour compiler le script ; livrer le script et la relecture statique, et indiquer précisément que la compilation n'a pas été testée, sans la déclarer réussie.

## Contraintes et références
- Référence officielle : [Yarn Spinner - Documentation](https://docs.yarnspinner.dev/). Synthèse originale, sans reproduction du texte source ; page non consultée en détail lors de la création, vérifier les versions, la licence et l'applicabilité au contexte.
- Création : DEL-20261026-GAMEDEV-CREA-AGENTS.

# GDExtension & Native Module Development

## Objectif
Produire un livrable maîtrisé : extension native Godot 4.x (GDExtension C++ ou Rust, ou module moteur) documentée, avec fichier `.gdextension`, binaires par plateforme et exemple d'appel GDScript.


## Quand l'utiliser (triggers)
- Demande portant sur « GDExtension & Native Module Development » ou sur le livrable : extension native Godot 4.x documentée (API exposée, binaires, exemple d'appel GDScript).
- Besoin de vérifier ce résultat : l'extension se charge dans la version Godot cible sur chaque plateforme déclarée et l'exemple GDScript s'exécute sans erreur ni fuite mémoire signalée.

## Hors périmètre
- Ne pas remplacer les domaines des agents complémentaires : présenter les interfaces et transmettre les besoins à l'agent rattaché (voir table de routage).
- L'exécution système, les modifications de fichiers, les compilations, les tests et les publications relèvent de l'agent rattaché (voir table de routage) ; cette skill n'accorde aucun outil supplémentaire.
- Ne pas confondre conception d'une API native, revue statique du code et résultat d'une compilation ou d'un chargement réel dans l'éditeur.
- Ne pas écrire la logique de gameplay GDScript, les scènes ni l'export du projet : ces sujets relèvent de l'agent de développement Godot.

## Inputs requis
- Version cible de Godot 4.x, branche godot-cpp ou crate gdext correspondante, langage (C++ ou Rust), plateformes et architectures visées.
- Besoin fonctionnel natif (performance, accès bas niveau, bibliothèque tierce) et classes ou méthodes à exposer.
- Chaîne d'outils disponible (compilateur, SCons/CMake/Cargo), licences des dépendances et contraintes de sécurité.
- Critères d'acceptation et limites d'action ; marquer les éléments inconnus avant de conclure.

## Sorties attendues
- Extension native : sources, fichier `.gdextension`, matrice de compatibilité version godot-cpp/gdext ↔ Godot, binaires ou instructions de build par plateforme.
- Documentation de l'API exposée (classes, méthodes, propriétés, signaux) et exemple d'appel GDScript.
- Preuves ou références par constat ; hypothèses, exceptions et vérifications non réalisées séparées.
- Brief des décisions ou actions nécessaires pour l'agent rattaché, sans les annoncer déjà exécutées.

## Workflow recommandé
1. Cadrer les inputs : version Godot, langage, plateformes, besoin natif et dépendances ; vérifier que le besoin justifie du code natif plutôt que du GDScript.
2. Fixer la compatibilité : choisir la branche godot-cpp ou la version gdext alignée sur la version Godot cible et consigner la décision.
3. Concevoir l'API exposée (classes enregistrées, propriétés, signaux, gestion des types Variant) et la stratégie de propriété mémoire.
4. Implémenter l'extension et son fichier `.gdextension`, puis préparer la compilation par plateforme avec une cible debug et une cible release.
5. Vérifier le livrable par ce critère : l'extension se charge dans la version Godot cible sur chaque plateforme déclarée et l'exemple GDScript s'exécute sans erreur ni fuite mémoire signalée.
6. Restituer API documentée, binaires, exemple d'appel, hypothèses, risques et prochaines actions ; faire passer le code natif sensible par l'agent de sécurité et signaler explicitement les blocages.

## Garde-fous
- L'extension se charge dans la version Godot cible sur chaque plateforme déclarée et l'exemple GDScript s'exécute sans erreur ni fuite mémoire signalée.
- Ne pas inventer d'API godot-cpp, gdext ou Godot : en cas d'incertitude, vérifier la documentation de la version ciblée.
- Ne pas mélanger des versions incompatibles de godot-cpp et de Godot ; expliciter la compatibilité.
- Code natif manipulant des pointeurs, des tampons ou des entrées externes : passage obligatoire par l'agent de sécurité.
- Ne pas inventer de mesure, d'accord, de preuve ou de source ; distinguer observé, inféré et non testé.
- Privilégier les outils libres maintenus, vérifier la licence de chaque dépendance (MIT, Apache, GPL) et ne pas introduire de composant EOL.
- Aucun secret en dur ; ne pas transmettre de code ou d'artefact privé à un service tiers.
- Lire la référence dans son contexte : elle éclaire la méthode, elle ne certifie pas ce livrable et n'impose pas de seuil universel.

## Templates copier/coller
### Entrée
```text
Objet : GDExtension & Native Module Development
Inputs : version Godot 4.x, langage (C++/Rust), plateformes, besoin natif, dépendances et licences
Version / périmètre autorisé :
Résultat demandé : extension native documentée (API exposée, .gdextension, binaires, exemple d'appel GDScript)
Contraintes et inconnues :
```

### Sortie
```text
Résultat : extension native documentée (API exposée, .gdextension, binaires, exemple d'appel GDScript)
| Élément examiné | Preuve / source / version | Conclusion | Limite / action |
|---|---|---|---|
Compatibilité (godot-cpp/gdext ↔ Godot) :
API exposée :
Exemple d'appel GDScript :
Hypothèses :
Risques :
Prochaines actions :
```

## Checklist QA interne
- [ ] Les inputs et les limites d'autorisation sont identifiés.
- [ ] Les trois analyses sont documentées : compatibilité de version godot-cpp/gdext ↔ Godot ; API exposée et propriété mémoire ; build et chargement par plateforme.
- [ ] Licences des dépendances vérifiées et versions des compilateurs non EOL.
- [ ] Le critère d'acceptation est vérifié ou explicitement marqué non vérifié.
- [ ] Aucun résultat de compilation ou d'exécution n'est inventé.

## KPI reliés
- Plateformes déclarées sur lesquelles l'extension se charge / plateformes déclarées (dénominateur conservé).
- Part des méthodes exposées documentées avec exemple d'appel GDScript / méthodes exposées.
- Nombre de fuites ou d'erreurs de chargement restant ouvertes au critère : l'extension se charge dans la version Godot cible sur chaque plateforme déclarée sans erreur ni fuite signalée.

## Definition of done
- [ ] Extension native documentée (API exposée, `.gdextension`, binaires ou procédure de build, exemple d'appel GDScript) livrée dans le périmètre convenu.
- [ ] L'extension se charge dans la version Godot cible sur chaque plateforme déclarée et l'exemple GDScript s'exécute sans erreur ni fuite mémoire signalée.
- [ ] Preuves, inconnues, exceptions et actions restantes sont lisibles ; aucune réussite globale en cas de vérification bloquante manquante.

## Exemples d'usage
**Cas nominal** : à partir de Godot 4.x cible, d'un besoin de calcul intensif en C++ et de deux plateformes visées, produire une extension exposant une classe native avec exemple GDScript, puis vérifier le critère d'acceptation ci-dessus.

**Cas limite** : une plateforme ne peut pas être compilée ou testée faute de chaîne d'outils ; livrer les éléments établis et indiquer précisément ce qui empêche la validation, sans déclarer cette plateforme prise en charge.

## Contraintes et références
- Référence officielle : [Godot - GDExtension](https://docs.godotengine.org/en/stable/tutorials/scripting/gdextension/index.html). Synthèse originale, sans reproduction du texte source ; page non consultée en détail lors de la création, vérifier les versions et l'applicabilité au contexte.
- Création : DEL-20261026-GAMEDEV-CREA-AGENTS.

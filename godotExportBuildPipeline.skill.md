# Godot Export & Build Pipeline

## Objectif
Configurer et fiabiliser les pipelines d'export/build Godot 4.x multi-plateformes (Windows, Linux, Web/HTML5, mobile Android/iOS), gérer les templates d'export, la signature des builds, l'optimisation de la taille et les automatisations CI de build.

## Quand l'utiliser (triggers)
- « export Godot », « build pipeline Godot », « export_presets.cfg ».
- « déploiement itch.io », « build Steam », « export Android/iOS Godot », « CI Godot ».
- Préparation d'une release multi-plateformes ou d'une démo publique.
- Échec récurrent d'export ou de signature de build.

## Hors périmètre
- Gameplay/scripting GDScript pur → compétence de base de l'agent l'agent de développement Godot.
- Performance runtime CPU/GPU (profiling, optimisation frame time) → compétence de base de l'agent pour le profiling runtime.
- Conception de l'architecture du jeu (scènes, patterns, structure de projet) → compétence de base de l'agent.

## Inputs requis
- Projet Godot 4.x fonctionnel (project.godot, scènes, scripts).
- Plateformes cibles à exporter (Windows, Linux, Web, Android, iOS).
- Certificats/clés de signature disponibles (keystore Android, certificats Apple Developer, certificat de signature de code Windows le cas échéant).
- Contraintes de taille/quota des plateformes de distribution cibles (itch.io, Steam, Google Play, App Store).
- Version de Godot utilisée et disponibilité des templates d'export correspondants.

## Sorties attendues
- Fichier `export_presets.cfg` configuré et versionné par plateforme.
- Builds signés et fonctionnels pour chaque plateforme cible.
- Pipeline CI automatisé (GitHub Actions/GitLab CI) déclenchant les exports.
- Artefacts publiés sur les plateformes de distribution (itch.io, Steam, stores mobiles).
- Rapport de build (taille finale, temps de build, anomalies rencontrées).

## Workflow recommandé
1. Configuration des export presets par plateforme dans `export_presets.cfg` (résolution, architecture, options de compression, permissions).
2. Gestion et installation des templates d'export Godot correspondant à la version du moteur utilisée (variantes stable/mono selon usage de C#).
3. Signature et certificats : génération/configuration du keystore Android, notarization macOS/iOS via Apple Developer, code signing Windows si distribution hors store.
4. Optimisation de la taille du build (compression des assets, exclusion des ressources inutiles via `.gdignore`/filtres d'export, compression des textures en formats adaptés par plateforme).
5. Intégration dans une CI (GitHub Actions/GitLab CI) avec mise en cache des templates Godot et du moteur pour accélérer les builds successifs.
6. Publication automatisée ou semi-automatisée : itch.io via `butler`, Steam via SteamPipe (`steamcmd`), stores mobiles via Google Play Console/App Store Connect.

## Garde-fous
- Toujours valider un export en local avant intégration en CI (éviter de découvrir une erreur de signature en pipeline).
- Ne jamais committer les clés privées/certificats/keystores dans le dépôt Git ; utiliser des secrets CI chiffrés.
- Vérifier la cohérence de version entre le moteur Godot du projet et les templates d'export installés (source fréquente d'échec silencieux).
- Tester le build exporté sur un environnement représentatif de la cible réelle (pas uniquement l'éditeur Godot).
- Documenter toute exception (plateforme non supportée, feature désactivée à l'export) dans le rapport de build.

## Template d'entrée (copier/coller)
```text
[Projet Godot]
- Version Godot : ...
- Plateformes cibles : ...
- Utilisation C#/Mono : oui/non

[Distribution]
- Plateformes de publication : ...
- Certificats/clés disponibles : ...

[Contraintes]
- Taille max autorisée : ...
- Fréquence de build souhaitée : ...
```

## Template de sortie (copier/coller)
```text
[Configuration export]
- export_presets.cfg : ...
- Templates installés : ...

[Builds produits]
- Windows : chemin/taille/statut
- Web : chemin/taille/statut
- Android/iOS : chemin/taille/statut

[Pipeline CI]
- Fichier workflow : ...
- Déclencheur : ...
- Temps de build moyen : ...

[Anomalies]
- Liste des anomalies rencontrées : ...
```

## Checklist QA interne
- `export_presets.cfg` versionné et cohérent avec les plateformes cibles déclarées.
- Templates d'export installés correspondent à la version Godot du projet.
- Builds signés testés sur un device/environnement réel par plateforme.
- Aucune clé/certificat en clair dans le dépôt.
- Pipeline CI exécuté avec succès sur au moins un run complet avant mise en production.

## KPI reliés
- Taux de succès des builds CI (builds réussis / builds lancés).
- Temps moyen de build par plateforme.
- Taille finale du build par plateforme (évolution dans le temps).
- Nombre d'incidents de signature/certificat par cycle de release.

## Definition of done
- Export presets configurés et validés pour toutes les plateformes cibles.
- Pipeline CI opérationnel et déclenché automatiquement (tag/branche release).
- Builds signés et publiés sur les plateformes de distribution ciblées.
- Rapport de build documenté et partagé.

## Exemples d'usage

### Exemple 1 : Pipeline CI de release Windows + Web sur tag Git
**Contexte** : Une petite équipe indépendante développe un jeu de puzzle en Godot 4.2 et souhaite automatiser la publication d'une build Windows et d'une build Web (HTML5) sur itch.io à chaque tag de version (ex. `v1.2.0`).
**Action** : L'agent l'agent de développement Godot configure `export_presets.cfg` pour les presets Windows Desktop et Web, installe les templates d'export 4.2 correspondants, met en place un workflow GitHub Actions déclenché sur push de tag qui exécute `godot --headless --export-release` pour chaque plateforme, puis publie automatiquement les artefacts via `butler push` vers itch.io avec les channels `windows` et `html5`.
**Résultat** : Chaque tag `vX.Y.Z` déclenche un build complet en moins de 6 minutes, les deux builds sont publiées automatiquement sur itch.io sans intervention manuelle, et le nombre d'erreurs de publication manuelle est ramené à zéro sur les 5 releases suivantes.

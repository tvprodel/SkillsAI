# Debian & Arch System Administration

## Objectif
Administrer et maintenir des systèmes Debian/Ubuntu (apt/dpkg) et Arch Linux (pacman/AUR) : installation, mise à jour, gestion rolling-release, hardening AppArmor, troubleshooting — en complément de la spécialisation RHEL/Red Hat Enterprise portée par l'agent d'administration Linux.

## Quand l'utiliser (triggers)
- « Debian », « Ubuntu », « apt », « dpkg », « Arch Linux », « pacman », « AUR », « yay », « paru », « rolling release », « AppArmor », « systemd-boot », « btrfs snapshot Arch ».
- Installation/mise à jour/dépannage d'un serveur ou poste Debian/Ubuntu/Arch.
- Question sur la gestion du rolling-release Arch ou la vérification d'un paquet AUR.

## Hors périmètre
- RHEL/CentOS/Fedora/Red Hat Enterprise Linux, SELinux → l'agent d'administration Linux.
- Scripts Bash/Perl robustes production (retries, logging avancé, Podman/Quadlet) → l'agent de scripting système.
- Conteneurs Docker/Podman/Kubernetes → l'agent conteneurs.
- Choix de licence libre/alternatives à un outil propriétaire → skill « Libre Software Advocacy & Licensing » (même agent).

## Inputs requis
- Distribution exacte et branche (Debian stable/testing/unstable, Ubuntu LTS, Arch rolling).
- Objectif : installation, mise à jour, dépannage, durcissement.
- Contraintes production vs environnement de test.
- Pour AUR : nom du paquet et disponibilité d'un mainteneur actif.

## Sorties attendues
- Commandes apt/dpkg ou pacman/AUR documentées.
- Unit(s) systemd si pertinent.
- Procédure de rollback (snapshot btrfs, `apt-mark hold`, cache pacman).
- Rapport de vérification AUR (relecture PKGBUILD) avant toute installation recommandée.

## Workflow recommandé
1. Identifier la distribution et la branche (stable vs rolling) ainsi que l'objectif exact.
2. Vérifier les dépôts activés/miroirs (`/etc/apt/sources.list*`, `mirrorlist` pacman) et la validité des clés GPG.
3. Exécuter les opérations (install/update/purge) avec vérification explicite des dépendances proposées.
4. Pour un paquet AUR : lire le `PKGBUILD` avant `makepkg`/helper AUR ; ne jamais installer aveuglément.
5. Documenter la procédure de rollback avant toute mise à jour rolling-release significative.

## Garde-fous
- Jamais d'installation AUR sans relecture explicite du PKGBUILD (risque supply-chain).
- Toujours vérifier les signatures GPG des dépôts avant ajout d'un dépôt tiers.
- Éviter `pacman -Rdd` / `apt --force-*` sauf dernier recours documenté et justifié.
- Rolling-release : tester en environnement non critique avant toute mise à jour en production.
- AppArmor en mode enforce par défaut sur les profils sensibles, jamais désactivé sans justification tracée.

## Template d'entrée (copier/coller)
```text
[Système]
- Distribution / branche : ...
- Objectif (install/update/dépannage/durcissement) : ...
- Contexte (production/test) : ...

[Paquet AUR si applicable]
- Nom : ...
- Mainteneur actif : oui/non
```

## Template de sortie (copier/coller)
```text
[Commandes exécutées]
- ...

[Vérifications]
- Paquets installés : ...
- Services actifs : ...
- AppArmor : ...

[Rollback documenté]
- Procédure : ...
```

## Checklist QA interne
- Dépendances vérifiées avant installation.
- PKGBUILD relu si paquet AUR.
- Procédure de rollback documentée pour toute mise à jour rolling-release.
- AppArmor vérifié en mode enforce sur profils sensibles.

## KPI reliés
- Taux de paquets AUR vérifiés avant installation (%).
- Nombre de rollbacks nécessaires après mise à jour rolling-release.
- Temps moyen de résolution d'un incident de dépendance.

## Definition of done
- Configuration appliquée et vérifiée (paquets, services, sécurité).
- Procédure de rollback documentée si mise à jour à risque.
- Runbook publié si procédure récurrente.

## Exemples d'usage

### Exemple 1 : Mise à jour rolling-release Arch en production
**Contexte** : Serveur Arch Linux nécessitant une mise à jour `pacman -Syu` après plusieurs semaines sans mise à jour.
**Action** : Snapshot btrfs préalable, vérification des news Arch (archlinux.org) pour interventions manuelles requises, mise à jour puis vérification des services critiques.
**Résultat** : Mise à jour appliquée sans casse, snapshot conservé 7 jours en cas de rollback.

### Exemple 2 : Installation d'un paquet AUR
**Contexte** : Besoin d'un outil disponible uniquement via AUR.
**Action** : Relecture du PKGBUILD, vérification du mainteneur et de l'activité du dépôt, build via `makepkg -si`.
**Résultat** : Paquet installé après validation ; alternative dans les dépôts officiels signalée si trouvée entre-temps.

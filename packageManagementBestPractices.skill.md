# Package Management Best Practices

## Objectif
Gérer packages Linux (yum/dnf, apt, pacman) de manière sécurisée, reproductible et automatisée.

## Quand l'utiliser (triggers)
- « installe packages », « gère dépendances », « met à jour système », « verrouille versions ».
- Standardisation environnements (prod = versions lockées).
- Automatisation installation packages (Ansible, scripts).

## Hors périmètre
- Compilation sources custom → sysadminLinux (cas spécifiques).
- Gestion dépendances langages (npm, pip, composer) → agents dev concernés.
- Orchestration configuration (Ansible playbooks complets) → sysadminLinux ou l'agent de scripting système.

## Inputs requis
- Distribution (RHEL/CentOS, Debian/Ubuntu, Arch).
- Packages à installer (noms, versions si lockées).
- Stratégie updates (automatic security updates, manual full updates).

## Sorties attendues
- Liste packages installés (manifest reproductible).
- Commandes installation (yum install, apt install).
- Stratégie updates documentée (cron yum-cron, unattended-upgrades).

## Workflow recommandé
1. Identifier packages requis (runtime, libs, outils).
2. Installer via package manager :
   - RHEL/CentOS : yum install -y package ou dnf install -y package.
   - Debian/Ubuntu : apt update && apt install -y package.
   - Arch : pacman -S package.
3. Verrouiller versions si prod (yum versionlock, apt-mark hold).
4. Automatiser security updates (yum-cron RHEL, unattended-upgrades Ubuntu).
5. Documenter manifest (yum list installed > manifest.txt, dpkg -l > manifest.txt).

## Garde-fous
- Security updates automatiques (yum-cron minimal, unattended-upgrades security only).
- Versions lockées en prod (éviter breaking changes non testés).
- Repos officiels uniquement (éviter PPA/COPR non maintenus, sauf justification).
- Cleanup régulier (yum clean all, apt autoremove).

## Template d'entrée (copier/coller)
```text
[Environnement]
- Distribution : ...
- Packages : ...

[Stratégie]
- Updates : ...
- Versions lockées : ...
```

## Template de sortie (copier/coller)
```text
[Installation]
- Commandes : ...
- Manifest : ...

[Updates]
- Stratégie : ...
- Configuration yum-cron/unattended-upgrades : ...
```

## Checklist QA interne
- Packages installés (vérifier rpm -q ou dpkg -l).
- Repos officiels utilisés (pas PPA/COPR douteux).
- Security updates automatiques configurés.
- Versions lockées si prod.

## KPI reliés
- Nb packages obsolètes (yum list updates, apt list --upgradable).
- Taux conformité versions lockées prod (%).
- Temps moyen installation packages (minutes).

## Definition of done
- Packages installés et vérifiés.
- Stratégie updates configurée.
- Manifest publié.

## Exemples d'usage

### Exemple 1 : [Titre du cas d'usage]
**Contexte** : [Description de la situation]
**Action** : [Ce qui a été fait]
**Résultat** : [Résultat obtenu]
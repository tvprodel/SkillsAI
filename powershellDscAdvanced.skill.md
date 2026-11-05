# PowerShell DSC Advanced

## Objectif
Maîtriser PowerShell Desired State Configuration (DSC) pour configurations Windows Server idempotentes, reproductibles et versionées.

## Quand l'utiliser (triggers)
- « configure Windows Server de manière déclarative », « DSC », « Configuration as Code Windows ».
- Besoin d'automatisation configuration serveurs Windows à grande échelle.
- Standardisation configuration serveurs (compliance, drift detection).

## Hors périmètre
- Scripts PowerShell impératifs simples (scripts .ps1 basiques suffisent).
- Configuration Linux → sysadminLinux (Ansible preferred).
- Infrastructure as Code cloud → l'agent d'architecture cloud (Terraform/ARM).

## Inputs requis
- Configuration cible (rôles Windows, features, services, registry keys, fichiers).
- Environnement (nb serveurs, domaine AD, credentials).
- Stratégie déploiement (push mode LCM vs pull server).

## Sorties attendues
- Configuration DSC (.ps1 DSC syntax) avec ressources natives ou modules communautaires.
- MOF compilés prêts à appliquer (Start-DscConfiguration).
- Runbook application DSC avec tests idempotence.

## Workflow recommandé
1. Définir configuration cible (rôles, features, services, registry).
2. Coder Configuration DSC avec ressources (WindowsFeature, Service, Registry, File, etc.).
3. Compiler MOF (. .\Config.ps1; ConfigName).
4. Tester en environnement dev (Start-DscConfiguration -Path).
5. Valider idempotence (réexécuter, vérifier no changes).

## Garde-fous
- Idempotence obligatoire : DSC doit être réentrant sans effet de bord.
- Pas de secrets hardcodés : credentials via PSDscAllowPlainTextPassword=$false + certificates.
- Modules DSC à jour : utiliser modules communautaires maintenus (xWebAdministration, xNetworking).

## Template d'entrée (copier/coller)
```text
[Configuration cible]
- Rôles/features : ...
- Services : ...
- Registry keys : ...

[Environnement]
- Nb serveurs : ...
- Domaine AD : ...
```

## Template de sortie (copier/coller)
```text
[Configuration DSC]
- Code DSC : ...
- Ressources utilisées : ...

[MOF compilés]
- Chemin MOFs : ...

[Tests idempotence]
- Résultat réexécution : ...
```

## Checklist QA interne
- Configuration DSC compile sans erreurs.
- Ressources utilisées sont natives ou modules validés.
- Idempotence testée (2 runs successifs, 2ème = no changes).
- Pas de secrets hardcodés.

## KPI reliés
- Taux succès application DSC première tentative.
- Temps moyen application configuration (minutes).
- Taux drift détecté (Test-DscConfiguration).

## Definition of done
- Configuration DSC codée et compilée.
- Tests idempotence passés.
- Runbook application publié.

## Exemples d'usage

### Exemple 1 : [Titre du cas d'usage]
**Contexte** : [Description de la situation]
**Action** : [Ce qui a été fait]
**Résultat** : [Résultat obtenu]
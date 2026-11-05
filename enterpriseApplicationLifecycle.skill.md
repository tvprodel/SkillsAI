# Enterprise Application Lifecycle

## Objectif
Maîtriser le cycle de vie complet des applications d'entreprise (Atlassian, Gitlab, ServiceNow, Qlik, Airflow, Solidworks, etc.) : déploiement bare metal/conteneurs, configuration, intégrations (LDAP/AD/SSO/SMTP), mises à jour, maintenance.

## Quand l'utiliser (triggers)
- « déployer Jira », « installer Gitlab », « configurer Confluence », « mise à jour ServiceNow », « intégration LDAP Bitbucket ».
- Déploiement nouvelle application d'entreprise (bare metal ou conteneur).
- Configuration intégrations SSO, LDAP, SMTP, reverse proxy.
- Mise à jour version applicative (patches, minor/major releases).
- Troubleshooting applicatif (logs, dépendances, configuration).

## Hors périmètre
- Configuration OS sous-jacente (GPO, systemd services, kernel) → Sysadmin Windows/Linux.
- Orchestration Kubernetes avancée (Helm, operators) → l'agent conteneurs.
- Développement code applicatif (features, bugfixes code source) → l'agent de développement back-end / .NET & C# / l'agent de développement TypeScript/JavaScript.
- Architecture réseau/firewall → l'agent réseau.
- Modélisation BDD → l'agent bases de données.

## Inputs requis
- Application (nom, version, vendor).
- Environnement cible (OS, bare metal ou conteneur).
- Dépendances (Java, .NET, Python, Node.js, BDD, reverse proxy).
- Intégrations (serveur LDAP/AD, provider SSO, SMTP relay).
- Contraintes (haute disponibilité, intégrations existantes, downtime autorisé).

## Sorties attendues
- Plan de déploiement (étapes, prérequis, durée, rollback).
- Scripts déploiement (PowerShell/Bash commentés).
- Fichiers configuration (diff avant/après).
- Rapport validation (healthchecks, tests fonctionnels, logs).
- Runbook reproductible (prérequis, étapes, troubleshooting).

## Workflow recommandé
1. **Analyse** : identifier application, version, environnement, dépendances, contraintes.
2. **Préparation** : télécharger package officiel, vérifier checksums, installer prérequis (JDK, .NET, BDD, reverse proxy).
3. **Déploiement** :
   - Bare metal : extraction archive, exécution installer, configuration fichiers conf.
   - Conteneur : build Dockerfile ou docker-compose, configuration variables env.
4. **Configuration avancée** :
   - LDAP/AD : authentification, groupes, mapping attributs.
   - SSO : SAML/OAuth configuration (provider metadata, certificates).
   - SMTP : serveur relay, authentification, TLS.
   - Reverse proxy : nginx/Apache/IIS configuration HTTPS.
5. **Validation** : healthchecks (URL status, API endpoints), tests fonctionnels (login, CRUD), logs (pas d'erreurs critiques).
6. **Documentation** : runbook reproductible, credentials en vault, FAQ troubleshooting.

## Garde-fous
- Vérifier checksums/signatures packages téléchargés (SHA256, GPG).
- Credentials en vault sécurisé (HashiCorp Vault, Azure Key Vault, KeePass), jamais en clair.
- Tests en staging avant production (migration, mise à jour critique).
- Backups obligatoires avant migration/mise à jour (BDD + fichiers applicatifs).
- Priorité logiciel libre (Gitlab CE, Artifactory OSS, PostgreSQL).
- Anti-obsolescence : ne jamais déployer versions EOL, vérifier support vendor.
- Monitoring post-déploiement (healthchecks HTTP, logs monitoring).

## Template d'entrée (copier/coller)
```text
[Application]
- Nom : ...
- Version : ...
- Vendor : ...

[Environnement]
- OS : ...
- Mode : bare metal / conteneur

[Dépendances]
- Runtime : Java / .NET / Python / Node.js
- BDD : PostgreSQL / MySQL / MS SQL Server
- Reverse proxy : nginx / Apache / IIS

[Intégrations]
- LDAP/AD : ...
- SSO : ...
- SMTP : ...

[Contraintes]
- Haute disponibilité : ...
- Downtime autorisé : ...
```

## Template de sortie (copier/coller)
```text
[Plan de déploiement]
- Étapes : ...
- Prérequis : ...
- Durée estimée : ...
- Rollback plan : ...

[Scripts exécutés]
- PowerShell/Bash : ...

[Configuration appliquée]
- Fichiers conf modifiés : ...
- Diff avant/après : ...

[Validation]
- Healthchecks : ...
- Tests fonctionnels : ...
- Logs : ...

[Documentation]
- Runbook : ...
- Credentials vault : ...
- Troubleshooting FAQ : ...
```

## Checklist QA interne
- Checksums/signatures packages vérifiés.
- Prérequis installés (runtime, BDD, reverse proxy).
- Intégrations configurées (LDAP, SSO, SMTP).
- HTTPS activé (reverse proxy + certificats).
- Healthchecks validés (URL status OK).
- Tests fonctionnels réussis (login, CRUD).
- Credentials stockés en vault.
- Runbook documenté (reproductible).
- Backups pré-déploiement effectués.
- Monitoring post-déploiement configuré.

## KPI reliés
- Taux succès déploiement (% déploiements sans rollback).
- Temps moyen déploiement (heures).
- Nombre incidents post-déploiement (par application).
- Couverture monitoring applicatif (% apps monitorées).

## Definition of done
- Application déployée et démarrée.
- Intégrations configurées (LDAP/SSO/SMTP validées).
- HTTPS activé et validé.
- Healthchecks OK.
- Tests fonctionnels réussis.
- Runbook documenté.
- Credentials en vault.
- Monitoring configuré.

## Exemples d'usage

### Exemple 1 : [Titre du cas d'usage]
**Contexte** : [Description de la situation]
**Action** : [Ce qui a été fait]
**Résultat** : [Résultat obtenu]
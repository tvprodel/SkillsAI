# Application Migration Data Transfer

## Objectif
Maîtriser la migration complète d'applications d'entreprise serveur-à-serveur avec transfert de données : planification migration, backup source, transfert BDD + fichiers + configurations, reconfiguration application cible, validation fonctionnelle, rollback plan.

## Quand l'utiliser (triggers)
- « migrer Jira vers nouveau serveur », « migration Confluence avec données », « déplacer Gitlab serveur A vers B », « upgrade hardware ServiceNow avec migration ».
- Migration hardware (serveur physique vieillissant, upgrade RAM/CPU).
- Migration OS (Windows Server 2012 → 2022, RHEL 7 → 9).
- Migration cloud (on-prem → cloud, cloud → cloud).
- Consolidation serveurs (fusion plusieurs instances applicatives).

## Hors périmètre
- Migration cloud stratégique (6R, architecture cloud, IaC) → l'agent d'architecture cloud.
- Développement code migration (ETL custom, transformations données complexes) → l'agent de développement back-end / .NET & C#.
- Modélisation BDD post-migration (refonte schéma, optimisation) → l'agent bases de données.
- Configuration réseau migration (VPN site-to-site, routing) → l'agent réseau.

## Inputs requis
- Application (nom, version, stack technique).
- Serveur source (OS, hostname, IP, chemins installation).
- Serveur cible (OS, hostname, IP, prérequis installés).
- Données à migrer (BDD, fichiers uploads/attachments, configurations, logs si nécessaire).
- Contraintes (downtime autorisé, fenêtre maintenance, rollback plan).
- Intégrations à reconfigurer (LDAP, SSO, SMTP, API externes).

## Sorties attendues
- Plan migration (étapes, durée, downtime, rollback).
- Scripts migration (backup, export BDD, rsync/robocopy fichiers, import BDD cible).
- Rapport validation (tests fonctionnels, vérification données, performances).
- Runbook rollback (procédure retour arrière si échec).
- Documentation post-migration (nouvelles URL, configurations modifiées).

## Workflow recommandé
1. **Analyse et planification** :
   - Inventaire source : application version, BDD (type, taille, schéma), fichiers (chemins, taille totale), configurations (fichiers conf, variables env, intégrations).
   - Inventaire cible : OS, prérequis (runtime, BDD, reverse proxy), capacité disque/RAM.
   - Estimation durée : backup (selon taille BDD), transfert (selon bande passante), import, reconfiguration, tests.
   - Définir fenêtre maintenance (downtime autorisé, communication utilisateurs).
2. **Backup source** :
   - BDD : dump complet (pg_dump PostgreSQL, mysqldump MySQL, backup SQL Server).
   - Fichiers : rsync/robocopy répertoires uploads/attachments/logs.
   - Configurations : copie fichiers conf, export variables env, capture intégrations (LDAP, SSO, SMTP).
   - Vérifier intégrité backups (checksums, test restore partiel si critique).
3. **Préparation cible** :
   - Installer prérequis (runtime Java/.NET/Python, BDD version compatible, reverse proxy).
   - Créer utilisateur/BDD applicatif (permissions).
   - Configurer reverse proxy (nginx/Apache/IIS avec certificats SSL si HTTPS).
4. **Transfert données** :
   - BDD : copier dump vers cible (scp/rsync), importer (psql, mysql, sqlcmd).
   - Fichiers : rsync (Linux) ou robocopy (Windows) répertoires uploads/attachments.
   - Configurations : copier fichiers conf, adapter chemins/hostnames si nécessaires.
5. **Reconfiguration application cible** :
   - Mettre à jour fichiers conf (database connection string, chemins fichiers, URL base).
   - Reconfigurer intégrations (LDAP/AD hostnames, SSO URLs, SMTP relay).
   - Ajuster reverse proxy (URL publique, redirections).
   - Démarrer application cible, vérifier logs (pas d'erreurs critiques).
6. **Validation fonctionnelle** :
   - Tests de base : login (LDAP/SSO), navigation, opérations CRUD (création/lecture/modification/suppression).
   - Vérification données : spot check données migrées (échantillon utilisateurs, projets, tickets selon application).
   - Tests intégrations : SMTP (envoi email), LDAP (sync groupes), SSO (login externe).
   - Tests performance : temps réponse API, requêtes BDD lentes si benchmark dispo.
7. **Bascule production** :
   - Arrêt serveur source (mode maintenance ou shutdown).
   - Mise à jour DNS/load balancer vers serveur cible.
   - Communication utilisateurs (nouvelle URL si changement, fin maintenance).
   - Monitoring post-migration (logs, healthchecks, métriques performances).
8. **Rollback plan** :
   - Si échec critique : restaurer backup BDD source, redémarrer serveur source, rebasculer DNS.
   - Documenter procédure rollback (étapes, durée, critères déclenchement).

## Garde-fous
- Backups complets validés avant migration (BDD + fichiers + configurations).
- Test restore partiel backup avant migration (vérifier intégrité).
- Downtime communiqué utilisateurs (email, bannière application, Slack/Teams).
- Migration en fenêtre maintenance (hors heures ouvrées si possible).
- Rollback plan documenté et testé (dry-run si critique).
- Vérification checksums transfert fichiers (rsync -c, robocopy /L).
- Tests fonctionnels complets avant bascule production.
- Monitoring post-migration (logs, healthchecks, alertes).

## Template d'entrée (copier/coller)
```text
[Application]
- Nom : ...
- Version : ...
- Stack : ... (Java/Tomcat, .NET/IIS, Python/Django, etc.)

[Serveur source]
- OS : ...
- Hostname/IP : ...
- Chemins installation : ...
- BDD : type / taille / schéma
- Fichiers : chemins / taille totale

[Serveur cible]
- OS : ...
- Hostname/IP : ...
- Prérequis : ... (installés ou à installer)

[Contraintes]
- Downtime autorisé : ...
- Fenêtre maintenance : ...
- Rollback plan : ... (critères déclenchement)

[Intégrations]
- LDAP/AD : ...
- SSO : ...
- SMTP : ...
- API externes : ...
```

## Template de sortie (copier/coller)
```text
[Plan migration]
- Étapes : ...
- Durée estimée : ...
- Downtime : ...
- Rollback plan : ...

[Backup source]
- BDD dump : ... (fichier, taille, checksum)
- Fichiers : ... (chemins, taille, checksum)
- Configurations : ...

[Transfert données]
- BDD import cible : ... (commande, durée)
- Fichiers rsync/robocopy : ... (commande, durée)
- Configurations : ... (fichiers modifiés)

[Reconfiguration cible]
- Fichiers conf : ... (diff avant/après)
- Intégrations : ... (LDAP, SSO, SMTP reconfigurés)
- Reverse proxy : ... (URL, redirections)

[Validation]
- Tests fonctionnels : ... (résultats)
- Vérification données : ... (échantillon validé)
- Tests intégrations : ... (SMTP, LDAP, SSO OK)
- Tests performance : ... (temps réponse)

[Bascule production]
- DNS/load balancer : ... (nouvelle IP/hostname)
- Communication utilisateurs : ...
- Monitoring post-migration : ...

[Rollback]
- Procédure : ...
- Critères déclenchement : ...
```

## Checklist QA interne
- Backup source complet (BDD + fichiers + configurations).
- Test restore partiel backup (intégrité validée).
- Checksums transfert fichiers vérifiés.
- BDD import cible réussi (pas d'erreurs).
- Application cible démarrée (logs OK).
- Tests fonctionnels réussis (login, CRUD, intégrations).
- Vérification données (échantillon validé).
- DNS/load balancer basculé.
- Rollback plan documenté et testé.
- Monitoring post-migration configuré.

## KPI reliés
- Taux succès migration (% migrations sans rollback).
- Temps moyen migration (heures).
- Downtime réel vs downtime prévu (écart %).
- Nombre incidents post-migration (par application).

## Definition of done
- Application migrée et démarrée sur serveur cible.
- Tests fonctionnels réussis (login, CRUD, intégrations).
- Vérification données validée (échantillon).
- DNS/load balancer basculé.
- Monitoring post-migration configuré.
- Rollback plan documenté.
- Communication utilisateurs effectuée.

## Exemples d'usage

### Exemple 1 : [Titre du cas d'usage]
**Contexte** : [Description de la situation]
**Action** : [Ce qui a été fait]
**Résultat** : [Résultat obtenu]
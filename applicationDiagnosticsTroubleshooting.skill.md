# Application Diagnostics & Troubleshooting

## Objectif
Maîtriser le diagnostic méthodique et le troubleshooting d'applications d'entreprise (Atlassian, Gitlab, ServiceNow, Qlik, Solidworks, etc.) : analyse root cause, lecture logs/stacktraces, corrélation d'incidents, diagnostic dépendances/intégrations, diagnostic performance applicative, résolution incidents N2/N3.

## Quand l'utiliser (triggers)
- « Jira ne démarre pas », « erreur 500 Gitlab », « ServiceNow lent », « problème connexion LDAP », « certificat SSL expiré », « migration échouée ».
- Application d'entreprise inaccessible ou en erreur.
- Performance applicative dégradée (lenteur, timeouts).
- Incidents intégrations (SSO/LDAP/SMTP/API).
- Support N2/N3 : incidents escaladés depuis support N1.
- Diagnostic post-déploiement ou post-migration.

## Hors périmètre
- Diagnostic OS sous-jacente (crash système, kernel panic, services système) → Sysadmin Windows/Linux.
- Diagnostic réseau/firewall (connectivité réseau, règles firewall, VPN) → l'agent réseau.
- Diagnostic BDD (corruption BDD, optimisation requêtes complexes, modélisation) → l'agent bases de données.
- Développement correctifs code source application → l'agent de développement back-end / .NET & C# / l'agent de développement TypeScript/JavaScript.
- Audit sécurité applicative (vulnérabilités OWASP, CVE) → l'agent de sécurité.

## Inputs requis
- Application (nom, version, vendor).
- Symptômes observés (messages d'erreur, comportements anormaux, performance dégradée).
- Contexte (quand le problème a commencé, changements récents, environnement).
- Logs applicatifs disponibles (chemins, extraits pertinents).
- Configuration actuelle (fichiers conf, variables env).
- Intégrations actives (LDAP/AD, SSO, SMTP, reverse proxy, API tierces).

## Sorties attendues
- Diagnostic root cause (cause racine identifiée, preuves).
- Plan de remédiation (étapes correction, risques, rollback).
- Scripts correction (PowerShell/Bash commentés si applicable).
- Rapport incident (symptômes → hypothèses → analyse → root cause → remédiation → validation).
- Actions préventives (monitoring, alertes, documentation).

## Workflow recommandé
1. **Collecte symptômes** :
   - Recueillir description précise du problème (quoi, quand, fréquence, impact).
   - Identifier changements récents (déploiement, mise à jour, configuration, migration).
   - Vérifier statut services applicatifs (démarrés/arrêtés, healthchecks).
2. **Hypothèses initiales** :
   - Lister causes probables (configuration, dépendances, intégrations, certificats, ressources).
   - Prioriser par probabilité (logs, erreurs connues, historique incidents similaires).
3. **Isolation et tests** :
   - Logs applicatifs : analyser stacktraces, messages d'erreur, warnings (catalina.out, application.log, nginx error.log).
   - Dépendances : vérifier runtime (Java, .NET, Python, Node.js), BDD (connectivité, credentials), reverse proxy (config, certificats).
   - Intégrations : tester LDAP/AD (ldapsearch), SSO (metadata SAML/OAuth), SMTP (telnet SMTP), API tierces (curl, Postman).
   - Ressources : vérifier CPU, RAM, disque, network (top, htop, df, netstat).
   - Certificats : vérifier validité, expiration, chaîne de confiance (openssl s_client).
4. **Root cause** :
   - Identifier cause racine unique ou combinaison de causes.
   - Prouver avec logs, tests, métriques (reproduire problème, isoler composant défaillant).
5. **Remédiation** :
   - Appliquer correction (configuration, restart service, renouvellement certificat, rollback).
   - Valider résolution (healthchecks OK, tests fonctionnels réussis, logs clean).
6. **Documentation et prévention** :
   - Documenter incident (symptômes, root cause, remédiation, durée, impact).
   - Ajouter FAQ troubleshooting pour incidents similaires.
   - Configurer monitoring/alertes si absent (healthchecks, logs monitoring, expiration certificats).

## Garde-fous
- Ne jamais modifier configuration production sans backup préalable.
- Tests en staging avant application correction production (si possible).
- Logs : toujours consulter logs complets (pas seulement extraits), attention aux timezone logs.
- Dépendances : vérifier compatibilité versions (Java/JDK, .NET Framework/.NET Core, BDD).
- Certificats : vérifier chaîne complète (certificat intermédiaire, root CA), pas seulement certificat serveur.
- Intégrations LDAP/SSO : vérifier credentials, permissions, mapping attributs, certificats TLS.
- Performance : corréler avec métriques système (CPU, RAM, disque, network), pas seulement logs applicatifs.
- Escalation : si root cause hors périmètre applicatif (OS, réseau, BDD, sécurité), déléguer immédiatement à agent compétent.

## Template d'entrée (copier/coller)
```text
[Application]
- Nom : ...
- Version : ...
- Environnement : production / staging / dev

[Symptômes]
- Description : ...
- Quand : ...
- Fréquence : permanente / intermittente
- Impact : bloquant / dégradé / mineur

[Contexte]
- Changements récents : ...
- Logs extraits : ...

[Configuration actuelle]
- Fichiers conf pertinents : ...
- Variables env : ...

[Intégrations]
- LDAP/AD : ...
- SSO : ...
- SMTP : ...
- API tierces : ...
```

## Template de sortie (copier/coller)
```text
[Diagnostic]
- Symptômes : ...
- Hypothèses testées : ...
- Root cause : ...
- Preuves : ...

[Remédiation]
- Plan correction : ...
- Scripts exécutés : ...
- Risques : ...
- Rollback plan : ...

[Validation]
- Healthchecks : ...
- Tests fonctionnels : ...
- Logs post-correction : ...

[Actions préventives]
- Monitoring configuré : ...
- Alertes ajoutées : ...
- Documentation mise à jour : ...
```

## Checklist QA interne
- Symptômes documentés avec précision (quoi, quand, fréquence, impact).
- Logs applicatifs complets consultés (pas seulement extraits).
- Dépendances vérifiées (runtime, BDD, reverse proxy, certificats).
- Intégrations testées (LDAP/SSO/SMTP/API).
- Root cause identifiée avec preuves (logs, tests, métriques).
- Correction appliquée et validée (healthchecks OK, tests fonctionnels réussis).
- Incident documenté (rapport complet avec timeline).
- Actions préventives planifiées (monitoring, alertes, FAQ).

## KPI reliés
- MTTR (Mean Time To Repair) : temps moyen résolution incident (heures).
- Taux résolution première intervention (% incidents résolus sans escalation).
- Taux incidents récurrents (% incidents identiques sur période).
- Couverture monitoring applicatif (% apps avec healthchecks/alertes).

## Definition of done
- Root cause identifiée et prouvée (logs, tests, métriques).
- Correction appliquée et validée (healthchecks OK, tests fonctionnels réussis).
- Incident documenté (rapport complet avec symptômes → root cause → remédiation).
- Actions préventives planifiées ou appliquées (monitoring, alertes, FAQ).
- Aucune régression introduite (validation fonctionnelle post-correction).

## Exemples d'usage

### Exemple 1 : Gitlab inaccessible après renouvellement certificat SSL
**Contexte** : Gitlab retourne erreur 502 Bad Gateway après renouvellement certificat SSL. Symptômes : nginx démarre mais reverse proxy vers Gitlab échoue.
**Action** :
1. Logs nginx : `SSL_do_handshake() failed (SSL: error:14094410:SSL routines:ssl3_read_bytes:sslv3 alert handshake failure)`.
2. Hypothèse : certificat intermédiaire manquant dans chaîne SSL nginx.
3. Vérification : `openssl s_client -connect gitlab.example.com:443 -showcerts` → certificat intermédiaire absent.
4. Correction : concaténer certificat serveur + certificat intermédiaire dans `/etc/nginx/ssl/gitlab.crt`, reload nginx.
5. Validation : `curl -I https://gitlab.example.com` → 200 OK, login Gitlab réussi.
**Résultat** : Root cause = certificat intermédiaire manquant. Remédiation = ajout certificat intermédiaire. MTTR = 25 minutes. Action préventive = documenter procédure renouvellement certificats avec chaîne complète.

### Exemple 2 : Jira lent après migration serveur
**Contexte** : Jira migré vers nouveau serveur (Ubuntu 22.04, PostgreSQL 15, Tomcat 9). Performance très dégradée (chargement pages > 30s). Symptômes : CPU serveur < 20%, RAM < 50%.
**Action** :
1. Logs Jira : `Slow query detected: SELECT * FROM project WHERE id = ? (execution time: 12000ms)`.
2. Hypothèse : indexes BDD manquants après migration.
3. Vérification PostgreSQL : `EXPLAIN ANALYZE SELECT * FROM project WHERE id = 123` → Seq Scan au lieu de Index Scan.
4. Root cause : migration BDD n'a pas copié les indexes (dump sans `--create` option).
5. Correction : re-créer indexes manquants via scripts SQL fournis par Atlassian, VACUUM ANALYZE.
6. Validation : chargement pages < 2s, logs Jira sans slow queries.
**Résultat** : Root cause = indexes BDD manquants. Remédiation = re-création indexes + VACUUM ANALYZE. MTTR = 1h20. Action préventive = checklist migration BDD avec vérification indexes post-migration.

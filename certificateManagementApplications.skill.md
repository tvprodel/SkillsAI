# Certificate Management Applications

## Objectif
Maîtriser la gestion complète des certificats SSL/TLS pour applications d'entreprise (Jira, Gitlab, ServiceNow, Confluence, etc.) : génération CSR, installation certificats, configuration HTTPS, renouvellement automatique, troubleshooting certificats expirés.

## Quand l'utiliser (triggers)
- « certificat Jira expiré », « configurer HTTPS Gitlab », « générer CSR ServiceNow », « renouveler certificat Confluence ».
- Activation HTTPS pour application d'entreprise.
- Renouvellement certificat expiré ou proche expiration.
- Migration certificat auto-signé vers certificat CA (Let's Encrypt, DigiCert, etc.).
- Troubleshooting erreurs certificats (navigateur, API HTTPS).

## Hors périmètre
- Certificats infrastructure globaux (load balancers, firewalls, VPN) → l'agent réseau.
- PKI d'entreprise (CA interne, distribution certificats utilisateurs) → Sysadmin Windows (AD CS).
- Certificats conteneurs orchestrés (cert-manager Kubernetes) → l'agent conteneurs.

## Inputs requis
- Application (nom, version, URL HTTPS cible).
- Type certificat (auto-signé, Let's Encrypt, CA commercial, wildcard).
- Domaine(s) (FQDN principal, SAN Subject Alternative Names).
- CA (Certification Authority) si certificat commercial.
- Reverse proxy (nginx, Apache, IIS, Tomcat natif).

## Sorties attendues
- CSR (Certificate Signing Request) généré.
- Certificat installé (certificat + chaîne CA + clé privée sécurisée).
- Configuration HTTPS appliquée (reverse proxy ou application native).
- Tests validation (navigateur, curl, openssl s_client).
- Procédure renouvellement (manuel ou automatique Let's Encrypt).

## Workflow recommandé
1. **Analyse** : identifier application, URL cible, reverse proxy ou HTTPS natif, type certificat (auto-signé/Let's Encrypt/commercial).
2. **Génération CSR** :
   - OpenSSL (Linux) : `openssl req -new -newkey rsa:2048 -nodes -keyout app.key -out app.csr`
   - IIS (Windows) : IIS Manager > Server Certificates > Create Certificate Request
   - Renseigner : FQDN, organisation, pays, SAN si wildcard/multi-domaines.
3. **Obtention certificat** :
   - Auto-signé : `openssl x509 -req -days 365 -in app.csr -signkey app.key -out app.crt`
   - Let's Encrypt : certbot (nginx/Apache) ou acme.sh (standalone)
   - CA commercial : soumettre CSR, récupérer certificat + chaîne CA
4. **Installation certificat** :
   - nginx : copier certificat/clé dans /etc/nginx/ssl/, configurer server block HTTPS
   - Apache : copier dans /etc/ssl/, configurer VirtualHost HTTPS
   - IIS : Import certificat dans IIS Manager, binding HTTPS site
   - Tomcat : créer keystore PKCS12, configurer server.xml connector HTTPS
   - Application native (Jira, Gitlab) : suivre doc vendor (souvent keystore Java ou fichiers PEM)
5. **Configuration HTTPS** :
   - nginx : `listen 443 ssl; ssl_certificate /path/cert.crt; ssl_certificate_key /path/cert.key;`
   - Apache : `SSLEngine on; SSLCertificateFile /path/cert.crt; SSLCertificateKeyFile /path/cert.key;`
   - IIS : binding HTTPS avec certificat sélectionné
   - Redirection HTTP → HTTPS si demandé
6. **Validation** :
   - Navigateur : accès HTTPS, cadenas vert, vérifier certificat (validité, émetteur, SAN)
   - Curl : `curl -v https://app.domain.com` (vérifier SSL handshake OK)
   - OpenSSL : `openssl s_client -connect app.domain.com:443 -servername app.domain.com` (vérifier chaîne certificat)
7. **Renouvellement** :
   - Let's Encrypt : configurer certbot auto-renew (cron ou systemd timer)
   - CA commercial : alerte expiration, renouveler manuellement ou via API CA
   - Documenter procédure renouvellement (fréquence, commandes, contacts CA)

## Garde-fous
- Clé privée sécurisée (permissions 600, jamais en version control).
- Chaîne CA complète installée (certificat intermédiaire + root CA).
- HTTPS uniquement (désactiver HTTP ou redirection obligatoire).
- TLS 1.2+ uniquement (désactiver SSLv3, TLS 1.0/1.1).
- Cipher suites sécurisées (ECDHE, AES-GCM, désactiver RC4, 3DES).
- Alerte expiration certificat (60 jours avant, 30 jours, 7 jours).
- Backups certificat/clé avant renouvellement (rollback si problème).

## Template d'entrée (copier/coller)
```text
[Application]
- Nom : ...
- URL HTTPS cible : ...

[Certificat]
- Type : auto-signé / Let's Encrypt / commercial
- Domaine(s) : ... (FQDN + SAN si wildcard)
- CA : ... (si commercial)

[Infrastructure]
- Reverse proxy : nginx / Apache / IIS / Tomcat natif
- OS : ...
```

## Template de sortie (copier/coller)
```text
[CSR généré]
- Fichier : app.csr
- Commande : ...

[Certificat obtenu]
- Fichier : app.crt (certificat) + app.key (clé privée) + ca-chain.crt (chaîne CA)
- Source : ... (Let's Encrypt, DigiCert, auto-signé)

[Configuration HTTPS]
- Reverse proxy : ...
- Fichiers conf modifiés : ...
- Redirection HTTP → HTTPS : oui/non

[Validation]
- Navigateur : ...
- Curl : ...
- OpenSSL s_client : ...

[Renouvellement]
- Procédure : ...
- Fréquence : ...
- Alertes expiration : ...
```

## Checklist QA interne
- CSR généré avec FQDN + SAN corrects.
- Certificat obtenu (validité 90 jours Let's Encrypt, 1-2 ans commercial).
- Chaîne CA complète installée.
- Clé privée sécurisée (permissions 600).
- HTTPS configuré (reverse proxy ou application native).
- Redirection HTTP → HTTPS activée.
- TLS 1.2+ uniquement (pas SSLv3, TLS 1.0/1.1).
- Cipher suites sécurisées (pas RC4, 3DES).
- Tests validation réussis (navigateur, curl, openssl).
- Alerte expiration configurée (60/30/7 jours).
- Procédure renouvellement documentée.

## KPI reliés
- Nombre certificats expirés (cible 0).
- Temps moyen renouvellement certificat (heures).
- Taux automatisation renouvellement (% Let's Encrypt auto-renew).
- Incidents HTTPS post-installation (nombre par trimestre).

## Definition of done
- Certificat installé et validé.
- HTTPS activé et accessible.
- Tests validation réussis (navigateur + curl + openssl).
- Redirection HTTP → HTTPS configurée.
- Alerte expiration configurée.
- Procédure renouvellement documentée.

## Exemples d'usage

### Exemple 1 : [Titre du cas d'usage]
**Contexte** : [Description de la situation]
**Action** : [Ce qui a été fait]
**Résultat** : [Résultat obtenu]
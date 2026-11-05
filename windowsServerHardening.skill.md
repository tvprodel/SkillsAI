# Windows Server Hardening

## Objectif
Sécuriser Windows Server selon CIS Benchmarks et best practices Microsoft (attack surface reduction, least privilege, audits).

## Quand l'utiliser (triggers)
- « sécurise Windows Server », « hardening », « CIS Benchmarks », « compliance sécurité ».
- Mise en conformité serveurs avant production.
- Audit sécurité post-installation.

## Hors périmètre
- Sécurité applicative (code, OWASP) → l'agent de sécurité.
- Sécurité réseau (firewalls, VPN) → networkFirewall.
- Azure cloud security → l'agent d'architecture cloud.

## Inputs requis
- Version Windows Server (2016/2019/2022).
- Rôles installés (DC, IIS, File Server, etc.).
- Niveau CIS Benchmark visé (Level 1 / Level 2).
- Environnement (production, dev, DMZ).

## Sorties attendues
- Checklist hardening appliquée (CIS Benchmarks items cochés).
- Scripts PowerShell/DSC hardening (disable SMBv1, enable Windows Defender, configure firewall).
- Rapport compliance (scores CIS, écarts détectés, remédiation).

## Workflow recommandé
1. Baseline actuelle : scanner serveur (Microsoft Security Compliance Toolkit, Nessus).
2. Appliquer CIS Level 1 (minimum) :
   - Disable SMBv1 (Set-SmbServerConfiguration -EnableSMB1Protocol $false).
   - Enable Windows Defender (Set-MpPreference).
   - Configure Windows Firewall (netsh advfirewall, deny-all puis allow sélectif).
   - Disable unnecessary services (Print Spooler si non utilisé, Remote Registry).
   - Enable auditing (auditpol /set).
3. AppLocker ou WDAC (Windows Defender Application Control) si Level 2.
4. BitLocker pour chiffrement disques (Enable-BitLocker).
5. Audits réguliers (Event Viewer logs 4624 logon success, 4625 logon failure, 4720 user created).

## Garde-fous
- Tests post-hardening : vérifier que services critiques fonctionnent toujours.
- Backup avant hardening (snapshots VM ou Windows Server Backup).
- Documentation écarts CIS (justifier si Level 2 non applicable contexte métier).

## Template d'entrée (copier/coller)
```text
[Serveur]
- OS : ...
- Rôles : ...
- Niveau CIS : ...

[Contraintes]
- Services critiques : ...
```

## Template de sortie (copier/coller)
```text
[Hardening appliqué]
- Items CIS Level 1 : ...
- Scripts : ...

[Compliance]
- Score CIS : ...
- Écarts : ...

[Tests]
- Services OK : ...
```

## Checklist QA interne
- CIS Level 1 minimum appliqué (> 90% items).
- SMBv1 disabled.
- Windows Firewall enabled et configuré.
- BitLocker enabled (si requis).
- Audits enabled (auditpol).

## KPI reliés
- Score CIS Benchmark (% conformité).
- Nb vulnérabilités critiques détectées (scan Nessus).
- Temps moyen hardening serveur (heures).

## Definition of done
- Hardening appliqué et testé.
- Scripts et checklist documentés.
- Rapport compliance publié.

## Exemples d'usage

### Exemple 1 : [Titre du cas d'usage]
**Contexte** : [Description de la situation]
**Action** : [Ce qui a été fait]
**Résultat** : [Résultat obtenu]
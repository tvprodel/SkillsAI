# Linux Security Hardening

## Objectif
Sécuriser Linux selon CIS Benchmarks (RHEL/Ubuntu) : SELinux/AppArmor, firewall, SSH, sudo, audits.

## Quand l'utiliser (triggers)
- « sécurise Linux », « hardening », « CIS Benchmarks Linux », « SELinux enforcing ».
- Mise en conformité serveurs avant production.
- Audit sécurité post-installation.

## Hors périmètre
- Sécurité applicative (code, OWASP) → l'agent de sécurité.
- Sécurité réseau (firewalls avancés, VPN) → networkFirewall.
- Cloud security → l'agent d'architecture cloud.

## Inputs requis
- Distribution (RHEL/CentOS, Debian/Ubuntu).
- Rôles serveur (web, BDD, file server).
- Niveau CIS Benchmark visé (Level 1 / Level 2).

## Sorties attendues
- Checklist hardening appliquée (CIS items cochés).
- Scripts Bash/Ansible hardening (SELinux enforcing, firewalld rules, SSH hardening).
- Rapport compliance (scores CIS, écarts, remédiation).

## Workflow recommandé
1. Baseline actuelle : scanner (Lynis, OpenSCAP).
2. Appliquer CIS Level 1 (minimum) :
   - SELinux enforcing (RHEL) : setenforce 1, /etc/selinux/config SELINUX=enforcing.
   - AppArmor enforcing (Ubuntu) : aa-enforce /etc/apparmor.d/*.
   - Firewalld/iptables : deny-all puis allow sélectif (SSH 22, HTTP 80/443 si web).
   - SSH hardening : /etc/ssh/sshd_config (PermitRootLogin no, PasswordAuthentication no, PubkeyAuthentication yes).
   - Sudo policies : /etc/sudoers (moindre privilège, logs sudo).
   - Disable unnecessary services (telnet, rsh, ftp si non utilisés).
   - Audits : auditd enabled, rules /etc/audit/rules.d/.
3. fail2ban (SSH brute force protection).
4. Automatic security updates (yum-cron, unattended-upgrades).
5. Audits réguliers : journalctl, /var/log/secure, /var/log/auth.log.

## Garde-fous
- Tests post-hardening : vérifier accès SSH keys, services critiques OK.
- Backup avant hardening (snapshots VM).
- SELinux troubleshooting : audit2allow si services bloqués (analyser avant allow).

## Template d'entrée (copier/coller)
```text
[Serveur]
- Distribution : ...
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
- SSH keys : ...
- Services OK : ...
```

## Checklist QA interne
- CIS Level 1 minimum appliqué (> 90% items).
- SELinux/AppArmor enforcing.
- Firewalld/iptables configuré (deny-all + allow sélectif).
- SSH hardening (no root login, keys only).
- fail2ban enabled.

## KPI reliés
- Score CIS Benchmark (% conformité).
- Nb vulnérabilités critiques (scan Lynis/OpenSCAP).
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
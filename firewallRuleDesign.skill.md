# Firewall Rule Design

## Objectif
Concevoir règles firewall sécurisées (iptables, pfSense, cloud SG) selon principe Zero Trust (deny-all puis allow sélectif).

## Quand l'utiliser (triggers)
- « règles firewall », « iptables », « pfSense », « security groups », « ACL réseau », « Zero Trust ».
- Sécurisation infrastructure réseau.
- Audit/refonte règles firewall existantes.

## Hors périmètre
- Sécurité applicative (OWASP, code) → l'agent de sécurité.
- Architecture réseau complète (VLAN, routing) → networkFirewall (autre skill).
- Cloud IaC provisioning → l'agent d'architecture cloud.

## Inputs requis
- Infrastructure (on-prem iptables/pfSense, cloud AWS SG/Azure NSG).
- Services exposés (web HTTP/HTTPS, SSH management, API).
- Zones sécurisées (DMZ, internal, management).
- IPs sources autorisées (office IPs, VPN).

## Sorties attendues
- Règles firewall (iptables script, pfSense XML, Terraform SG).
- Documentation justification deny/allow par règle.
- Tests validation (nmap scan, logs firewall).

## Workflow recommandé
1. Principe deny-all puis allow sélectif :
   - iptables :
     ```bash
     iptables -P INPUT DROP
     iptables -P FORWARD DROP
     iptables -P OUTPUT ACCEPT
     iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
     iptables -A INPUT -p tcp --dport 22 -s 10.0.0.0/8 -j ACCEPT  # SSH management subnet only
     iptables -A INPUT -p tcp --dport 80 -j ACCEPT  # HTTP from internet
     iptables -A INPUT -p tcp --dport 443 -j ACCEPT  # HTTPS from internet
     ```
   - AWS Security Group :
     ```hcl
     ingress {
       from_port = 443
       to_port = 443
       protocol = "tcp"
       cidr_blocks = ["0.0.0.0/0"]
       description = "HTTPS from internet"
     }
     ingress {
       from_port = 22
       to_port = 22
       protocol = "tcp"
       cidr_blocks = ["10.0.0.0/8"]
       description = "SSH management subnet only"
     }
     ```
2. Logging (iptables -j LOG, pfSense logs, VPC Flow Logs).
3. Tests : nmap scan, vérifier ports fermés (timeout), logs firewall (allowed/denied).

## Garde-fous
- Deny-all par défaut (DROP INPUT/FORWARD).
- Allow sélectif (ports, IPs sources explicites).
- SSH management subnet uniquement (jamais 0.0.0.0/0).
- Logging enabled (audit, troubleshooting).
- Revue régulière (cleanup rules obsolètes).

## Template d'entrée (copier/coller)
```text
[Infrastructure]
- Type firewall : ...
- Zones : ...

[Services]
- Exposés : ...
- IPs sources : ...
```

## Template de sortie (copier/coller)
```text
[Règles]
- Script/config : ...
- Justifications : ...

[Tests]
- nmap : ...
- Logs : ...
```

## Checklist QA interne
- Deny-all défaut.
- Allow sélectif (ports, IPs).
- SSH restricted (management subnet).
- Logging enabled.
- Tests nmap validés.

## KPI reliés
- Nb règles too permissive (0.0.0.0/0 SSH).
- Nb règles obsolètes (cleanup).
- Taux blocage trafic non autorisé (%).

## Definition of done
- Règles conçues et appliquées.
- Tests nmap validés.
- Documentation publiée.

## Exemples d'usage

### Exemple 1 : [Titre du cas d'usage]
**Contexte** : [Description de la situation]
**Action** : [Ce qui a été fait]
**Résultat** : [Résultat obtenu]
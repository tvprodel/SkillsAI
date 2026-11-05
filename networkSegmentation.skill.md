# Network Segmentation

## Objectif
Concevoir segmentation réseau (VLAN, subnets, micro-segmentation, Zero Trust) pour isoler workloads et réduire blast radius.

## Quand l'utiliser (triggers)
- « segmentation réseau », « VLAN », « micro-segmentation », « Zero Trust networking », « DMZ ».
- Isolation environnements (prod/dev).
- Conformité (PCI-DSS, HIPAA segmentation requirements).

## Hors périmètre
- Firewall rules détaillées → skill Firewall Rule Design.
- VPN → skill VPN Configuration.
- Cloud networking (VPC design) → l'agent d'architecture cloud.

## Inputs requis
- Workloads à isoler (web, app, BDD, management).
- Compliance requirements (PCI-DSS, HIPAA, ISO 27001).
- Infrastructure (on-prem switches VLAN, cloud VPC subnets).

## Sorties attendues
- Diagramme segmentation (zones, VLAN, subnets, firewall zones).
- Configuration VLAN (switches 802.1Q trunking).
- Plan IP (subnets CIDR par zone).
- Matrice flux autorisés (zone A → zone B ports/protocols).

## Workflow recommandé
1. Définir zones sécurisées :
   - DMZ (web servers, public-facing).
   - Internal (app servers, APIs backend).
   - Database (BDD isolée, accès app servers uniquement).
   - Management (admin access, monitoring, backups).
2. Subnetting :
   - DMZ : 10.0.1.0/24.
   - Internal : 10.0.2.0/24.
   - Database : 10.0.3.0/24.
   - Management : 10.0.254.0/24.
3. VLAN (si on-prem) :
   - VLAN 10 DMZ, VLAN 20 Internal, VLAN 30 Database, VLAN 254 Management.
   - Trunking 802.1Q switches.
4. Firewall rules inter-zones (deny-all puis allow sélectif) :
   - DMZ → Internal : deny.
   - Internal → Database : allow TCP 3306/5432.
   - Management → All : allow (admin access).
5. Micro-segmentation (cloud, Kubernetes Network Policies) :
   - Isolation pod-to-pod Kubernetes.
   - Security groups per workload cloud.

## Garde-fous
- DMZ isolée (pas accès direct internal/database).
- Database zone accès restricted (app servers uniquement).
- Management zone accès MFA + VPN.
- Matrice flux documentée (justifier chaque allow inter-zones).

## Template d'entrée (copier/coller)
```text
[Workloads]
- Liste : ...
- Compliance : ...

[Infrastructure]
- On-prem/cloud : ...
```

## Template de sortie (copier/coller)
```text
[Zones]
- Liste : ...
- Subnets : ...

[VLAN]
- Configuration : ...

[Matrice flux]
- Zone A → Zone B : ...
```

## Checklist QA interne
- Zones définies (DMZ, Internal, Database, Management).
- Subnets planifiés (CIDR).
- VLAN configurés (802.1Q) si on-prem.
- Matrice flux documentée.
- DMZ isolée.

## KPI reliés
- Nb zones (complexité).
- Taux isolation (% workloads isolés).
- Nb flux inter-zones (surface attack).

## Definition of done
- Segmentation conçue.
- VLAN/subnets configurés.
- Matrice flux publiée.

## Exemples d'usage

### Exemple 1 : [Titre du cas d'usage]
**Contexte** : [Description de la situation]
**Action** : [Ce qui a été fait]
**Résultat** : [Résultat obtenu]
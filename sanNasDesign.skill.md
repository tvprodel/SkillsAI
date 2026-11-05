# SAN/NAS Design

## Objectif
Concevoir architecture stockage SAN/NAS (Fibre Channel, iSCSI, NFS, SMB) performante, résiliente et scalable.

## Quand l'utiliser (triggers)
- « SAN », « NAS », « Fibre Channel », « iSCSI », « NFS », « SMB », « stockage entreprise », « LUNs », « IOPS ».
- Conception infrastructure stockage on-prem.
- Migration stockage DAS → SAN/NAS.

## Hors périmètre
- Cloud storage (S3, Blob) → skill Cloud Storage Strategies.
- Backups → skill Backup Recovery Automation.
- Réseau stockage détaillé → networkFirewall (collaboration).

## Inputs requis
- Workloads (VMs, BDD, file shares).
- Performances (IOPS requis, latency < Xms).
- Capacité (TB total, growth projection).
- Résilience (RAID level, redundancy controllers).

## Sorties attendues
- Architecture SAN/NAS (topology, controllers, disks SSD/HDD).
- Configuration LUNs/volumes (sizing, RAID, multipathing).
- Plan IOPS (workloads vs IOPS disks).
- Sizing coûts (disks, controllers, switches FC si SAN).

## Workflow recommandé
1. **SAN vs NAS** :
   - SAN (block-level, Fibre Channel/iSCSI) : VMs, BDD (high IOPS, low latency).
   - NAS (file-level, NFS/SMB) : file shares, backups, ISO/templates (throughput, moins latency-sensitive).
2. **SAN design** :
   - Fibre Channel (8/16/32 Gbps, switches FC, zoning).
   - iSCSI (over Ethernet 10GbE/25GbE, VLAN dédié, multipathing).
   - LUNs : RAID 10 (performance, 50% usable) ou RAID 6 (capacity, 2 disks parity).
   - Controllers HA (dual controllers, failover).
3. **NAS design** :
   - NFS (Linux, vSphere datastores).
   - SMB/CIFS (Windows, file shares).
   - Volumes : RAID 6 (capacity, résilience).
   - Snapshots (COW copy-on-write, retention 7j/30j).
4. **Sizing IOPS** :
   - SSD : 10k-50k IOPS/disk.
   - HDD : 100-200 IOPS/disk.
   - Calcul : nb VMs × IOPS/VM = total IOPS requis → nb disks SSD/HDD.
5. **Multipathing** (SAN) : MPIO Windows, DM-Multipath Linux (load balancing, failover).

## Garde-fous
- SSD workloads critiques (VMs, BDD).
- HDD archivage/backups.
- RAID 10 performance (pas RAID 5 VMs production).
- Controllers HA (dual, failover < 30s).
- Multipathing configuré (failover paths).

## Template d'entrée (copier/coller)
```text
[Workloads]
- VMs/BDD : ...
- File shares : ...

[Performances]
- IOPS requis : ...
- Latency : ...

[Capacité]
- TB total : ...
```

## Template de sortie (copier/coller)
```text
[Architecture]
- SAN/NAS : ...
- Topology : ...

[Sizing]
- Disks SSD/HDD : ...
- IOPS plan : ...

[Coûts]
- Estimation : ...
```

## Checklist QA interne
- SAN/NAS choix justifié.
- RAID level adapté.
- Controllers HA.
- IOPS sizing validé.
- Multipathing configuré (SAN).

## KPI reliés
- IOPS total (disks).
- Latency (ms).
- Capacité utilisée (% TB).

## Definition of done
- Architecture SAN/NAS conçue.
- Sizing disks validé.
- Coûts estimés.

## Exemples d'usage

### Exemple 1 : [Titre du cas d'usage]
**Contexte** : [Description de la situation]
**Action** : [Ce qui a été fait]
**Résultat** : [Résultat obtenu]
# Backup Recovery Automation

## Objectif
Concevoir stratégie backup/restore automatisée (Veeam, Bacula, cloud native) avec RTO/RPO définis, tests DR réguliers, immutabilité.

## Quand l'utiliser (triggers)
- « backups », « Veeam », « Bacula », « AWS Backup », « restore », « RTO », « RPO », « disaster recovery », « 3-2-1 ».
- Définition stratégie backup production.
- Audit/optimisation backups existants.

## Hors périmètre
- Infrastructure stockage (SAN/NAS, cloud) → skills SAN/NAS Design, Cloud Storage Strategies.
- PRA/PCA global (compute failover) → l'agent de gestion des risques, l'agent d'architecture cloud.
- Monitoring → agents techniques.

## Inputs requis
- Systèmes à sauvegarder (VMs, BDD, file shares).
- RTO (Recovery Time Objective, temps max restauration).
- RPO (Recovery Point Objective, perte données max acceptable).
- Rétention (jours/semaines/mois/années).

## Sorties attendues
- Stratégie backup 3-2-1 (3 copies, 2 médias, 1 off-site).
- Configuration jobs backup (Veeam, Bacula, cloud native).
- Tests restore (restore test VM/file, mesurer RTO réel).
- Runbooks restore (procédures disaster recovery).

## Workflow recommandé
1. **Stratégie 3-2-1** :
   - 3 copies données : production + backup 1 (on-prem disk) + backup 2 (cloud ou tape).
   - 2 médias différents : disk + cloud (ou tape).
   - 1 off-site : cloud S3/Blob ou tape off-site.
2. **RTO/RPO par criticité** :
   - Tier 1 (critique) : RTO < 4h, RPO < 1h → backups fréquents (hourly), replication.
   - Tier 2 (standard) : RTO < 24h, RPO < 4h → backups daily.
   - Tier 3 (archivage) : RTO < 72h, RPO < 24h → backups weekly.
3. **Veeam** :
   - Jobs backup (daily full + incremental).
   - Backup copy job (vers cloud S3/Blob).
   - Immutability (immutable backups, protection ransomware).
   - Instant VM Recovery (boot VM from backup, RTO minutes).
4. **Bacula** :
   - Director, Storage Daemon, File Daemon.
   - Schedules (Full monthly, Differential weekly, Incremental daily).
   - Retention pools (30j/90j/1an).
5. **Cloud native** :
   - AWS Backup : policies (daily snapshots EBS, RDS, S3).
   - Azure Backup : Recovery Services Vault, policies.
6. **Tests DR** :
   - Restore test VM mensuel (vérifier backup intégrité).
   - Mesurer RTO réel (temps restore complète).
   - Runbooks DR (procédures restore, contacts, escalation).

## Garde-fous
- Stratégie 3-2-1 obligatoire.
- Immutability backups (ransomware protection).
- Tests restore réguliers (mensuel minimum Tier 1).
- RTO/RPO mesurés (pas théoriques).
- Runbooks DR maintenus (revue trimestrielle).

## Template d'entrée (copier/coller)
```text
[Systèmes]
- VMs/BDD/files : ...

[RTO/RPO]
- Tier 1 : ...
- Tier 2 : ...

[Rétention]
- Durée : ...
```

## Template de sortie (copier/coller)
```text
[Stratégie 3-2-1]
- Copies : ...
- Médias : ...
- Off-site : ...

[Jobs backup]
- Veeam/Bacula/cloud : ...

[Tests DR]
- Restore test : ...
- RTO mesuré : ...

[Runbooks]
- Procédures : ...
```

## Checklist QA interne
- Stratégie 3-2-1.
- RTO/RPO définis.
- Immutability backups.
- Tests restore mensuels (Tier 1).
- Runbooks DR publiés.

## KPI reliés
- RTO réel vs objectif (écart).
- RPO réel vs objectif (écart).
- Taux succès restore (%).

## Definition of done
- Stratégie backup définie.
- Jobs configurés et testés.
- Tests restore validés.
- Runbooks DR publiés.

## Exemples d'usage

### Exemple 1 : [Titre du cas d'usage]
**Contexte** : [Description de la situation]
**Action** : [Ce qui a été fait]
**Résultat** : [Résultat obtenu]
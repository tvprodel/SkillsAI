# Cloud Storage Strategies

## Objectif
Concevoir stratégies stockage cloud hybride (S3, Azure Blob, GCS) : tiers, lifecycle, versioning, replication, coûts optimisés.

## Quand l'utiliser (triggers)
- « S3 », « Azure Blob », « GCS », « cloud storage », « lifecycle policies », « tiering », « stockage hybride ».
- Conception stockage cloud ou migration on-prem → cloud.
- Optimisation coûts stockage cloud.

## Hors périmètre
- Stockage on-prem (SAN/NAS) → skill SAN/NAS Design.
- Backups détaillés → skill Backup Recovery Automation.
- IaC provisioning → l'agent d'architecture cloud.

## Inputs requis
- Data types (hot/warm/cold/archive).
- Volumes (TB par tier).
- Access patterns (fréquence read/write).
- Compliance (retention, immutability).

## Sorties attendues
- Stratégie tiers (Standard/IA/Glacier S3, Hot/Cool/Archive Blob).
- Lifecycle policies (auto-tiering après Xj).
- Configuration versioning, replication, immutability.
- Coûts estimés (storage + requests + data transfer).

## Workflow recommandé
1. **Tiers cloud** :
   - **AWS S3** :
     - S3 Standard : hot data (accès fréquent).
     - S3 Intelligent-Tiering : auto-tiering (unknown patterns).
     - S3 Standard-IA (Infrequent Access) : warm data (< 1×/mois).
     - S3 Glacier Flexible/Deep Archive : cold data (archivage 90j+/7ans+).
   - **Azure Blob** :
     - Hot : accès fréquent.
     - Cool : accès < 1×/mois (30j retention min).
     - Archive : archivage (180j retention min, latency restore heures).
   - **GCP GCS** :
     - Standard, Nearline (30j), Coldline (90j), Archive (365j).
2. **Lifecycle policies** (auto-tiering) :
   ```json
   {
     "Rules": [{
       "Id": "Archive old logs",
       "Status": "Enabled",
       "Filter": {"Prefix": "logs/"},
       "Transitions": [
         {"Days": 90, "StorageClass": "STANDARD_IA"},
         {"Days": 365, "StorageClass": "GLACIER"}
       ],
       "Expiration": {"Days": 2555}
     }]
   }
   ```
3. **Versioning** (compliance, protect deletes) :
   - S3 Versioning enabled (MFA Delete protection).
   - Azure Blob soft delete (retention 30j).
4. **Replication** (DR, compliance multi-région) :
   - S3 CRR (Cross-Region Replication).
   - Azure Blob GRS (Geo-Redundant Storage).
5. **Immutability** (ransomware, compliance) :
   - S3 Object Lock (WORM, retention 1-10 ans).
   - Azure Blob immutability policies.

## Garde-fous
- Lifecycle policies (éviter stockage hot inutile).
- Versioning si compliance (pas si data volatile costs).
- Immutability backups (ransomware protection).
- Egress costs (data transfer out cloud coûteux, minimize).

## Template d'entrée (copier/coller)
```text
[Data types]
- Hot/warm/cold : ...
- Volumes TB : ...

[Access patterns]
- Fréquence : ...

[Compliance]
- Retention : ...
- Immutability : ...
```

## Template de sortie (copier/coller)
```text
[Tiers]
- Standard : ...
- IA/Cool : ...
- Glacier/Archive : ...

[Lifecycle]
- Policies : ...

[Coûts]
- Storage : ...
- Requests : ...
- Transfer : ...
```

## Checklist QA interne
- Tiers adaptés (hot/warm/cold).
- Lifecycle policies configurées.
- Versioning si compliance.
- Immutability backups.
- Coûts estimés.

## KPI reliés
- Coût storage $/TB/mois.
- Nb objets par tier (%).
- Egress costs $/mois.

## Definition of done
- Stratégie tiers définie.
- Lifecycle policies configurées.
- Coûts estimés publiés.

## Exemples d'usage

### Exemple 1 : [Titre du cas d'usage]
**Contexte** : [Description de la situation]
**Action** : [Ce qui a été fait]
**Résultat** : [Résultat obtenu]
# Data Catalog & Lineage

## Objectif
Mettre en place et maintenir un catalogue de données centralisé avec métadonnées complètes, lineage (traçabilité end-to-end des transformations) et gouvernance pour faciliter découvrabilité, collaboration et conformité (RGPD, audit).

## Quand l'utiliser (triggers)
- Mise en place d'un data catalog (AWS Glue Catalog, Azure Purview, Alation, DataHub)
- Traçabilité des transformations données (lineage column-level ou table-level)
- Documentation métadonnées : schémas, owners, descriptions, tags, glossaire métier
- Gouvernance données : ownership, classification (PII, sensible), politiques d'accès
- Audit et conformité : lineage pour RGPD (right to erasure, data provenance)
- Découvrabilité données : moteur recherche métadonnées pour self-service analytics
- Impact analysis : identifier tables impactées par changement upstream

## Hors périmètre
- ❌ Data quality monitoring (validation, checks) → dataQualityMonitoring.skill.md
- ❌ Pipelines ETL/ELT → etlPipelineDesignOrchestration.skill.md
- ❌ Architecture data lake → dataLakeArchitectureStorage.skill.md
- ❌ Contrôle d'accès technique (IAM, RBAC) → l'agent d'architecture cloud
- ❌ Conformité juridique RGPD → l'agent de conformité RGPD

## Inputs requis
- **Inventaire sources** : tables BDD, fichiers data lake, APIs, dashboards BI
- **Stack cible** : AWS Glue Catalog, Azure Purview, DataHub, Alation, Amundsen
- **Besoins gouvernance** : classification PII, ownership par équipe, audit trail
- **Use cases** : self-service analytics, conformité RGPD, impact analysis
- **Niveau lineage** : table-level (quelles tables alimentent quoi) ou column-level (quelle colonne source → colonne destination)

## Sorties attendues
- **Catalogue de données** : métadonnées centralisées (schémas, descriptions, owners, tags)
- **Lineage graph** : visualisation DAG des flux de données (sources → transformations → destinations)
- **Glossaire métier** : termes business standardisés (ex: "Revenu" = SUM(amount) WHERE status='paid')
- **Classification données** : tags PII, sensible, public, interne
- **Documentation ownership** : owner technique et business par dataset
- **Procédures gouvernance** : workflow demande accès, validation modifications schéma

## Workflow recommandé
1. **Inventaire initial** :
   - Scanner automatiquement toutes les sources (crawler AWS Glue, Azure Purview scan)
   - Lister tables, colonnes, types, volumétrie, dernière MAJ
   - Identifier datasets prioritaires (plus utilisés, critiques métier)

2. **Enrichissement métadonnées** :
   - Documenter descriptions (table, colonnes) avec contexte business
   - Assigner owners (technique + business) par dataset
   - Classifier données (PII, sensible, public) avec tags
   - Créer glossaire métier (définitions termes business)

3. **Capture du lineage** :
   - Instrumenter pipelines ETL/ELT (OpenLineage, Marquez)
   - Parser SQL queries (extraction automatique lineage)
   - Visualiser graph de lineage (table-level ou column-level)

4. **Gouvernance et politiques** :
   - Définir workflow demande accès (auto-approval, validation manuelle)
   - Configurer alerting sur changements schéma (breaking changes)
   - Auditer accès données (qui a consulté quoi, quand)

5. **Adoption et maintenance** :
   - Former équipes au catalogue (recherche, consultation lineage)
   - Automatiser mise à jour métadonnées (crawlers quotidiens)
   - Monitorer usage catalogue (métriques adoption)

## Garde-fous
- **GF1 - Owner obligatoire** : Tout dataset doit avoir owner technique ET business documenté. Mesure : 100% datasets avec owner.
- **GF2 - Classification PII** : Toute colonne contenant données personnelles (email, phone, adresse) doit être tagguée PII. Mesure : 100% colonnes PII identifiées.
- **GF3 - Lineage à jour** : Lineage doit être rafraîchi quotidiennement (crawl automatique). Mesure : lineage <24h de fraîcheur.
- **GF4 - Descriptions non-vides** : Tables critiques (top 20% usage) doivent avoir description ≥50 caractères. Mesure : 100% top tables documentées.
- **GF5 - Glossaire métier** : Termes business clés (KPI, métriques) doivent être dans glossaire avec définition. Mesure : 100% KPI dans glossaire.
- **GF6 - Audit trail** : Changements métadonnées (schéma, owner, classification) doivent être audités. Mesure : 100% changements tracés.
- **GF7 - Impact analysis** : Avant changement breaking (suppression colonne), analyser impact downstream. Mesure : 0 breaking change sans impact analysis.

## Template d'entrée (copier/coller)
```text
[Périmètre catalogue/lineage]
- Domaines, systèmes et jeux de données : ...
- Owners/stewards et consommateurs : ...
- Métadonnées, classifications et exigences PII : ...
- Sources de lineage disponibles et outil/catalogue : ...
```

## Template de sortie (copier/coller)
```text
[Catalogue et traçabilité]
- Jeux de données et métadonnées normalisées : ...
- Owners, classifications et règles d'accès : ...
- Lineage source → transformation → consommation : ...
- Lacunes, risques qualité/conformité et actions : ...
```

## Templates copier/coller

### Template AWS Glue Crawler (Python Boto3)
```python
import boto3

glue_client = boto3.client('glue')

# Create crawler to scan S3 data lake
response = glue_client.create_crawler(
    Name='data-lake-crawler',
    Role='arn:aws:iam::123456789012:role/AWSGlueServiceRole',
    DatabaseName='data_catalog',
    Targets={
        'S3Targets': [
            {
                'Path': 's3://data-lake/silver/',
                'Exclusions': ['*/temp/*', '*/_backup/*']
            },
            {
                'Path': 's3://data-lake/gold/',
            }
        ]
    },
    Schedule='cron(0 2 * * ? *)',  # Daily at 2 AM
    SchemaChangePolicy={
        'UpdateBehavior': 'UPDATE_IN_DATABASE',  # Auto-update schema
        'DeleteBehavior': 'LOG'  # Log table deletions
    },
    Configuration='{"Version":1.0,"CrawlerOutput":{"Partitions":{"AddOrUpdateBehavior":"InheritFromTable"}}}'
)

print(f"Crawler created: {response['Name']}")

# Start crawler
glue_client.start_crawler(Name='data-lake-crawler')
```

### Template DataHub metadata ingestion (YAML)
```yaml
# datahub_ingestion.yml
source:
  type: postgres
  config:
    host_port: localhost:5432
    database: analytics
    username: ${POSTGRES_USER}
    password: ${POSTGRES_PASSWORD}
    include_tables: true
    include_views: true
    profiling:
      enabled: true
      profile_table_level_only: false  # Column-level profiling
    
sink:
  type: datahub-rest
  config:
    server: http://datahub-gms:8080

# Run ingestion
# datahub ingest -c datahub_ingestion.yml
```

### Template OpenLineage event (JSON)
```json
{
  "eventType": "COMPLETE",
  "eventTime": "2024-01-15T10:30:00.000Z",
  "run": {
    "runId": "550e8400-e29b-41d4-a716-446655440000",
    "facets": {
      "nominalTime": {
        "nominalStartTime": "2024-01-15T00:00:00.000Z",
        "nominalEndTime": "2024-01-15T23:59:59.000Z"
      }
    }
  },
  "job": {
    "namespace": "my-data-platform",
    "name": "orders_etl_pipeline",
    "facets": {
      "documentation": {
        "description": "ETL pipeline transforming orders from bronze to gold"
      },
      "sourceCode": {
        "language": "python",
        "sourceCode": "https://github.com/org/repo/blob/main/pipelines/orders_etl.py"
      }
    }
  },
  "inputs": [
    {
      "namespace": "postgres",
      "name": "analytics.bronze.orders",
      "facets": {
        "schema": {
          "fields": [
            {"name": "order_id", "type": "VARCHAR"},
            {"name": "user_id", "type": "VARCHAR"},
            {"name": "amount", "type": "DECIMAL"}
          ]
        },
        "dataQuality": {
          "rowCount": 10523,
          "bytes": 1048576
        }
      }
    }
  ],
  "outputs": [
    {
      "namespace": "s3",
      "name": "data-lake.gold.orders",
      "facets": {
        "schema": {
          "fields": [
            {"name": "order_id", "type": "string"},
            {"name": "user_id", "type": "string"},
            {"name": "total_amount", "type": "decimal"},
            {"name": "order_date", "type": "date"}
          ]
        },
        "dataQuality": {
          "rowCount": 10523,
          "bytes": 524288
        },
        "columnLineage": {
          "fields": {
            "total_amount": {
              "inputFields": [
                {
                  "namespace": "postgres",
                  "name": "analytics.bronze.orders",
                  "field": "amount"
                }
              ],
              "transformationType": "IDENTITY",
              "transformationDescription": "SUM(amount)"
            }
          }
        }
      }
    }
  ]
}
```

### Template classification PII (Python script)
```python
import re

def classify_column_pii(column_name, sample_values):
    """
    Detect PII columns based on name patterns and sample values
    Returns: 'PII', 'SENSITIVE', 'PUBLIC'
    """
    
    # Patterns PII
    pii_patterns = {
        'email': r'[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}',
        'phone': r'\+?\d{10,15}',
        'ssn': r'\d{3}-\d{2}-\d{4}',
        'credit_card': r'\d{4}[\s-]?\d{4}[\s-]?\d{4}[\s-]?\d{4}'
    }
    
    column_lower = column_name.lower()
    
    # Check column name
    if any(keyword in column_lower for keyword in ['email', 'mail', 'e-mail']):
        return 'PII'
    if any(keyword in column_lower for keyword in ['phone', 'mobile', 'tel', 'telephone']):
        return 'PII'
    if any(keyword in column_lower for keyword in ['ssn', 'social_security', 'passport', 'driver_license']):
        return 'PII'
    if any(keyword in column_lower for keyword in ['address', 'street', 'city', 'zip', 'postal']):
        return 'PII'
    if any(keyword in column_lower for keyword in ['credit_card', 'card_number', 'cvv', 'card_holder']):
        return 'PII'
    
    # Check sample values (first 100 rows)
    for value in sample_values[:100]:
        if value is None:
            continue
        value_str = str(value)
        
        # Test regex patterns
        for pii_type, pattern in pii_patterns.items():
            if re.match(pattern, value_str):
                return 'PII'
    
    # Sensitive but not PII
    if any(keyword in column_lower for keyword in ['salary', 'income', 'revenue', 'password', 'secret']):
        return 'SENSITIVE'
    
    return 'PUBLIC'

# Usage
import pandas as pd

df = pd.read_parquet("data/customers.parquet")

for col in df.columns:
    classification = classify_column_pii(col, df[col].dropna().tolist())
    print(f"{col}: {classification}")
    
    # Tag in Glue Catalog or DataHub
    if classification == 'PII':
        # glue_client.tag_resource(...) or datahub API call
        pass
```

## Checklist QA interne
- [ ] Un inventaire complet des sources est-il disponible (tables, fichiers, APIs) ?
- [ ] Chaque dataset a-t-il un owner technique ET business documenté ?
- [ ] Les colonnes PII sont-elles identifiées et classifiées (tags) ?
- [ ] Un glossaire métier est-il créé avec définitions des termes clés ?
- [ ] Le lineage est-il capturé (table-level minimum) et à jour (<24h) ?
- [ ] Les tables critiques (top 20%) ont-elles des descriptions complètes ?
- [ ] Un workflow de demande d'accès est-il en place ?
- [ ] Les changements métadonnées sont-ils audités (qui, quand, quoi) ?
- [ ] Un impact analysis est-il effectué avant breaking changes ?
- [ ] Le catalogue est-il accessible et utilisé par les équipes (formation faite) ?

## KPI
- **Couverture métadonnées** : (tables documentées / total tables) × 100, cible >80%
- **Taux ownership** : (tables avec owner / total tables) × 100, cible 100%
- **Taux classification PII** : (colonnes PII taggées / total colonnes PII détectées) × 100, cible 100%
- **Adoption catalogue** : utilisateurs actifs/mois, requêtes de recherche/mois, cible +20%/trimestre
- **Fraîcheur lineage** : âge moyen lineage (heures depuis dernière MAJ), cible <24h
- **Qualité descriptions** : longueur moyenne descriptions tables critiques, cible ≥50 caractères

## Definition of done
- ✅ Catalogue initialisé (AWS Glue Catalog, DataHub, ou autre) avec inventaire complet
- ✅ Crawlers automatiques configurés (quotidien) pour MAJ métadonnées
- ✅ Owners documentés (technique + business) pour 100% tables critiques
- ✅ Classification PII appliquée sur toutes colonnes contenant données personnelles
- ✅ Glossaire métier créé avec définitions termes clés (KPI, métriques)
- ✅ Lineage capturé (table-level minimum) et visualisable (graph)
- ✅ Workflow demande accès configuré avec auto-approval ou validation
- ✅ Audit trail activé (changements métadonnées tracés)
- ✅ Formation équipes effectuée (recherche catalogue, consultation lineage)
- ✅ Métriques adoption monitorées (utilisateurs actifs, requêtes recherche)

## Exemples

### Exemple 1 : Data catalog e-commerce (AWS Glue + DataHub)
**Contexte** : 200 tables data lake S3, besoin découvrabilité pour équipes analytics.

**Mise en place** :
1. Crawler AWS Glue scan quotidien S3 bronze/silver/gold
2. Métadonnées exportées vers DataHub (API)
3. Owners assignés par domain (marketing, finance, ops)
4. Classification PII sur colonnes email, phone, address
5. Glossaire : "MRR" = Monthly Recurring Revenue, "CAC" = Customer Acquisition Cost

**Résultat** : Temps découverte datasets réduit de 2h → 10min, self-service analytics +40%, conformité RGPD facilitée.

---

### Exemple 2 : Lineage column-level (OpenLineage + Marquez)
**Contexte** : Pipeline Airflow complexe (15 DAGs, 50 transformations), besoin impact analysis.

**Implémentation** :
1. Instrumentation OpenLineage dans chaque DAG Airflow
2. Events lineage publiés vers Marquez (API)
3. Graph lineage visualisé : source PostgreSQL → silver Parquet → gold Delta → BI dashboard
4. Column-level lineage : "total_revenue" dashboard ← SUM(amount) gold ← amount silver ← amount bronze

**Résultat** : Impact analysis avant suppression colonne "discount" → identifié 3 dashboards impactés → migration planifiée.

---

### Exemple 3 : Gouvernance RGPD (Azure Purview)
**Contexte** : Conformité RGPD, droit à l'oubli (right to erasure), traçabilité données personnelles.

**Mise en place** :
1. Scan Azure Purview sur ADLS Gen2, Azure SQL, Synapse
2. Classification automatique PII (ML-based) + validation manuelle
3. Lineage end-to-end : CRM → data lake → analytics → BI
4. Procédure erasure : requête utilisateur → identification toutes occurrences via lineage → suppression coordonnée

**Résultat** : Conformité RGPD validée (audit externe), délai traitement demande erasure réduit de 5j → 1j.

## Contraintes
- **Volumétrie max** : Ce skill couvre catalogues jusqu'à 10K+ tables. Au-delà, optimiser crawlers (sampling, partitioning).
- **Lineage complexe** : Transformations custom (UDF, code Python) nécessitent instrumentation manuelle OpenLineage.
- **Gouvernance organisationnelle** : Politiques d'accès, workflow approbation → l'agent de conformité RGPD pour volet juridique.
- **Infrastructure catalog** : Déploiement, scaling, HA du catalogue → l'agent d'architecture cloud.

## Exemples d'usage

### Exemple 1 : Tracer l'origine d'un indicateur financier
**Contexte** : Les équipes ne s'accordent pas sur la source d'un indicateur affiché dans plusieurs tableaux de bord.  
**Input** : Tables sources, transformations SQL/ETL, rapport consommateur, définitions métier et owners connus.  
**Output** : Chaîne de lineage source→transformations→rapport, métadonnées et responsables manquants, et liste des impacts à vérifier avant toute modification.

### Exemple 2 : Repérer les jeux de données contenant des coordonnées personnelles
**Contexte** : Une revue de conformité doit identifier les datasets où peuvent se trouver des adresses électroniques et documenter leur usage.  
**Input** : Inventaire des sources, schémas/colonnes, descriptions disponibles et règles de classification approuvées.  
**Output** : Candidats à classifier avec provenance et owner proposés, lineage des usages aval et éléments à faire confirmer par les responsables conformité et données.

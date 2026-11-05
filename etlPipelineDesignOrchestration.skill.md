# ETL Pipeline Design & Orchestration

## Objectif
Concevoir, implémenter et orchestrer des pipelines ETL/ELT robustes, maintenables et performants pour l'ingestion, la transformation et le chargement de données à grande échelle.

## Quand l'utiliser (triggers)
- Conception d'un pipeline d'ingestion de données (batch ou near real-time)
- Orchestration de workflows data avec Airflow, Prefect, Dagster ou Azure Data Factory
- Transformation de données brutes vers modèles analytics (staging → warehouse → marts)
- Migration de pipelines legacy vers architecture moderne (ex: ETL on-prem → cloud ELT)
- Optimisation de pipelines existants (performance, coûts, résilience)
- Mise en place de dépendances inter-tâches et gestion d'erreurs

## Hors périmètre
- ❌ Analyse métier et définition KPI → l'agent d'analyse de données
- ❌ Architecture cloud infrastructure → l'agent d'architecture cloud
- ❌ Modélisation de schéma BDD → l'agent bases de données
- ❌ Pipelines ML (feature engineering, training) → l'agent de machine learning
- ❌ Streaming temps réel complexe → streamingDataProcessing.skill.md

## Inputs requis
- **Source de données** : type (API, fichiers, BDD, streaming), format, volumétrie, fréquence de refresh
- **Destination** : data warehouse, data lake, format cible (Parquet, Delta, Iceberg)
- **Transformations attendues** : nettoyage, agrégation, enrichissement, dénormalisation
- **agent de coordination cible** : Airflow, Prefect, Dagster, Azure Data Factory, AWS Glue
- **Contraintes** : SLA (latence max), budget, dépendances upstream/downstream

## Sorties attendues
- **DAG Airflow/Prefect/Dagster** : code Python structuré avec tasks, dépendances, retries, alerting
- **Scripts de transformation** : Python/PySpark/SQL selon volumétrie et complexité
- **Documentation pipeline** : architecture (Mermaid), SLA, backfill, monitoring
- **Tests unitaires** : validation transformations, gestion erreurs, idempotence
- **Config CI/CD** : déploiement automatisé du pipeline (GitOps)

## Workflow recommandé
1. **Analyse des sources** :
   - Profiler les données sources (volumétrie, distribution, qualité)
   - Identifier les clés de partitionnement et d'incrémentialité
   - Documenter le schéma source et les transformations attendues

2. **Design du pipeline** :
   - Choisir l'approche (ETL vs ELT, batch vs micro-batch)
   - Définir les couches (bronze/silver/gold ou staging/warehouse/marts)
   - Spécifier les transformations par étape avec dépendances

3. **Implémentation** :
   - Coder les tasks (Python/PySpark/SQL) avec gestion d'erreurs
   - Structurer le DAG avec dépendances, retries, timeouts
   - Ajouter logs structurés et métriques (durée, rows processed, erreurs)

4. **Tests et validation** :
   - Tests unitaires (transformations, edge cases, données invalides)
   - Tests d'intégration (pipeline end-to-end sur données de test)
   - Validation idempotence (relance du pipeline = même résultat)

5. **Déploiement et monitoring** :
   - Déployer via CI/CD (git push → tests → deploy)
   - Configurer alerting (SLA breach, erreurs, anomalies volumétrie)
   - Documenter procédure de backfill et rollback

## Garde-fous
- **GF1 - Idempotence obligatoire** : Tout pipeline doit être re-exécutable sans effet de bord (upsert, deduplication, clés naturelles). Preuve : relancer 2 fois le pipeline sur les mêmes données = même résultat final.
- **GF2 - Gestion explicite des erreurs** : Chaque task doit avoir une stratégie définie (retry, fail, skip, alert). Interdire les `try/except` silencieux sans log. Mesure : 100% des tasks ont `retries`, `retry_delay` et `on_failure_callback`.
- **GF3 - Partitionnement par date** : Pipelines batch doivent traiter par partition (jour, heure) pour permettre backfill ciblé. Interdire les `SELECT * FROM table` sans filtre date. Mesure : 0 requête full-scan en production.
- **GF4 - SLA documenté** : Chaque pipeline critique doit avoir un SLA (ex: "données J-1 disponibles avant 8h"). Mesure : SLA formalisé dans le code (ex: Airflow SLA miss callback).
- **GF5 - Logs structurés** : Utiliser logging JSON avec contexte (pipeline_name, task_id, run_date, row_count). Interdire `print()`. Mesure : 100% logs parsables par outil monitoring (Datadog, ELK).
- **GF6 - Séparation environnements** : Dev/Staging/Prod doivent avoir des DAGs séparés (pas de if/else sur env dans le code). Mesure : 0 condition `if ENV == "prod"` dans le DAG.
- **GF7 - Coût monitoring** : Pipelines cloud doivent tracker les coûts (Glue DPU, BigQuery slots). Alerter si coût > budget. Mesure : dashboard coût par pipeline disponible.

## Template d'entrée (copier/coller)
```text
[Besoin de pipeline]
- Sources, destinations, formats et owners : ...
- Volumes, fréquence, latence et fenêtres de traitement : ...
- Transformations/règles métier et qualité attendue : ...
- Contraintes d'accès, sécurité, reprise et coûts : ...
```

## Template de sortie (copier/coller)
```text
[Design ETL/ELT]
- Étapes d'extraction, transformation et chargement : ...
- Orchestration, dépendances et idempotence : ...
- Contrôles qualité, retries, reprise et alertes : ...
- Tests, observabilité, owner et critères d'acceptation : ...
```

## Templates copier/coller

### Template DAG Airflow (Python)
```python
from airflow import DAG
from airflow.operators.python import PythonOperator
from airflow.providers.postgres.hooks.postgres import PostgresHook
from datetime import datetime, timedelta
import logging

logger = logging.getLogger(__name__)

default_args = {
    'owner': 'data-engineer',
    'depends_on_past': False,
    'email_on_failure': True,
    'email_on_retry': False,
    'retries': 2,
    'retry_delay': timedelta(minutes=5),
}

def extract_data(ds, **context):
    """Extract data from source (idempotent)"""
    logger.info(f"Extracting data for {ds}")
    # Extraction logic with date partition
    hook = PostgresHook(postgres_conn_id='source_db')
    sql = f"""
        SELECT * FROM source_table
        WHERE event_date = '{ds}'
    """
    rows = hook.get_records(sql)
    logger.info(f"Extracted {len(rows)} rows for {ds}")
    return rows

def transform_data(ti, ds, **context):
    """Transform data (idempotent)"""
    rows = ti.xcom_pull(task_ids='extract')
    logger.info(f"Transforming {len(rows)} rows for {ds}")
    # Transformation logic
    transformed = [
        {'id': r[0], 'value': r[1] * 2, 'date': ds}
        for r in rows
    ]
    logger.info(f"Transformed {len(transformed)} rows")
    return transformed

def load_data(ti, ds, **context):
    """Load data to warehouse (upsert for idempotence)"""
    data = ti.xcom_pull(task_ids='transform')
    logger.info(f"Loading {len(data)} rows for {ds}")
    hook = PostgresHook(postgres_conn_id='warehouse_db')
    # Upsert logic (idempotent)
    hook.run(f"DELETE FROM target_table WHERE date = '{ds}'")
    hook.insert_rows('target_table', data, target_fields=['id', 'value', 'date'])
    logger.info(f"Loaded {len(data)} rows for {ds}")

with DAG(
    'example_etl_pipeline',
    default_args=default_args,
    description='Extract, Transform, Load pipeline example',
    schedule_interval='0 2 * * *',  # Daily at 2 AM
    start_date=datetime(2024, 1, 1),
    catchup=False,
    tags=['etl', 'example'],
) as dag:
    
    extract = PythonOperator(
        task_id='extract',
        python_callable=extract_data,
    )
    
    transform = PythonOperator(
        task_id='transform',
        python_callable=transform_data,
    )
    
    load = PythonOperator(
        task_id='load',
        python_callable=load_data,
    )
    
    extract >> transform >> load
```

### Template transformation PySpark (ELT)
```python
from pyspark.sql import SparkSession
from pyspark.sql.functions import col, to_date, current_timestamp
import logging

logger = logging.getLogger(__name__)

def transform_bronze_to_silver(spark, input_path, output_path, partition_date):
    """
    Transform bronze (raw) to silver (cleaned) layer
    Idempotent: overwrites partition
    """
    logger.info(f"Processing partition {partition_date}")
    
    # Read bronze data (partitioned by date)
    df_bronze = spark.read.parquet(f"{input_path}/date={partition_date}")
    
    logger.info(f"Read {df_bronze.count()} rows from bronze")
    
    # Transformations
    df_silver = (df_bronze
        .filter(col("status") == "active")  # Filter invalid rows
        .withColumn("processed_at", current_timestamp())
        .withColumn("date", to_date(col("event_timestamp")))
        .dropDuplicates(["id"])  # Deduplication
    )
    
    logger.info(f"Transformed to {df_silver.count()} rows")
    
    # Write to silver (partition overwrite mode = idempotent)
    (df_silver.write
        .mode("overwrite")
        .partitionBy("date")
        .parquet(f"{output_path}/date={partition_date}")
    )
    
    logger.info(f"Wrote partition {partition_date} to silver")

if __name__ == "__main__":
    spark = SparkSession.builder.appName("bronze_to_silver").getOrCreate()
    transform_bronze_to_silver(
        spark,
        input_path="s3://data-lake/bronze/events",
        output_path="s3://data-lake/silver/events",
        partition_date="2024-01-15"
    )
```

### Template config Azure Data Factory (JSON)
```json
{
  "name": "CopyPipeline",
  "properties": {
    "activities": [
      {
        "name": "CopyFromBlobToSQL",
        "type": "Copy",
        "inputs": [
          {
            "referenceName": "SourceBlobDataset",
            "type": "DatasetReference"
          }
        ],
        "outputs": [
          {
            "referenceName": "SinkSQLDataset",
            "type": "DatasetReference"
          }
        ],
        "typeProperties": {
          "source": {
            "type": "DelimitedTextSource",
            "storeSettings": {
              "type": "AzureBlobStorageReadSettings",
              "recursive": true,
              "wildcardFileName": "*.csv"
            }
          },
          "sink": {
            "type": "AzureSqlSink",
            "writeBehavior": "upsert",
            "upsertSettings": {
              "useTempDB": true,
              "keys": ["id"]
            }
          },
          "enableStaging": false,
          "parallelCopies": 4
        }
      }
    ],
    "parameters": {
      "sourceContainer": {
        "type": "string"
      },
      "sinkTable": {
        "type": "string"
      }
    }
  }
}
```

## Checklist QA interne
- [ ] Le pipeline est-il idempotent ? (relancer 2 fois = même résultat)
- [ ] Chaque task a-t-elle une stratégie d'erreur définie ? (retries, on_failure_callback)
- [ ] Le pipeline traite-t-il par partition (date) pour permettre backfill ?
- [ ] Les logs sont-ils structurés (JSON) avec contexte (pipeline, task, date, row_count) ?
- [ ] Un SLA est-il documenté et implémenté (si pipeline critique) ?
- [ ] Les transformations ont-elles des tests unitaires ?
- [ ] Le pipeline a-t-il été testé en intégration end-to-end ?
- [ ] La documentation inclut-elle un diagramme d'architecture (Mermaid) ?
- [ ] Le déploiement est-il automatisé via CI/CD ?
- [ ] Les coûts sont-ils monitorés (si cloud) ?

## KPI
- **Taux de succès** : (runs réussis / runs totaux) × 100, cible ≥ 95%
- **Respect SLA** : (runs dans SLA / runs totaux) × 100, cible 100%
- **Durée médiane** : temps médian d'exécution du pipeline, suivre régression
- **Coût par GB ingéré** : coût total / volumétrie traitée, optimiser si ↑
- **Taux de retraitement** : (backfills / runs totaux) × 100, cible < 5%
- **Couverture tests** : (transformations testées / transformations totales) × 100, cible ≥ 80%

## Definition of done
- ✅ DAG/pipeline déployé en production avec schedule actif
- ✅ Tests unitaires et d'intégration passent (couverture ≥ 80%)
- ✅ Idempotence validée (relance manuelle = résultat identique)
- ✅ SLA documenté et alerting configuré (si applicable)
- ✅ Logs structurés JSON émis avec contexte complet
- ✅ Documentation complète (architecture Mermaid, procédure backfill, monitoring)
- ✅ Pipeline exécuté avec succès sur 3 jours consécutifs (validation production)
- ✅ Coûts monitorés et dans budget (si cloud)

## Exemples

### Exemple 1 : Pipeline ETL daily batch (Airflow + PostgreSQL)
**Contexte** : Ingérer quotidiennement les commandes e-commerce depuis une BDD source vers un data warehouse pour analytics.

**Inputs** :
- Source : PostgreSQL `orders` table (100K lignes/jour)
- Destination : Snowflake warehouse
- Transformations : Enrichissement avec données clients, calcul metrics (total_amount, item_count)
- Schedule : Quotidien à 2h du matin
- SLA : Données J-1 disponibles avant 8h

**Pipeline Airflow** :
1. `extract_orders` : SELECT sur orders WHERE order_date = '{{ ds }}'
2. `enrich_with_customers` : JOIN avec table customers
3. `calculate_metrics` : Agrégations (total_amount, item_count)
4. `load_to_snowflake` : MERGE INTO (upsert) sur clé naturelle order_id
5. `validate_data_quality` : COUNT, CHECK constraints (total_amount > 0)

**Résultat** : Pipeline idempotent, SLA respecté (données dispo à 6h), alerting Slack en cas d'échec.

---

### Exemple 2 : Pipeline ELT cloud (AWS Glue + S3 + Athena)
**Contexte** : Ingérer des logs JSON depuis S3, transformer en format Parquet partitionné, requêtable via Athena.

**Inputs** :
- Source : S3 `s3://logs/raw/*.json` (10GB/jour)
- Destination : S3 `s3://logs/processed/` en Parquet
- Transformations : Parse JSON, extract fields, partition par date
- Schedule : Toutes les heures (near real-time)

**Glue Job (PySpark)** :
```python
df = spark.read.json("s3://logs/raw/2024-01-15/")
df_clean = df.select("timestamp", "user_id", "event_type", "properties")
df_clean.write.mode("overwrite").partitionBy("date").parquet("s3://logs/processed/")
```

**Résultat** : Logs disponibles dans Athena en <1h, coût réduit de 60% (Parquet vs JSON), requêtes 10x plus rapides.

---

### Exemple 3 : Pipeline incrémental CDC (Debezium + Kafka + Snowflake)
**Contexte** : Répliquer en temps réel les changements d'une BDD transactionnelle (PostgreSQL) vers Snowflake via Kafka.

**Inputs** :
- Source : PostgreSQL avec Debezium CDC
- Transport : Kafka topic `db.orders.changes`
- Destination : Snowflake table `orders_replica`
- Latence cible : <5 minutes

**Architecture** :
1. Debezium capture les changements (INSERT/UPDATE/DELETE) dans PostgreSQL
2. Événements publiés dans Kafka
3. Snowflake Kafka connector consomme et applique les changements (MERGE)

**Résultat** : Réplication quasi temps réel, latence médiane 2 min, zéro downtime.

## Contraintes
- **Volumétrie max** : Ce skill couvre pipelines jusqu'à plusieurs TB/jour. Au-delà, consulter l'agent d'architecture cloud pour architecture distribuée avancée.
- **Transformation complexe** : Logique métier lourde (ex: scoring, ML inference) → déléguer à l'agent de machine learning ou l'agent d'analyse de données selon contexte.
- **Streaming temps réel** : Pipelines sub-seconde (Kafka Streams, Flink) → streamingDataProcessing.skill.md.
- **Gouvernance données** : Catalogage, lineage, data quality rules → dataCatalogLineage.skill.md + dataQualityMonitoring.skill.md.

## Exemples d'usage

### Exemple 1 : Charger quotidiennement les commandes dans un entrepôt
**Contexte** : Les rapports de ventes utilisent des exports manuels et doivent être actualisés avant le début de journée.  
**Input** : Source transactionnelle, schéma cible, watermark/incrémental disponible, volume quotidien, SLA et règles de déduplication.  
**Output** : DAG avec extraction incrémentale, transformations isolées, chargement idempotent, tests sur données de référence et alertes en cas de retard.

### Exemple 2 : Rejouer une période après correction d'une transformation
**Contexte** : Une règle d'arrondi incorrecte a affecté quelques jours de données déjà chargées; le recalcul ne doit pas dupliquer les lignes.  
**Input** : Fenêtre de dates touchée, code et version concernés, clés de déduplication, destination et procédure de backfill.  
**Output** : Plan de rejeu borné et reproductible, contrôles avant/après, stratégie d'upsert et critères d'arrêt si les totaux diffèrent.

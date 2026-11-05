# Data Quality Monitoring

## Objectif
Implémenter des systèmes robustes de validation, monitoring et alerting de la qualité des données pour garantir fiabilité, complétude et exactitude des datasets en production (data pipelines, data lake, data warehouse).

## Quand l'utiliser (triggers)
- Mise en place de data quality checks sur pipelines ETL/ELT
- Validation de données après ingestion (schéma, complétude, cohérence)
- Monitoring continu de la qualité (drift detection, anomalies)
- Définition de SLA data quality (freshness, completeness, accuracy)
- Alert

ing automatique en cas de dégradation qualité
- Audit qualité pré-migration ou pré-release
- Profiling de nouveaux datasets (statistiques, distributions, outliers)

## Hors périmètre
- ❌ Pipelines ETL/ELT (orchestration, transformation) → etlPipelineDesignOrchestration.skill.md
- ❌ Gouvernance données (catalogues, lineage, ownership) → dataCatalogLineage.skill.md
- ❌ Architecture data lake/warehouse → dataLakeArchitectureStorage.skill.md
- ❌ Tests logiciels (unit, integration) → l'agent qualité
- ❌ Modélisation BDD (contraintes, indexes) → l'agent bases de données

## Inputs requis
- **Dataset cible** : table, fichier Parquet, topic Kafka, API endpoint
- **SLA qualité** : complétude >95%, fraîcheur <24h, accuracy >99%
- **Règles métier** : contraintes (email valide, montant >0, date cohérente)
- **Baseline** : statistiques historiques (volumétrie, distributions, null rate)
- **Seuils alerting** : déclenchement alert si complétude <90%, volumétrie -30%, etc.

## Sorties attendues
- **Data quality rules** : config Great Expectations, dbt tests, ou SQL constraints
- **Dashboard qualité** : Grafana, Tableau avec métriques (complétude, freshness, accuracy)
- **Alerting** : Slack/PagerDuty en cas de violation SLA
- **Rapport profiling** : statistiques (min/max/mean/median, distribution, outliers, null rate)
- **Documentation** : SLA data quality formalisé, procédure incident

## Workflow recommandé
1. **Profiling initial** :
   - Analyser le dataset (volumétrie, schéma, types, null rate, distributions)
   - Identifier les colonnes critiques (PK, FK, business keys)
   - Calculer baseline statistiques (volumétrie attendue, null rate acceptable)

2. **Définition des règles** :
   - Complétude : aucune colonne critique à NULL (ex: user_id, order_id)
   - Schéma : types corrects, colonnes requises présentes
   - Cohérence : relations logiques (end_date >= start_date, montant >0)
   - Unicité : PK sans duplicates
   - Freshness : données <24h (ou <1h selon SLA)

3. **Implémentation** :
   - Coder les checks (Great Expectations, dbt tests, SQL custom)
   - Intégrer dans le pipeline (fail si critical check échoue, warn si non-critical)
   - Exporter métriques vers monitoring (Prometheus, Datadog)

4. **Monitoring et alerting** :
   - Dashboard temps réel (complétude, freshness, volumétrie, anomalies)
   - Alertes configurées (Slack si complétude <90%, PagerDuty si critical check fail)
   - Historique tendances (drift detection)

5. **Amélioration continue** :
   - Analyser les incidents qualité (root cause, correction)
   - Ajuster baseline et seuils selon évolution métier
   - Ajouter nouvelles rules si patterns d'erreur détectés

## Garde-fous
- **GF1 - Critical checks bloquants** : Checks critical (schéma, PK duplicates) doivent FAIL le pipeline. Non-critical (null rate >seuil) = warning. Mesure : 100% critical checks = blocking.
- **GF2 - Baseline documentée** : Chaque dataset doit avoir baseline statistiques (volumétrie attendue, null rate, distributions). Mesure : 100% datasets avec baseline.
- **GF3 - SLA freshness** : Toute table analytics doit avoir SLA freshness (ex: <24h). Mesure : 100% tables avec SLA freshness défini.
- **GF4 - Alerting non-spam** : Seuils alerting ajustés pour éviter faux positifs (>3 alerts/jour = revoir seuils). Mesure : <3 alerts non-actionables/semaine.
- **GF5 - Metrics exportées** : Exporter métriques qualité vers système central (Prometheus, Datadog). Mesure : 100% pipelines avec métriques qualité exportées.
- **GF6 - Tests pré-prod** : Data quality checks doivent être testés en dev/staging avant prod. Mesure : 0 nouveau check déployé directement en prod.
- **GF7 - Ownership défini** : Chaque dataset doit avoir owner responsable qualité. Mesure : 100% datasets avec owner documenté.

## Template d'entrée (copier/coller)
```text
[Contexte qualité]
- Dataset/pipeline, propriétaire et consommateurs : ...
- Schéma, règles métier et niveau de qualité attendu : ...
- Fréquence, volumes et seuils d'alerte : ...
- Outils disponibles et contraintes d'accès : ...
```

## Template de sortie (copier/coller)
```text
[Résultat du contrôle]
- Règles et dimensions qualité vérifiées : ...
- Mesures observées, échantillon et période : ...
- Anomalies, seuils dépassés et impact : ...
- Alertes, owner, correction et suivi : ...
```

## Templates copier/coller

### Template Great Expectations suite (Python)
```python
import great_expectations as ge
from great_expectations.core.batch import BatchRequest

# Load dataset
context = ge.get_context()
batch_request = BatchRequest(
    datasource_name="my_datasource",
    data_connector_name="default_inferred_data_connector_name",
    data_asset_name="orders",
)
validator = context.get_validator(batch_request=batch_request)

# Expectations (data quality rules)
validator.expect_table_row_count_to_be_between(min_value=1000, max_value=100000)
validator.expect_column_values_to_not_be_null(column="order_id")
validator.expect_column_values_to_be_unique(column="order_id")
validator.expect_column_values_to_be_of_type(column="order_date", type_="datetime64")
validator.expect_column_values_to_be_between(column="amount", min_value=0, max_value=100000)
validator.expect_column_pair_values_a_to_be_greater_than_b(
    column_A="end_date", column_B="start_date"
)

# Run validation
results = validator.validate()

# Check results
if not results["success"]:
    print("❌ Data quality validation FAILED")
    for result in results["results"]:
        if not result["success"]:
            print(f"  - {result['expectation_config']['expectation_type']}")
    raise Exception("Data quality check failed")
else:
    print("✅ Data quality validation PASSED")

# Save expectations suite
validator.save_expectation_suite(discard_failed_expectations=False)
```

### Template dbt data tests (SQL)
```sql
-- models/orders.sql
SELECT
    order_id,
    user_id,
    order_date,
    amount,
    status
FROM {{ ref('stg_orders') }}

-- tests/orders_tests.yml
version: 2

models:
  - name: orders
    description: "Orders table with data quality tests"
    tests:
      - dbt_utils.expression_is_true:
          expression: "amount > 0"
      - dbt_utils.recency:
          datepart: day
          field: order_date
          interval: 1  # Data must be <1 day old
    
    columns:
      - name: order_id
        description: "Primary key"
        tests:
          - unique
          - not_null
      
      - name: user_id
        description: "Foreign key to users"
        tests:
          - not_null
          - relationships:
              to: ref('users')
              field: user_id
      
      - name: order_date
        tests:
          - not_null
          - dbt_utils.at_least_one
      
      - name: amount
        tests:
          - not_null
          - dbt_expectations.expect_column_values_to_be_between:
              min_value: 0
              max_value: 1000000
      
      - name: status
        tests:
          - accepted_values:
              values: ['pending', 'paid', 'shipped', 'delivered', 'cancelled']
```

### Template SQL custom checks (PostgreSQL)
```sql
-- Data quality checks SQL script
-- Run daily after ETL pipeline

-- Check 1: No NULL in critical columns
SELECT
    'orders' AS table_name,
    'order_id' AS column_name,
    COUNT(*) AS null_count,
    CASE WHEN COUNT(*) > 0 THEN 'FAIL' ELSE 'PASS' END AS status
FROM orders
WHERE order_id IS NULL

UNION ALL

SELECT
    'orders',
    'user_id',
    COUNT(*),
    CASE WHEN COUNT(*) > 0 THEN 'FAIL' ELSE 'PASS' END
FROM orders
WHERE user_id IS NULL;

-- Check 2: No duplicates on PK
SELECT
    'orders' AS table_name,
    'order_id' AS column_name,
    COUNT(*) - COUNT(DISTINCT order_id) AS duplicate_count,
    CASE WHEN COUNT(*) - COUNT(DISTINCT order_id) > 0 THEN 'FAIL' ELSE 'PASS' END AS status
FROM orders;

-- Check 3: Volumétrie dans range attendu (1K-100K rows/jour)
WITH daily_count AS (
    SELECT
        DATE(order_date) AS date,
        COUNT(*) AS row_count
    FROM orders
    WHERE order_date >= CURRENT_DATE - INTERVAL '1 day'
    GROUP BY DATE(order_date)
)
SELECT
    'orders' AS table_name,
    'row_count' AS metric,
    row_count,
    CASE
        WHEN row_count < 1000 THEN 'FAIL - Too few rows'
        WHEN row_count > 100000 THEN 'FAIL - Too many rows'
        ELSE 'PASS'
    END AS status
FROM daily_count;

-- Check 4: Freshness (données <24h)
SELECT
    'orders' AS table_name,
    'freshness' AS metric,
    MAX(order_date) AS latest_data,
    EXTRACT(EPOCH FROM (NOW() - MAX(order_date))) / 3600 AS hours_old,
    CASE
        WHEN EXTRACT(EPOCH FROM (NOW() - MAX(order_date))) / 3600 > 24 THEN 'FAIL'
        ELSE 'PASS'
    END AS status
FROM orders;

-- Check 5: Null rate acceptable (<5% sur colonnes non-critiques)
SELECT
    'orders' AS table_name,
    'phone' AS column_name,
    ROUND(100.0 * COUNT(*) FILTER (WHERE phone IS NULL) / COUNT(*), 2) AS null_rate_pct,
    CASE
        WHEN ROUND(100.0 * COUNT(*) FILTER (WHERE phone IS NULL) / COUNT(*), 2) > 5 THEN 'WARN'
        ELSE 'PASS'
    END AS status
FROM orders;
```

### Template profiling report (Python pandas)
```python
import pandas as pd
import numpy as np

def profile_dataset(df, name="dataset"):
    """Generate profiling report for a DataFrame"""
    
    report = {
        "dataset_name": name,
        "row_count": len(df),
        "column_count": len(df.columns),
        "memory_usage_mb": df.memory_usage(deep=True).sum() / 1024**2,
        "columns": {}
    }
    
    for col in df.columns:
        col_profile = {
            "dtype": str(df[col].dtype),
            "null_count": int(df[col].isnull().sum()),
            "null_rate_pct": round(100 * df[col].isnull().sum() / len(df), 2),
            "unique_count": int(df[col].nunique()),
            "unique_rate_pct": round(100 * df[col].nunique() / len(df), 2),
        }
        
        # Numeric columns: stats
        if pd.api.types.is_numeric_dtype(df[col]):
            col_profile.update({
                "min": float(df[col].min()),
                "max": float(df[col].max()),
                "mean": float(df[col].mean()),
                "median": float(df[col].median()),
                "std": float(df[col].std()),
                "q25": float(df[col].quantile(0.25)),
                "q75": float(df[col].quantile(0.75)),
            })
            
            # Outliers (IQR method)
            Q1 = df[col].quantile(0.25)
            Q3 = df[col].quantile(0.75)
            IQR = Q3 - Q1
            outliers = ((df[col] < Q1 - 1.5*IQR) | (df[col] > Q3 + 1.5*IQR)).sum()
            col_profile["outlier_count"] = int(outliers)
            col_profile["outlier_rate_pct"] = round(100 * outliers / len(df), 2)
        
        # Categorical columns: top values
        if pd.api.types.is_object_dtype(df[col]) or pd.api.types.is_categorical_dtype(df[col]):
            top_values = df[col].value_counts().head(5).to_dict()
            col_profile["top_5_values"] = {str(k): int(v) for k, v in top_values.items()}
        
        report["columns"][col] = col_profile
    
    return report

# Usage
df = pd.read_parquet("data/orders.parquet")
profile = profile_dataset(df, name="orders")

# Print report
import json
print(json.dumps(profile, indent=2))

# Flags quality issues
for col, stats in profile["columns"].items():
    if stats["null_rate_pct"] > 10:
        print(f"⚠️ {col}: High null rate ({stats['null_rate_pct']}%)")
    if stats.get("outlier_rate_pct", 0) > 5:
        print(f"⚠️ {col}: High outlier rate ({stats['outlier_rate_pct']}%)")
```

## Checklist QA interne
- [ ] Des data quality rules sont-elles définies pour complétude, schéma, cohérence, unicité ?
- [ ] Les checks critical bloquent-ils le pipeline en cas d'échec ?
- [ ] Un SLA freshness est-il défini et monitoré (ex: <24h) ?
- [ ] Une baseline statistiques est-elle documentée (volumétrie, null rate, distributions) ?
- [ ] Les métriques qualité sont-elles exportées vers système monitoring ?
- [ ] Un dashboard qualité existe-t-il (Grafana, Tableau) ?
- [ ] Des alertes sont-elles configurées (Slack, PagerDuty) avec seuils ajustés ?
- [ ] Les checks ont-ils été testés en dev/staging avant prod ?
- [ ] Un owner est-il défini pour chaque dataset critique ?
- [ ] Un runbook incident qualité est-il documenté ?

## KPI
- **Complétude** : (colonnes critiques non-NULL / total colonnes critiques) × 100, cible >95%
- **Freshness** : âge données (heures depuis dernière maj), cible <24h (ou <1h selon SLA)
- **Accuracy** : (rows valides / total rows) × 100 (validation rules métier), cible >99%
- **Volumétrie delta** : variation jour J vs J-1, alerter si >±30%
- **Null rate** : % NULL par colonne, suivre évolution, alerter si dérive >5 points
- **Taux incidents qualité** : (incidents qualité / total pipelines runs) × 100, cible <1%

## Definition of done
- ✅ Data quality rules implémentées (Great Expectations, dbt tests, ou SQL)
- ✅ Checks critical configurés en mode FAIL (bloquent pipeline)
- ✅ SLA freshness défini et monitoré (ex: <24h)
- ✅ Baseline statistiques documentée (volumétrie attendue, null rate, distributions)
- ✅ Dashboard qualité créé (Grafana/Tableau) avec métriques clés
- ✅ Alerting configuré (Slack/PagerDuty) avec seuils validés
- ✅ Métriques qualité exportées vers Prometheus/Datadog
- ✅ Tests qualité validés en dev/staging (3 jours sans faux positifs)
- ✅ Owner dataset documenté avec contact
- ✅ Runbook incident qualité rédigé (procédure si check fail)

## Exemples

### Exemple 1 : Validation orders table (dbt + Slack alerting)
**Contexte** : Table `orders` critique (analytics revenue), besoin qualité 99.9%.

**Data quality rules** :
- Complétude : order_id, user_id, order_date, amount NON NULL
- Unicité : order_id unique (PK)
- Cohérence : amount >0, order_date dans les 2 dernières années
- Freshness : données <24h
- Volumétrie : 1K-10K rows/jour

**Implémentation** : dbt tests (voir template ci-dessus) + Airflow sensor + Slack webhook si fail.

**Résultat** : Taux incidents qualité réduit de 80%, détection anomalies en <1h (vs 1 jour avant).

---

### Exemple 2 : Profiling nouveau dataset (Great Expectations)
**Contexte** : Intégration d'un nouveau partenaire avec dataset clients inconnu (10M rows).

**Profiling** :
1. Analyse initiale (pandas profiling) : 50 colonnes, null rate 0-40%, 5 colonnes avec outliers
2. Baseline : volumétrie 10M ±20%, null rate <30% acceptable sur colonnes non-critiques
3. Rules : email format valide (regex), phone 10 digits, age 0-120

**Résultat** : Détection de 15% emails invalides → correction à la source avant mise en prod.

---

### Exemple 3 : Monitoring drift detection (Prometheus + Grafana)
**Contexte** : Surveillance continue qualité sur data lake (100+ tables).

**Métriques exportées** :
- Complétude par table (gauge Prometheus)
- Freshness par table (age en heures)
- Volumétrie quotidienne (compteur)
- Null rate par colonne critique

**Dashboard Grafana** : Heatmap complétude toutes tables, alerte si <95%, graphique tendance volumétrie.

**Résultat** : Drift détecté sur table `events` (null rate passé de 2% à 15% en 1 semaine) → investigation révèle bug dans pipeline → fix appliqué.

## Contraintes
- **Volumétrie max** : Ce skill couvre datasets jusqu'à plusieurs TB. Au-delà, utiliser sampling statistique (Great Expectations sampling, dbt incremental checks).
- **Profiling big data** : Pour datasets >100GB, utiliser PySpark ou Dask pour profiling distribué.
- **Gouvernance avancée** : Catalogage, lineage, ownership → dataCatalogLineage.skill.md.
- **Tests logiciels** : Tests unitaires code → l'agent qualité.

## Exemples d'usage

### Exemple 1 : Surveiller la fraîcheur des données de commandes
**Contexte** : Un tableau de bord opérationnel affiche des commandes en retard parce que le chargement nocturne échoue parfois sans notification claire.  
**Input** : Table cible, horaire attendu, historique des chargements, propriétaire, seuil de fraîcheur et procédure d'escalade.  
**Output** : Contrôle de fraîcheur et de volumétrie, seuils d'avertissement/blocage, alerte actionnable et procédure de diagnostic avec owner.

### Exemple 2 : Contrôler les montants et identifiants après ingestion
**Contexte** : Des doublons de factures et des identifiants absents sont découverts par les analystes après la mise à jour des rapports.  
**Input** : Schéma, règles métier validées, baseline de volume/nulls, exemples anonymisés de défauts et criticité des colonnes.  
**Output** : Règles d'unicité, complétude et cohérence, sévérités distinctes, intégration préproduction et rapport d'anomalies traçable.

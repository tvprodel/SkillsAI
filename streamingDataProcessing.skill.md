# Streaming Data Processing

## Objectif
Concevoir, implémenter et opérer des pipelines de traitement de données en temps réel (sub-seconde à quelques minutes) avec Kafka, Flink, Spark Streaming ou Kinesis pour use cases nécessitant faible latence (alerting, monitoring, ML inference temps réel).

## Quand l'utiliser (triggers)
- Traitement d'événements en temps réel (clics web, IoT sensors, logs applicatifs)
- Architecture event-driven avec Kafka ou Kinesis comme backbone
- Transformation streaming (filtrage, agrégation fenêtrée, enrichissement)
- Détection d'anomalies temps réel (fraude, intrusion, défaillances)
- ML inference en temps réel (scoring, recommandations, prédictions)
- Réplication CDC (Change Data Capture) avec latence <1 minute
- Dashboards temps réel et metrics streaming

## Hors périmètre
- ❌ Batch processing (>1h latency) → etlPipelineDesignOrchestration.skill.md
- ❌ Architecture data lake → dataLakeArchitectureStorage.skill.md
- ❌ Infrastructure Kafka/Kinesis (broker setup, scaling) → l'agent d'architecture cloud
- ❌ ML model training → l'agent de machine learning
- ❌ Requêtes SQL analytics → l'agent bases de données

## Inputs requis
- **Source de données** : Kafka topics, Kinesis streams, event hubs, socket streams
- **Volumétrie** : events/sec (1K, 100K, 1M+), taille moyenne message (bytes)
- **Latence cible** : sub-seconde, <1min, <5min
- **Transformations** : filtrage, windowing (tumbling/sliding/session), join streams, enrichissement
- **Sink/destination** : Kafka, base de données, data lake, dashboard (Grafana, Kibana)
- **Contraintes** : exactly-once semantics, back-pressure, fault-tolerance

## Sorties attendues
- **Pipeline streaming** : code Flink/Spark Streaming/Kafka Streams
- **Config déploiement** : YAML Kubernetes, Docker Compose, ou cloud-managed config
- **Schéma Avro/Protobuf** : si serialisation structurée nécessaire
- **Monitoring** : métriques latence (P50/P95/P99), throughput, lag, erreurs
- **Documentation** : architecture (Mermaid), tuning parameters, runbook incidents

## Workflow recommandé
1. **Analyse du flux** :
   - Identifier la source (Kafka topic, Kinesis stream, API webhook)
   - Mesurer le throughput réel (events/sec, bytes/sec)
   - Définir la latence acceptable (sub-seconde, <1min, <5min)

2. **Design du pipeline** :
   - Choisir la techno (Flink si latence critique, Spark si cohabitant batch+stream, Kafka Streams si simple)
   - Définir les transformations (map, filter, aggregate, join)
   - Spécifier le windowing (tumbling 1min, sliding 5min, session timeout 10min)

3. **Implémentation** :
   - Coder le pipeline avec checkpointing (fault-tolerance)
   - Gérer le back-pressure (Kafka consumer lag, Flink watermarks)
   - Implémenter exactly-once semantics si requis (Flink + Kafka transactional)

4. **Tests et tuning** :
   - Tester avec volumétrie réelle (load testing)
   - Tuner le parallelism (Flink slots, Spark executors)
   - Mesurer latence end-to-end (P95, P99)

5. **Déploiement et monitoring** :
   - Déployer sur Kubernetes ou cloud-managed (AWS MSK, Azure Event Hubs)
   - Monitorer lag, throughput, latency, erreurs (Prometheus, Datadog)
   - Configurer alerting (lag >1min, erreurs >1%)

## Garde-fous
- **GF1 - Checkpointing obligatoire** : Tout pipeline Flink/Spark doit avoir checkpointing activé (fault-tolerance). Mesure : 100% des jobs avec checkpoint interval <5min.
- **GF2 - Watermarks pour event-time** : Utiliser event-time (timestamp événement) et non processing-time. Configurer watermarks pour gérer late events. Mesure : 0 job en processing-time sur données métier.
- **GF3 - Back-pressure monitoring** : Monitorer consumer lag Kafka (<1min acceptable, >5min critique). Alerter si lag croissant. Mesure : alerte si lag >seuil.
- **GF4 - Idempotence sink** : Sink (écriture destination) doit être idempotent (upsert, deduplication). Mesure : 0 duplicate en cas de replay.
- **GF5 - Schema registry** : Utiliser Avro/Protobuf + schema registry pour évolution schéma. Interdire JSON sans schéma. Mesure : 100% topics avec schéma.
- **GF6 - Parallelism adaptatif** : Ajuster parallelism selon throughput (auto-scaling si cloud). Mesure : utilisation CPU 60-80% (ni sous-utilisé, ni saturé).
- **GF7 - Latency SLA** : Définir SLA latency (ex: P95 <500ms) et alerter si dépassement. Mesure : P95 latency < SLA sur 24h.

## Template d'entrée (copier/coller)
```text
[Besoin de traitement streaming]
- Sources/topics, événements et schémas : ...
- Volume/throughput, pics et latence cible : ...
- Fenêtrage, état, garanties de livraison : ...
- Destinations, SLA, sécurité et rétention : ...
```

## Template de sortie (copier/coller)
```text
[Design streaming]
- Sources, transformations et sinks : ...
- Sémantique de livraison, état et reprise : ...
- Contrôles de qualité, monitoring et alertes : ...
- Tests de charge, limites et critères de mise en service : ...
```

## Templates copier/coller

### Template Flink streaming job (Python PyFlink)
```python
from pyflink.datastream import StreamExecutionEnvironment
from pyflink.datastream.connectors.kafka import FlinkKafkaConsumer, FlinkKafkaProducer
from pyflink.common.serialization import SimpleStringSchema
from pyflink.common.typeinfo import Types
import json

def process_event(event_str):
    """Transform event (filter, enrich, aggregate)"""
    event = json.loads(event_str)
    # Filtrage
    if event.get('status') != 'active':
        return None
    # Enrichissement
    event['processed_at'] = str(datetime.now())
    return json.dumps(event)

# Setup environment
env = StreamExecutionEnvironment.get_execution_environment()
env.enable_checkpointing(60000)  # Checkpoint every 60s (fault-tolerance)
env.set_parallelism(4)

# Kafka source
kafka_consumer = FlinkKafkaConsumer(
    topics='input-topic',
    deserialization_schema=SimpleStringSchema(),
    properties={
        'bootstrap.servers': 'kafka:9092',
        'group.id': 'flink-consumer-group',
        'auto.offset.reset': 'earliest'
    }
)

# Kafka sink
kafka_producer = FlinkKafkaProducer(
    topic='output-topic',
    serialization_schema=SimpleStringSchema(),
    producer_config={
        'bootstrap.servers': 'kafka:9092',
        'transaction.timeout.ms': '900000'  # Exactly-once semantics
    }
)

# Pipeline
(env.add_source(kafka_consumer)
    .map(process_event, output_type=Types.STRING())
    .filter(lambda x: x is not None)
    .add_sink(kafka_producer)
)

env.execute("Flink Streaming Job")
```

### Template Spark Structured Streaming (Scala)
```scala
import org.apache.spark.sql.SparkSession
import org.apache.spark.sql.functions._
import org.apache.spark.sql.streaming.Trigger

val spark = SparkSession.builder
  .appName("Spark Streaming")
  .config("spark.sql.shuffle.partitions", "4")
  .getOrCreate()

// Read from Kafka
val kafkaDF = spark.readStream
  .format("kafka")
  .option("kafka.bootstrap.servers", "kafka:9092")
  .option("subscribe", "input-topic")
  .option("startingOffsets", "earliest")
  .load()

// Transform
val processedDF = kafkaDF
  .selectExpr("CAST(value AS STRING) as json")
  .select(from_json(col("json"), schema).as("data"))
  .select("data.*")
  .filter(col("status") === "active")
  .withColumn("processed_at", current_timestamp())

// Write to Kafka (with checkpointing)
val query = processedDF
  .selectExpr("CAST(id AS STRING) as key", "to_json(struct(*)) as value")
  .writeStream
  .format("kafka")
  .option("kafka.bootstrap.servers", "kafka:9092")
  .option("topic", "output-topic")
  .option("checkpointLocation", "/tmp/checkpoint")
  .trigger(Trigger.ProcessingTime("10 seconds"))  // Micro-batch 10s
  .start()

query.awaitTermination()
```

### Template Kafka Streams (Java)
```java
import org.apache.kafka.streams.KafkaStreams;
import org.apache.kafka.streams.StreamsBuilder;
import org.apache.kafka.streams.kstream.*;
import java.time.Duration;

public class KafkaStreamsApp {
    public static void main(String[] args) {
        StreamsBuilder builder = new StreamsBuilder();
        
        // Read from topic
        KStream<String, String> source = builder.stream("input-topic");
        
        // Transform: filter + map
        KStream<String, String> processed = source
            .filter((key, value) -> value.contains("active"))
            .mapValues(value -> value.toUpperCase());
        
        // Windowed aggregation (tumbling 1 minute)
        KTable<Windowed<String>, Long> counts = processed
            .groupByKey()
            .windowedBy(TimeWindows.of(Duration.ofMinutes(1)))
            .count();
        
        // Write to topic
        processed.to("output-topic");
        
        // Start streams
        KafkaStreams streams = new KafkaStreams(builder.build(), getProperties());
        streams.start();
        
        Runtime.getRuntime().addShutdownHook(new Thread(streams::close));
    }
}
```

### Template windowing aggregation (Flink SQL)
```sql
-- Tumbling window: aggregate events in 1-minute non-overlapping windows
CREATE TABLE events (
    user_id STRING,
    event_type STRING,
    event_timestamp TIMESTAMP(3),
    WATERMARK FOR event_timestamp AS event_timestamp - INTERVAL '5' SECOND
) WITH (
    'connector' = 'kafka',
    'topic' = 'events',
    'properties.bootstrap.servers' = 'kafka:9092',
    'format' = 'json'
);

SELECT
    TUMBLE_START(event_timestamp, INTERVAL '1' MINUTE) as window_start,
    user_id,
    event_type,
    COUNT(*) as event_count
FROM events
GROUP BY
    TUMBLE(event_timestamp, INTERVAL '1' MINUTE),
    user_id,
    event_type;

-- Sliding window: 5-minute window, sliding every 1 minute (overlap)
SELECT
    HOP_START(event_timestamp, INTERVAL '1' MINUTE, INTERVAL '5' MINUTE) as window_start,
    event_type,
    COUNT(*) as event_count
FROM events
GROUP BY
    HOP(event_timestamp, INTERVAL '1' MINUTE, INTERVAL '5' MINUTE),
    event_type;

-- Session window: group events with max 10-minute gap between events
SELECT
    SESSION_START(event_timestamp, INTERVAL '10' MINUTE) as session_start,
    user_id,
    COUNT(*) as events_in_session
FROM events
GROUP BY
    SESSION(event_timestamp, INTERVAL '10' MINUTE),
    user_id;
```

## Checklist QA interne
- [ ] Le checkpointing est-il activé (Flink/Spark) avec interval <5min ?
- [ ] Les watermarks sont-ils configurés pour event-time processing ?
- [ ] Le consumer lag Kafka est-il monitoré avec alerting (seuil <1min) ?
- [ ] Le sink est-il idempotent (upsert, deduplication) ?
- [ ] Un schema registry est-il utilisé (Avro/Protobuf) ?
- [ ] Le parallelism est-il ajusté selon throughput (CPU 60-80%) ?
- [ ] La latency P95 est-elle mesurée et < SLA ?
- [ ] Un load testing a-t-il été effectué avec volumétrie réelle ?
- [ ] Un runbook incident est-il documenté (lag critique, job failure) ?
- [ ] Les métriques sont-elles exportées (Prometheus, Datadog) ?

## KPI
- **Latency P95/P99** : temps end-to-end (ingestion → sink), cible <500ms (P95), <1s (P99)
- **Throughput** : events/sec traités, suivre vs volumétrie source
- **Consumer lag** : délai entre dernière production Kafka et dernière consommation, cible <1min
- **Uptime** : % temps job actif sans erreur, cible >99.9%
- **Back-pressure rate** : % temps où le pipeline est ralenti par sink lent, cible <5%
- **Checkpoint duration** : temps pris par checkpoint Flink/Spark, cible <10s

## Definition of done
- ✅ Pipeline déployé en production avec checkpointing activé
- ✅ Watermarks configurés pour event-time processing (si applicable)
- ✅ Consumer lag Kafka monitoré avec alerting (<1min)
- ✅ Schema registry configuré (Avro/Protobuf) avec versioning
- ✅ Load testing validé à 1.5x volumétrie peak attendue
- ✅ Latency P95 mesurée et < SLA (ex: <500ms)
- ✅ Idempotence sink validée (replay = pas de duplicates)
- ✅ Runbook incident documenté (lag critique, job failure, back-pressure)
- ✅ Métriques exportées (Prometheus/Datadog) et dashboards créés
- ✅ Pipeline actif 24h sans erreur (validation stabilité)

## Exemples

### Exemple 1 : Real-time analytics dashboard (Kafka + Flink + Elasticsearch)
**Contexte** : Dashboard temps réel de métriques e-commerce (ventes, clics, conversions) avec latence <10s.

**Pipeline** :
1. Source : Kafka topic `clickstream` (10K events/sec)
2. Flink job : windowing tumbling 10s, agrégation par product_id
3. Sink : Elasticsearch index `metrics-realtime`
4. Viz : Kibana dashboard refresh 10s

**Résultat** : Latency P95 = 8s, dashboard utilisable pour monitoring live, alerte si conversion rate drop >20%.

---

### Exemple 2 : Fraud detection temps réel (Kinesis + Spark Streaming + ML)
**Contexte** : Détection fraude carte bancaire en temps réel avec scoring ML (latence <1s pour bloquer transaction).

**Pipeline** :
1. Source : Kinesis stream `transactions` (1K events/sec)
2. Spark Streaming : enrichissement (historique client), scoring ML (modèle pré-entraîné), seuil >0.8 = fraude
3. Sink : DynamoDB (transactions suspectes) + SNS alert

**Résultat** : Latency P95 = 700ms, taux détection fraude +30%, faux positifs -15%.

---

### Exemple 3 : CDC replication (Debezium + Kafka + Flink + PostgreSQL)
**Contexte** : Répliquer en temps réel les changements PostgreSQL source vers PostgreSQL replica (latency <30s).

**Pipeline** :
1. Debezium CDC capture changes dans PostgreSQL source
2. Kafka topic `db.orders.changes` (INSERT/UPDATE/DELETE events)
3. Flink job : parse CDC events, transform, MERGE INTO PostgreSQL replica
4. Monitoring : lag Kafka, latency replication

**Résultat** : Latency P95 = 25s, exactly-once semantics, zéro perte de données.

## Contraintes
- **Volumétrie max** : Ce skill couvre pipelines jusqu'à 1M events/sec. Au-delà, consulter l'agent d'architecture cloud pour architecture distribuée multi-cluster.
- **ML inference complexe** : Modèles lourds (deep learning) avec latence >100ms → l'agent de machine learning pour optimisation (quantization, batching).
- **Batch processing** : Latence >1h acceptable → etlPipelineDesignOrchestration.skill.md (plus simple et moins coûteux).
- **Infrastructure Kafka/Kinesis** : Scaling brokers, replication, monitoring cluster → l'agent d'architecture cloud.

## Exemples d'usage

### Exemple 1 : Détecter en temps quasi réel des transactions à examiner
**Contexte** : Une équipe doit repérer des transactions inhabituelles peu après leur émission, sans bloquer le flux comptable si l'analyse est indisponible.  
**Input** : Schéma d'événement approuvé, débit de pointe, latence cible, fenêtre temporelle, règles d'idempotence et destination des alertes.  
**Output** : Pipeline événementiel avec event-time/watermarks, checkpointing, sink dédupliqué, seuils de lag et scénario de reprise; les critères de détection restent fournis par le métier.

### Exemple 2 : Suivre la température d'équipements industriels
**Contexte** : Des capteurs envoient des mesures et l'équipe maintenance veut être alertée sur des dépassements persistants malgré des événements tardifs.  
**Input** : Format et fréquence des messages, identifiant équipement, seuils approuvés, tolérance aux retards, volume de pointe et canal d'alerte.  
**Output** : Fenêtrage event-time adapté, watermark documenté, traitement des doublons/retards, métriques de latence/lag et tests de panne/rejeu.

# SQL Analytics & Data Quality

## Objectif

Maîtriser les requêtes SQL analytiques avancées (agrégations, fenêtrage, CTE, sous-requêtes corrélées) pour extraire, transformer et analyser des données métier, tout en garantissant leur qualité (complétude, cohérence, exactitude). Produire des analyses ad-hoc robustes et documentées.

---

## Quand l'utiliser

- Extraction de données métier complexes (multi-tables, historiques, agrégations)
- Analyse ad-hoc sur demande métier ("combien de clients ont acheté X en Y mois ?")
- Audit de qualité des données (détection NULL, doublons, incohérences, outliers)
- Préparation de jeux de données pour dashboards ou exports
- Requêtes de cohérence inter-systèmes (CRM vs facturation vs stock)
- Calculs de métriques métier nécessitant logique SQL complexe (fenêtrage, récursif)
- Optimisation de requêtes lentes (>10s) sans changer le schéma base

**Déclencheurs** :
- "Extrais les clients ayant [critère complexe]"
- "Combien de [entité] entre [date1] et [date2] avec [filtre] ?"
- "Vérifie la qualité des données dans [table]"
- "Pourquoi ces deux requêtes donnent des résultats différents ?"
- "Optimise cette requête qui prend 45 secondes"

---

## Hors périmètre

- ❌ **Modélisation de schéma base (MCD/MLD/MPD, normalisation)** → l'agent bases de données
- ❌ **Création d'index, tuning moteur, plans d'exécution détaillés** → l'agent bases de données
- ❌ **Migration de schéma, scripts DDL réversibles** → l'agent bases de données
- ❌ **Architecture data warehouse/lake** → l'agent bases de données + l'agent d'architecture logicielle
- ❌ **Feature engineering pour ML** → l'agent de machine learning
- ❌ **Statistiques inférentielles pour ML (tests d'hypothèse, feature importance)** → l'agent data science
- ❌ **Visualisation de données** (dashboards, graphiques) → Skill précédent (Business KPI Analysis & Dashboard Design)

**Frontière l'agent bases de données** :
- l'agent d'analyse de données (ce skill) : Requêtes SQL analytiques (DML SELECT avancé), data quality, extractions ad-hoc
- L'agent bases de données : Schéma base (DDL), optimisation infrastructure (index, partitions, tuning moteur)

---

## Inputs requis

### Contexte métier
- **Question business** : Quelle question métier l'analyse doit-elle répondre ?
- **Niveau de précision** : Ordre de grandeur acceptable ou chiffre exact requis ?
- **Urgence** : Analyse ad-hoc immédiate ou étude approfondie sur 2-3 jours ?

### Accès aux données
- **SGBD** : PostgreSQL, MySQL, MariaDB, SQL Server, Oracle, BigQuery, Snowflake, Redshift
- **Droits SQL** : Read-only (SELECT) ou full (CREATE TEMP TABLE) ?
- **Schéma de données** : Diagramme ER ou documentation des tables disponibles
- **Volume** : <1k lignes, 1k-1M, 1M-100M, >100M (adapte stratégie selon volume)

### Critères de qualité attendue
- **Complétude** : Taux de NULL acceptable (<5%, <1%, 0%) ?
- **Cohérence** : Contraintes métier à vérifier (foreign keys, totaux, plages valides)
- **Fraîcheur** : Données à jour (temps-réel, J-1, J-7) ?

---

## Sorties attendues

### Livrables standards
1. **Requête SQL documentée** : Code SQL avec commentaires (objectif, logique, sources, filtres)
2. **Résultat de l'analyse** : Export CSV/Excel ou capture d'écran du résultat
3. **Rapport de qualité données** : % de complétude, doublons détectés, outliers, anomalies
4. **Recommandations** : Actions correctives si qualité <95% (nettoyage, investigation source)
5. **Métadonnées** : Date d'exécution, nombre de lignes retournées, temps d'exécution

### Format requête SQL standard
```sql
-- Titre: [Nom de l'analyse]
-- Objectif: [Question métier à répondre]
-- Auteur: l'agent d'analyse de données
-- Date: YYYY-MM-DD
-- SGBD: [PostgreSQL/MySQL/etc.]
-- Temps d'exécution estimé: [< 1s / 1-10s / > 10s]

-- [Logique détaillée de la requête en français]

WITH ... AS (...),
     ... AS (...)

SELECT ...
FROM ...
WHERE ...
GROUP BY ...
HAVING ...
ORDER BY ...
LIMIT ...;
```

---

## Workflow recommandé

### Phase 1 : Compréhension du besoin (15-30 min)
1. **Reformuler la question métier** en langage SQL mental (quelles tables, jointures, filtres ?)
2. **Identifier les sources de données** : Tables principales, tables de référence, tables d'historique
3. **Estimer la complexité** : Simple (1 table), moyen (2-3 tables + jointures), complexe (5+ tables, fenêtrage, récursif)

### Phase 2 : Exploration du schéma (15-45 min si schéma inconnu)
1. **Lister les tables pertinentes** :
   ```sql
   -- PostgreSQL
   SELECT table_name 
   FROM information_schema.tables 
   WHERE table_schema = 'public';
   ```
2. **Examiner la structure de chaque table** :
   ```sql
   \d table_name  -- PostgreSQL
   DESCRIBE table_name;  -- MySQL
   ```
3. **Vérifier les cardinalités** (combien de lignes par table ?) :
   ```sql
   SELECT COUNT(*) FROM table_name;
   ```
4. **Identifier les clés de jointure** : Primary keys, foreign keys, colonnes communes

### Phase 3 : Construction incrémentale de la requête (30 min - 2h)
**Principe** : Construire par couches successives (CTE), tester à chaque étape.

1. **CTE 1 - Base data** : Extraction brute avec filtres métier
   ```sql
   WITH base_data AS (
       SELECT * 
       FROM orders 
       WHERE order_date >= '2024-01-01'
   )
   SELECT * FROM base_data LIMIT 10;  -- Test
   ```

2. **CTE 2 - Enrichissement** : Jointures avec tables de référence
   ```sql
   WITH base_data AS (...),
        enriched AS (
            SELECT b.*, c.customer_name, p.product_name
            FROM base_data b
            JOIN customers c ON b.customer_id = c.id
            JOIN products p ON b.product_id = p.id
        )
   SELECT * FROM enriched LIMIT 10;  -- Test
   ```

3. **CTE 3 - Agrégations** : Calculs métier
   ```sql
   WITH ... ,
        aggregated AS (
            SELECT 
                customer_id,
                COUNT(*) AS order_count,
                SUM(total) AS revenue
            FROM enriched
            GROUP BY customer_id
        )
   SELECT * FROM aggregated ORDER BY revenue DESC LIMIT 10;  -- Test
   ```

4. **Requête finale** : Ajout des filtres finaux, tri, limite

### Phase 4 : Audit de qualité données (30 min - 1h)
1. **Détection NULL** :
   ```sql
   SELECT 
       COUNT(*) AS total_rows,
       COUNT(column1) AS non_null_column1,
       ROUND((COUNT(column1)::numeric / COUNT(*)) * 100, 2) AS completeness_pct
   FROM table_name;
   ```

2. **Détection doublons** :
   ```sql
   SELECT 
       key_column,
       COUNT(*) AS occurrence_count
   FROM table_name
   GROUP BY key_column
   HAVING COUNT(*) > 1;
   ```

3. **Détection outliers** (méthode IQR - InterQuartile Range) :
   ```sql
   WITH quartiles AS (
       SELECT 
           PERCENTILE_CONT(0.25) WITHIN GROUP (ORDER BY value) AS q1,
           PERCENTILE_CONT(0.75) WITHIN GROUP (ORDER BY value) AS q3
       FROM table_name
   ),
   bounds AS (
       SELECT 
           q1,
           q3,
           q3 - q1 AS iqr,
           q1 - 1.5 * (q3 - q1) AS lower_bound,
           q3 + 1.5 * (q3 - q1) AS upper_bound
       FROM quartiles
   )
   SELECT *
   FROM table_name, bounds
   WHERE value < lower_bound OR value > upper_bound;
   ```

4. **Cohérence inter-tables** :
   ```sql
   -- Vérifier que toutes les foreign keys existent
   SELECT DISTINCT o.customer_id
   FROM orders o
   LEFT JOIN customers c ON o.customer_id = c.id
   WHERE c.id IS NULL;  -- Devrait retourner 0 ligne
   ```

### Phase 5 : Optimisation si requête lente (>10s)
1. **Analyser le plan d'exécution** :
   ```sql
   EXPLAIN ANALYZE
   SELECT ... FROM ... WHERE ...;
   ```

2. **Identifier les goulots** : Sequential Scan sur grande table, Nested Loop coûteux

3. **Optimisations sans changer le schéma** :
   - Limiter les colonnes SELECT (éviter SELECT *)
   - Filtrer tôt (WHERE avant JOIN si possible)
   - Utiliser EXISTS au lieu de IN pour grandes tables
   - Matérialiser les CTE si réutilisées (WITH ... AS MATERIALIZED)
   - Partitionner la requête par plages de dates

4. **Signaler si index nécessaire** → Escalader vers l'agent bases de données

---

## Garde-fous

### GF1 - Test sur échantillon AVANT production
**Règle** : Toute requête sur table >1M lignes doit d'abord être testée avec LIMIT 1000.

**Justification** : Éviter de surcharger la base et bloquer les utilisateurs avec une requête mal optimisée.

**Mesure** : Chronométrer le temps d'exécution sur échantillon. Si >5s sur 1k lignes, optimiser avant de retirer le LIMIT.

**Preuve** : Log du temps d'exécution sur échantillon avant exécution full.

### GF2 - Documentation obligatoire des requêtes complexes
**Règle** : Toute requête avec >3 CTE ou >5 jointures doit avoir :
- Un bloc commentaire en-tête (objectif, auteur, date)
- Un commentaire par CTE expliquant sa logique
- La requête versionnée dans Git

**Justification** : Garantir la maintenabilité et la reproductibilité de l'analyse.

**Mesure** : Audit du fichier SQL (présence commentaires, versioning Git).

**Preuve** : Fichier .sql avec historique Git montrant commits documentés.

### GF3 - Validation croisée des résultats critiques
**Règle** : Pour toute analyse critique (décision business >10k€), valider le résultat par 2 méthodes différentes :
- Requête SQL A (méthode principale)
- Requête SQL B (approche alternative) OU export Excel avec formules OU requête sur outil BI

**Justification** : Détecter les erreurs de logique SQL avant qu'elles n'impactent une décision stratégique.

**Mesure** : Écart entre les 2 méthodes doit être <1%.

**Preuve** : Capture d'écran des 2 résultats avec delta calculé.

### GF4 - Rapport de qualité données obligatoire
**Règle** : Tout export de données pour analyse doit inclure un rapport de qualité :
- % de complétude (non-NULL)
- Nombre de doublons détectés
- Nombre d'outliers (>Q3 + 1.5*IQR)
- Période couverte (min/max dates)

**Justification** : Connaître les limites des données avant d'analyser évite les conclusions erronées.

**Mesure** : Checklist 4 métriques calculées et documentées.

**Preuve** : Section "Data Quality Report" en préambule de l'analyse.

### GF5 - Pas de modification de données en production
**Règle** : STRICTEMENT INTERDIT d'exécuter UPDATE, DELETE, TRUNCATE, DROP en production sans validation DBA.

**Justification** : Risque de perte de données irréversible.

**Mesure** : Auditer les requêtes exécutées (logs SQL).

**Preuve** : Toute requête DML de modification doit passer par l'agent bases de données avec validation + backup préalable.

---

## Template d'entrée (copier/coller)
```text
[Demande d'analyse SQL]
- Question métier et décision à soutenir : ...
- SGBD, schéma/tables et période : ...
- Définition des métriques et résultats attendus : ...
- Accès disponible, contraintes de volume/performance : ...
```

## Template de sortie (copier/coller)
```text
[Résultat d'analyse]
- Requête et hypothèses de calcul : ...
- Résultats avec période, périmètre et unités : ...
- Contrôles de qualité et limites : ...
- Interprétation, recommandations et validations requises : ...
```

## Templates copier/coller

### Template 1 : Requête SQL analytique standard

```sql
-- ============================================
-- Analyse: [Titre court de l'analyse]
-- ============================================
-- Objectif métier: [Question business à répondre]
-- Auteur: l'agent d'analyse de données
-- Date création: YYYY-MM-DD
-- Dernière mise à jour: YYYY-MM-DD
-- SGBD: [PostgreSQL 14 / MySQL 8 / etc.]
-- Temps d'exécution: [< 1s / 1-10s / > 10s]
-- Nombre de lignes: [~ estimation]
-- ============================================

-- CTE 1: Extraction base de données brutes
WITH base_data AS (
    SELECT 
        -- Colonnes nécessaires uniquement (éviter SELECT *)
        id,
        created_at,
        customer_id,
        total_amount,
        status
    FROM orders
    WHERE 
        -- Filtres métier
        created_at >= '2024-01-01'
        AND status IN ('completed', 'shipped')
        -- Filtrer tôt pour réduire le volume
),

-- CTE 2: Enrichissement avec données de référence
enriched_data AS (
    SELECT 
        b.*,
        c.customer_name,
        c.segment,
        c.country
    FROM base_data b
    INNER JOIN customers c ON b.customer_id = c.id
    -- Jointure INNER si foreign key garantie, LEFT si nullable
),

-- CTE 3: Calculs métier et agrégations
aggregated_metrics AS (
    SELECT 
        segment,
        country,
        COUNT(DISTINCT customer_id) AS unique_customers,
        COUNT(*) AS total_orders,
        SUM(total_amount) AS total_revenue,
        AVG(total_amount) AS avg_order_value,
        -- Fenêtrage pour ranking
        ROW_NUMBER() OVER (PARTITION BY segment ORDER BY SUM(total_amount) DESC) AS rank_in_segment
    FROM enriched_data
    GROUP BY segment, country
)

-- Requête finale: Tri et limite
SELECT 
    segment,
    country,
    unique_customers,
    total_orders,
    ROUND(total_revenue::numeric, 2) AS total_revenue,
    ROUND(avg_order_value::numeric, 2) AS avg_order_value,
    rank_in_segment
FROM aggregated_metrics
WHERE rank_in_segment <= 10  -- Top 10 par segment
ORDER BY total_revenue DESC;
```

### Template 2 : Audit qualité données

```sql
-- ============================================
-- Audit qualité données: [Nom table]
-- ============================================
-- Date: YYYY-MM-DD
-- Auteur: l'agent d'analyse de données
-- ============================================

-- 1. Complétude (% non-NULL)
SELECT 
    'completeness_check' AS check_type,
    COUNT(*) AS total_rows,
    COUNT(column1) AS non_null_column1,
    ROUND((COUNT(column1)::numeric / NULLIF(COUNT(*), 0)) * 100, 2) AS completeness_pct_column1,
    COUNT(column2) AS non_null_column2,
    ROUND((COUNT(column2)::numeric / NULLIF(COUNT(*), 0)) * 100, 2) AS completeness_pct_column2
FROM table_name;

-- 2. Doublons sur clé primaire
SELECT 
    'duplicates_check' AS check_type,
    primary_key_column,
    COUNT(*) AS occurrence_count
FROM table_name
GROUP BY primary_key_column
HAVING COUNT(*) > 1
ORDER BY occurrence_count DESC;

-- 3. Outliers (méthode IQR)
WITH quartiles AS (
    SELECT 
        PERCENTILE_CONT(0.25) WITHIN GROUP (ORDER BY numeric_column) AS q1,
        PERCENTILE_CONT(0.50) WITHIN GROUP (ORDER BY numeric_column) AS median,
        PERCENTILE_CONT(0.75) WITHIN GROUP (ORDER BY numeric_column) AS q3
    FROM table_name
),
bounds AS (
    SELECT 
        q1,
        q3,
        q3 - q1 AS iqr,
        q1 - 1.5 * (q3 - q1) AS lower_bound,
        q3 + 1.5 * (q3 - q1) AS upper_bound
    FROM quartiles
)
SELECT 
    'outliers_check' AS check_type,
    COUNT(*) AS outlier_count,
    MIN(numeric_column) AS min_value,
    MAX(numeric_column) AS max_value,
    (SELECT lower_bound FROM bounds) AS lower_bound,
    (SELECT upper_bound FROM bounds) AS upper_bound
FROM table_name, bounds
WHERE numeric_column < lower_bound OR numeric_column > upper_bound;

-- 4. Cohérence foreign keys
SELECT 
    'foreign_key_check' AS check_type,
    COUNT(*) AS orphan_rows
FROM table_child tc
LEFT JOIN table_parent tp ON tc.parent_id = tp.id
WHERE tp.id IS NULL;

-- 5. Période couverte
SELECT 
    'period_check' AS check_type,
    MIN(date_column) AS min_date,
    MAX(date_column) AS max_date,
    MAX(date_column) - MIN(date_column) AS period_days
FROM table_name;
```

### Template 3 : Rapport d'analyse SQL (Markdown)

```markdown
# Rapport d'Analyse SQL : [Titre]

**Date** : YYYY-MM-DD  
**Analyste** : l'agent d'analyse de données  
**Demandeur** : [Nom Stakeholder]

---

## Question métier

[Reformuler la question business en 1-2 phrases]

---

## Périmètre de l'analyse

- **Période** : [Date début] - [Date fin]
- **Sources de données** : [Liste des tables utilisées]
- **Filtres appliqués** : [Liste des critères métier]
- **Volume analysé** : [X lignes / Y transactions / Z clients]

---

## Méthodologie

[Expliquer brièvement la logique SQL utilisée, sans détailler le code]

Exemple :
1. Extraction des commandes complétées sur les 6 derniers mois
2. Enrichissement avec données clients (segment, pays)
3. Agrégation par segment et pays
4. Calcul du CA, nombre de commandes, panier moyen
5. Classement des top 10 par segment

---

## Qualité des données

| Métrique | Valeur | Commentaire |
|----------|--------|-------------|
| Complétude (champ X) | 98,5% | 1,5% de NULL détectés, impact négligeable |
| Doublons détectés | 0 | Aucun doublon sur clé primaire |
| Outliers identifiés | 12 | 12 commandes >10k€ (validées comme vraies ventes entreprise) |
| Période couverte | 2024-01-01 à 2024-06-30 | 181 jours |

**Conclusion qualité** : ✅ Données exploitables, qualité >95%

---

## Résultats clés

[Présenter les 3-5 insights principaux en bullet points]

- **Insight 1** : Le segment B2B représente 65% du CA mais seulement 20% des commandes
- **Insight 2** : Le panier moyen B2B (€425) est 8x supérieur au B2C (€52)
- **Insight 3** : La France et la Belgique totalisent 80% du CA total

---

## Données détaillées

[Tableau des résultats ou lien vers export CSV]

| Segment | Pays | Clients uniques | Commandes | CA (€) | Panier moyen (€) |
|---------|------|-----------------|-----------|--------|------------------|
| B2B | FR | 145 | 1,234 | 524,850 | 425.32 |
| B2B | BE | 78 | 687 | 289,100 | 420.87 |
| ... | ... | ... | ... | ... | ... |

**Export complet** : [Lien vers fichier CSV]

---

## Recommandations

[Actions business suggérées basées sur l'analyse]

1. **Action 1** : Investir davantage en acquisition B2B (ROI 8x supérieur au B2C)
2. **Action 2** : Créer des offres spécifiques FR/BE (80% du CA actuel)
3. **Action 3** : Investiguer les 12 commandes >10k€ pour comprendre les leviers de vente entreprise

---

## Annexes

### Requête SQL utilisée

```sql
[Coller la requête complète ici]
```

### Temps d'exécution

- **Échantillon (LIMIT 1000)** : 0,8s
- **Requête complète** : 4,2s

---

**Contact** : l'agent d'analyse de données - [email]
```

---

## Checklist QA interne

**Avant de livrer une analyse SQL, valider** :

### Requête SQL
- [ ] La requête a un bloc commentaire en-tête (objectif, auteur, date, SGBD, temps estimé)
- [ ] Chaque CTE a un commentaire expliquant sa logique
- [ ] La requête a été testée sur échantillon (LIMIT 1000) avant exécution complète
- [ ] Le plan d'exécution a été analysé si temps >10s (EXPLAIN ANALYZE)
- [ ] Aucune requête de modification (UPDATE, DELETE) n'a été exécutée sans validation DBA

### Qualité des données
- [ ] Le taux de complétude est calculé et documenté (>95% requis)
- [ ] Les doublons ont été détectés et traités (si applicables)
- [ ] Les outliers ont été identifiés et justifiés ou corrigés
- [ ] La cohérence des foreign keys a été vérifiée
- [ ] La période couverte est explicite (min/max dates)

### Documentation
- [ ] Un rapport d'analyse Markdown est produit (question, méthodologie, résultats, recommandations)
- [ ] La requête SQL est versionnée dans Git avec message de commit descriptif
- [ ] Un export CSV des résultats est fourni (si >100 lignes)
- [ ] Le temps d'exécution est documenté

### Validation croisée
- [ ] Les résultats critiques (décision >10k€) ont été validés par 2 méthodes indépendantes
- [ ] L'écart entre les 2 méthodes est <1%

---

## KPI de la skill

| KPI | Formule | Cible | Fréquence mesure |
|-----|---------|-------|------------------|
| Taux de qualité données | (Analyses avec qualité >95% / Analyses totales) x 100 | ≥ 90% | Mensuel |
| Taux de requêtes optimisées | (Requêtes <10s / Requêtes totales) x 100 | ≥ 80% | Mensuel |
| Taux de documentation complète | (Analyses avec rapport Markdown / Analyses totales) x 100 | 100% | Mensuel |
| Taux de validation croisée (analyses critiques) | (Analyses critiques validées 2x / Analyses critiques totales) x 100 | 100% | Mensuel |

---

## Definition of done

Une analyse SQL est considérée **terminée** si :

1. ✅ **Requête documentée** : Bloc commentaire en-tête + commentaire par CTE + versionnée Git
2. ✅ **Qualité données validée** : Rapport de qualité produit avec complétude >95%
3. ✅ **Performance acceptable** : Temps d'exécution <10s OU optimisation documentée si >10s
4. ✅ **Résultats livrés** : Rapport Markdown + export CSV (si applicable)
5. ✅ **Validation croisée** : Si analyse critique (>10k€), résultats validés par 2 méthodes avec écart <1%

---

## Exemples

### Exemple 1 : Analyse churn client

**Question** : Quels clients ont arrêté d'acheter depuis >90 jours mais étaient actifs avant ?

**Requête** :
```sql
WITH last_order AS (
    SELECT 
        customer_id,
        MAX(order_date) AS last_order_date,
        COUNT(*) AS lifetime_orders
    FROM orders
    WHERE status = 'completed'
    GROUP BY customer_id
),
churned_customers AS (
    SELECT 
        lo.*,
        CURRENT_DATE - lo.last_order_date AS days_since_last_order
    FROM last_order lo
    WHERE 
        lo.last_order_date < CURRENT_DATE - INTERVAL '90 days'
        AND lo.lifetime_orders >= 2  -- Actifs (au moins 2 commandes)
)
SELECT 
    cc.*,
    c.customer_name,
    c.email,
    c.segment
FROM churned_customers cc
JOIN customers c ON cc.customer_id = c.id
ORDER BY cc.lifetime_orders DESC;
```

**Résultat** : 347 clients churnés identifiés → campagne de réactivation email

### Exemple 2 : Audit qualité données produits

**Problème** : Incohérences entre stock théorique (ERP) et stock réel (inventaire)

**Requête** :
```sql
SELECT 
    p.product_id,
    p.product_name,
    erp.stock_quantity AS stock_erp,
    inv.stock_quantity AS stock_inventory,
    erp.stock_quantity - inv.stock_quantity AS delta,
    CASE 
        WHEN ABS(erp.stock_quantity - inv.stock_quantity) <= 5 THEN 'OK'
        WHEN ABS(erp.stock_quantity - inv.stock_quantity) <= 20 THEN 'Warning'
        ELSE 'Critical'
    END AS status
FROM products p
LEFT JOIN erp_stock erp ON p.product_id = erp.product_id
LEFT JOIN inventory inv ON p.product_id = inv.product_id
WHERE ABS(erp.stock_quantity - inv.stock_quantity) > 5
ORDER BY ABS(delta) DESC;
```

**Résultat** : 23 produits avec delta >20 unités → investigation logistique lancée

### Exemple 3 : Top produits par segment client

**Question** : Quels sont les 5 produits les plus vendus par segment client (B2B vs B2C) ?

**Requête** :
```sql
WITH sales_by_segment_product AS (
    SELECT 
        c.segment,
        p.product_name,
        SUM(oi.quantity) AS total_quantity,
        SUM(oi.quantity * oi.unit_price) AS total_revenue,
        ROW_NUMBER() OVER (PARTITION BY c.segment ORDER BY SUM(oi.quantity * oi.unit_price) DESC) AS rank
    FROM order_items oi
    JOIN orders o ON oi.order_id = o.id
    JOIN customers c ON o.customer_id = c.id
    JOIN products p ON oi.product_id = p.id
    WHERE o.order_date >= CURRENT_DATE - INTERVAL '6 months'
    GROUP BY c.segment, p.product_name
)
SELECT 
    segment,
    product_name,
    total_quantity,
    ROUND(total_revenue::numeric, 2) AS total_revenue,
    rank
FROM sales_by_segment_product
WHERE rank <= 5
ORDER BY segment, rank;
```

**Résultat** : Top 5 B2B ≠ Top 5 B2C → adapter l'assortiment catalogue par cible

---

## Contraintes

- **Read-only en production** : Aucune modification de données (UPDATE, DELETE, TRUNCATE) sans validation de l'agent bases de données + backup préalable
- **Limiter les exports volumétriques** : Éviter les exports >1M lignes en CSV (privilégier filtres ou agrégations)
- **Versioning obligatoire** : Toute requête réutilisable (>1 exécution) doit être versionnée dans Git
- **Respect RGPD** : Anonymiser ou masquer les données personnelles (email, téléphone, adresse) dans les exports

---

**Date de création** : 2026-08-04  
**Dernière mise à jour** : 2026-08-04  
**Agents propriétaires** : l'agent d'analyse de données

## Exemples d'usage

### Exemple 1 : Calculer les clients ayant renouvelé un abonnement
**Contexte** : Le métier veut mesurer les renouvellements mensuels sans compter plusieurs fois les modifications d'un même contrat.  
**Input** : Schéma des abonnements/événements, définition validée d'un renouvellement, période, fuseau horaire et droits SQL en lecture seule.  
**Output** : Requête documentée avec bornes temporelles, règles de déduplication et contrôles de rapprochement, ainsi que les limites de la définition métier.

### Exemple 2 : Comparer les totaux de facturation et de commandes
**Contexte** : Deux rapports donnent des montants différents pour le même mois de clôture.  
**Input** : Schémas disponibles, requêtes actuelles, définition du montant net, statuts inclus, devise et période concernée.  
**Output** : Requête de rapprochement non destructive, anomalies par catégorie (statut, devise, doublon, date), comptages de contrôle et hypothèses à confirmer avant correction des sources.

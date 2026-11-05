# Web Data Extraction & Structuring

## Objectif
Transformer des données brutes extraites du web (HTML parsé, réponses JSON d'API internes, résultats de scraping statique/dynamique) en jeux de données propres, normalisés et exportables (CSV/JSON/BDD).

## Quand l'utiliser (triggers)
- « structurer les données extraites », « normaliser », « export CSV/JSON », « nettoyer les données scrapées », « schéma de données scraping ».
- Après toute extraction (statique ou dynamique) nécessitant mise en forme avant exploitation.

## Hors périmètre
- Extraction brute elle-même → skills Static/Dynamic Web Scraping.
- Implémentation du code de transformation → **l'agent de développement back-end**.
- Pipeline de stockage final (data lake, warehouse, orchestration) → **l'agent d'ingénierie des données**.

## Inputs requis
- Données brutes extraites (échantillon représentatif).
- Schéma cible attendu (champs, types, contraintes).
- Format de sortie souhaité (CSV, JSON, JSON Lines, base de données).
- Règles de déduplication/normalisation métier (ex : formats de date, devises, unités).

## Sorties attendues
- Schéma de données normalisé (nom de champ, type, nullable, contrainte).
- Règles de nettoyage/normalisation documentées (trim, encodage, casse, formats).
- Stratégie de déduplication (clé unique, hash de contenu).
- Format d'export final et convention de nommage des fichiers.

## Workflow recommandé
1. Analyser un échantillon de données brutes pour identifier incohérences (encodage, valeurs manquantes, doublons).
2. Définir le schéma cible (types, contraintes, valeurs par défaut).
3. Spécifier les règles de normalisation (dates ISO 8601, unités, casse, espaces).
4. Définir la stratégie de déduplication (clé métier ou hash).
5. Choisir le format d'export adapté à l'usage aval (CSV pour tableur, JSON/JSONL pour pipeline, BDD pour requêtage).
6. Transmettre la spécification à **l'agent de développement back-end** (implémentation) et/ou **l'agent d'ingénierie des données** (si pipeline/stockage pérenne).

## Garde-fous
- Ne jamais conserver de données personnelles au-delà du besoin strict (minimisation) → valider avec **l'agent de conformité RGPD** si données personnelles identifiées.
- Documenter la provenance (URL source, date de collecte) pour traçabilité.
- Valider l'encodage (UTF-8) systématiquement pour éviter la corruption de caractères.
- Prévoir une validation de schéma avant export final (types cohérents, champs obligatoires renseignés).

## Template d'entrée (copier/coller)
```text
[Données brutes]
- Échantillon : ...
- Source (URL, date de collecte) : ...

[Schéma cible]
- Champs : nom | type | nullable

[Règles de normalisation]
- Dates, unités, casse : ...
```

## Template de sortie (copier/coller)
```text
[Schéma normalisé]
- Champ | Type | Contrainte

[Règles de nettoyage]
- ...

[Déduplication]
- Clé/hash : ...

[Format d'export]
- CSV/JSON/JSONL/BDD : ...
```

## Checklist QA interne
- Schéma cible validé avec le demandeur.
- Règles de normalisation testées sur échantillon.
- Déduplication définie et testée.
- Traçabilité de la provenance des données assurée.
- Vérification RGPD effectuée si données personnelles présentes.

## KPI reliés
- Taux de complétude des champs obligatoires (%).
- Taux de doublons résiduels après déduplication (%).
- Taux d'erreurs de type/format détectées en validation.

## Definition of done
- Schéma normalisé documenté et validé.
- Règles de nettoyage/déduplication spécifiées.
- Spécification transmise à l'agent de développement back-end et/ou l'agent d'ingénierie des données.

## Exemples d'usage

### Exemple 1 : Normalisation de prix multi-devises
**Contexte** : Données de prix extraites de plusieurs sites avec formats hétérogènes (virgule/point, devises différentes).
**Action** : Schéma cible défini avec champ `price_eur` normalisé (float, 2 décimales) et champ `currency_source` conservé pour traçabilité.
**Résultat** : Export CSV validé avec 0 valeur non convertie.

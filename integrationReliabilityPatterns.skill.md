# Integration Reliability Patterns

## Objectif
Concevoir des integrations robustes avec idempotence, retry/backoff, DLQ, timeouts et observabilite minimale.

## Quand l'utiliser (triggers)
- Workflows multi-systemes critiques.
- Erreurs intermittentes d'API, webhooks ou files.
- Besoin d'industrialiser un flux d'integration.

## Hors périmètre
- Simple script one-shot sans contrainte de fiabilite.
- Optimisation purement UX sans integration backend.

## Inputs requis
- Systeme source et cible.
- SLA/SLO attendus.
- Volume et frequence des messages/evenements.

## Sorties attendues
- Architecture d'integration resiliente.
- Matrice des patterns de fiabilite.
- Plan de supervision et alerting.

## Workflow recommandé
1. Cartographier les points de panne (network, API, broker, schema).
2. Definir les garanties (at-least-once, exactly-once logique, ordering).
3. Appliquer les patterns: retry, backoff, idempotence key, DLQ, circuit breaker.
4. Ajouter observabilite et runbook de remediation.

## Garde-fous
- Pas de secret en dur.
- Eviter les retries infinis sans garde.
- Valider la compatibilite schema avant prod.

## Template d'entrée (copier/coller)
```text
[Contexte]
- Source : ...
- Cible : ...
- Debit : ...

[Objectif]
- SLA/SLO : ...
- Contraintes de fiabilite : ...
```

## Template de sortie (copier/coller)
```text
[Patterns choisis]
1) ...
2) ...

[Gestion des erreurs]
- Retry : ...
- DLQ : ...
- Alerting : ...
```

## Checklist QA interne
- Idempotence testee.
- DLQ et replay documentes.
- Alertes actionnables avec owner.

## KPI reliés
- Taux d'echec d'integration.
- MTTR incidents integration.
- Taux de messages en DLQ.

## Definition of done
- Design resiliente validee.
- Runbook de recuperation disponible.
- Observabilite minimale en place.

## Exemples d'usage

### Exemple 1 : [Titre du cas d'usage]
**Contexte** : [Description de la situation]
**Action** : [Ce qui a été fait]
**Résultat** : [Résultat obtenu]
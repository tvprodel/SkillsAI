# System Monitoring & Observability

## Objectif
Concevoir et implémenter des architectures de monitoring et d'observabilité système proactives (métriques, logs, traces, alertes) pour infrastructure on-prem et hybride, permettant la détection préventive des dégradations.

## Quand l'utiliser (triggers)
- « monitoring système », « observabilité infra », « Prometheus Grafana », « architecture alerting », « SLI SLO système ».
- Besoin de visibilité centralisée sur infrastructure distribuée.
- Détection proactive de dégradations (avant incident).
- Consolidation métriques/logs multi-OS (Linux/Windows/containers).

## Hors périmètre
- Monitoring applicatif (APM, tracing apps) → l'agent d'architecture.
- Implémentation agents monitoring → Sysadmin Windows/Linux.
- Configuration dashboards détaillés → délégation post-conception.

## Inputs requis
- Périmètre infra à monitorer (nombre serveurs, OS, services critiques).
- Outils imposés ou libre choix (Prometheus, Grafana, ELK, Zabbix, commercial).
- Exigences SLI/SLO (disponibilité, latence, taux d'erreur cibles).
- Contraintes retention et volumétrie logs/métriques.

## Sorties attendues
- Architecture monitoring (outils, flux de collecte, stockage, visualisation).
- Métriques système clés à collecter (CPU, RAM, disk, network, I/O, processes).
- Stratégie alerting (seuils, escalade, notification channels).
- Dashboards types (overview infra, drill-down par serveur, SLI/SLO).
- Plan de rétention données (métriques courtes vs agrégées, logs archivage).

## Workflow recommandé
1. Identifier services critiques et métriques clés (golden signals : latence, traffic, erreurs, saturation).
2. Choisir stack monitoring (recommandé : Prometheus + Grafana + ELK pour logs, open source).
3. Concevoir architecture collecte (agents sur serveurs → collecteur central → stockage TSDB).
4. Définir SLI/SLO par service critique (ex: disponibilité API > 99.9%, latence P95 < 200ms).
5. Configurer alertes proactives (seuils préventifs : CPU > 80% = warning, > 90% = critical).
6. Concevoir dashboards multi-niveaux (overview global, drill-down par OS/service).

## Garde-fous
- Alertes proactives (détection avant incident) >> alertes réactives (après incident).
- Éviter alert fatigue : seuils calibrés, pas d'alertes non actionnables.
- Retention adaptée (métriques courtes 15j, agrégées 1 an, logs critiques 90j).
- Privilégier open source (Prometheus, Grafana, ELK) vs solutions propriétaires coûteuses.
- Métriques au format standard (OpenMetrics, Prometheus format).

## Template d'entrée (copier/coller)
```text
[Contexte]
- Infra : ... serveurs (Linux/Windows/containers)
- Services critiques : ...
- Outils : Prometheus, Grafana, ELK, autre

[Objectif]
- SLI/SLO cibles : ...
- Retention : ...
```

## Template de sortie (copier/coller)
```text
[Architecture monitoring]
- Stack : ...
- Flux collecte : ...
- Stockage TSDB : ...

[Métriques clés]
- Système : CPU, RAM, disk, network, I/O
- Services : ...

[Stratégie alerting]
- Seuils : ...
- Escalade : ...
- Channels : email, Slack, PagerDuty

[Dashboards]
- Overview global : ...
- Drill-down par serveur : ...
- SLI/SLO : ...

[Rétention]
- Métriques : 15j détail, 1 an agrégé
- Logs : 90j

[Hypothèses]
- ...

[Risques]
- ...
```

## Métriques de succès
- Taux de détection proactive > 70% (alertes préventives vs incidents non détectés).
- Zéro alert fatigue (< 5% alertes non actionnables).
- SLI/SLO définis et dashboardés pour 100% des services critiques.
- Rétention conforme aux exigences (métriques + logs).

## Checklist QA interne
- Chaque signal collecté est relié à un service, un SLI/SLO ou un besoin opérationnel.
- Les seuils, fenêtres, owners et actions d'alerte sont explicites et actionnables.
- La rétention, les accès et les risques de bruit ou de données sensibles sont considérés.

## Definition of done
- Le plan de monitoring décrit les signaux, tableaux de bord, alertes et responsabilités.
- Les SLI/SLO et critères de validation sont mesurables pour les services concernés.
- Les limites de couverture, rétention et escalade sont documentées.

## Exemples d'usage

### Exemple 1 : Mettre en place le suivi d'un service critique multi-OS
**Contexte** : Un service repose sur des hôtes Windows, Linux et un stockage partagé; les incidents sont détectés par les utilisateurs avant l'équipe d'exploitation.  
**Input** : Inventaire des composants, flux de dépendance, SLI/SLO métier, outils disponibles, rétention et canaux d'astreinte.  
**Output** : Architecture de collecte, métriques de saturation/disponibilité, dashboards par vue globale et composant, alertes actionnables et runbook d'escalade.

### Exemple 2 : Réduire les alertes répétitives sur l'espace disque
**Contexte** : Une alerte fixe se déclenche fréquemment sur des volumes temporaires sans incident, tandis qu'un volume critique a été rempli rapidement.  
**Input** : Historique d'utilisation et de croissance, criticité des volumes, seuils actuels, durée avant saturation et actions possibles.  
**Output** : Seuils basés sur criticité et temps estimé avant saturation, regroupement/suppression des alertes non actionnables et tests de notification sans modifier la collecte en production sans validation.

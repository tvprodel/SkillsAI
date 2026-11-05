# IaC On-Prem Automation

## Objectif
Définir et implémenter des stratégies d'Infrastructure as Code pour infrastructure on-prem et hybride via Ansible, Terraform on-prem, scripts de provisioning standardisés, idempotents et versionnés.

## Quand l'utiliser (triggers)
- « automatise le provisioning », « stratégie Ansible », « Terraform on-prem », « IaC pour infra existante ».
- Migration d'une infra manuelle vers IaC.
- Standardisation configuration multi-serveurs.
- Besoin d'idempotence et versioning des configs.

## Hors périmètre
- IaC cloud (Terraform AWS/Azure/GCP, CloudFormation) → l'agent d'architecture cloud.
- Scripts système spécifiques Bash/Perl → l'agent de scripting système.
- Implémentation finale des playbooks → Sysadmin Windows/Linux.

## Inputs requis
- Inventaire infra existante (nombre de serveurs, OS, rôles).
- Scope IaC (provisioning VMs, configuration OS, déploiement apps).
- Outils imposés ou libre choix (Ansible, Terraform, scripts).
- Stratégie de versioning (Git, branching model).

## Sorties attendues
- Plan d'automatisation (scope, outils, repos Git, stratégie branching).
- Structure de code IaC (roles Ansible, modules Terraform, organisation repos).
- Standards d'idempotence et gestion des secrets (Ansible Vault, variables).
- Stratégie de tests IaC (tests de syntaxe, dry-run, validation post-apply).
- Roadmap migration vers IaC (priorisation serveurs, timeline).

## Workflow recommandé
1. Auditer infra existante (inventaire, configs manuelles actuelles).
2. Définir scope IaC (provisioning, configuration, déploiement).
3. Choisir outils (Ansible pour config, Terraform pour provisioning recommandé).
4. Concevoir structure repos (roles Ansible par fonction, modules Terraform par composant).
5. Définir stratégie secrets (Vault, variables chiffrées) et tests (dry-run, validation).
6. Prioriser migration (serveurs critiques en dernier, tests sur non-prod d'abord).

## Garde-fous
- Idempotence obligatoire : exécution multiple = même résultat, pas d'effets de bord.
- Versionner tout le code IaC (Git mandatory).
- Tester sur environnement non-prod avant prod.
- Secrets JAMAIS en clair (Vault ou variables d'environnement).
- Privilégier Ansible/Terraform open source vs solutions propriétaires.

## Template d'entrée (copier/coller)
```text
[Contexte]
- Inventaire infra : ... serveurs (Linux/Windows)
- Scope IaC : provisioning / configuration / déploiement
- Outils : Ansible, Terraform, autre

[Objectif]
- Standardisation : ...
- Timeline migration : ...
```

## Template de sortie (copier/coller)
```text
[Plan d'automatisation]
- Outils : ...
- Scope : ...
- Repos Git : ...

[Structure code IaC]
- Ansible roles : ...
- Terraform modules : ...

[Stratégie secrets]
- Vault : ...

[Stratégie tests]
- Dry-run : ...
- Validation : ...

[Roadmap migration]
- Phase 1 : ...
- Phase 2 : ...

[Hypothèses]
- ...

[Risques]
- ...
```

## Métriques de succès
- 100% du code IaC sous contrôle de version (Git).
- Tests d'idempotence passés (exécution 2x = résultat identique).
- Zéro secret en clair dans le code.
- Taux de couverture IaC > 80% de l'infra cible.

## Checklist QA interne
- Le plan respecte le périmètre d'infrastructure on-prem/hybride et identifie ses dépendances.
- Idempotence, gestion des secrets, versionnement et validation non-production sont couverts.
- Les tests proposés incluent un second passage et des critères de retour arrière.

## Definition of done
- La structure IaC et la stratégie de migration sont documentées et versionnables.
- Les critères d'idempotence, de sécurité des secrets et de validation sont vérifiables.
- Les prérequis et risques de déploiement sont listés pour approbation avant exécution.

## Exemples d'usage

### Exemple 1 : Standardiser la configuration de serveurs Linux
**Contexte** : Une équipe administre plusieurs serveurs construits manuellement et les écarts de configuration compliquent les correctifs.  
**Input** : Inventaire non sensible des hôtes et rôles, baseline approuvée, environnements de test, règles de gestion des secrets et dépôt Git cible.  
**Output** : Découpage de rôles/playbooks idempotents, plan de migration par lots, tests de syntaxe/dry-run et vérification d'un second passage sans changement inattendu.

### Exemple 2 : Passer une configuration Windows répétitive sous contrôle de version
**Contexte** : Les réglages de services et de journalisation varient entre plusieurs serveurs applicatifs.  
**Input** : État cible validé, différences actuelles, contraintes d'exploitation, fenêtre de test et outil d'automatisation retenu.  
**Output** : Stratégie IaC adaptée à l'environnement, gestion des secrets hors dépôt, pilote en non-production et critères de retour arrière avant déploiement élargi.

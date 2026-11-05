# Reporting Structure d'Exécution

## Objectif
Restituer systématiquement les résultats d'exécution de l'agent de coordination à son demandeur (l'utilisateur, ou l'agent qui a transmis le brief) au format structuré [RAPPORT D'EXÉCUTION], avec une courte prose du persona en accompagnement (jamais en remplacement des données factuelles).

**Note historique** : le fichier conserve son ancien nom (`reportingStructureOrchestra`) pour ne pas casser les liens. Depuis le 2026-10-06, il n'existe plus d'agents distincts pour l'exécution et la coordination : l'agent de coordination exécute lui-même et rend compte directement.

## Quand l'utiliser (triggers)
- Fin d'exécution d'une tâche système (terminal, édition, build, déploiement).
- Rapport de statut intermédiaire ou feedback de progression.
- Compte-rendu d'anomalie.
- Clôture d'une délégation reçue d'un autre agent.

## Hors périmètre
- Documentation technique détaillée (déléguer à l'agent de documentation de code).
- Communication utilisateur final externe (déléguer à l'agent de rédaction technique).
- Reporting stratégique ou roadmap (déléguer à l'agent de stratégie produit).

## Inputs requis
- Brief reçu (tache_id, objectif, critères de succès) de l'utilisateur ou de l'agent demandeur.
- Actions réalisées (commandes, déploiements, vérifications).
- Résultats obtenus (codes retour, logs, états).
- Anomalies détectées (ou « rien » si aucune).

## Sorties attendues
Format obligatoire [RAPPORT D'EXÉCUTION] avec :
- tache_id : identifiant unique de la délégation (ex : DEL-YYYYMMDD-XXX)
- statut : SUCCES / ECHEC / PARTIEL / BLOQUE
- actions_realisees : liste factuelle des actions exécutées
- resultat : codes retour, logs pertinents, états post-exécution
- anomalies : liste des problèmes rencontrés (ou « rien »)
- recommandation : prochaine action suggérée (si ECHEC/PARTIEL/BLOQUE)

Prose du persona en accompagnement (1-2 phrases, ton cohérent avec l'agent de coordination).

## Workflow recommandé
1. **Récupérer** le brief avec tache_id et critères de succès.
2. **Compiler** les actions réalisées de manière factuelle.
3. **Extraire** les résultats pertinents (codes retour, logs clés, états).
4. **Lister** les anomalies rencontrées (ou « rien »).
5. **Formuler** une recommandation si statut non-SUCCES.
6. **Structurer** le rapport au format [RAPPORT D'EXÉCUTION].
7. **Ajouter** 1-2 phrases de prose cohérente avec le persona.
8. **Transmettre** au demandeur : l'utilisateur, ou l'agent délégant si le brief venait de lui.

## Garde-fous
- **Format strict** : respecter exactement la structure [RAPPORT D'EXÉCUTION].
- **tache_id correct** : reprendre l'identifiant de la délégation.
- **Statut valide** : SUCCES / ECHEC / PARTIEL / BLOQUE uniquement.
- **Actions factuelles** : décrire ce qui a été fait, pas ce qui aurait dû être fait.
- **Résultat avec logs** : toujours fournir codes retour et logs pertinents.
- **Anomalies ou « rien »** : expliciter les problèmes ou confirmer l'absence.
- **Recommandation si échec** : toujours proposer une action suivante si statut non-SUCCES.
- **Prose cohérente** : jamais au détriment de la clarté ou de la complétude des données.

## Template d'entrée (copier/coller)
```text
[Brief reçu]
- tache_id : ...
- objectif : ...
- criteres_succes : ...

[Actions realisees]
- ...

[Resultats]
- codes_retour : ...
- logs : ...
- etats : ...

[Anomalies]
- ...
```

## Template de sortie (copier/coller)
```text
[RAPPORT D'EXÉCUTION]
- tache_id : DEL-YYYYMMDD-XXX
- statut : SUCCES / ECHEC / PARTIEL / BLOQUE
- actions_realisees :
  1) ...
  2) ...
- resultat :
  - code_retour : ...
  - stdout : ...
  - stderr : ...
  - etat_post_execution : ...
- anomalies : rien / liste des problèmes
- recommandation : prochaine action / rien si SUCCES

[Prose persona]
1-2 phrases courtes, cohérentes avec le persona.
```

## Checklist QA interne
- [ ] Format [RAPPORT D'EXÉCUTION] strict respecté
- [ ] tache_id correct (repris du brief)
- [ ] Statut valide parmi (SUCCES / ECHEC / PARTIEL / BLOQUE)
- [ ] Actions factuelles listées
- [ ] Résultat avec codes retour et logs pertinents
- [ ] Anomalies explicites ou « rien »
- [ ] Recommandation présente si statut non-SUCCES
- [ ] Prose cohérente sans masquer l'information factuelle

## KPI reliés
- Taux de rapports valides au format structuré
- Taux de rapports incomplets nécessitant clarification
- Temps moyen entre fin d'exécution et émission du rapport
- Taux de rapports avec anomalies non documentées

## Definition of done
- Rapport structuré [RAPPORT D'EXÉCUTION] émis
- Toutes les rubriques présentes et complètes
- Aucune information factuelle masquée par le style
- Rapport transmis au demandeur (utilisateur ou agent délégant)

## Exemples d'usage

### Exemple 1 : build exécuté pour le compte d'un agent
**Contexte** : l'agent de développement back-end transmet à l'agent de coordination un brief pour lancer la suite de tests.
**Action** : l'agent de coordination exécute la commande, relève le code retour et les logs.
**Résultat** : rapport avec statut SUCCES, un test ignoré signalé en anomalie, recommandation « rien », transmis à l'agent délégant.

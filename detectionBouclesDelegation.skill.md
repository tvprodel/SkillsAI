# Détection Boucles Délégation

## Objectif
Détecter et signaler les boucles de délégation (A → B → A) : tâches revenues 2+ fois au même agent sans avancement, patterns récurrents d'échec, chaînes circulaires de routage.

## Quand l'utiliser (triggers)
- Tâche revenue 2+ fois au même agent.
- Pattern récurrent d'échec sur même type de demande.
- Ping-pong entre 2 agents sans livrable.
- Historique de délégations montrant cycle répétitif.
- Statut BLOQUÉ sans cause racine identifiée.

## Hors périmètre
- Optimisation de workflow sans boucle détectée (→ l'agent de coordination).
- Refactoring taxonomie agents (→ l'agent de coordination, revue mensuelle).
- Résolution technique du blocage (→ agent spécialisé concerné).

## Inputs requis
- Historique des délégations sur la tâche (agent A → agent B → agent C → ...).
- Identité de la tâche (titre, objectif, DoD).
- Statuts successifs (TODO / DOING / BLOCKED / renvoyé).
- Raisons de renvoi si documentées.

## Sorties attendues
- **Boucle identifiée** : schéma de la chaîne circulaire (A → B → A OU A → B → C → A).
- **Cause racine** : frontière floue, DoD ambigu, compétence partagée, brief incomplet.
- **Recommandation de sortie de boucle** : découpage de tâche, owner unique, clarification périmètre, escalade à l'agent de coordination (qui arbitre ; si l'agent de coordination est lui-même dans la boucle, escalade à l'utilisateur).
- **Impact de la boucle** : délai accumulé, taux de rework, moral équipe.

## Workflow recommandé

1. **Reconstituer l'historique de délégations** :
   - Tracer la chaîne : Agent 1 → Agent 2 → Agent 3 → ...
   - Identifier les retours : Agent X revenue 2+ fois.

2. **Détecter le cycle** :
   - **Boucle simple** : A → B → A (ex : l'agent de planification → l'agent produit → l'agent de planification).
   - **Boucle complexe** : A → B → C → A (ex : l'agent de coordination → l'agent de scripting système → l'agent de coordination → l'agent de scripting système).
   - **Ping-pong** : A ↔ B répété 3+ fois sans avancement.

3. **Analyser la cause racine** :
   - **Frontière floue** : tâche à cheval entre 2 périmètres (ex : "prioriser features" = l'agent produit ou l'agent de planification ?).
   - **DoD ambigu** : critère de succès non partagé, interprétation divergente.
   - **Compétence partagée** : aucun des deux agents n'a la pleine compétence (ex : infra cloud + code applicatif).
   - **Brief incomplet** : informations manquantes, agents se renvoient pour clarification.
   - **Absence d'owner unique** : responsabilité diffuse, chacun attend l'autre.

4. **Quantifier l'impact** :
   - **Délai accumulé** : temps écoulé depuis première délégation.
   - **Nombre de cycles** : combien de fois la tâche a été renvoyée.
   - **Taux de rework** : proportion de livrables incomplets.

5. **Formuler recommandation de sortie** :
   - **Découper la tâche** : séparer les périmètres (ex : l'agent produit définit priorités, l'agent de planification estime durées).
   - **Désigner owner unique** : arbitrer qui est responsable final.
   - **Clarifier périmètre** : reformuler DoD avec critères mesurables.
   - **Escalader à l'agent de coordination** : si boucle persiste après 2 cycles, sortir du niveau opérationnel (l'agent de coordination arbitre ; si l'agent de coordination est dans la boucle, escalade à l'utilisateur).

6. **Tracer la détection** :
   - Consigner la boucle dans rapport mensuel ou log incidents.
   - Alimenter base de connaissance des patterns d'erreur récurrents.

## Garde-fous

- Distinguer **boucle légitime** (aller-retour pour clarification ponctuelle) et **boucle bloquante** (2+ cycles sans avancement).
- Ne jamais désigner arbitrairement un owner sans critère objectif : utiliser la matrice RACI du guide d'orchestration.
- Tracer chaque boucle détectée pour capitalisation (éviter récurrence).
- Rester neutre : pas de jugement sur les agents, uniquement constat factuel.

## Template d'entrée (copier/coller)

```text
[Tâche concernée]
- Titre : ...
- Objectif : ...
- DoD : ...

[Historique délégations]
- Cycle 1 : Agent A → Agent B (raison : ...)
- Cycle 2 : Agent B → Agent A (raison : ...)
- Cycle 3 : Agent A → Agent C (raison : ...)
- ...

[Statuts successifs]
- TODO → DOING → renvoyé → DOING → renvoyé → BLOCKED
```

## Template de sortie (copier/coller)

```text
[Constat]
- Boucle détectée : [schéma de la chaîne circulaire]
  Ex : Agent A → Agent B → Agent A (2 cycles)
- Type : Boucle simple / Boucle complexe / Ping-pong

[Raisonnement]
- Cause racine identifiée : ...
  (Frontière floue / DoD ambigu / Compétence partagée / Brief incomplet / Absence owner unique)
- Indices observables : ...

[Recommandation]
- Action de sortie prioritaire : ...
  (Découper tâche / Désigner owner unique / Clarifier DoD / Escalader à l'agent de coordination)
- Agent owner final recommandé : ...
- Niveau de confiance : XX %

[Impact de la boucle]
- Délai accumulé : X jours/heures
- Nombre de cycles : X
- Taux de rework : XX %
- Conséquence estimée si non résolue : ...
```

## Checklist QA interne

- [ ] Historique de délégations reconstitué intégralement.
- [ ] Cycle clairement identifié (schéma A → B → A OU A → B → C → A).
- [ ] Cause racine analysée avec indices observables.
- [ ] Recommandation de sortie actionnaire (verbe + objet précis).
- [ ] Owner final recommandé avec justification RACI.
- [ ] Impact quantifié (délai, cycles, rework).
- [ ] Format de sortie standard respecté.

## KPI reliés

- **Taux de boucles détectées** : (boucles identifiées / délégations totales analysées) x 100
  - Cible : 100% des boucles réelles détectées (aucune fuite)
  - Mesure : comparer les détections de cette compétence à un audit manuel mensuel

- **Délai moyen de détection** : temps entre début boucle (2e retour) et signalement
  - Cible : <= 1 cycle (détection au 2e retour, pas au 3e)
  - Mesure : timestamp 2e retour - timestamp signalement

- **Taux de sorties de boucle réussies** : (boucles résolues après recommandation / boucles détectées) x 100
  - Cible : >= 85%
  - Mesure : comparer statut tâche 1 semaine après recommandation

- **Taux de faux positifs** : (boucles signalées à tort / signalements totaux) x 100
  - Cible : <= 10%
  - Mesure : distinction boucle légitime (clarification 1 A/R) vs bloquante (2+ cycles)

## Definition of done

Une détection de boucle de délégation est considérée terminée si :

1. **Boucle identifiée avec schéma de chaîne circulaire**
   - Mesure : présence d'un schéma A → B → A OU A → B → C → A documenté
   - Preuve : format "Agent X → Agent Y → Agent X (N cycles)" avec N >= 2

2. **Cause racine analysée** parmi les 5 types documentés
   - Mesure : cause assignée parmi : Frontière floue / DoD ambigu / Compétence partagée / Brief incomplet / Absence owner unique
   - Preuve : justification de la cause avec indices observables (ex : "DoD ambigu : critère 'optimisé' sans métrique")

3. **Recommandation de sortie de boucle formulée**
   - Mesure : au moins 1 action corrective parmi : Découper tâche / Désigner owner unique / Clarifier périmètre / Escalader à l'agent de coordination
   - Preuve : format "Recommandation : [action] avec [critère de succès mesurable]"

4. **Impact de la boucle quantifié** (délai accumulé, nb cycles, taux rework)
   - Mesure : présence de 3 métriques impact : Délai / Nb cycles / Taux rework
   - Preuve : valeurs chiffrées (ex : "Délai accumulé : 2h30, 3 cycles, rework 66%")

5. **Traçabilité assurée** dans rapport mensuel ou log incidents
   - Mesure : boucle consignée dans fichier de suivi avec référence unique
   - Preuve : entrée ajoutée dans multiAgentsFiles/Logs/ avec format standard

## Exemples types

### Cas 1 : Boucle simple (agent produit ↔ agent de planification)
**Input** :
```text
Tâche : "Estimer durées phases projet"
Historique :
- L'agent de planification → l'agent produit ("besoin priorités d'abord")
- L'agent produit → l'agent de planification ("estimation = rôle de l'agent de planification")
Statut : BLOCKED après 2 cycles
```

**Output** :
```text
[Constat]
- Boucle détectée : l'agent de planification → l'agent produit → l'agent de planification (2 cycles)
- Type : Ping-pong (aucun avancement)

[Raisonnement]
- Cause racine : Frontière floue entre roadmap stratégique (agent produit) et planning opérationnel (agent de planification).
- L'agent produit définit priorités et séquence logique (vision produit).
- L'agent de planification estime durées par phase (planification opérationnelle).
- Aucun des deux n'a livré son périmètre.

[Recommandation]
- Découper la tâche :
  1) Agent produit : définir priorités et séquence des features (output : roadmap priorisée).
  2) Agent de planification : estimer durées par phase sur base de la roadmap (output : planning avec durées).
- Owner final : l'agent de planification (estimation = périmètre opérationnel selon RACI).
- Niveau de confiance : 80%

[Impact de la boucle]
- Délai accumulé : 3 jours
- Nombre de cycles : 2
- Taux de rework : 100% (aucun livrable)
- Conséquence si non résolue : Blocage persistant, escalade obligatoire vers l'agent de coordination.
```

### Cas 2 : Boucle complexe (l'agent de coordination → l'agent de scripting système → l'agent de coordination)
**Input** :
```text
Tâche : "Modifier fichier config.yaml"
Historique :
- L'agent de coordination → l'agent de scripting système ("script de modification nécessaire")
- L'agent de scripting système → l'agent de coordination ("action système, à exécuter par l'agent de coordination")
- L'agent de coordination → l'agent de scripting système ("je veux d'abord le script validé")
Statut : BLOCKED après 2 cycles
```

**Output** :
```text
[Constat]
- Boucle détectée : l'agent de coordination → l'agent de scripting système → l'agent de coordination → l'agent de scripting système (2 cycles)
- Type : Boucle simple avec incompréhension de périmètre

[Raisonnement]
- Cause racine : DoD ambigu entre production du script et exécution système.
- L'agent de coordination dispose des outils d'édition et d'exécution : elle exécute elle-même toute action système.
- L'agent de scripting système produit et revoit le script ; il ne l'exécute pas et renvoie donc à l'agent de coordination.
- Le brief ne précisait pas qui livre quoi (script validé, puis exécution).

[Recommandation]
- Clarifier le périmètre en deux étapes :
  1) l'agent de scripting système livre le script revu (ou le contenu du fichier) avec critères de succès.
  2) l'agent de coordination exécute directement, vérifie le résultat avec preuves et rend compte.
- Niveau de confiance : 95%

[Impact de la boucle]
- Délai accumulé : 1 heure
- Nombre de cycles : 2
- Taux de rework : 100% (aucun livrable)
- Conséquence si non résolue : Tâche orpheline, workflow bloqué.
```

### Cas 3 : Ping-pong récurrent (agent d'architecture ↔ agent de développement)
**Input** :
```text
Tâche : "Concevoir API RESTful pour module auth"
Historique :
- Agent d'architecture → agent de développement ("implémente l'API")
- Agent de développement → agent d'architecture ("besoin spec interfaces d'abord")
- Agent d'architecture → agent de développement ("spec fournie, implémente")
- Agent de développement → agent d'architecture ("spec incomplète, erreurs manquantes")
Statut : DOING après 3 cycles, délai +2 jours
```

**Output** :
```text
[Constat]
- Boucle détectée : agent d'architecture ↔ agent de développement (3 cycles)
- Type : Ping-pong avec DoD ambigu

[Raisonnement]
- Cause racine : DoD incomplet côté agent d'architecture.
- Spec API fournie mais manque : gestion erreurs, codes HTTP, schémas validation, authentification.
- L'agent de développement renvoie à chaque élément manquant.
- Aucun critère de succès partagé sur "spec complète".

[Recommandation]
- Définir DoD explicite pour spec API (checklist complétude) :
  - Endpoints (URL, méthodes HTTP)
  - Schémas requête/réponse (JSON Schema ou OpenAPI)
  - Codes HTTP et messages d'erreur
  - Authentification/autorisation
  - Exemples de requêtes
- L'agent d'architecture livre spec complète selon DoD.
- L'agent de développement implémente sans renvoi si DoD respectée.
- Niveau de confiance : 85%

[Impact de la boucle]
- Délai accumulé : 2 jours
- Nombre de cycles : 3
- Taux de rework : 66% (2 renvois sur 3 cycles)
- Conséquence si non résolue : Délai projet, frustration équipe, qualité spec dégradée.
```

## Liens
- Skill complémentaire : [Audit Cohérence Logique Brief](./auditCoherenceLogiqueBrief.skill.md)
- Skill complémentaire : [Calibration Confiance Décisionnelle](./calibrationConfianceDecisionnelle.skill.md)
- Guide d'orchestration : [AGENTS.md](../agents.md)

## Exemples d'usage

### Exemple 1 : Détecter un ping-pong entre deux agents
**Contexte** : Une demande d'évolution revient plusieurs fois entre l'équipe produit et l'équipe technique sans décision exploitable.  
**Input** : Historique horodaté des délégations, briefs, raisons de renvoi, statuts et DoD communiqué.  
**Output** : Chaîne de renvois factuelle, cause probable (frontière, brief ou owner), impact constaté et proposition d'un owner et d'une prochaine action.

### Exemple 2 : Distinguer clarification légitime et boucle bloquante
**Contexte** : Un spécialiste a renvoyé une tâche une fois pour préciser une contrainte; le demandeur hésite à l'escalader.  
**Input** : Demande initiale, précision apportée, livrable produit depuis et nombre de cycles sans avancement.  
**Output** : Classification justifiée comme clarification ponctuelle ou boucle bloquante, éléments manquants et seuil de relance/escalade selon les règles de l'équipe.

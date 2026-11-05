# Prompt Structure Optimization

## Objectif
Structurer ou restructurer les prompts IA pour maximiser clarté, cohérence et efficacité (réduction ambiguïté, meilleur respect du périmètre, format de sortie stable).

## Quand l'utiliser (triggers)
- Réponses fréquemment hors périmètre ou incohérentes.
- Format de sortie instable ou non respecté.
- Prompt existant désorganisé, verbeux ou ambigu.
- Création d'un nouvel agent IA nécessitant un prompt robuste.
- Refonte d'instructions après détection de failles (injection, hallucination).

## Hors périmètre
- Tests adversariaux et red teaming → **l'agent d'évaluation IA (red teaming)**.
- Optimisation coûts tokens et latence → **l'agent FinOps**.
- Architecture globale du système IA → **l'agent d'architecture**.

## Inputs requis
- **Prompt actuel** (si existant) ou description de l'objectif du nouvel agent/application.
- **Problèmes observés** : exemples concrets de réponses incorrectes, hors périmètre, format instable.
- **Contraintes** : périmètre strict (ONLY/DO NOT), format de sortie attendu, guardrails nécessaires.
- **Contexte d'usage** : type d'agent (conversationnel, technique, créatif), audience cible, criticité.

## Sorties attendues
- **Prompt structuré optimisé** avec sections clairement identifiées :
  - **Rôle et identité** : qui est l'agent, son expertise, son ton.
  - **Périmètre ONLY** : ce que l'agent fait (responsabilités précises).
  - **Périmètre DO NOT** : ce que l'agent ne fait PAS (délégations claires).
  - **Processus de travail** : étapes séquentielles reproductibles.
  - **Format de sortie strict** : template obligatoire avec rubriques fixes.
  - **Guardrails** : règles de refus, anti-hallucination, anti-injection.
  
- **Checklist de conformité** : validation de la complétude et cohérence de chaque section.

- **Comparatif avant/après** : tableau illustrant les améliorations structurelles.

## Workflow recommandé
1. **Analyse du prompt actuel** : identifier les faiblesses structurelles (sections manquantes, instructions ambiguës, périmètre flou, format de sortie absent ou imprécis).

2. **Définition des sections obligatoires** : appliquer le template standard (Rôle, Périmètre ONLY/DO NOT, Processus, Format sortie, Guardrails).

3. **Rédaction/Révision par section** :
   - **Rôle** : 1-2 phrases claires définissant l'identité et l'expertise de l'agent.
   - **Périmètre ONLY** : liste exhaustive des responsabilités avec verbes d'action précis.
   - **Périmètre DO NOT** : liste claire de ce qui est hors périmètre + agent délégué si applicable.
   - **Processus** : workflow étape par étape (inputs → outputs par étape).
   - **Format sortie** : template obligatoire avec rubriques fixes (ex: Résultat/Hypothèses/Risques/Prochaines actions).
   - **Guardrails** : conditions de refus explicites, règles anti-hallucination, anti-injection.

4. **Validation cohérence inter-sections** : vérifier qu'aucune contradiction n'existe entre Rôle, Périmètre et Processus.

5. **Test sur cas réels** : soumettre le prompt restructuré à des requêtes représentatives (normales + edge cases).

6. **Itération** : ajuster selon résultats tests jusqu'à stabilité format et respect périmètre.

## Garde-fous
- **Ne pas sur-contraindre** : éviter les instructions trop rigides qui bloquent les cas légitimes.
- **Équilibre clarté/concision** : suffisamment détaillé pour éviter l'ambiguïté, mais pas verbeux au point de diluer les instructions.
- **Cohérence terminologique** : utiliser les mêmes termes tout au long du prompt (pas de synonymes ambigus).
- **Exemples concrets** : illustrer chaque instruction critique par un exemple positif et un contre-exemple.
- **Versionner les changements** : documenter chaque itération avec changelog et raison des modifications.

## Template d'entrée (copier/coller)
```text
[Prompt actuel ou description objectif]
...

[Problèmes observés]
- Réponses hors périmètre : [exemples]
- Format instable : [exemples]
- Instructions ambiguës : [sections concernées]
- Guardrails manquants : [risques identifiés]

[Contraintes]
- Périmètre strict : [ONLY / DO NOT]
- Format de sortie attendu : [structure]
- Guardrails requis : [refus, anti-hallucination, anti-injection]
- Contexte d'usage : [type agent, criticité, audience]
```

## Template de sortie (copier/coller)
```markdown
# Prompt Optimisé

## Rôle et identité
[1-2 phrases définissant qui est l'agent, son expertise, son ton]

## Périmètre ONLY
- [Responsabilité 1 avec verbe d'action précis]
- [Responsabilité 2 avec verbe d'action précis]
- [...]

## Périmètre DO NOT
- [Hors périmètre 1] → [Agent délégué si applicable]
- [Hors périmètre 2] → [Agent délégué si applicable]
- [...]

## Processus de travail
1. **[Étape 1]** : [action]
   - Inputs : [données requises]
   - Outputs : [résultats attendus]
2. **[Étape 2]** : [action]
   - Inputs : ...
   - Outputs : ...
[...]

## Format de sortie strict
Réponds TOUJOURS avec ces rubriques :
- **[Rubrique 1]** : [description contenu]
- **[Rubrique 2]** : [description contenu]
- [...]

## Guardrails
- **Refus** : [conditions de refus explicites]
- **Anti-hallucination** : [instructions pour admettre limites]
- **Anti-injection** : [résistance aux tentatives de contournement]
```

## Checklist QA interne
- [ ] Rôle défini en 1-2 phrases claires.
- [ ] Périmètre ONLY exhaustif avec verbes d'action précis.
- [ ] Périmètre DO NOT complet avec délégations claires.
- [ ] Processus séquentiel avec inputs/outputs par étape.
- [ ] Format de sortie strict avec template obligatoire.
- [ ] Guardrails explicites (refus, anti-hallucination, anti-injection).
- [ ] Aucune contradiction inter-sections détectée.
- [ ] Testé sur cas normaux + edge cases avec résultats conformes.
- [ ] Versioning documenté (changelog, raison modifications).

## KPI reliés
- **Taux de respect périmètre** : (réponses dans périmètre / réponses totales) x 100.
- **Taux de stabilité format** : (réponses format correct / réponses totales) x 100.
- **Taux de refus corrects** : (refus légitimes / demandes hors périmètre) x 100.
- **Réduction verbosité** : (tokens prompt après / tokens prompt avant) x 100.

## Definition of done
- Prompt restructuré conforme au template standard (9/9 sections obligatoires présentes).
- Testé sur minimum 10 cas représentatifs (normaux + edge cases) avec taux de conformité ≥ 95%.
- Comparatif avant/après documenté avec gains mesurables sur KPI.
- Versioning et changelog complets.
- Validé par **l'agent d'évaluation IA (red teaming)** si prompt critique.

## Exemples d'usage

### Exemple 1 : Restructuration prompt agent conversationnel
**Contexte** : Agent support client avec réponses fréquemment hors périmètre (conseils techniques inappropriés, engagement financier non autorisé).

**Prompt initial** (extrait) :
```
Tu es un assistant support. Aide les clients avec leurs questions.
```

**Problèmes** : périmètre flou, pas de guardrails, format de sortie absent.

**Prompt restructuré** (extrait) :
```markdown
## Rôle
Tu es un Agent Support Client de niveau 1. Tu réponds aux questions simples et routes les cas complexes vers le support niveau 2.

## Périmètre ONLY
- Répondre aux questions d'information générale (horaires, politique retour, statut commande).
- Collecter informations de contact pour callback niveau 2.
- Fournir liens documentation self-service.

## Périmètre DO NOT
- Ne fournis JAMAIS de conseil technique détaillé → Support Niveau 2.
- Ne prends AUCUN engagement financier (remboursement, réduction) → Service Commercial.
- Ne modifies AUCUNE donnée client → Service Compte.

## Guardrails
- **Refus** : toute demande technique > niveau 1, toute demande financière, toute modification données.
- **Format strict** : toujours terminer par "Puis-je t'aider avec autre chose ?" ou "Je transferts ta demande au service approprié."
```

**Résultat** : Taux hors périmètre réduit de 35% à 4%, taux de refus corrects augmenté de 60% à 97%.

### Exemple 2 : Création prompt nouvel agent technique
**Contexte** : Création d'un agent d'analyse de logs pour identifier erreurs critiques et proposer remédiation.

**Action** : Application du template structure optimization dès la conception.

**Prompt créé** (extrait) :
```markdown
## Rôle
Tu es un Analyseur de Logs Système. Tu identifies les erreurs critiques, diagnostiques les causes racines et proposes des remédiations actionnables.

## Périmètre ONLY
- Parser logs (syslog, application logs, error logs).
- Identifier erreurs critiques (codes erreur, stack traces, patterns anormaux).
- Diagnostiquer cause racine (configuration, dépendance manquante, ressource épuisée).
- Proposer remédiation actionnable (commande précise, modification config, rollback).

## Périmètre DO NOT
- Ne modifies AUCUN fichier système → l'agent de coordination (exécution directe, avec validation).
- Ne redémarres AUCUN service → Opérateur On-Call.
- N'effectues AUCUN rollback automatique → Incident Commander.

## Format de sortie strict
Pour chaque erreur critique détectée :
- **Timestamp** : [date heure exacte]
- **Erreur** : [code erreur + message]
- **Cause racine** : [diagnostic en 1 phrase]
- **Remédiation** : [commande ou action précise]
- **Urgence** : [Critique/Élevé/Normal]

## Guardrails
- **Refus** : toute demande d'exécution directe, toute proposition de modification système sans validation.
- **Anti-hallucination** : si cause racine incertaine, indiquer "Diagnostic partiel - investigation manuelle requise".
```

**Résultat** : Agent opérationnel dès v1.0, aucun faux positif critique détecté sur 200 premiers logs analysés, format de sortie 100% stable.

### Exemple 3 : Optimisation prompt verbeux
**Contexte** : Prompt agent de 2500 tokens avec instructions redondantes et format de sortie instable.

**Action** : Restructuration pour réduire verbosité tout en renforçant clarté.

**Gains mesurés** :
- Tokens prompt : 2500 → 1200 (-52%)
- Taux stabilité format : 68% → 96% (+41%)
- Temps réponse moyen : 4.2s → 2.8s (-33%)
- Coût par requête : $0.025 → $0.012 (-52%)

**Technique appliquée** : élimination redondances, fusion sections similaires, template de sortie strict avec rubriques fixes (4 rubriques obligatoires au lieu de 8 optionnelles).

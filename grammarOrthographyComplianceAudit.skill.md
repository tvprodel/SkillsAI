# Grammar & Orthography Compliance Audit

## Objectif
Auditer et corriger la grammaire, l'orthographe, la syntaxe et la ponctuation en français, anglais et néerlandais, sur du contenu textuel déjà rédigé, sans en modifier le ton ni le fond.

## Quand l'utiliser (triggers)
- Relecture de documentation utilisateur, technique, API avant publication.
- Revue de micro-copie d'interface (CTA, tooltips, messages d'erreur).
- Audit de copy marketing (landing pages, emails) avant diffusion.
- Correction de commentaires de code (docstrings, README, CHANGELOG).
- Audit de régression mensuel : vérification systématique des fichiers nouveaux/modifiés depuis le dernier passage.

## Hors périmètre
- Traduction ou localisation culturelle (→ l'agent de traduction et localisation).
- Rédaction initiale de contenu (→ l'agent de rédaction technique, l'agent de microcopie, l'agent de copywriting).
- Modification du fond métier ou du sens du texte sans validation de l'auteur original.
- Adaptation de ton ou de registre (→ l'agent de traduction et localisation).

## Inputs requis
- Texte ou fichier(s) à auditer (langue(s) cible(s) : FR/EN/NL).
- Contexte : public cible, type de contenu (doc utilisateur, microcopie, copy marketing, code comments).
- Rapport de checkpoint mensuel (optionnel) : liste des fichiers nouveaux/modifiés générée par `grammarAZertYOrthMonthlyAudit.py`.

## Sorties attendues
- Tableau de corrections (avant/après/justification/langue/type).
- Rapport d'audit : fichiers revus, nombre d'erreurs par type, statut des corrections.
- Statistiques : taux de corrections validées, types d'erreurs les plus fréquents.

## Workflow recommandé
1. **Réception du périmètre** : fichier(s) fourni(s) ou rapport de checkpoints mensuel.
2. **Analyse linguistique FR/EN/NL** : détection des erreurs de grammaire, orthographe, syntaxe, ponctuation, accords, conjugaison. Utilisation optionnelle de LanguageTool (open source) en complément.
3. **Proposition de corrections** : tableau avant/après avec justification grammaticale. Distinguer erreur objective vs préférence stylistique.
4. **Renvoi à l'auteur original** : validation par le propriétaire du texte avant application.
5. **Mise à jour du rapport d'audit** : enregistrement du statut des corrections.

## Garde-fous
- Ne jamais altérer le sens ni le ton du texte.
- Toujours fournir une justification grammaticale pour chaque correction.
- Distinguer clairement erreur objective (règle violée) vs suggestion stylistique (optionnelle).
- Priorité logiciel libre : LanguageTool (open source, https://languagetool.org) en complément de l'analyse humaine/agent.

## Template d'entrée (copier/coller)
```text
[Périmètre]
- Fichier(s) : ...
- Langue(s) : FR / EN / NL
- Type de contenu : doc utilisateur / microcopie / copy marketing / code comments
- Rapport de checkpoint (si audit mensuel) : ...

[Contexte]
- Public cible : ...
- Contraintes : ...
```

## Template de sortie (copier/coller)
```text
[Corrections proposées]
| Fichier | Ligne | Avant | Après | Justification | Langue | Type |
|---------|-------|-------|-------|---------------|--------|------|
| ... | ... | ... | ... | ... | ... | Erreur objective / Suggestion stylistique |

[Rapport d'audit]
- Fichiers revus : X
- Erreurs trouvées : Y (grammaire: A, orthographe: B, syntaxe: C, ponctuation: D, accords: E, conjugaison: F)
- Corrections validées : Z
- Corrections refusées : W
- Fichiers restants : ...

[Statistiques]
- Taux de corrections validées : ...%
- Types d'erreurs les plus fréquents : ...
```

## Checklist QA interne
- [ ] Toutes les erreurs objectives détectées et justifiées.
- [ ] Distinction claire erreur objective vs préférence stylistique.
- [ ] Aucune modification du sens ou du ton du texte.
- [ ] Justification grammaticale fournie pour chaque correction.
- [ ] Corrections renvoyées à l'auteur original pour validation.
- [ ] Rapport d'audit complet et à jour.

## KPI reliés
- Taux de corrections validées (cible : >= 85%).
- Taux de régression (erreurs réintroduites après correction, cible : <= 5%).
- Couverture d'audit mensuel (% fichiers nouveaux/modifiés revus, cible : 100%).
- Types d'erreurs les plus fréquents (pour formation/documentation).

## Definition of done
- 100% des fichiers du périmètre audité (rapport de checkpoint ou fichiers fournis).
- Toutes les erreurs objectives détectées et proposées en correction avec justification.
- Corrections renvoyées à l'auteur original pour validation.
- Rapport d'audit complet avec statut des corrections.
- 0 régression introduite (mesure : aucune nouvelle erreur introduite par la correction).

## Exemples d'usage

### Exemple 1 : Relecture documentation utilisateur FR
**Contexte** : Documentation Getting Started d'une API REST, public développeurs francophones.  
**Action** : Audit FR de `docs/gettingStarted.md`, détection de 12 erreurs (8 orthographe, 3 accords, 1 conjugaison).  
**Résultat** : Tableau de corrections proposé, 11/12 validées par l'agent de rédaction technique, 1 refusée (préférence stylistique), corrections appliquées.

### Exemple 2 : Audit mensuel de régression multi-projets
**Contexte** : Exécution mensuelle du script `grammarAZertYOrthMonthlyAudit.py`, 2 projets (`myAgentsTemplate`, `SalamancaDoc`), 45 fichiers nouveaux/modifiés détectés.  
**Action** : Revue systématique des 45 fichiers, détection de 28 erreurs (15 orthographe, 8 grammaire, 5 ponctuation).  
**Résultat** : Rapport d'audit mensuel généré, corrections proposées aux auteurs respectifs, 26/28 validées, 2 refusées (choix stylistiques volontaires).

### Exemple 3 : Correction microcopie UI EN/NL
**Contexte** : Interface dashboard multilingue (EN/NL), revue des CTA et tooltips.  
**Action** : Audit EN et NL de `src/components/Dashboard.vue`, détection de 5 erreurs (3 EN accords, 2 NL orthographe).  
**Résultat** : Corrections proposées à l'agent frontend, 5/5 validées, appliquées avant release.

# Execution Commande Shell

## Objectif
Executer des commandes shell en production de maniere robuste, tracee et reversible, avec verification systematique de l'environnement et capture complete des resultats.

## Quand l'utiliser (triggers)
- Execution de commandes shell / bash / terminal
- Deploiements manuels ou semi-automatises
- Builds, compilations, packaging
- Operations Git (clone, pull, tag, push)
- Modifications systeme necessitant des commandes shell

## Hors périmètre
- Developpement de scripts Bash/Perl complexes (deleguer a l'agent de scripting système)
- Architecture d'automatisation globale (deleguer a l'agent d'intégration et d'automatisation)
- Decisions d'architecture ou de conception (deleguer a l'agent d'architecture)

## Inputs requis
- Commande exacte a executer
- Contexte d'execution (environnement, repertoire, utilisateur)
- Mode d'execution : dry-run (simulation) ou reel
- Criteres de succes explicites (code retour attendu, sortie attendue, etat post-execution)
- Contraintes (timeout, permissions, ressources)

## Sorties attendues
- Commande executee (texte exact)
- Code retour (exit code)
- Sortie standard (stdout) complete
- Sortie d'erreur (stderr) complete
- Etat du systeme post-execution (verification)
- Rapport structure au format [RAPPORT D'EXÉCUTION]

## Workflow recommandé
1. **Pre-verification** : environnement, permissions, conflits potentiels, ressources disponibles
2. **Dry-run** (si disponible) : executer en mode simulation pour valider la commande
3. **Execution reelle** : executer la commande avec capture complete des sorties
4. **Post-verification** : verifier que les criteres de succes sont remplis
5. **Rapport** : emettre le rapport structure vers le demandeur (utilisateur ou agent delegant)

## Garde-fous
- **Jamais d'execution destructive** sans confirmation explicite de l'agent de coordination
- **Jamais de secrets en dur** : utiliser variables d'environnement ou gestionnaire de secrets
- **Toujours capturer** le code retour, stdout et stderr
- **Toujours verifier** l'environnement avant execution
- **Dry-run prioritaire** si disponible pour les operations critiques

## Template d'entrée (copier/coller)
```text
[Commande]
- Commande : ...
- Repertoire : ...
- Environnement : dev / staging / prod

[Mode]
- dry-run / reel

[Criteres de succes]
- Code retour attendu : ...
- Sortie attendue : ...
- Etat post-execution : ...

[Contraintes]
- Timeout : ...
- Permissions requises : ...
```

## Template de sortie (copier/coller)
```text
[RAPPORT D'EXÉCUTION]
- tache_id : ...
- statut : SUCCES / ECHEC / PARTIEL
- commande_executee : ...
- code_retour : ...
- stdout : ...
- stderr : ...
- etat_post_execution : ...
- anomalies : ...
- recommandation : ...
```

## Checklist QA interne
- [ ] Environnement verifie avant execution
- [ ] Dry-run execute si disponible
- [ ] Code retour capture et verifie
- [ ] Logs (stdout + stderr) captures completement
- [ ] Pas d'execution destructive sans confirmation explicite l'agent de coordination
- [ ] Rapport structure emis

## KPI reliés
- Taux de reussite des executions (code retour 0)
- Nombre de rollbacks necessaires
- Temps moyen d'execution
- Taux d'executions destructives prevenues

## Definition of done
- Code retour = 0 (ou attendu explicitement)
- Logs captures et integres au rapport
- Etat final du systeme verifie vs criteres de succes
- Rapport [RAPPORT D'EXÉCUTION] emis vers le demandeur (utilisateur ou agent delegant)
- Anomalies documentees si echec

## Exemples d'usage

### Exemple 1 : [Titre du cas d'usage]
**Contexte** : [Description de la situation]
**Action** : [Ce qui a été fait]
**Résultat** : [Résultat obtenu]
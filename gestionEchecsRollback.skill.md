# Gestion Echecs & Rollback

## Objectif
Gerer systematiquement les echecs d'execution avec documentation precise, evaluation de rollback et proposition claire a l'agent de coordination, sans execution autonome de remediation.

## Quand l'utiliser (triggers)
- Echec d'execution (code retour non-zero)
- Erreur bloquante detectee
- Besoin de rollback ou annulation
- Recuperation apres incident
- Activation de plan de contingence

## Hors périmètre
- Decisions de rollback autonomes (toujours demander validation de l'agent de coordination)
- Architecture de resilience globale (deleguer a l'agent d'architecture)
- Gestion d'incidents critiques multi-systemes (deleguer a l'agent de fiabilite/incidents)

## Inputs requis
- Tache echouee (commande, deploiement, operation)
- Logs d'erreur complets (stdout, stderr, traces)
- Etat du systeme post-echec (services, fichiers, BDD)
- Contexte d'execution (environnement, utilisateur, timestamp)

## Sorties attendues
- Documentation complete de l'anomalie
- Diagnostic de la cause probable
- Evaluation de faisabilite du rollback
- Proposition de remediation a l'agent de coordination (avec options)
- Pas d'execution autonome de rollback

## Workflow recommandé
1. **Documenter** l'echec avec logs complets et contexte
2. **Diagnostiquer** la cause probable (erreur config, permission, ressource, timeout, etc.)
3. **Evaluer** la faisabilite du rollback (reversible ? risques ? impacts ?)
4. **Proposer** options de remediation a l'agent de coordination (rollback / retry / contournement)
5. **Attendre** validation de l'agent de coordination avant toute action de recuperation

## Garde-fous
- **Anomalie systematiquement documentee** avec logs complets
- **Pas d'insistance en boucle** : apres 1 echec, remonter a l'agent de coordination (pas de retry aveugle)
- **Pas d'improvisation** : proposer des options, pas executer sans validation
- **Rollback evalue mais jamais execute sans ordre l'agent de coordination**
- **Proposition claire** : options avec risques/impacts documentes
- **Aucun rollback automatique** meme si trivial

## Template d'entrée (copier/coller)
```text
[Tache echouee]
- Commande / operation : ...
- Timestamp : ...

[Logs erreur]
- stdout : ...
- stderr : ...

[Etat systeme post-echec]
- Services : ...
- Fichiers : ...
- BDD : ...

[Contexte]
- Environnement : ...
- Utilisateur : ...
```

## Template de sortie (copier/coller)
```text
[Documentation anomalie]
- Tache : ...
- Erreur : ...
- Logs : ...

[Diagnostic]
- Cause probable : ...
- Type : config / permission / ressource / timeout / autre

[Evaluation rollback]
- Reversible : oui / non / partiel
- Risques rollback : ...
- Impacts rollback : ...

[Proposition a l'agent de coordination]
Option 1 : ...
Option 2 : ...
Option 3 : ...

Recommandation : ...
```

## Checklist QA interne
- [ ] Echec documente avec logs complets
- [ ] Pas d'insistance en boucle (1 echec = remontee l'agent de coordination)
- [ ] Pas d'improvisation ou de retry aveugle
- [ ] Rollback evalue avec risques/impacts
- [ ] Proposition claire a l'agent de coordination avec options documentees
- [ ] Aucune action autonome de rollback

## KPI reliés
- Taux de rollbacks reussis (parmi ceux executes)
- Temps moyen echec -> proposition l'agent de coordination
- Taux d'escalade vers l'agent de fiabilite/incidents
- Nombre d'echecs recurrents (meme cause)

## Definition of done
- Echec documente avec logs et contexte complet
- Evaluation de rollback complete (faisabilite, risques, impacts)
- Proposition structuree emise a l'agent de coordination avec options
- Aucune action autonome de remediation executee
- Anomalie tracee pour analyse post-mortem

## Exemples d'usage

### Exemple 1 : [Titre du cas d'usage]
**Contexte** : [Description de la situation]
**Action** : [Ce qui a été fait]
**Résultat** : [Résultat obtenu]
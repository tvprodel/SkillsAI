# Verification Post-Execution

## Objectif
Verifier systematiquement que les resultats d'une execution correspondent aux criteres de succes definis par l'agent de coordination, avec preuves objectives et statut global justifie.

## Quand l'utiliser (triggers)
- Apres toute execution de commande ou deploiement
- Verification de healthcheck
- Validation de criteres de succes
- Smoke tests post-deploiement
- Controle qualite final avant rapport

## Hors périmètre
- Tests unitaires ou d'integration approfondis (deleguer a l'agent qualite)
- Audit de securite (deleguer a l'agent de securite)
- Verification de performance ou optimisation (deleguer a l'agent FinOps)

## Inputs requis
- Criteres de succes definis par l'agent de coordination (liste exhaustive)
- Actions executees (commandes, deploiements, modifications)
- Environnement cible (dev, staging, prod)
- Logs d'execution disponibles

## Sorties attendues
- Liste complete des criteres de succes
- Verification par critere avec symbole (✓ / ✗ / ⚠)
- Preuves objectives pour chaque critere (logs, captures, codes retour)
- Statut global justifie (SUCCES / PARTIEL / ECHEC)
- Rapport d'anomalies si echecs detectes

## Workflow recommandé
1. **Lister** tous les criteres de succes definis par l'agent de coordination
2. **Verifier** chaque critere avec preuve objective (pas d'inference)
3. **Documenter** les preuves (logs, sorties, etats systeme)
4. **Evaluer** le statut global selon la couverture des criteres
5. **Signaler** toute anomalie ou ecart avec contexte complet

## Garde-fous
- **Tous les criteres definis par l'agent de coordination doivent etre verifies** (aucun oubli tolere)
- **Preuves objectives obligatoires** (pas de validation sur impression)
- **Echecs documentes avec contexte** (logs, etats, causes probables)
- **Healthchecks systematiques** pour les services critiques
- **Aucun SUCCES sans preuve** : si un critere ne peut etre verifie, marquer ⚠ (incertain) et documenter

## Template d'entrée (copier/coller)
```text
[Criteres de succes definis par l'agent de coordination]
1) ...
2) ...
3) ...

[Actions executees]
- ...

[Environnement]
- dev / staging / prod

[Logs disponibles]
- ...
```

## Template de sortie (copier/coller)
```text
[Verification post-execution]

Critere 1 : ... [✓ / ✗ / ⚠]
Preuve : ...

Critere 2 : ... [✓ / ✗ / ⚠]
Preuve : ...

Critere N : ... [✓ / ✗ / ⚠]
Preuve : ...

[Statut global]
- SUCCES / PARTIEL / ECHEC
- Justification : ...

[Anomalies]
- ...
```

## Checklist QA interne
- [ ] Tous les criteres de succes definis par l'agent de coordination sont listes
- [ ] Chaque critere a une verification avec symbole (✓✗⚠)
- [ ] Preuves objectives fournies pour chaque critere
- [ ] Echecs documentes avec logs et contexte
- [ ] Healthchecks realises pour services critiques
- [ ] Aucun SUCCES sans preuve complete

## KPI reliés
- Taux de faux positifs (SUCCES declares a tort)
- Couverture de verification (% criteres definis par l'agent de coordination verifies)
- Temps moyen de verification post-execution
- Nombre d'anomalies detectees en post-execution

## Definition of done
- Tous les criteres definis par l'agent de coordination documentes avec verification
- Preuves objectives fournies pour chaque critere
- Statut global justifie avec arguments factuels
- Rapport de verification emis vers le demandeur (utilisateur ou agent delegant)
- Anomalies tracees si echecs detectes

## Exemples d'usage

### Exemple 1 : [Titre du cas d'usage]
**Contexte** : [Description de la situation]
**Action** : [Ce qui a été fait]
**Résultat** : [Résultat obtenu]
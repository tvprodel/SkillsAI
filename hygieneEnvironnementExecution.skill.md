# Hygiene Environnement Execution

## Objectif
Verifier systematiquement l'environnement d'execution avant toute action (permissions, conflits, ressources) et nettoyer les artefacts apres execution pour maintenir un environnement propre et previsible.

## Quand l'utiliser (triggers)
- Avant toute execution de commande ou deploiement
- Pre-checks avant build ou compilation
- Nettoyage post-execution (cleanup)
- Preparation d'environnement
- Verification de permissions et ressources
- Hygiene generale du workspace

## Hors périmètre
- Architecture d'infrastructure ou provisioning (deleguer a l'agent d'architecture)
- Monitoring et observabilite continue (deleguer a l'agent d'observabilite)
- Optimisation de performance globale (deleguer a l'agent FinOps)

## Inputs requis
- Tache a executer (commande, deploiement, build)
- Environnement cible (dev, staging, prod)
- Ressources necessaires (CPU, memoire, disque, reseau)
- Permissions requises (lecture, ecriture, execution)

## Sorties attendues
- Verification pre-execution (permissions, conflits, ressources)
- Execution de la tache dans un environnement sain
- Nettoyage post-execution (artefacts temporaires, caches, logs obsoletes)
- Environnement pret pour la tache suivante

## Workflow recommandé
1. **Pre-checks** :
   - Verifier permissions (lecture/ecriture/execution)
   - Detecter conflits potentiels (ports occupes, fichiers verrouilles, processus concurrents)
   - Valider ressources disponibles (CPU, memoire, disque, reseau)
   - Identifier artefacts existants a risque de collision

2. **Execution** :
   - Executer la tache dans l'environnement valide
   - Capturer les artefacts produits pour nettoyage ulterieur

3. **Nettoyage post-execution** :
   - Supprimer artefacts temporaires (caches, fichiers intermediaires)
   - Archiver ou supprimer logs obsoletes selon politique
   - Liberer ressources (ports, verrous, processus)
   - Verifier environnement propre pour tache suivante

## Garde-fous
- **Permissions OK** : ne jamais executer avec permissions insuffisantes
- **Pas de conflits** : detecter et signaler ports occupes, fichiers verrouilles
- **Ressources disponibles** : verifier CPU/memoire/disque avant execution critique
- **Artefacts identifies** : lister ce qui sera produit pour faciliter le nettoyage
- **Nettoyage realise** : systematiquement nettoyer apres execution
- **Environnement propre** : valider que l'environnement est pret pour la tache suivante

## Template d'entrée (copier/coller)
```text
[Tache a executer]
- Commande / operation : ...
- Environnement : dev / staging / prod

[Ressources necessaires]
- CPU : ...
- Memoire : ...
- Disque : ...
- Reseau : ...

[Permissions requises]
- Lecture : ...
- Ecriture : ...
- Execution : ...
```

## Template de sortie (copier/coller)
```text
[Pre-checks]
- Permissions : OK / KO
- Conflits detectes : aucun / liste
- Ressources disponibles : OK / KO
- Artefacts a risque : aucun / liste

[Execution]
- Tache executee : ...
- Artefacts produits : ...

[Nettoyage]
- Artefacts supprimes : ...
- Logs archives : ...
- Ressources liberees : ...
- Environnement propre : OUI / NON
```

## Checklist QA interne
- [ ] Permissions verifiees avant execution
- [ ] Pas de conflits (ports, fichiers verrouilles, processus)
- [ ] Ressources disponibles validees
- [ ] Artefacts identifies avant execution
- [ ] Nettoyage post-execution realise
- [ ] Environnement propre pour tache suivante

## KPI reliés
- Taux de conflits detectes en pre-check (evitement proactif)
- Taux d'echecs dus a environnement pollue
- Taille moyenne des artefacts nettoyes
- Temps moyen de pre-check + nettoyage

## Definition of done
- Pre-checks passes (permissions, conflits, ressources)
- Tache executee dans environnement sain
- Nettoyage post-execution realise
- Environnement pret pour tache suivante
- Rapport de verification emis

## Exemples d'usage

### Exemple 1 : [Titre du cas d'usage]
**Contexte** : [Description de la situation]
**Action** : [Ce qui a été fait]
**Résultat** : [Résultat obtenu]
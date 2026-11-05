# Content Regression Checkpointing

## Objectif
Détecter automatiquement les fichiers texte nouveaux ou modifiés depuis le dernier audit de grammaire/orthographe, pour éviter de revoir systématiquement tout le contenu à chaque passage et concentrer l'effort sur les changements réels.

## Quand l'utiliser (triggers)
- Audit mensuel de grammaire/orthographe : lancement du script `grammarAZertYOrthMonthlyAudit.py` en tâche planifiée.
- Workflow de pre-commit/pre-release : vérification systématique avant diffusion.
- Audit de régression post-refactoring : s'assurer qu'aucune erreur n'a été introduite.

## Hors périmètre
- Analyse du contenu lui-même (grammaire, orthographe) → l'agent de relecture grammaticale.
- Traduction ou localisation → l'agent de traduction et localisation.
- Génération de contenu initial → l'agent de rédaction technique, l'agent de microcopie, l'agent de copywriting.

## Inputs requis
- **Racines de projets** : chemins absolus des projets à scanner (ex: `myAgentsTemplate`, `SalamancaDoc`).
- **Extensions surveillées** : `*.md`, `*.mdx`, `*.txt` (configurables).
- **Checkpoint précédent** : fichier JSON avec hash SHA256 de chaque fichier du dernier passage (ex: `multiAgentsFiles/checkpoints/grammarAZertYOrthCheckpoint.json`).
- **Serveur LanguageTool** (optionnel) : URL d'un serveur LanguageTool local pour pré-analyse grammaticale automatisée.

## Sorties attendues
- **Rapport d'audit** : fichier Markdown listant les fichiers nouveaux/modifiés à revoir par l'agent de relecture grammaticale.
- **Checkpoint mis à jour** : fichier JSON avec nouveaux hash SHA256 de tous les fichiers scannés.
- **Statistiques** : nombre de fichiers nouveaux, modifiés, inchangés, racines introuvables.

## Workflow recommandé
1. **Chargement du checkpoint précédent** : lecture du fichier JSON de checkpoint (hash SHA256 par fichier).
2. **Scan des racines de projets** : parcours récursif des dossiers, collecte des fichiers correspondant aux extensions surveillées.
3. **Calcul des hash SHA256** : hash de chaque fichier détecté.
4. **Comparaison avec checkpoint précédent** :
   - Fichier absent du checkpoint précédent → **nouveau**.
   - Fichier présent avec hash différent → **modifié**.
   - Fichier présent avec hash identique → **inchangé** (ignoré).
5. **Génération du rapport d'audit** : liste des fichiers nouveaux/modifiés avec statut et suggestions LanguageTool (si serveur disponible).
6. **Sauvegarde du nouveau checkpoint** : mise à jour du fichier JSON avec les nouveaux hash.

## Garde-fous
- **Ne jamais re-analyser un fichier inchangé** : optimisation coût/latence.
- **Gestion multi-projets** : racines configurables, support chemins absolus.
- **Robustesse aux racines manquantes** : signaler les chemins introuvables sans bloquer le scan des autres.
- **Fréquence recommandée** : mensuelle (tâche planifiée Windows ou cron).
- **Backup du checkpoint** : versionner le fichier JSON pour rollback si besoin.

## Template d'entrée (copier/coller)
```powershell
# Paramètres du script grammarAZertYOrthMonthlyAudit.py
-ProjectRoots @("C:\path\to\project1", "C:\path\to\project2")
-CheckpointPath "C:\path\to\checkpoints\grammarAZertYOrthCheckpoint.json"
-ReportRoot "C:\path\to\Logs\Agents"
-LanguageToolUrl "http://localhost:8081/v2/check"  # optionnel
```

## Template de sortie (copier/coller)
```markdown
# Audit Grammaire & Orthographe (FR/EN/NL) - YYYY-MM-DD_HHMMSS

**Owner** : l'agent de relecture grammaticale (Team Content)  
**Fréquence** : mensuelle  
**Racines projets scannées** : projet1, projet2  
**Racines introuvables** : projet3 (si applicable)

## Fichiers à revoir (X)

| Fichier | Statut | Suggestions LanguageTool |
|---|---|---|
| path/to/file1.md | Nouveau | 3 (détails via LanguageTool) |
| path/to/file2.md | Modifié | N/A (revue manuelle l'agent de relecture grammaticale requise) |

## Statistiques
- Fichiers nouveaux : X
- Fichiers modifiés : Y
- Fichiers inchangés : Z (non listés)
- Fichiers total scannés : X+Y+Z
```

## Checklist QA interne
- [ ] Checkpoint précédent chargé avec succès (ou créé si premier passage).
- [ ] Toutes les racines de projets configurées scannées (sauf celles introuvables, signalées).
- [ ] Hash SHA256 calculé pour chaque fichier détecté.
- [ ] Comparaison avec checkpoint précédent effectuée.
- [ ] Rapport d'audit généré avec liste complète fichiers nouveaux/modifiés.
- [ ] Nouveau checkpoint sauvegardé avec succès.
- [ ] Aucun fichier inchangé listé dans le rapport (optimisation).

## KPI reliés
- **Taux de détection** : (fichiers nouveaux/modifiés détectés / fichiers réellement changés) x 100 (cible : 100%).
- **Taux de faux positifs** : (fichiers signalés à tort comme modifiés / fichiers signalés) x 100 (cible : 0%).
- **Gain d'efficacité** : (temps audit avec checkpoints / temps audit sans checkpoints) x 100 (cible : < 30%, i.e. 70% de gain).
- **Couverture multi-projets** : (racines scannées / racines configurées) x 100 (cible : 100%).

## Definition of done
- Checkpoint précédent chargé (ou créé si premier passage).
- Toutes les racines de projets configurées scannées (sauf celles introuvables, signalées dans le rapport).
- Hash SHA256 calculé pour chaque fichier détecté.
- Comparaison effectuée, fichiers nouveaux/modifiés identifiés correctement (mesure : vérification manuelle échantillon).
- Rapport d'audit généré avec liste complète et suggestions LanguageTool (si serveur disponible).
- Nouveau checkpoint sauvegardé (preuve : fichier JSON mis à jour avec date/heure actuelle).
- Aucun fichier inchangé listé dans le rapport (mesure : inspection du rapport).

## Exemples d'usage

### Exemple 1 : Premier passage (création checkpoint initial)
**Contexte** : Aucun checkpoint existant, première exécution du script sur 2 projets (`myAgentsTemplate`, `SalamancaDoc`).  
**Action** : Scan de 150 fichiers (100 myAgentsTemplate + 50 SalamancaDoc), création du checkpoint initial avec 150 hash SHA256.  
**Résultat** : Rapport d'audit listant les 150 fichiers comme "nouveaux", checkpoint créé. l'agent de relecture grammaticale revoit les 150 fichiers, corrections proposées.

### Exemple 2 : Audit mensuel avec 10 fichiers modifiés
**Contexte** : Checkpoint du mois précédent avec 150 fichiers. Pendant le mois : 5 fichiers modifiés, 5 nouveaux, 140 inchangés.  
**Action** : Scan de 155 fichiers (150 précédents + 5 nouveaux), comparaison hash, détection de 10 fichiers à revoir (5 nouveaux + 5 modifiés).  
**Résultat** : Rapport d'audit listant les 10 fichiers, checkpoint mis à jour (155 hash). l'agent de relecture grammaticale revoit uniquement les 10 fichiers (gain 93% vs revue complète).

### Exemple 3 : Racine de projet introuvable
**Contexte** : 3 racines configurées (`myAgentsTemplate`, `SalamancaDoc`, `Projet3`), mais `Projet3` a été déplacé.  
**Action** : Scan de `myAgentsTemplate` et `SalamancaDoc` OK, erreur sur `Projet3`, signalée dans le rapport.  
**Résultat** : Rapport d'audit avec section "Racines introuvables: Projet3", checkpoint mis à jour pour les 2 projets scannés, utilisateur informé pour corriger la configuration.

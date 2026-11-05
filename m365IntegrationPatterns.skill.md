# M365 Integration Patterns

**Compétence** : Concevoir et implémenter intégrations Microsoft 365 : SharePoint/OneDrive, Planner, Power Automate, co-édition temps réel, gestion permissions.

**Agents utilisateurs** : l'agent Microsoft 365 (principal), l'agent d'intégration et d'automatisation (automatisations complexes)

## Quand l'utiliser (triggers)
- Intégrer SharePoint/OneDrive avec Teams/Outlook
- Automatiser workflows avec Power Automate basique
- Configurer co-édition temps réel (Office Online)
- Gérer permissions et partages Microsoft 365
- Intégrer Planner/Tasks dans écosystème M365

## Hors périmètre
- Infrastructure SharePoint Server → l'agent de packaging applicatif
- Power Automate Premium (workflows complexes, RPA) → l'agent d'intégration et d'automatisation
- Développement custom API Microsoft Graph → l'agent de développement .NET
- Sécurité réseau/firewall M365 → l'agent réseau et sécurité réseau

---

## Compétences

### 1. Intégrations SharePoint/OneDrive ↔ Teams/Outlook

**Description** : Connecter SharePoint et OneDrive avec Teams et Outlook pour centraliser collaboration fichiers.

**SharePoint ↔ Teams** :

**Ajouter bibliothèque SharePoint dans Teams** :
```
Configuration :
1. Teams → Canal → Onglet "+" → SharePoint
2. Options :
   - Bibliothèque SharePoint site existant
   - Page SharePoint
   - Liste SharePoint

Exemple : Onglet "Documents Projet X"
- Connecter bibliothèque SharePoint "/sites/ProjetX/Documents partagés"
- Tous fichiers SharePoint accessibles depuis Teams
- Co-édition temps réel directement dans Teams

Avantages :
- Centralisation fichiers (pas de doublons OneDrive personnel)
- Permissions SharePoint héritées (gouvernance centralisée)
- Versioning automatique SharePoint
```

**SharePoint comme stockage backend Teams** :
```
Chaque équipe Teams crée automatiquement :
- Site SharePoint associé (/sites/[NomEquipe])
- Bibliothèque "Documents partagés" (onglet "Fichiers" Teams)
- Listes SharePoint (si onglet "Listes" ajouté)

Architecture :
Équipe Teams "Marketing France"
└── Site SharePoint "/sites/MarketingFrance"
    ├── Documents partagés (fichiers canal "Général")
    ├── Canal Créatifs (sous-dossier "Créatifs")
    ├── Canal Événements (sous-dossier "Événements")
    └── Listes SharePoint (si configurées)

Accès :
- Via Teams : Onglet "Fichiers"
- Via SharePoint : URL /sites/MarketingFrance/Documents partagés
- Via OneDrive : Synchronisation locale (voir ci-dessous)
```

**OneDrive ↔ Outlook (pièces jointes cloud)** :

**Envoyer pièce jointe OneDrive depuis Outlook** :
```
Nouveau message → Joindre fichier → Parcourir emplacements cloud

Options :
1. Lien OneDrive :
   - Destinataire accède fichier OneDrive (pas de copie)
   - Permissions configurables (lecture seule, modification)
   - Mises à jour fichier visibles tous destinataires

2. Copie locale :
   - Fichier copié en pièce jointe classique
   - Pas de lien OneDrive (destinataire reçoit snapshot)

Recommandation :
- Lien OneDrive pour fichiers volumineux (> 5 Mo)
- Lien OneDrive pour collaboration continue (modifications partagées)
- Copie locale pour archivage (destinataire garde version figée)
```

**Synchronisation OneDrive local** :
```
OneDrive → Synchroniser bibliothèque SharePoint

Configuration :
1. SharePoint → Bibliothèque "Documents partagés" → Synchroniser
2. Client OneDrive synchronise dossier local :
   C:\Users\[User]\OneDrive - [Entreprise]\[NomSite]\Documents partagés
3. Modifications locales → Synchronisation automatique SharePoint

Avantages :
- Accès hors ligne (fichiers locaux)
- Explorateur fichiers Windows (pas besoin navigateur)
- Synchronisation bidirectionnelle automatique

Limites :
- Limite 300k fichiers par bibliothèque synchronisée
- Chemins > 400 caractères non supportés
- Fichiers > 250 Go non synchronisables
```

**Livrables** :
- Onglets SharePoint configurés dans Teams (par canal/équipe)
- Synchronisation OneDrive locale active (bibliothèques clés)
- Guide partage fichiers OneDrive depuis Outlook

**Pièges à éviter** :
- Doublons OneDrive personnel vs SharePoint équipe (privilégier SharePoint pour projets)
- Permissions OneDrive trop ouvertes (vérifier "Toute personne avec lien")
- Synchronisation trop de bibliothèques (saturation disque local)

---

### 2. Power Automate basique (automatisations no-code/low-code)

**Description** : Créer workflows automatisés simples reliant applications Microsoft 365.

**Templates Power Automate courants** :

**1. Email → SharePoint/OneDrive** :
```
Workflow : "Enregistrer pièce jointe email dans SharePoint"

Déclencheur : Quand email reçu (Outlook)
Conditions :
- De : client@entreprise.com
- Objet : Contient "Facture"
- A pièce jointe : Oui

Actions :
1. Enregistrer pièce jointe dans SharePoint /sites/Comptabilité/Factures
2. Envoyer notification Teams canal "Compta" avec lien fichier
3. Créer item liste SharePoint "Factures à traiter" (statut : Nouveau)

Résultat : Factures clients archivées automatiquement + notification équipe compta
```

**2. Formulaire Forms → Création tâche Planner/Création ticket** :
```
Workflow : "Nouvelle demande support → Ticket Planner"

Déclencheur : Nouvelle réponse Forms (formulaire "Demande Support IT")

Actions :
1. Extraire champs Forms :
   - Nom utilisateur
   - Description problème
   - Priorité (Basse/Moyenne/Haute)
   - Catégorie (Matériel/Logiciel/Réseau)

2. Créer tâche Planner :
   - Plan : "Support IT"
   - Compartiment : Selon catégorie
   - Titre : "[Priorité] Demande de [Nom utilisateur]"
   - Description : Copier description problème
   - Échéance : J+2 si Haute, J+5 si Moyenne, J+10 si Basse

3. Envoyer email confirmation utilisateur :
   - Objet : "Demande enregistrée - Ticket #[ID]"
   - Contenu : Récapitulatif + lien Planner

Résultat : Demandes support automatiquement transformées en tâches Planner
```

**3. Approbation workflow** :
```
Workflow : "Approbation note de frais"

Déclencheur : Nouveau fichier OneDrive dossier "Notes de frais"

Actions :
1. Extraire métadonnées fichier (nom, montant si dans nom fichier)
2. Démarrer approbation :
   - Titre : "Approbation note de frais [Nom employé]"
   - Approbateur : manager@entreprise.com
   - Détails : Lien fichier OneDrive

3. Si approuvé :
   - Déplacer fichier vers "Notes de frais/Approuvées"
   - Envoyer email employé : "Note de frais approuvée"
   - Créer ligne Excel tableau "Comptabilité notes de frais"

4. Si refusé :
   - Déplacer fichier vers "Notes de frais/Refusées"
   - Envoyer email employé : "Note de frais refusée - Raison : [Commentaires approbateur]"

Résultat : Process approbation automatisé, traçabilité complète
```

**4. Synchronisation calendrier → Liste SharePoint** :
```
Workflow : "Créer événement SharePoint pour réunions importantes"

Déclencheur : Nouveau rendez-vous Outlook (catégorie "Projet X")

Actions :
1. Vérifier si catégorie = "Projet X"
2. Créer item liste SharePoint "Événements Projet X" :
   - Titre : Objet réunion
   - Date : Date/heure début
   - Participants : Liste participants
   - Lieu : Salle/Teams

3. Envoyer notification Teams canal "Projet X" :
   - Message : "Nouvelle réunion planifiée : [Titre] le [Date]"
   - Lien : Vers item SharePoint

Résultat : Réunions importantes trackées dans liste SharePoint centralisée
```

**Livrables** :
- 5-10 workflows Power Automate types (templates réutilisables)
- Documentation workflows (déclencheur, actions, résultat attendu)
- Guide utilisateur création workflow basique

**Pièges à éviter** :
- Workflows trop complexes (> 30 actions = difficulté maintenance, privilégier l'agent d'intégration et d'automatisation)
- Boucles infinies (workflow A déclenche B qui déclenche A)
- Permissions insuffisantes (workflow échoue si accès SharePoint/OneDrive manquant)
- Quotas dépassés (Power Automate gratuit limité 750 exécutions/mois, Premium nécessaire au-delà)

---

### 3. Co-édition temps réel et synchronisation

**Description** : Configurer et optimiser co-édition simultanée fichiers Office (Word, Excel, PowerPoint).

**Co-édition Office Online** :

**Prérequis co-édition** :
```
Conditions :
1. Fichier stocké SharePoint/OneDrive (PAS de fichier local synchronisé)
2. Fichier format moderne (.docx, .xlsx, .pptx, pas .doc/.xls/.ppt)
3. Éditeurs disposent licences Microsoft 365 (Office Online minimum)
4. Pas de protection fichier (pas de mot de passe, pas de mode lecture seule)

Architecture :
Fichier : /sites/ProjetX/Documents partagés/Rapport.docx
├── Utilisateur 1 : Édite section 1 (paragraphe 1-5)
├── Utilisateur 2 : Édite section 2 (paragraphe 6-10)
├── Utilisateur 3 : Commente section 1 (suggestions)
└── Serveur SharePoint : Synchronise modifications temps réel (< 5 secondes)
```

**Fonctionnalités co-édition** :
```
Indicateurs visuels (Word/Excel/PowerPoint Online) :
- Curseurs colorés : Position chaque éditeur en temps réel
- Initiales : Bulle avec nom éditeur (survol)
- Sélections : Zones éditées en surbrillance couleur
- Présence : Liste éditeurs actifs (coin supérieur droit)

Synchronisation :
- Modifications : Visibles tous éditeurs < 5 secondes
- Conflits : Résolution automatique (dernière modification gagne)
- Versioning : SharePoint sauvegarde versions automatiquement (restauration possible)

Commentaires et révisions :
- Commentaires : Visibles temps réel (mode révision)
- Suivi modifications : Activable (Word) pour traçabilité éditions
- @Mentions : Notifier collègue spécifique (@nom dans commentaire)
```

**Co-édition Excel spécificités** :

**Mode co-édition Excel** :
```
Excel Online vs Excel Desktop :

Excel Online :
- Co-édition native (toujours active si fichier SharePoint/OneDrive)
- Limitations : Pas de macros VBA, pas de Power Query édition
- Idéal : Saisie données, tableaux simples, graphiques basiques

Excel Desktop (Microsoft 365) :
- Co-édition disponible si "Enregistrement automatique" activé
- Activer : Fichier → Options → Enregistrer → ✅ Enregistrement automatique OneDrive/SharePoint
- Synchronisation : Toutes 5-10 secondes
- Fonctionnalités complètes : VBA, Power Query, Power Pivot

Conflits co-édition Excel :
- Cellule modifiée simultanément → Dernière modification gagne
- Notification : "Modifications en conflit détectées" (historique versions)
- Bonnes pratiques : Répartir zones édition (utilisateur 1 = colonnes A-D, utilisateur 2 = colonnes E-H)
```

**Synchronisation fichiers hors ligne** :

**Mode hors ligne OneDrive** :
```
OneDrive → Paramètres → Fichiers à la demande

Options :
1. Disponible en ligne uniquement :
   - Fichier cloud (pas d'espace disque local)
   - Téléchargement à l'ouverture

2. Toujours conserver sur cet appareil :
   - Fichier téléchargé localement (accès hors ligne)
   - Synchronisation automatique reconnexion

3. Libérer de l'espace :
   - Supprimer copie locale (garder cloud uniquement)

Co-édition hors ligne :
- Modifications hors ligne enregistrées localement
- Synchronisation automatique reconnexion réseau
- Conflits possibles (si autres éditeurs pendant hors ligne)
- Résolution manuelle conflits (choisir version à conserver)
```

**Livrables** :
- Configuration co-édition validée (fichiers SharePoint/OneDrive)
- Guide bonnes pratiques co-édition (répartition zones, gestion conflits)
- Paramétrage fichiers à la demande OneDrive

**Pièges à éviter** :
- Fichiers locaux synchronisés (OneDrive sync) = co-édition limitée (privilégier Office Online/Desktop avec enregistrement auto)
- Modifications simultanées même cellule Excel = conflits fréquents (coordonner zones)
- Protection fichiers (mot de passe) bloque co-édition (retirer protection)
- Versions Office anciennes (< 2016) non compatibles co-édition temps réel

---

### 4. Gestion permissions et partages

**Description** : Configurer permissions granulaires et partages sécurisés dans écosystème Microsoft 365.

**Niveaux permissions SharePoint/OneDrive** :

**Permissions SharePoint** :
```
Hiérarchie permissions :
1. Propriétaire (Full Control) :
   - Gérer site, permissions, bibliothèques
   - Supprimer éléments
   - Modifier structure site

2. Membre (Edit) :
   - Ajouter, modifier, supprimer fichiers/dossiers
   - Créer listes, bibliothèques (si autorisé)

3. Visiteur (Read) :
   - Lire fichiers, listes
   - Télécharger fichiers
   - Pas de modification

Permissions personnalisées :
- Contribute : Ajouter/modifier fichiers, pas supprimer
- Design : Modifier pages site (webmasters)
- Approve : Approuver éléments (workflows)
```

**Partage externe OneDrive/SharePoint** :

**Types liens partage** :
```
OneDrive/SharePoint → Partager fichier

Options partage :
1. Toute personne avec le lien (Anyone) :
   - Lien anonyme (pas d'authentification)
   - ⚠️ Risque : Lien transmissible (contrôle limité)
   - Usage : Documents publics uniquement

2. Personnes de [Organisation] (Organization) :
   - Authentification Microsoft 365 requise
   - Limité utilisateurs tenant (domaine entreprise)
   - Sécurisé : Contrôle accès

3. Personnes spécifiques (Specific people) :
   - Emails individuels (internes ou invités externes)
   - Plus sécurisé (liste accès explicite)
   - Recommandé : Documents sensibles

4. Personnes ayant déjà accès (Existing access) :
   - Lien pour utilisateurs ayant déjà permissions
   - Pas de nouveaux accès accordés
   - Utile : Partager URL sans modifier permissions

Permissions lien :
- Peut afficher (Read) : Lecture seule
- Peut modifier (Edit) : Lecture + écriture

Expiration lien :
- Définir date expiration (ex: 30 jours)
- Lien désactivé automatiquement après expiration
- Recommandé : Documents temporaires (projets courts)

Mot de passe lien (OneDrive) :
- Protéger lien par mot de passe
- Destinataires doivent saisir mot de passe avant accès
- Sécurité renforcée (même si lien transmis)
```

**Gestion invités externes (Guests)** :

**Inviter utilisateurs externes SharePoint/Teams** :
```
Configuration admin Microsoft 365 (prérequis) :
- Centre admin → Paramètres → Org settings → Guests
- ✅ Autoriser partage externe (SharePoint/OneDrive/Teams)
- Restrictions : Domaines autorisés/bloqués (ex: autoriser uniquement @partenaire.com)

Inviter invité :
1. SharePoint/Teams → Partager site/équipe
2. Ajouter email externe (ex: contact@partenaire.com)
3. Permissions : Membre (Edit) ou Visiteur (Read)
4. Message personnalisé (optionnel)
5. Envoyer → Invité reçoit email avec lien acceptation

Processus invité :
1. Clic lien email → Accepter invitation
2. Compte invité créé automatiquement (Azure AD B2B)
3. Accès limité aux ressources partagées (pas d'accès global tenant)

Permissions invités :
- Accès uniquement sites/équipes/fichiers partagés explicitement
- Pas de création équipes (sauf si autorisé admin)
- Affichage annuaire limité (contacts équipe uniquement)

Audit invités :
- Centre admin → Utilisateurs → Invités
- Lister tous invités actifs
- Supprimer invités inactifs (nettoyage régulier)
```

**Audit et rapports partages** :

**Vérifier qui a accès fichier** :
```
SharePoint/OneDrive → Fichier → "..." → Gérer l'accès

Informations affichées :
- Liens actifs (Anyone, Organization, Specific people)
- Utilisateurs avec accès direct (permissions explicites)
- Accès hérité (permissions site/dossier parent)

Actions :
- Révoquer lien : Désactiver lien partage
- Modifier permissions : Changer Read ↔ Edit
- Copier lien : Obtenir URL partage

Audit complet (Admin SharePoint) :
- Centre admin SharePoint → Rapports → Partage
- Fichiers partagés en externe (par site, utilisateur)
- Liens anonymes actifs (risque sécurité)
- Invités par domaine (partenaires externes)
```

**Livrables** :
- Politique partages entreprise (guidelines sécurisées)
- Configuration permissions types (par site/bibliothèque)
- Audit invités externes (liste + nettoyage)
- Guide utilisateur partage sécurisé

**Pièges à éviter** :
- Liens "Toute personne" sur documents sensibles (privilégier "Personnes spécifiques")
- Invités jamais supprimés (dérive accès, audit régulier obligatoire)
- Permissions héritées non vérifiées (utilisateurs accès via dossier parent)
- Partage sans expiration (lien actif indéfiniment = risque sécurité)

---

## Objectif

Intégrer et automatiser écosystème Microsoft 365 pour :
- Centraliser collaboration fichiers (SharePoint/OneDrive ↔ Teams/Outlook)
- Automatiser workflows simples (Power Automate no-code)
- Optimiser co-édition temps réel (synchronisation, conflits)
- Sécuriser partages et permissions (gouvernance accès)

---

## Inputs requis

- **Besoin intégration** : SharePoint/OneDrive, Planner, Power Automate, permissions
- **Architecture actuelle** : Sites SharePoint, structure Teams, OneDrive
- **Workflows à automatiser** : Processus manuels fréquents (emails, approbations, etc.)
- **Politique sécurité** : Règles partage externe, invités, expiration liens
- **Niveau maturité M365** : Débutant, intermédiaire, avancé

---

## Sorties attendues

**Intégrations** :
- Onglets SharePoint configurés Teams (bibliothèques clés)
- Synchronisation OneDrive active (fichiers locaux)
- Guide partage OneDrive depuis Outlook

**Automatisations** :
- 5-10 workflows Power Automate types (templates)
- Documentation workflows (déclencheur, actions)

**Co-édition** :
- Configuration validée (fichiers SharePoint/OneDrive)
- Guide bonnes pratiques (zones, conflits)

**Permissions** :
- Politique partages documentée
- Audit invités réalisé (nettoyage)
- Configuration permissions types

---

## Workflow recommandé

1. **Audit architecture** : Sites SharePoint, équipes Teams, structure OneDrive
2. **Identifier besoins intégration** : Fichiers à centraliser, workflows à automatiser
3. **Configurer intégrations** : SharePoint ↔ Teams, OneDrive ↔ Outlook
4. **Créer workflows Power Automate** : Templates 5-10 cas usage fréquents
5. **Activer co-édition** : Fichiers SharePoint/OneDrive, enregistrement auto
6. **Définir politique partages** : Guidelines sécurisées, types liens autorisés
7. **Configurer permissions** : Sites, bibliothèques, fichiers sensibles
8. **Auditer invités** : Liste, nettoyage, suivi régulier
9. **Former utilisateurs** : Sessions pratiques, guides
10. **Mesurer adoption** : KPI utilisation, feedback

---

## Garde-fous

- **SharePoint** : Limiter propriétaires sites (max 2-5 par site, redondance)
- **Power Automate** : Workflows simples uniquement (> 30 actions → l'agent d'intégration et d'automatisation)
- **Partages** : Interdire "Toute personne" par défaut (activer uniquement si justifié)
- **Invités** : Audit trimestriel obligatoire (supprimer inactifs > 90 jours)
- **Co-édition** : Fichiers SharePoint/OneDrive uniquement (éviter fichiers locaux synchronisés)

---

## Template d'entrée (copier/coller)
```text
[Environnement Microsoft 365]
- Services et tenant concernés : ...
- Sites, bibliothèques, équipes ou flux actuels : ...
- Utilisateurs, groupes et permissions concernés : ...
- Résultat attendu et contraintes : ...
```

## Template de sortie (copier/coller)
```text
[Intégration proposée]
- Composants et flux configurés : ...
- Permissions et propriétaire : ...
- Tests de synchronisation/co-édition : ...
- Limites, erreurs et contrôles à maintenir : ...
```

## Templates copier/coller

**Template workflow Power Automate : Email → SharePoint** :
```
Nom : Enregistrer PJ emails dans SharePoint

Déclencheur : Quand email reçu (Outlook)
Condition : A pièce jointe = Oui ET De = [expéditeur cible]

Actions :
1. Pour chaque pièce jointe :
   - Enregistrer dans SharePoint [Chemin bibliothèque]
2. Envoyer notification Teams [Canal] : "Nouveau fichier : [Nom PJ]"
```

**Template permissions SharePoint bibliothèque** :
```
Bibliothèque : Documents partagés Projet X

Permissions :
- Propriétaires (2) : chef.projet@entreprise.com, backup@entreprise.com
- Membres (équipe projet, 15 pers) : Contribute (Ajouter/Modifier, pas Supprimer)
- Visiteurs (direction, 5 pers) : Read (Lecture seule)
- Invités externes (client, 2 pers) : Read, expiration 90 jours
```

**Template lien partage sécurisé** :
```
Partage fichier sensible (Rapport financier Q2)

Type lien : Personnes spécifiques
Emails : direction@entreprise.com, cfo@entreprise.com
Permission : Peut afficher (Read)
Expiration : 30 jours
Mot de passe : FinQ2_2026! (communiqué séparément)
```

---

## Checklist QA interne

- [ ] Onglets SharePoint configurés Teams (bibliothèques clés accessibles)
- [ ] Synchronisation OneDrive active (fichiers offline disponibles)
- [ ] Workflows Power Automate testés (déclencheur, actions, résultat validés)
- [ ] Co-édition fonctionnelle (curseurs temps réel visibles, synchronisation < 5s)
- [ ] Politique partages documentée (guidelines, types liens autorisés)
- [ ] Permissions configurées (propriétaires, membres, visiteurs, invités)
- [ ] Audit invités réalisé (liste actifs, inactifs supprimés)
- [ ] Guide utilisateur fourni (intégrations, workflows, partages)
- [ ] Formation utilisateurs réalisée (sessions pratiques)

---

## KPI

- **Adoption SharePoint** : % fichiers centralisés SharePoint vs OneDrive personnel (cible ≥ 80%)
- **Automatisation** : Nombre workflows actifs Power Automate (cible 10-20 workflows types)
- **Co-édition** : % fichiers co-édités simultanément (indicateur collaboration)
- **Sécurité** : % liens "Toute personne" sur total partages (cible < 10%)
- **Invités** : Taux invités inactifs > 90j (cible < 5%, audit trimestriel)

---

## Definition of done

- [ ] Intégrations SharePoint ↔ Teams configurées (onglets actifs)
- [ ] Synchronisation OneDrive active (fichiers clés hors ligne)
- [ ] Workflows Power Automate créés (5-10 templates fonctionnels)
- [ ] Co-édition validée (tests simultanés, synchronisation temps réel)
- [ ] Politique partages documentée et diffusée
- [ ] Permissions configurées (sites, bibliothèques, fichiers sensibles)
- [ ] Audit invités réalisé (liste + nettoyage)
- [ ] Guide utilisateur fourni (captures, workflows)
- [ ] Formation utilisateurs réalisée (sessions pratiques)
- [ ] KPI adoption mesurés (SharePoint ≥ 80%, liens sécurisés ≥ 90%)

---

## Exemples

**Exemple 1 : Intégration SharePoint ↔ Teams projet**
```
Équipe Teams : "Projet Migration ERP"
Site SharePoint : /sites/ProjetMigrationERP

Configuration :
1. Canal "Général" → Onglet "Documents" (par défaut = SharePoint /Documents partagés)
2. Canal "Cahier charges" → Onglet "+ SharePoint" → Bibliothèque "/Cahier charges"
3. Canal "Tests" → Onglet "+ SharePoint" → Liste "Tests UAT" (suivi bugs)

Synchronisation OneDrive locale :
- Bibliothèque "Documents partagés" synchronisée
- Chemin local : C:\Users\[User]\OneDrive - Entreprise\Projet Migration ERP\Documents partagés
- Accès hors ligne : Oui

Résultat : Fichiers projet centralisés SharePoint, accessibles Teams + hors ligne
```

**Exemple 2 : Workflow Power Automate demande congés**
```
Nom : Demande congés → Approbation manager

Déclencheur : Nouvelle réponse Forms "Demande congés"

Actions :
1. Extraire champs Forms :
   - Employé : [Nom]
   - Dates : [Date début] - [Date fin]
   - Nombre jours : [Calcul auto]
   - Type : Congés payés / RTT / Exceptionnel

2. Démarrer approbation :
   - Titre : "Demande congés [Nom] : [Dates]"
   - Approbateur : [Manager email]
   - Timeout : 5 jours

3. Si approuvé :
   - Créer événement Outlook calendrier partagé "Absences Équipe" (toute journée)
   - Envoyer email employé : "Congés approuvés"
   - Ajouter ligne Excel OneDrive "Suivi congés 2026.xlsx"

4. Si refusé :
   - Envoyer email employé : "Congés refusés - Raison : [Commentaires manager]"

Résultat : Process approbation congés 100% automatisé, traçabilité Excel
```

**Exemple 3 : Partage sécurisé dossier externe partenaire**
```
Contexte : Partager documents projet avec partenaire externe (durée projet 6 mois)

Configuration SharePoint :
1. Créer dossier "Partenaire X" dans /sites/ProjetY/Documents partagés
2. Permissions dossier (héritage rompu) :
   - Propriétaire : chef.projet@entreprise.com
   - Membres internes (équipe, 8 pers) : Contribute
   - Invités externes (partenaire, 3 pers) : Read
3. Inviter invités :
   - Emails : contact1@partenaire.com, contact2@partenaire.com, contact3@partenaire.com
   - Permission : Visiteur (Read)
   - Expiration : 180 jours (fin projet prévue)
4. Notification Teams canal "Projet Y" : "Dossier partenaire configuré : [Lien]"

Audit :
- Mensuel : Vérifier activité invités (qui accède, quand)
- Fin projet : Supprimer invités (ou prolonger si maintenance)

Résultat : Partage sécurisé, traçable, temporaire (expiration auto)
```

---

## Contraintes

- **Quotas OneDrive** : 1 To/utilisateur (Microsoft 365 E3/E5), extensible sur demande admin
- **Quotas SharePoint** : 25 To + 10 Go/licence achetée (tenant global)
- **Synchronisation OneDrive** : Max 300k fichiers par bibliothèque, chemins < 400 caractères
- **Power Automate** : Gratuit limité 750 exécutions/mois, Premium obligatoire au-delà (ou workflows complexes RPA)
- **Invités** : Limité 5x nombre licences (ex: 100 licences = max 500 invités), audit régulier recommandé
- **Co-édition** : Nécessite licences Microsoft 365 (Office Online minimum), fichiers modernes (.docx/.xlsx/.pptx)

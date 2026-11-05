# Teams Collaboration Best Practices

**Compétence** : Concevoir et administrer une architecture Microsoft Teams efficace : gouvernance canaux/équipes, paramétrage réunions, intégration apps tierces, politiques notifications.

**Agents utilisateurs** : l'agent Microsoft 365 (principal)

## Quand l'utiliser (triggers)
- Structurer équipes et canaux (architecture d'équipe)
- Configurer gouvernance Teams (stratégies, permissions)
- Optimiser réunions Teams (paramétrage, enregistrement, transcription)
- Intégrer apps tierces dans Teams (onglets, bots, connecteurs)
- Gérer notifications et politiques de messagerie

## Hors périmètre
- Infrastructure Teams Backend (Exchange Online, AD) → l'agent de packaging applicatif
- Développement custom apps Teams → l'agent de développement .NET
- Gouvernance Microsoft 365 globale (licences, tenant) → hors périmètre
- Sécurité réseau/firewall Teams → l'agent réseau et sécurité réseau

---

## Compétences

### 1. Architecture canaux/équipes et gouvernance

**Description** : Concevoir une structure Teams cohérente et gouvernable pour optimiser collaboration et adoption.

**Principes d'architecture Teams** :

**Structure recommandée** :
```
Équipe (Team)
├── Canal Général (par défaut, non supprimable)
├── Canaux standards (publics, tous membres)
│   ├── 📢 Annonces
│   ├── 💬 Discussion générale
│   ├── 📁 Ressources partagées
│   └── 🎯 Projets actifs
└── Canaux privés (accès restreint)
    ├── 🔒 Direction
    └── 🔐 RH - Confidentiel

Bonnes pratiques :
- Max 200 canaux par équipe (limite Microsoft)
- Canaux thématiques (éviter trop de canaux = adoption faible)
- Nommage cohérent : emoji + titre clair
- Canaux privés pour sujets sensibles uniquement (difficulté gouvernance)
```

**Types d'équipes** :
```
Équipe de projet : Cycle de vie limité, archivage automatique
- Exemple : "Projet Migration ERP 2026"
- Configuration : Archivage auto après 6 mois inactivité

Équipe départementale : Permanente, structure stable
- Exemple : "Marketing France"
- Configuration : Canaux standards + canaux privés direction

Équipe transverse : Multi-départements, collaboration ponctuelle
- Exemple : "Comité Innovation"
- Configuration : Invités externes autorisés, canaux publics prioritaires
```

**Gouvernance et stratégies** :

**Stratégie de nommage** :
```powershell
# Exemple convention nommage (via Azure AD)
Format : [Département]-[Projet/Fonction]-[Localisation]
Exemples :
- MKT-CampagneQ2-FR
- IT-SupportN1-BE
- FIN-Comptabilité-Siège

Avantages :
- Recherche facilitée
- Cohérence visuelle
- Identification rapide
```

**Stratégie d'expiration** :
```
Configuration recommandée :
- Équipes projets : expiration 180 jours (notification propriétaires J-30)
- Équipes départementales : pas d'expiration
- Équipes inactives (0 activité 90j) : notification renouvellement obligatoire

Outil : Centre d'administration Microsoft 365 → Groupes Microsoft 365 → Stratégies d'expiration
```

**Permissions et rôles** :
```
Propriétaire (Owner) :
- Gérer membres/paramètres équipe
- Créer/supprimer canaux
- Max 100 propriétaires par équipe (recommandation : 2-5)

Membre (Member) :
- Publier messages, fichiers
- Créer canaux (si autorisé par propriétaire)

Invité (Guest) :
- Accès limité (uniquement équipes invitées)
- Pas de création d'équipe
- Permissions restreintes (configurable)

Bonnes pratiques :
- Minimum 2 propriétaires par équipe (redondance)
- Désactiver création canaux par membres (gouvernance stricte)
- Limiter invités externes (politique sécurité)
```

**Livrables** :
- Architecture Teams documentée (organigramme équipes/canaux)
- Guide de gouvernance (nommage, expiration, permissions)
- Matrice de décision (Équipe vs Canal vs Chat de groupe)

**Pièges à éviter** :
- Trop de canaux = adoption faible, confusion utilisateurs
- Canaux privés excessifs = silos communication
- Pas de stratégie expiration = équipes fantômes (dérive)

---

### 2. Réunions efficaces (paramétrage, enregistrement, transcription)

**Description** : Configurer et optimiser réunions Teams pour productivité maximale.

**Workflows clés** :

**Paramétrage réunion avancé** :
```
Options de réunion (Paramètres avancés) :

Qui peut contourner salle d'attente ?
- Recommandé : Tous (si réunion interne)
- Sécurisé : Uniquement organisateur et co-organisateurs (si invités externes)

Qui peut présenter ?
- Par défaut : Tous les participants
- Recommandé présentations formelles : Uniquement organisateur

Autoriser micro pour participants ?
- Activé par défaut (participants peuvent se démuter)
- Désactiver pour webinaires > 50 participants (contrôle organisateur)

Autoriser caméra ?
- Activé par défaut
- Désactiver pour économiser bande passante (réunions > 100 participants)

Activer chat réunion ?
- Activé par défaut (recommandé pour collaboration)
- Désactiver pour présentations formelles (éviter distractions)

Autoriser réactions (👍, ❤️, 😂) ?
- Activé (engagement réunions)
- Désactiver si réunions très formelles
```

**Enregistrement et transcription** :
```
Enregistrement cloud :
- Démarrage : Bouton "Enregistrer" (organisateur/co-organisateurs uniquement)
- Stockage : OneDrive organisateur (réunion unique) ou SharePoint (réunion canal)
- Durée conservation : 60 jours par défaut (configurable tenant)
- Permissions : Partagé automatiquement avec participants

Transcription automatique (FR/EN/NL/DE...) :
- Activation : Paramètres réunion → Activer transcription
- Disponibilité : Post-réunion (délai 5-15 minutes selon durée)
- Recherche : Recherche plein texte dans transcription
- Export : Téléchargement VTT, DOCX

Sous-titres en direct :
- Activation : Pendant réunion → "..." → Activer sous-titres en direct
- Langues : FR, EN, NL, DE, ES, IT, PT
- Précision : ~85-90% (selon qualité audio)

Livrables :
- Vidéo enregistrement cloud (MP4)
- Transcription (VTT, DOCX)
- Chat réunion (archivé)
- Fichiers partagés pendant réunion
```

**Templates réunions récurrentes** :
```
Configuration réunion modèle :
1. Créer réunion type (ex: "Standup Hebdo Équipe Dev")
2. Paramétrer options (salle d'attente, présentateurs, enregistrement auto)
3. Ajouter ordre du jour type (template)
4. Configurer récurrence (quotidien, hebdo, mensuel)
5. Enregistrer comme modèle réutilisable

Ordre du jour standardisé (canal Wiki Teams) :
# Standup Hebdo Équipe Dev
- Tour de table (5 min/personne)
- Revue sprint (avancement, blocages)
- Prochaines actions
- Questions ouvertes
```

**Livrables** :
- Politique réunions Teams (guidelines entreprise)
- Templates réunions récurrentes
- Guide utilisateur enregistrement/transcription

**Pièges à éviter** :
- Enregistrement sans consentement participants (RGPD : informer avant d'enregistrer)
- Salle d'attente désactivée = risque sécurité (zoombombing)
- Transcription auto uniquement si langue audio supportée (vérifier liste langues)

---

### 3. Intégration apps tierces dans Teams

**Description** : Intégrer applications tierces (Jira, Trello, GitHub, Asana, etc.) directement dans Teams.

**Types d'intégrations** :

**1. Onglets personnalisés (Tabs)** :
```
Ajouter onglet app tierce dans canal :
1. Ouvrir canal → Icône "+" → Sélectionner app (Jira, Trello, Planner, etc.)
2. Configurer connexion (authentification OAuth app tierce)
3. Sélectionner vue (tableau Trello, dashboard Jira, etc.)
4. Nommer onglet → Enregistrer

Exemples apps populaires :
- Jira : Tableau Kanban projet
- Trello : Board équipe
- GitHub : Pull requests repository
- Asana : Tâches projet
- Planner : Planning équipe Microsoft

Avantages :
- Contexte centralisé (pas de switch entre apps)
- Notifications temps réel dans Teams
- Collaboration synchrone (commentaires Jira dans Teams)
```

**2. Connecteurs entrants (Incoming Webhooks)** :
```
Recevoir notifications apps tierces dans canal Teams :
1. Canal → "..." → Connecteurs → Configurer
2. Sélectionner connecteur (ex: "Webhook entrant")
3. Copier URL webhook
4. Configurer app tierce (ex: GitHub → Settings → Webhooks → Ajouter URL Teams)
5. Tester notification

Exemples notifications :
- GitHub : Push commits, Pull Requests, Issues
- Jira : Création ticket, changement statut
- Azure DevOps : Build réussi/échoué
- Monitoring : Alertes production (Datadog, Prometheus)

Format notification (JSON) :
{
    "@type": "MessageCard",
    "title": "Build échoué : myAgentsTemplate",
    "text": "Erreur compilation phase 2",
    "themeColor": "FF0000"
}
```

**3. Bots conversationnels** :
```
Ajouter bot dans Teams :
1. Apps Teams → Rechercher bot (ex: "Polly", "Karma", "WhoBot")
2. Ajouter à équipe/canal/chat personnel
3. Interagir via commandes (@BotName commande)

Exemples bots utiles :
- Polly : Sondages/votes rapides
- Karma : Reconnaissance pairs (+1 @collègue)
- WhoBot : Trombinoscope automatique
- Growbot : Feedback 360°

Commandes bot type :
@Polly create poll "Préférence date réunion?" "Lundi 14h" "Mardi 10h" "Mercredi 15h"
@Karma leaderboard (affiche top contributeurs mois)
```

**4. Power Automate (automatisations)** :
```
Créer automatisation Teams ↔ apps tierces :
1. Power Automate → Créer flux
2. Déclencheur : "Quand message posté dans canal Teams" (ou app tierce)
3. Actions : Poster message Teams, créer tâche Planner, etc.

Exemples flux :
- Email important reçu → Notification canal Teams
- Mention @moi dans canal → Créer tâche Planner
- Nouveau fichier SharePoint → Message Teams avec lien
- Réponse formulaire Forms → Créer ticket Jira

Flux type :
Déclencheur : Nouveau fichier OneDrive dossier "Factures"
Action 1 : Extraire métadonnées (nom, date, montant)
Action 2 : Poster message canal Teams "Compta" avec résumé
Action 3 : Créer ligne Excel tableau facturation
```

**Livrables** :
- Catalogue apps Teams recommandées (par use case)
- Guide configuration connecteurs (webhooks)
- Templates Power Automate réutilisables

**Pièges à éviter** :
- Apps non approuvées IT (vérifier catalogue entreprise avant installation)
- Trop de notifications = bruit (paramétrer filtres pertinents uniquement)
- Webhooks non sécurisés (URL webhook = secret, ne pas partager publiquement)

---

### 4. Paramétrage notifications et politiques de messagerie

**Description** : Optimiser notifications Teams pour réduire bruit et améliorer focus.

**Paramétrage notifications utilisateur** :

**Notifications par canal** :
```
Personnaliser notifications par canal :
1. Canal → "..." → Notifications du canal
2. Options :
   - Tous nouveaux messages (notifications toutes activités)
   - @Mentions uniquement (recommandé canaux très actifs)
   - Désactivé (canaux archives ou peu prioritaires)

Recommandations :
- Canaux projet actif : @Mentions uniquement
- Canaux annonces : Tous nouveaux messages
- Canaux archives : Désactivé
```

**Notifications mode Ne Pas Déranger** :
```
Planifier heures silencieuses :
1. Profil utilisateur → Paramètres → Notifications
2. Bloquer notifications pendant heures personnalisées
   - Exemple : 19h-8h en semaine, week-ends complets
3. Exceptions : Appels urgents uniquement (configurable)

Statut automatique :
- Disponible : 8h-12h, 14h-18h
- Absent déjeuner : 12h-14h
- Ne pas déranger : 19h-8h, week-ends
```

**Notifications prioritaires** :
```
Notifications urgentes uniquement (Important) :
1. Message → Options → Marquer comme Important (!)
2. Destinataire reçoit notification même si mode Ne Pas Déranger

À utiliser avec parcimonie :
- Incidents production
- Décisions urgentes requises
- Alertes critiques

⚠️ Abus = perte confiance équipe (utiliser uniquement si vraiment urgent)
```

**Politiques messagerie administrateur** :

**Politique messages (Admin Teams)** :
```
Centre admin Teams → Stratégies de messagerie :

Activer suppression messages ? : Oui (15 min après envoi recommandé)
Activer modification messages ? : Oui (utilisateurs peuvent corriger fautes)
Activer chat ? : Oui
Activer Giphy ? : Oui (modération : Modéré)
Activer memes/autocollants ? : Oui (selon culture entreprise)
Activer messages vocaux ? : Oui
Activer traduction messages ? : Oui (multilingue)
Activer messages immersifs (animations) ? : Non (distraction)

Stratégie lecture seule (canaux annonces uniquement) :
- Modération activée : Seuls propriétaires peuvent publier
- Membres peuvent réagir (👍) mais pas commenter
```

**Rétention messages** :
```
Centre admin Microsoft 365 → Conformité → Stratégies de rétention :

Rétention messages Teams :
- Conservation : 7 ans (conformité légale)
- Suppression automatique : Après 7 ans
- Exclusions : Messages canal "Général" (archivage permanent)

Types de conservation :
- Conversations chat (1:1, groupes)
- Messages canaux
- Fichiers partagés
```

**Livrables** :
- Guide utilisateur paramétrage notifications
- Politique messagerie entreprise (gouvernance)
- Templates stratégies administrateur

**Pièges à éviter** :
- Notifications tous canaux = surcharge cognitive (sélectionner canaux prioritaires)
- Marquer tous messages Important = perte sens urgence
- Rétention trop courte = perte historique conversations (minimum 1 an recommandé)

---

## Objectif

Optimiser collaboration Teams via :
- Architecture équipes/canaux cohérente et gouvernable
- Réunions efficaces (paramétrage, enregistrement, transcription)
- Intégrations apps tierces (centralisation outils)
- Notifications équilibrées (focus sans surcharge)

---

## Inputs requis

- **Contexte organisation** : taille équipe, départements, projets
- **Besoins collaboration** : synchrone/asynchrone, interne/externe
- **Apps tierces utilisées** : Jira, Trello, GitHub, etc.
- **Politique entreprise** : gouvernance IT, sécurité, conformité
- **Niveau maturité Teams** : débutant, intermédiaire, avancé

---

## Sorties attendues

**Architecture Teams** :
- Organigramme équipes/canaux documenté
- Guide gouvernance (nommage, expiration, permissions)
- Matrice décision (Équipe vs Canal vs Chat)

**Réunions** :
- Politique réunions Teams (guidelines)
- Templates réunions récurrentes
- Guide enregistrement/transcription

**Intégrations** :
- Catalogue apps Teams recommandées
- Configurations connecteurs/webhooks
- Flux Power Automate templates

**Notifications** :
- Guide utilisateur paramétrage
- Politique messagerie entreprise

---

## Workflow recommandé

1. **Audit situation actuelle** : Nombre équipes/canaux, apps utilisées, pain points collaboration
2. **Définir architecture cible** : Structure équipes/canaux optimale
3. **Configurer gouvernance** : Nommage, expiration, permissions
4. **Paramétrer réunions** : Options, enregistrement, templates
5. **Intégrer apps tierces** : Onglets, connecteurs, bots
6. **Optimiser notifications** : Paramétrage utilisateur + politiques admin
7. **Former utilisateurs** : Sessions onboarding, guides utilisateur
8. **Mesurer adoption** : KPI utilisation, feedback utilisateurs

---

## Garde-fous

- **Gouvernance stricte** : Stratégies nommage/expiration obligatoires (éviter dérive)
- **Sécurité** : Salle d'attente activée par défaut (réunions externes)
- **RGPD** : Informer participants avant enregistrement réunion (consentement)
- **Apps tierces** : Valider avec IT avant installation (sécurité, conformité)
- **Notifications** : Recommander @Mentions uniquement canaux très actifs (éviter surcharge)

---

## Template d'entrée (copier/coller)
```text
[Contexte Teams]
- Équipes, canaux et utilisateurs concernés : ...
- Mode de collaboration et réunions à soutenir : ...
- Applications intégrées et besoins de partage : ...
- Règles de gouvernance, rétention et sécurité : ...
```

## Template de sortie (copier/coller)
```text
[Configuration Teams proposée]
- Structure d'équipes/canaux et conventions : ...
- Paramètres réunions, apps et notifications : ...
- Permissions/owners et rétention : ...
- Vérifications et consignes de gouvernance : ...
```

## Templates copier/coller

**Template architecture équipe projet** :
```
Équipe : [NOM-PROJET]-[ANNÉE]
├── 📢 Général (annonces projet)
├── 💬 Discussion (questions, entraide)
├── 📁 Ressources (docs partagés)
├── 🎯 Sprint actuel (focus itération)
├── 📊 Reporting (KPI, dashboard)
└── 🔒 Comité pilotage (privé, direction)

Paramètres :
- Nommage : PRJ-[CodeProjet]-[Année]
- Expiration : 180 jours après fin projet
- Propriétaires : Chef projet + 1 backup
```

**Template ordre du jour réunion** :
```markdown
# Réunion [TYPE] - [DATE]

## Participants
- [Nom 1]
- [Nom 2]

## Ordre du jour
1. [Sujet 1] (5 min)
2. [Sujet 2] (10 min)
3. [Sujet 3] (15 min)

## Décisions
- [ ] [Décision 1]
- [ ] [Décision 2]

## Actions
- [ ] [Action 1] - @Responsable - Échéance
- [ ] [Action 2] - @Responsable - Échéance

## Prochaine réunion
- Date :
- Heure :
```

---

## Checklist QA interne

- [ ] Architecture équipes/canaux validée (max 200 canaux/équipe)
- [ ] Stratégie nommage configurée (convention cohérente)
- [ ] Stratégie expiration activée (équipes projets = 180j)
- [ ] Permissions définies (min 2 propriétaires/équipe)
- [ ] Options réunions configurées (salle d'attente, enregistrement)
- [ ] Apps tierces approuvées IT (sécurité validée)
- [ ] Notifications optimisées (@Mentions canaux actifs)
- [ ] Politique messagerie documentée (gouvernance)
- [ ] Formation utilisateurs réalisée (onboarding)

---

## KPI

- **Adoption** : % utilisateurs actifs Teams (cible ≥ 90%)
- **Engagement** : Messages/canal/semaine (cible 20-50 selon taille équipe)
- **Réunions** : % réunions enregistrées (cible 30-50% réunions importantes)
- **Satisfaction** : Feedback utilisateurs (échelle 1-5, cible ≥ 4)

---

## Definition of done

- [ ] Architecture Teams implémentée (équipes/canaux créés)
- [ ] Gouvernance configurée (nommage, expiration, permissions)
- [ ] Réunions paramétrées (options, enregistrement, templates)
- [ ] Apps tierces intégrées (onglets, connecteurs configurés)
- [ ] Notifications optimisées (guide utilisateur diffusé)
- [ ] Formation utilisateurs réalisée (onboarding, guides)
- [ ] KPI adoption validés (≥ 90% utilisateurs actifs)
- [ ] Feedback utilisateurs positif (≥ 4/5)

---

## Exemples

**Exemple 1 : Architecture département Marketing**
```
Équipe : MKT-France
├── 📢 Annonces (communication direction marketing)
├── 💬 Général (discussion quotidienne)
├── 🎨 Créatifs (assets, campagnes)
├── 📊 Analytics (dashboards, reporting)
├── 📅 Événements (salons, webinaires)
└── 🔒 Direction (privé, budget, RH)

Intégrations :
- Onglet Trello (board campagnes Q2)
- Connecteur Google Analytics (alertes trafic)
- Bot Polly (sondages rapides)

Notifications :
- Annonces : Tous messages
- Général : @Mentions uniquement
- Direction : Tous messages (canal privé)
```

**Exemple 2 : Template réunion récurrente Standup**
```
Réunion : Standup Hebdo Équipe Dev
Fréquence : Tous les lundis 9h30
Durée : 30 min
Enregistrement : Automatique (cloud)
Transcription : Activée (FR)

Ordre du jour :
1. Tour de table (5 min/personne max)
   - Réalisé semaine dernière
   - Prévu cette semaine
   - Blocages éventuels
2. Revue sprint (10 min)
   - Avancement vs objectifs
   - Métriques clés
3. Prochaines actions (5 min)

Template message post-réunion (auto-posté via Power Automate) :
📝 Compte-rendu Standup [DATE]
- Enregistrement : [Lien OneDrive]
- Transcription : [Lien]
- Actions : [Liste actions @responsables]
```

---

## Contraintes

- **Limites Microsoft Teams** : Max 200 canaux/équipe, 25k membres/équipe, 500k équipes/tenant
- **Stockage enregistrements** : OneDrive/SharePoint (quotas applicables)
- **Licences** : Certaines fonctionnalités nécessitent Microsoft 365 E3/E5 (enregistrement cloud, transcription, Power Automate Premium)
- **Apps tierces** : Certaines apps nécessitent abonnements séparés (Jira, Trello Premium, etc.)
- **Conformité** : Enregistrements réunions = données personnelles (RGPD : consentement, rétention limitée)

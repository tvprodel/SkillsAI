# Outlook Productivity Automation

**Compétence** : Automatiser et optimiser Outlook : règles automatiques, Quick Steps, gestion agenda avancée, signatures HTML, recherche avancée, archivage.

**Agents utilisateurs** : l'agent Microsoft 365 (principal)

## Quand l'utiliser (triggers)
- Automatiser tri emails (règles, Quick Steps)
- Optimiser gestion agenda (disponibilités, salles, délégations)
- Créer signatures HTML professionnelles
- Configurer recherche avancée et dossiers intelligents
- Paramétrer archivage et gestion quotas

## Hors périmètre
- Infrastructure Exchange Server → l'agent de packaging applicatif
- Migration boîtes mail → l'agent de packaging applicatif
- Sécurité email (SPF, DKIM, DMARC) → l'agent réseau et sécurité réseau
- Développement add-ins Outlook → l'agent de développement .NET

---

## Compétences

### 1. Règles automatiques et Quick Steps

**Description** : Automatiser actions récurrentes sur emails pour réduire temps traitement.

**Règles automatiques (Rules)** :

**Créer règle de tri** :
```
Fichier → Gérer les règles et alertes → Nouvelle règle

Exemple 1 : Déplacer emails d'expéditeur spécifique vers dossier
1. Modèle : "Déplacer les messages d'une personne vers un dossier"
2. Condition : De = client@entreprise.com
3. Action : Déplacer vers dossier "Clients/Entreprise X"
4. Exceptions : Aucune
5. Activer règle

Exemple 2 : Marquer emails urgents en rouge
1. Modèle : "Appliquer une catégorie aux messages d'une personne"
2. Condition : De = boss@entreprise.com OU Objet contient "URGENT"
3. Action : Catégorie "Rouge" + marquer comme important
4. Activer règle

Exemple 3 : Transférer automatiquement emails pendant absence
1. Modèle : "Transférer les messages à des personnes ou une liste de distribution publique"
2. Condition : Tous messages reçus
3. Action : Transférer à collegue@entreprise.com
4. Exception : Ne pas appliquer à messages marqués "Confidentiel"
5. Activer uniquement pendant absence (désactiver au retour)
```

**Règles côté serveur vs côté client** :
```
Côté serveur (recommandé) :
- Exécution même Outlook fermé
- Applicable si conditions simples (De, À, Objet)
- Icône règle sans ordinateur

Côté client (limité) :
- Exécution uniquement Outlook ouvert
- Requis si actions complexes (exécuter script, sons)
- Icône règle avec ordinateur

⚠️ Limiter règles côté serveur (max 256 Ko quotas Exchange)
```

**Quick Steps (actions 1 clic)** :

**Créer Quick Step personnalisé** :
```
Accueil → Quick Steps → Créer

Exemple 1 : Déplacer + Marquer lu + Catégorie
Nom : "Traité Client X"
Actions :
1. Déplacer vers dossier "Clients/Entreprise X"
2. Marquer comme lu
3. Catégorie "Vert"
Raccourci : Ctrl+Maj+1

Exemple 2 : Répondre avec template + Déplacer
Nom : "Réponse standard demande info"
Actions :
1. Répondre avec modèle "Template Infos Produit"
2. Déplacer vers dossier "Traité"
3. Marquer terminé
Raccourci : Ctrl+Maj+2

Exemple 3 : Transférer + Ajouter note
Nom : "Escalade manager"
Actions :
1. Transférer à manager@entreprise.com
2. Ajouter note : "FYI - Nécessite ton avis"
3. Catégorie "Orange" (en attente)
Raccourci : Ctrl+Maj+3
```

**Livrables** :
- Règles automatiques configurées et documentées
- Quick Steps personnalisés (top 5-10 actions fréquentes)
- Guide utilisateur raccourcis clavier

**Pièges à éviter** :
- Règles conflictuelles (ordre exécution important : vérifier priorité)
- Règles trop larges (risque déplacer emails importants par erreur)
- Quick Steps complexes (limiter à 5 actions max pour clarté)

---

### 2. Gestion agenda avancée (délégations, disponibilités, salles)

**Description** : Optimiser planification et partage agenda pour collaboration efficace.

**Délégation agenda** :

**Donner accès agenda à assistant** :
```
Calendrier → Partager → Autorisations

Niveaux d'accès :
- Disponibilité uniquement : Voir créneaux occupés/libres (pas de détails)
- Disponibilité, objet, lieu : Détails basiques visibles
- Tous les détails : Titre, participants, pièces jointes
- Éditeur : Peut modifier/créer rendez-vous
- Délégué : Éditeur + reçoit demandes réunion pour vous

Configuration délégation complète (assistant) :
1. Fichier → Paramètres du compte → Accès délégué
2. Ajouter assistant@entreprise.com
3. Permissions :
   - Calendrier : Éditeur + demandes réunion
   - Tâches : Éditeur
   - Boîte de réception : Lecteur (optionnel)
   - Contacts : Éditeur (optionnel)
4. Option : Copier demandes réunion à délégué et moi
5. OK

Délégué peut maintenant :
- Créer rendez-vous au nom du manager
- Accepter/refuser invitations réunion
- Voir agenda complet
```

**Calendriers partagés équipe** :
```
Créer calendrier partagé :
1. Nouveau calendrier → Nom "Congés Équipe Marketing"
2. Partager avec équipe (permissions Éditeur)
3. Ajouter au groupe Calendriers partagés

Superposition calendriers :
- Affichage → Superposer calendriers
- Voir disponibilités multiples personnes simultanément
- Utile planification réunions multi-participants
```

**Recherche disponibilités (Scheduling Assistant)** :
```
Nouvelle réunion → Assistant Planification

Fonctionnalités :
- Visualisation disponibilités tous participants
- Suggestions créneaux communs (Next 3 slots)
- Filtres : Durée, plage horaire, jour semaine
- Affichage heures travail vs heures perso

Bonnes pratiques :
- Inviter minimum participants nécessaires (facilite recherche créneaux)
- Respecter heures travail (éviter 8h-9h et 17h-18h si possible)
- Prévoir marge 5-10 min entre réunions (transition)
```

**Réservation salles et ressources** :

**Ajouter salle réunion** :
```
Nouvelle réunion → Ajouter salle

Configuration admin Exchange (prérequis) :
- Salles configurées comme ressources Exchange
- Acceptation automatique ou approbation manuelle
- Capacité, équipements (vidéoprojecteur, etc.)

Utilisateur :
1. Ajouter salle (ex: "Salle Réunion A - RDC - 12 pers")
2. Vérifier disponibilité (Assistant Planification)
3. Envoyer invitation → Salle répond automatiquement

Équipements (ressources) :
- Vidéoprojecteur, caméra Teams, tableau blanc
- Ajout identique aux salles
```

**Livrables** :
- Configuration délégation agenda documentée
- Calendriers partagés équipe créés
- Guide réservation salles

**Pièges à éviter** :
- Délégation trop large (risque modifications involontaires)
- Calendriers persos partagés publiquement (confidentialité)
- Salles réservées sans annulation si réunion annulée (libérer manuellement)

---

### 3. Signatures HTML et modèles de messages

**Description** : Créer signatures professionnelles et templates emails réutilisables.

**Signatures HTML** :

**Créer signature professionnelle** :
```html
<!-- Template signature HTML (copier dans éditeur signature Outlook) -->
<table style="font-family: Arial, sans-serif; font-size: 10pt; color: #333;">
  <tr>
    <td style="padding-right: 15px;">
      <img src="https://votresite.com/logo.png" alt="Logo" width="100">
    </td>
    <td style="border-left: 2px solid #0078D4; padding-left: 15px;">
      <strong style="font-size: 12pt; color: #0078D4;">Prénom NOM</strong><br>
      <span style="color: #666;">Titre Poste</span><br>
      <span style="font-size: 9pt;">Nom Entreprise</span><br><br>
      📧 <a href="mailto:prenom.nom@entreprise.com">prenom.nom@entreprise.com</a><br>
      📞 +32 2 XXX XX XX<br>
      🌐 <a href="https://www.entreprise.com">www.entreprise.com</a>
    </td>
  </tr>
</table>

<!-- Disclaimer légal (optionnel) -->
<p style="font-size: 8pt; color: #999; margin-top: 10px;">
Ce message et toutes les pièces jointes sont confidentiels. [Texte légal standard]
</p>
```

**Configuration Outlook** :
```
Fichier → Options → Courrier → Signatures

Créer signature :
1. Nouveau → Nom "Signature Pro"
2. Coller HTML ou créer visuellement
3. Définir par défaut :
   - Nouveaux messages : Signature Pro
   - Réponses/transferts : Signature courte (optionnel)

Signature courte (réponses) :
Prénom NOM | Titre Poste
📧 prenom.nom@entreprise.com | 📞 +32 2 XXX XX XX

Bonnes pratiques :
- Logo < 100 Ko (rapidité chargement)
- Images hébergées en ligne (pas de pièces jointes)
- Liens cliquables (mailto:, https://)
- Police standard (Arial, Calibri) pour compatibilité
```

**Modèles de messages (Templates)** :

**Créer modèle réutilisable** :
```
Créer template "Réponse standard demande info produit" :

1. Nouveau message
2. Rédiger contenu type :
   Objet : Informations Produit [NOM_PRODUIT]
   
   Bonjour,
   
   Merci pour votre intérêt pour nos produits.
   
   Vous trouverez ci-joint :
   - Brochure produit
   - Tarifs 2026
   - Conditions générales de vente
   
   Je reste à votre disposition pour toute question.
   
   Cordialement,
   [SIGNATURE]

3. Fichier → Enregistrer sous → Type : Modèle Outlook (*.oft)
4. Enregistrer dans C:\Users\[User]\AppData\Roaming\Microsoft\Templates

Utiliser template :
- Accueil → Nouveaux éléments → Autres éléments → Choisir le formulaire
- Sélectionner template → Personnaliser → Envoyer

Alternative Quick Step :
- Créer Quick Step "Réponse Info Produit"
- Action : Répondre avec modèle "Template Info Produit.oft"
- Raccourci : Ctrl+Maj+5
```

**Livrables** :
- Signatures HTML professionnelles (standard + courte)
- Templates emails fréquents (5-10 types)
- Guide création/utilisation templates

**Pièges à éviter** :
- Images signature trop lourdes (> 100 Ko = lenteur)
- Signatures trop longues (> 6 lignes = spam-like)
- Templates trop rigides (laisser espaces personnalisation)

---

### 4. Recherche avancée et archivage

**Description** : Retrouver emails rapidement et gérer archivage intelligent.

**Recherche avancée** :

**Syntaxe recherche Outlook** :
```
Champs recherche :
- de:client@entreprise.com (expéditeur)
- à:collegue@entreprise.com (destinataire)
- objet:facture (mots dans objet)
- a:pièce jointe (emails avec PJ)
- reçu:hier / reçu:cette semaine / reçu:01/01/2026 (date)
- catégorie:rouge (par catégorie couleur)
- importance:élevée (priorité haute)

Opérateurs logiques :
- ET : de:client@entreprise.com ET objet:facture
- OU : de:client1@entreprise.com OU de:client2@entreprise.com
- PAS : objet:facture PAS objet:payée

Exemples recherches complexes :
1. Factures impayées reçues ce mois :
   objet:facture ET reçu:ce mois PAS objet:(payée OU soldée)

2. Emails importants non lus de la direction :
   de:direction@entreprise.com ET importance:élevée ET lu:non

3. Emails avec PJ Excel dernière semaine :
   a:xlsx ET reçu:cette semaine
```

**Dossiers de recherche (Search Folders)** :
```
Créer dossier de recherche permanent :

Exemple : "Emails non lus VIP" (dirigeants uniquement)
1. Dossier → Nouveau dossier de recherche
2. Modèle : Messages non lus ou créer personnalisé
3. Critères : 
   - De : boss@entreprise.com, direction@entreprise.com
   - Statut : Non lu
4. Dossier créé → Rafraîchit automatiquement

Autres exemples utiles :
- "Grands messages" (> 1 Mo)
- "Anciens messages" (> 6 mois, à archiver)
- "Messages marqués pour suivi"
- "Catégorie projet X en cours"
```

**Archivage et gestion quotas** :

**Archivage automatique (AutoArchive)** :
```
Fichier → Options → Avancé → Paramètres d'archivage automatique

Configuration recommandée :
- Fréquence : Tous les 14 jours
- Archiver éléments antérieurs à : 6 mois
- Déplacer anciens éléments vers : C:\Archive\Outlook\archive.pst
- Supprimer définitivement éléments expirés : Non (conserver)

Exclusions par dossier :
- Boîte envoi : Ne pas archiver (< 3 mois)
- Éléments supprimés : Vider tous les 30 jours
- Projets actifs : Ne pas archiver automatiquement
```

**Archivage en ligne (Exchange Online)** :
```
Configuration admin Exchange Online :
- Activer archivage en ligne pour utilisateur
- Quota boîte principale : 50 Go
- Quota archive : 100 Go (extensible)

Stratégie déplacement automatique :
- Emails > 2 ans → Archive en ligne automatiquement
- Recherche intégrée (boîte principale + archive)
- Pas de fichier PST local nécessaire

Avantages :
- Accessible partout (cloud)
- Pas de gestion fichiers PST
- Conforme stratégies rétention entreprise
```

**Nettoyage boîte mail** :
```
Outils nettoyage rapide :

1. Affichage → Afficher en : Taille
   → Identifier emails volumineux
   → Supprimer PJ inutiles (garder email, supprimer PJ)

2. Catégories couleur :
   → Trier par catégorie "Non trié"
   → Archiver/supprimer emails non catégorisés > 6 mois

3. Conversations :
   → Nettoyer conversations (supprimer messages redondants)
   → Accueil → Nettoyer → Nettoyer la conversation

4. Boîte envoi :
   → Vider régulièrement (messages envoyés < valeur archivage)
```

**Livrables** :
- Guide recherche avancée (syntaxe, exemples)
- Dossiers de recherche configurés (top 5 cas usage)
- Stratégie archivage documentée
- Checklist nettoyage mensuel

**Pièges à éviter** :
- Fichiers PST locaux trop volumineux (> 10 Go = corruption risque élevé)
- Archivage automatique sans vérification (risque supprimer emails importants)
- Dossiers de recherche trop nombreux (impact performances)

---

## Objectif

Maximiser productivité Outlook via :
- Automatisation tri emails (règles, Quick Steps)
- Optimisation gestion agenda (délégations, salles)
- Communication professionnelle (signatures, templates)
- Retrouver informations rapidement (recherche, archivage)

---

## Inputs requis

- **Besoin utilisateur** : Automatisation, agenda, signatures, recherche, archivage
- **Volume emails** : Emails/jour reçus (impact règles, archivage)
- **Type organisation** : PME, grande entreprise (Exchange Server vs Exchange Online)
- **Contraintes IT** : Quotas, politiques archivage, permissions délégation
- **Niveau maturité Outlook** : Débutant, intermédiaire, avancé

---

## Sorties attendues

**Automatisation** :
- Règles automatiques configurées (5-10 règles clés)
- Quick Steps personnalisés (top 10 actions)
- Guide raccourcis clavier

**Agenda** :
- Délégations configurées (assistants)
- Calendriers partagés créés
- Guide réservation salles

**Signatures/Templates** :
- Signatures HTML (standard + courte)
- Templates emails (5-10 types fréquents)

**Recherche/Archivage** :
- Dossiers de recherche (top 5 cas usage)
- Stratégie archivage configurée
- Checklist nettoyage mensuel

---

## Workflow recommandé

1. **Audit situation actuelle** : Volume emails/jour, temps tri, pain points
2. **Identifier actions récurrentes** : Top 10 actions manuelles fréquentes
3. **Créer automatisations** : Règles + Quick Steps
4. **Optimiser agenda** : Délégations, calendriers partagés
5. **Standardiser communication** : Signatures, templates
6. **Paramétrer recherche** : Dossiers de recherche, syntaxe avancée
7. **Configurer archivage** : Stratégie automatique + nettoyage régulier
8. **Former utilisateur** : Sessions pratiques, guides
9. **Mesurer gains** : Temps gagné/jour, satisfaction

---

## Garde-fous

- **Règles automatiques** : Tester sur période limitée avant activation définitive
- **Délégation agenda** : Limiter aux personnes de confiance (risque modifications involontaires)
- **Signatures HTML** : Valider affichage tous clients email (Outlook, Gmail, Apple Mail)
- **Archivage** : Vérifier conformité stratégies rétention entreprise (légal, RGPD)
- **Quotas Exchange** : Surveiller régulièrement (alertes 80%, 90%, 100%)

---

## Template d'entrée (copier/coller)
```text
[Besoin Outlook]
- Client Outlook et type de compte : ...
- Processus à optimiser (tri, calendrier, signature, archivage) : ...
- Volume/fréquence et comportement actuel : ...
- Règles de confidentialité ou contraintes organisationnelles : ...
```

## Template de sortie (copier/coller)
```text
[Configuration proposée]
- Règles, Quick Steps ou réglages : ...
- Conditions, exceptions et portée : ...
- Résultats de test sur exemples représentatifs : ...
- Procédure de désactivation/retour arrière : ...
```

## Templates copier/coller

**Template règle tri client** :
```
Nom règle : Tri emails Client X
Condition : De = client@entreprise.com
Actions :
1. Déplacer vers dossier "Clients/Entreprise X"
2. Marquer comme lu
3. Catégorie "Vert"
Exceptions : Si objet contient "URGENT" → Laisser boîte réception
```

**Template Quick Step "Traité"** :
```
Nom : Traité et archivé
Actions :
1. Marquer comme lu
2. Catégorie "Vert"
3. Déplacer vers "Archive/Traité"
Raccourci : Ctrl+Maj+1
```

**Template signature HTML basique** :
```html
<p style="font-family: Arial; font-size: 10pt;">
  <strong style="color: #0078D4;">Prénom NOM</strong><br>
  Titre Poste<br>
  📧 <a href="mailto:email@entreprise.com">email@entreprise.com</a> | 
  📞 +32 2 XXX XX XX
</p>
```

---

## Checklist QA interne

- [ ] Règles automatiques testées (vérifier tri correct 1 semaine)
- [ ] Quick Steps fonctionnels (raccourcis clavier opérationnels)
- [ ] Délégation agenda validée (permissions correctes)
- [ ] Signatures HTML affichées correctement (test 3 clients email)
- [ ] Templates emails testés (personnalisation facile)
- [ ] Dossiers recherche rafraîchis automatiquement
- [ ] Archivage automatique configuré (fréquence, destination)
- [ ] Quotas surveillés (alertes actives)
- [ ] Guide utilisateur rédigé (captures écran)

---

## KPI

- **Temps gagné** : Réduction temps tri emails (heures/semaine)
- **Taux automatisation** : % emails traités automatiquement (cible 40-60%)
- **Utilisation Quick Steps** : Nombre utilisations/jour (adoption)
- **Taux archivage** : % emails archivés automatiquement (éviter saturation)
- **Satisfaction** : Feedback utilisateur (échelle 1-5, cible ≥ 4)

---

## Definition of done

- [ ] Règles automatiques configurées (5-10 règles clés)
- [ ] Quick Steps créés (top 10 actions fréquentes)
- [ ] Délégations agenda paramétrées (si applicable)
- [ ] Signatures HTML validées (affichage multi-clients)
- [ ] Templates emails créés (5-10 types)
- [ ] Dossiers recherche configurés (top 5 cas usage)
- [ ] Archivage automatique activé (stratégie documentée)
- [ ] Guide utilisateur fourni (captures, raccourcis)
- [ ] Formation utilisateur réalisée (session pratique)
- [ ] KPI temps gagné mesuré (≥ 30 min/jour)

---

## Exemples

**Exemple 1 : Quick Step "Escalade manager"**
```
Nom : Escalade urgent manager
Actions :
1. Transférer à manager@entreprise.com
2. Objet : Ajouter "[URGENT]" en préfixe
3. Ajouter note : "Merci de traiter en priorité"
4. Catégorie "Rouge"
5. Marquer suivi (échéance J+1)
Raccourci : Ctrl+Maj+9
```

**Exemple 2 : Recherche avancée facturation**
```
Recherche : Factures impayées > 30 jours

Syntaxe :
objet:facture ET reçu:< (aujourd'hui - 30 jours) PAS objet:(payée OU soldée OU annulée)

Dossier recherche permanent :
Nom : "Factures à relancer"
Rafraîchissement automatique quotidien
```

**Exemple 3 : Stratégie archivage projet**
```
Dossier projet : Clients/Projet Migration ERP

Paramètres archivage personnalisés :
- Ne pas archiver automatiquement (projet actif)
- Manuel après fin projet (date prévue : 31/12/2026)
- Archive vers : C:\Archive\Projets\Migration ERP 2026.pst
- Conservation : 7 ans (conformité légale)
```

---

## Contraintes

- **Quotas Exchange** : Boîte mail limitée (typiquement 50 Go), archive en ligne (100 Go)
- **Règles côté serveur** : Limité 256 Ko (environ 30-50 règles simples)
- **Fichiers PST** : Déconseillé au-delà 10 Go (risque corruption), privilégier archive en ligne
- **Signatures** : Gérées centralement par admin (GPO) dans certaines entreprises (modifications utilisateur bloquées)
- **Licences** : Archivage en ligne nécessite Exchange Online Plan 2 ou Microsoft 365 E3/E5

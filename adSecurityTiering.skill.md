# AD Security & Tiering

## Objectif
Sécuriser l'infrastructure Active Directory via un modèle de tiering (séparation des niveaux d'administration), le durcissement Kerberos/LDAP, et la réduction de la surface d'attaque des comptes à privilèges.

## Quand l'utiliser (triggers)
- « sécurité AD », « tiering model », « modèle à niveaux d'administration ».
- « durcir Kerberos », « LDAP signing », « comptes à privilèges AD », « Pass-the-Hash ».
- Audit de sécurité AD ou suite à un incident de compromission de compte administrateur.

## Hors périmètre
- Audit de sécurité applicatif générique (hors AD) → l'agent de sécurité (collaboration recommandée pour validation croisée).
- Sécurité réseau périmétrique (firewall, segmentation réseau) → l'agent réseau et sécurité réseau.

## Inputs requis
- Liste des comptes à privilèges existants (Domain Admins, Enterprise Admins, comptes de service).
- Topologie actuelle des postes d'administration (postes utilisateurs standards utilisés pour administrer AD ?).
- Niveau de maturité sécurité actuel (MFA en place, PAM, durcissement déjà réalisé).

## Sorties attendues
- Modèle de tiering (Tier 0 contrôleurs de domaine/comptes d'admin AD, Tier 1 serveurs, Tier 2 postes utilisateurs) avec règles d'étanchéité.
- Plan de durcissement Kerberos/LDAP (signature LDAP, désactivation NTLM si possible, politique de mots de passe des comptes de service).
- Recommandations de réduction des comptes à privilèges permanents (PAM, Just-In-Time admin).

## Workflow recommandé
1. Cartographier les comptes à privilèges et leur usage réel (administration quotidienne, comptes de service, comptes d'urgence).
2. Définir les tiers (0/1/2) et les règles d'interdiction de connexion croisée (un compte Tier 0 ne doit jamais se connecter sur un poste Tier 2).
3. Évaluer le durcissement Kerberos/LDAP actuel (LDAP signing, Kerberos armoring, protocoles legacy actifs).
4. Prioriser les actions par criticité (comptes Tier 0 sans MFA = priorité maximale).
5. Documenter un plan de mise en œuvre progressif (le tiering ne se déploie jamais d'un coup en production).

## Garde-fous
- Ne jamais recommander une suppression brutale de comptes de service sans plan de validation applicative préalable (risque d'interruption de service).
- Toujours prioriser la protection des comptes Tier 0 (contrôleurs de domaine, comptes Domain/Enterprise Admins) en premier.
- Un modèle de tiering doit être déployé progressivement avec une phase pilote, jamais en big-bang sur un environnement de production.

## Template d'entrée (copier/coller)
```text
[Périmètre]
- Forêt/domaine et systèmes d'administration concernés : ...
- Comptes privilégiés et usages observés : ...
- Segmentation actuelle des postes et serveurs : ...

[Objectif et contraintes]
- Modèle de tiering ou risque à examiner : ...
- Exigences de disponibilité, sécurité et conformité : ...
- Changements exclus de cette analyse : ...
```

## Template de sortie (copier/coller)
```text
[Modèle de tiering proposé]
- Tier 0 : ... (comptes/systèmes concernés)
- Tier 1 : ...
- Tier 2 : ...

[Plan de durcissement]
- Action prioritaire 1 : ...
- Action prioritaire 2 : ...

[Risques identifiés]
- ...
```

## Checklist QA interne
- Le modèle de tiering couvre bien tous les comptes à privilèges identifiés.
- Le plan de durcissement priorise les comptes Tier 0.
- Aucune action de suppression de compte de service n'est recommandée sans validation applicative.

## KPI reliés
- Nombre de comptes Domain/Enterprise Admins actifs (objectif : minimiser).
- Taux de couverture MFA sur les comptes à privilèges.
- Nombre de connexions croisées inter-tiers détectées (objectif : zéro).

## Definition of done
- Modèle de tiering documenté et validé par l'équipe sécurité/infrastructure.
- Plan de durcissement priorisé avec échéances.

## Exemples d'usage

### Exemple 1 : Suite à un audit révélant des comptes Domain Admins utilisés au quotidien
**Contexte** : L'audit de sécurité révèle que 4 administrateurs utilisent leur compte Domain Admin pour leur usage bureautique quotidien.
**Action** : L'agent propose un modèle de tiering avec comptes d'administration séparés (PAW - Privileged Access Workstations) pour les tâches Tier 0, et un plan de migration en 3 phases avec sensibilisation des administrateurs.
**Résultat** : Réduction du risque de compromission via phishing/malware sur les comptes à privilèges critiques.

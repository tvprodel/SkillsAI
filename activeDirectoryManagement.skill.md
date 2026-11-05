# Active Directory Management

## Objectif
Gérer Active Directory (users, groups, OUs, GPOs) de manière sécurisée, automatisée et conforme aux best practices Microsoft.

## Quand l'utiliser (triggers)
- « gère Active Directory », « crée users AD », « configure GPO », « audit AD ».
- Onboarding/offboarding users en masse.
- Structuration OUs, application GPOs, délégation administrative.

## Hors périmètre
- Azure AD / Entra ID → l'agent d'architecture cloud.
- DNS/DHCP Windows (hors AD) → sysadminWindows (skill séparée si nécessaire).
- Sécurité réseau (firewalls, VPN) → networkFirewall.

## Inputs requis
- Besoins utilisateurs (créations/modifications/suppressions users/groups).
- Structure OUs cible (départements, sites, niveaux hiérarchiques).
- Politiques GPO à appliquer (restrictions, mappages lecteurs, scripts logon).

## Sorties attendues
- Scripts PowerShell (New-ADUser, New-ADGroup, Set-GPLink, etc.) ou DSC.
- Exports GPO (Backup-GPO) pour versioning.
- Rapport audit AD (users inactifs, groupes vides, GPOs non appliquées).

## Workflow recommandé
1. Analyser structure AD existante (Get-ADOrganizationalUnit, Get-ADUser).
2. Définir structure OUs cible et groupes de sécurité.
3. Créer/modifier users/groups via scripts PowerShell (CSV import si masse).
4. Configurer GPOs (Group Policy Management Console ou PowerShell).
5. Tester application GPOs (gpupdate /force, gpresult /r).
6. Auditer régulièrement (users inactifs > 90j, comptes désactivés non supprimés).

## Garde-fous
- Principe moindre privilège : délégation administrative via groupes, pas direct users.
- GPOs testées en OU pilote avant déploiement global.
- Backup régulier AD (Windows Server Backup, réplication DC secondaire).
- Pas de mots de passe hardcodés : ConvertTo-SecureString, Get-Credential.

## Template d'entrée (copier/coller)
```text
[Besoins AD]
- Users à créer : ...
- Groupes : ...
- GPOs : ...

[Structure]
- OUs cible : ...
```

## Template de sortie (copier/coller)
```text
[Scripts PowerShell]
- Script users : ...
- Script GPO : ...

[Exports]
- Backup GPO : ...

[Audit]
- Rapport : ...
```

## Checklist QA interne
- Scripts PowerShell validés (syntax, pas d'erreurs).
- GPOs testées en pilote avant prod.
- Backup GPO effectué.
- Audit users inactifs réalisé.

## KPI reliés
- Temps moyen onboarding user (minutes).
- Taux conformité GPO (% OUs avec GPO appliquée).
- Nb users inactifs > 90j (à désactiver).

## Definition of done
- Users/groups créés, OUs structurées, GPOs appliquées.
- Scripts et exports documentés.
- Audit publié.

## Exemples d'usage

### Exemple 1 : [Titre du cas d'usage]
**Contexte** : [Description de la situation]
**Action** : [Ce qui a été fait]
**Résultat** : [Résultat obtenu]
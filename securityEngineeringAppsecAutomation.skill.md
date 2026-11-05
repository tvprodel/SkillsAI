# Security Engineering (AppSec Automation)

## Objectif
Industrialiser les controles securite dans le cycle de delivery.

## Quand l'utiliser (triggers)
- Vulnerabilites repetitives.
- Secrets exposes.
- Manque de controles CI/CD.

## Hors périmètre
- Audit ponctuel sans automatisation.
- Conformite purement documentaire.

## Inputs requis
- Pipeline CI/CD.
- Repos et dependances.
- Politique de securite cible.

## Sorties attendues
- Controles automatises (SAST/DAST/secrets).
- Seuils de blocage.
- Process d'exception.
- Plan de remediation.

## Workflow recommandé
1. Cartographier surfaces d'attaque.
2. Installer controles automatiques.
3. Integrer gate securite CI/CD.
4. Piloter remediation.

## Garde-fous
- Bloquer sur critiques/hautes par defaut.
- Exceptions temporaires et tracees.
- Jamais de secret en dur.

## Template d'entrée (copier/coller)
```text
[Contexte securite]
- Repos/pipeline : ...
- Risques principaux : ...

[Contrainte]
- Delai release : ...
- Politique risque : ...
```

## Template de sortie (copier/coller)
```text
[Controles]
- SAST : ...
- DAST : ...
- Secrets scanning : ...

[Policy]
- Seuil blocage : ...
- Exceptions : ...

[Plan remediation]
1) ...
2) ...
```

## Checklist QA interne
- Gates securite actifs.
- Exceptions justifiees.
- Suivi remediation en place.

## KPI reliés
- Taux vuln critiques ouvertes.
- Delai de remediation.
- Taux de conformite policy.

## Definition of done
- Pipeline securise et applique.
- Reduction mesurable des risques critiques.

## Exemples d'usage

### Exemple 1 : [Titre du cas d'usage]
**Contexte** : [Description de la situation]
**Action** : [Ce qui a été fait]
**Résultat** : [Résultat obtenu]
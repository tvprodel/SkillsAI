# GPO Advanced Design & Troubleshooting

## Objectif
Concevoir des stratégies de groupe (GPO) avancées — héritage, filtrage de sécurité, filtrage WMI, préférences — et diagnostiquer les problèmes d'application de GPO (héritage bloqué, conflits, lenteurs de démarrage/connexion).

## Quand l'utiliser (triggers)
- « design GPO complexe », « filtrage WMI », « héritage GPO bloqué », « préférences GPO ».
- « GPO ne s'applique pas », « conflit de stratégies de groupe », « lenteur de login GPO ».
- Audit ou refonte d'un ensemble de GPO existant devenu difficile à maintenir.

## Hors périmètre
- Application de GPO standards déjà définies (gestion courante) → l'agent d'administration Windows.
- Durcissement sécurité générique (CIS Benchmarks) hors GPO → l'agent de sécurité.

## Inputs requis
- Liste des GPO existantes et leur portée (domaine, site, OU).
- Symptôme observé si troubleshooting (comportement attendu vs observé, OU/utilisateur/machine concernés).
- Résultat d'un rapport `gpresult /h` ou `Get-GPResultantSetOfPolicy` si disponible.

## Sorties attendues
- Conception de GPO avec ordre d'application documenté (héritage, blocage, enforce).
- Diagnostic structuré des causes de non-application (ordre, filtrage de sécurité, filtrage WMI, réplication SYSVOL).
- Recommandations de consolidation si trop de GPO actives simultanément.

## Workflow recommandé
1. Cartographier l'arborescence OU et les GPO liées à chaque niveau (domaine, site, OU, sous-OU).
2. Identifier l'ordre d'application réel (Local > Site > Domaine > OU, avec Enforce et Block Inheritance).
3. Pour un design : définir la portée précise de chaque nouvelle GPO et son filtrage (sécurité et/ou WMI) pour éviter tout chevauchement non désiré.
4. Pour un troubleshooting : analyser `gpresult`/RSoP, vérifier la réplication SYSVOL, vérifier les permissions de lecture/application sur la GPO.
5. Documenter la cause racine et la correction appliquée.

## Garde-fous
- Ne jamais utiliser le filtrage WMI pour des critères qui changent fréquemment (impact performance au login).
- Limiter le nombre de GPO liées à une même OU (au-delà d'une dizaine, risque de lenteur de démarrage/connexion).
- Toujours vérifier la réplication SYSVOL avant de conclure à un problème de configuration GPO.

## Template d'entrée (copier/coller)
```text
[Contexte]
- Domaine, OU, GPO et groupes concernés : ...
- Résultat attendu et résultat observé : ...
- Étendue du problème (utilisateurs, postes, sites) : ...

[Diagnostic disponible]
- Ordre/héritage, filtrage de sécurité et WMI : ...
- Sorties gpresult/RSOP et événements pertinents : ...
- Changements récents et contraintes de production : ...
```

## Template de sortie (copier/coller)
```text
[Diagnostic ou conception GPO]
- GPO concernée(s) : ...
- Portée et ordre d'application : ...
- Filtrage appliqué (sécurité/WMI) : ...

[Cause racine (si troubleshooting)]
- ...

[Recommandation]
- ...
```

## Checklist QA interne
- L'ordre d'application (héritage, Enforce, Block Inheritance) est explicitement documenté.
- Le filtrage de sécurité/WMI est justifié et non redondant avec le filtrage OU.
- La réplication SYSVOL a été vérifiée en cas de troubleshooting.

## KPI reliés
- Temps de login moyen (impact du nombre/complexité des GPO).
- Nombre d'incidents GPO récurrents sur la même OU.

## Definition of done
- GPO conçue ou corrigée et testée sur un groupe pilote avant déploiement large.
- Documentation de la portée et du filtrage mise à jour.

## Exemples d'usage

### Exemple 1 : GPO ne s'appliquant pas sur une OU filiale
**Contexte** : Les utilisateurs d'une OU filiale ne reçoivent pas une GPO de restriction logicielle appliquée au niveau domaine.
**Action** : L'agent analyse le `gpresult /h` de la machine concernée, découvre un filtrage de sécurité excluant le groupe de l'OU filiale par erreur, et corrige la liste de sécurité de la GPO.
**Résultat** : La GPO s'applique correctement après rafraîchissement, confirmé par un second `gpresult`.

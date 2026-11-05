# Active Directory Architecture Design

## Objectif
Concevoir des architectures Active Directory robustes et évolutives (forêts, domaines, sites, unités d'organisation), en tenant compte de la croissance de l'organisation, des contraintes de latence réseau et des exigences de sécurité/gouvernance.

## Quand l'utiliser (triggers)
- « architecture AD multi-sites », « design forêt/domaine », « topologie Active Directory ».
- « combien de domaines/forêts », « structure OU », « modèle de délégation AD ».
- Croissance d'entreprise nécessitant une refonte de la structure AD existante.
- Fusion/acquisition nécessitant une intégration ou cohabitation de forêts AD.

## Hors périmètre
- Gestion courante des utilisateurs/groupes/GPO standards → l'agent d'administration Windows.
- Sécurité réseau générale (firewall, VPN) → l'agent réseau et sécurité réseau.
- Infrastructure cloud (Azure AD / Entra ID complet) → l'agent d'architecture cloud.

## Inputs requis
- Topologie organisationnelle actuelle (sites géographiques, effectifs, liens réseau/latence).
- Contraintes de gouvernance (délégation d'administration souhaitée, séparation des pouvoirs).
- Projection de croissance (fusions prévues, nouveaux sites, effectifs cibles).
- Exigences de conformité/sécurité applicables.

## Sorties attendues
- Schéma de forêt(s)/domaine(s) avec justification des choix (un ou plusieurs domaines, modèle de forêt ressource).
- Plan de sites et de liens de sites AD aligné sur la topologie réseau.
- Structure d'unités d'organisation (OU) avec modèle de délégation associé.
- Recommandations de niveau fonctionnel de forêt/domaine.

## Workflow recommandé
1. Recueillir la topologie réseau et organisationnelle actuelle et cible.
2. Déterminer le nombre de forêts/domaines nécessaires (critères : isolation de sécurité, autonomie administrative, contraintes légales/géographiques).
3. Concevoir la structure de sites AD et les liens de sites (coût, fréquence de réplication) alignés sur la latence réseau réelle.
4. Définir la structure d'OU et le modèle de délégation (qui administre quoi, à quel niveau).
5. Documenter les choix avec les alternatives écartées et leur justification.
6. Valider le plan avec un plan de migration/déploiement progressif si évolution d'une architecture existante.

## Garde-fous
- Toujours justifier un choix multi-domaines/multi-forêts par un besoin réel (isolation, légal, autonomie) : la complexité d'administration augmente significativement avec chaque domaine supplémentaire.
- Ne jamais concevoir une architecture sans valider la topologie réseau réelle (latence entre sites).
- Anticiper le niveau fonctionnel minimal requis par les applications existantes avant toute recommandation de montée de niveau.

## Template d'entrée (copier/coller)
```text
[Contexte AD]
- Organisation et sites concernés : ...
- Forêts/domaines et version fonctionnelle actuels : ...
- Topologie réseau et latences mesurées : ...

[Objectif et contraintes]
- Évolution recherchée : ...
- Besoins d'isolation, conformité et délégation : ...
- Croissance prévue et contraintes : ...
```

## Template de sortie (copier/coller)
```text
[Architecture proposée]
- Nombre de forêts : ... (justification)
- Nombre de domaines : ... (justification)
- Sites AD et liens de sites : ...
- Structure OU et délégation : ...

[Alternatives écartées]
- Option A : ... (raison du rejet)

[Prochaines étapes]
- Plan de migration/déploiement : ...
```

## Checklist QA interne
- Le nombre de domaines/forêts est justifié par un besoin documenté, pas par défaut.
- La topologie de sites reflète la réalité réseau (latence mesurée, pas supposée).
- Le modèle de délégation est explicite et aligné sur l'organisation cible.

## KPI reliés
- Temps de réplication AD inter-sites.
- Nombre d'incidents liés à une délégation d'administration mal définie.

## Definition of done
- Schéma d'architecture validé avec l'équipe infrastructure.
- Plan de sites et de délégation documenté et partagé.

## Exemples d'usage

### Exemple 1 : Extension internationale d'une PME
**Contexte** : Une PME ouvre 3 nouveaux bureaux internationaux avec une liaison réseau à latence variable vers le siège.
**Action** : L'agent l'agent Active Directory avancé conçoit un modèle à domaine unique avec 4 sites AD (siège + 3 bureaux), des liens de sites calibrés sur la latence mesurée, et une structure d'OU par pays avec délégation d'administration locale limitée à la gestion des mots de passe.
**Résultat** : Réplication AD stable sous 15 minutes entre sites, incidents de délégation réduits grâce à un périmètre d'administration locale clairement borné.

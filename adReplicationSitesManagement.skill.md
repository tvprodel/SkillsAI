# AD Replication & Sites Management

## Objectif
Diagnostiquer et résoudre les problèmes de réplication Active Directory entre contrôleurs de domaine, et concevoir une topologie de sites/liens de sites optimisée pour la bande passante et la latence réseau disponibles.

## Quand l'utiliser (triggers)
- « réplication AD cassée », « troubleshooting réplication », « repadmin », « USN rollback ».
- « liens de sites AD », « coût de site », « fréquence de réplication ».
- Lenteur de propagation de changements AD (nouveaux comptes, GPO) entre sites.

## Hors périmètre
- Conception initiale de l'architecture de sites lors d'un nouveau déploiement → Active Directory Architecture Design (skill associée, même agent).
- Problèmes réseau sous-jacents (coupures de liens, bande passante insuffisante) → l'agent réseau et sécurité réseau.

## Inputs requis
- Topologie des sites AD actuelle et des liens de sites (coût, intervalle de réplication).
- Sortie de `repadmin /replsummary` et `repadmin /showrepl` si troubleshooting.
- Description du symptôme (quels objets ne se répliquent pas, entre quels contrôleurs).

## Sorties attendues
- Diagnostic de la cause de l'échec de réplication (DNS, connectivité, USN rollback, conflit de schéma).
- Topologie de sites/liens de sites révisée avec coûts et intervalles justifiés.
- Plan de correction avec étapes de validation (`repadmin /replsummary` propre après correction).

## Workflow recommandé
1. Collecter `repadmin /replsummary` sur l'ensemble des contrôleurs de domaine pour identifier les échecs.
2. Analyser les erreurs spécifiques (`repadmin /showrepl` sur les contrôleurs en échec) : erreur DNS, erreur réseau, erreur de sécurité Kerberos.
3. Vérifier la résolution DNS des contrôleurs de domaine entre eux (cause la plus fréquente d'échec de réplication).
4. Pour la conception de sites : aligner les liens de sites sur la bande passante réelle disponible, avec des coûts reflétant la hiérarchie de préférence des chemins.
5. Documenter la correction et valider par un `repadmin /replsummary` propre.

## Garde-fous
- Ne jamais ignorer un échec de réplication de plus de 24h (risque de USN rollback ou de lingering objects).
- Toujours vérifier la résolution DNS en premier : c'est la cause la plus fréquente de problèmes de réplication AD.
- Un intervalle de réplication intersite ne doit jamais dépasser les besoins métier (changements critiques comme les verrouillages de compte).

## Template d'entrée (copier/coller)
```text
[Environnement]
- Sites et contrôleurs de domaine concernés : ...
- Sous-réseaux, liens et latences mesurées : ...
- État de réplication et événements observés : ...

[Besoin]
- Symptôme ou changement de topologie : ...
- Fenêtre d'observation et criticité : ...
- Contraintes de disponibilité : ...
```

## Template de sortie (copier/coller)
```text
[Diagnostic réplication]
- Contrôleurs en échec : ...
- Erreur identifiée : ...
- Cause racine : ...

[Topologie de sites proposée]
- Sites : ...
- Liens de sites (coût/intervalle) : ...

[Plan de correction]
- Étape 1 : ...
- Validation : repadmin /replsummary propre
```

## Checklist QA interne
- La résolution DNS entre contrôleurs a été vérifiée en priorité.
- Le diagnostic s'appuie sur une sortie `repadmin` réelle, pas une supposition.
- La topologie de sites proposée est alignée sur la bande passante réseau réelle.

## KPI reliés
- Taux d'échec de réplication AD (objectif : 0%).
- Délai moyen de convergence de réplication inter-sites.

## Definition of done
- `repadmin /replsummary` propre sur l'ensemble du domaine après correction.
- Topologie de sites documentée et validée.

## Exemples d'usage

### Exemple 1 : Réplication bloquée entre deux contrôleurs de domaine après migration réseau
**Contexte** : Après une migration d'infrastructure réseau, deux contrôleurs de domaine distants ne se répliquent plus.
**Action** : L'agent exécute `repadmin /showrepl` et identifie une erreur de résolution DNS suite au changement d'adresses IP non répercuté dans les enregistrements DNS des contrôleurs.
**Résultat** : Correction des enregistrements DNS, réplication rétablie et confirmée par `repadmin /replsummary` sans erreur.

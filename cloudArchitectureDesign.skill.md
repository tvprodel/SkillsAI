# Cloud Architecture Design

## Objectif
Concevoir des architectures cloud cibles (compute, réseau, stockage, données) robustes, sécurisées et scalables sur AWS/Azure/GCP ou hybride.

## Quand l'utiliser (triggers)
- « conçois une architecture », « propose un design cloud », « comment structurer notre infra ».
- Refonte structurelle d'une plateforme cloud existante.
- Besoin d'un schéma cible avant migration ou industrialisation.

## Hors périmètre
- Architecture applicative / design du code → l'agent d'architecture.
- Implémentation détaillée d'IaC → skill IaC Blueprint Generation.
- Suivi FinOps récurrent → l'agent FinOps.

## Inputs requis
- Contraintes business (budget, SLA, délais).
- Exigences non fonctionnelles (latence, disponibilité, sécurité).
- Contraintes de conformité et de résidence des données.
- Provider(s) imposé(s) ou libre choix.

## Sorties attendues
- Schéma d'architecture (texte structuré ou diagramme Mermaid).
- Liste des composants (compute, réseau, stockage, données) et leurs interactions.
- Justification chiffrée de chaque choix (coût, latence, résilience).
- Hypothèses explicites pour toute contrainte non fournie.

## Workflow recommandé
1. Clarifier contraintes et exigences non fonctionnelles.
2. Identifier les parcours et flux critiques.
3. Proposer 1 à 2 options d'architecture avec trade-offs.
4. Chiffrer coût/latence/résilience et recommander une cible.

## Garde-fous
- Pas de sur-ingénierie (YAGNI) : dimensionner au besoin réel.
- Signaler explicitement toute hypothèse non confirmée.
- Éviter le lock-in non justifié ; documenter les dépendances provider.

## Template d'entrée (copier/coller)
```text
[Contexte]
- Charge de travail : ...
- Provider(s) : ...

[Objectif]
- Contraintes (coût/SLA/conformité) : ...
- Exigences non fonctionnelles : ...
```

## Template de sortie (copier/coller)
```text
[Architecture cible]
- Composants : ...
- Flux critiques : ...

[Justification]
- Coût estimé : ...
- Résilience/latence : ...

[Hypotheses]
- ...
```

## Checklist QA interne
- Chaque composant a une justification.
- Les exigences non fonctionnelles sont couvertes.
- Les hypothèses sont explicites.

## KPI reliés
- Taux d'exigences non fonctionnelles couvertes.
- Écart coût estimé vs réel.
- Nombre de points de lock-in non justifiés.

## Definition of done
- Architecture cible publiée et justifiée.
- Trade-offs et hypothèses documentés.
- Prête à alimenter la génération d'IaC ou un plan de migration.

## Exemples d'usage

### Exemple 1 : [Titre du cas d'usage]
**Contexte** : [Description de la situation]
**Action** : [Ce qui a été fait]
**Résultat** : [Résultat obtenu]
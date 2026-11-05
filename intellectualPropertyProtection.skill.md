# Intellectual Property Protection

## Objectif
Protéger et gérer les actifs de propriété intellectuelle (marques, brevets, droits d'auteur, secrets d'affaires) et sécuriser l'usage de licences open source dans les projets de l'organisation.

## Quand l'utiliser (triggers)
- Dépôt de marque ou de brevet (Belgique, UE, international).
- Audit des licences open source des dépendances (GPL/AGPL/MIT/Apache).
- Contentieux ou risque de contrefaçon / concurrence déloyale.
- Rédaction d'un accord de cession ou de licence de propriété intellectuelle.
- Due diligence PI dans le cadre d'une levée de fonds ou d'une fusion-acquisition.

## Hors périmètre
- Implémentation technique des dépendances et remplacement de librairies → agent IT concerné (l'agent de développement back-end, l'agent de développement TypeScript/JavaScript, etc.).
- Avis technique pointu sur une licence FOSS spécifique (compatibilité technique) → consultation l'agent spécialisé GNU/Linux libre.
- Conformité RGPD sur les données incluses dans un actif PI → l'agent de conformité RGPD.

## Inputs requis
- Actif à protéger (nom de marque, invention, œuvre, code source).
- Marché géographique visé (Belgique, UE, international).
- Liste des dépendances techniques utilisées (si audit licences open source).
- Contrat de cession/licence existant (le cas échéant).

## Sorties attendues
- Stratégie de protection PI (régime de protection recommandé, calendrier).
- Dossier de dépôt marque/brevet (si applicable).
- Accord de cession ou de licence PI rédigé.
- Rapport d'audit des licences open source avec risques copyleft identifiés.

## Workflow recommandé
1. Identifier la protégeabilité de l'actif (marque, brevet, droit d'auteur, secret d'affaires).
2. Choisir le régime de protection adapté et le périmètre géographique.
3. Déposer la marque/le brevet ou rédiger l'accord de cession/licence.
4. Auditer les dépendances techniques et leurs licences open source.
5. Établir un plan de mitigation des risques copyleft (remplacement, dual licensing, divulgation).

## Garde-fous
- Prioriser les solutions libres et open source ; alternatives propriétaires uniquement si nécessaires et justifiées.
- Vérifier la compatibilité des licences avant toute intégration de dépendance.
- Ne jamais ignorer les obligations copyleft (GPL/AGPL) : documenter et traiter systématiquement.
- Ne jamais présumer qu'un actif est libre de droits sans vérification.

## Template d'entrée (copier/coller)
```text
[Actif à protéger]
- Type : marque / brevet / droit d'auteur / secret d'affaires
- Description : ...
- Marché visé : Belgique / UE / international

[Contexte technique]
- Dépendances concernées : ...
- Licences existantes connues : ...
```

## Template de sortie (copier/coller)
```text
[Stratégie de protection]
- Régime recommandé : ...
- Calendrier : ...

[Audit licences open source]
- Dépendance | Licence | Risque copyleft | Action recommandée
- ... | ... | ... | ...

[Plan de mitigation]
1) ...
2) ...
```

## Checklist QA interne
- Régime de protection justifié par le type d'actif et le marché visé.
- Toutes les dépendances critiques auditées (licence identifiée).
- Risques copyleft classés par criticité avec action associée.

## KPI reliés
- Nombre de risques PI identifiés vs mitigés.
- Délai moyen de dépôt marque/brevet.
- Taux de conformité des licences open source utilisées.

## Definition of done
- Stratégie de protection PI validée et documentée.
- Audit de licences open source réalisé sans risque copyleft non traité.

## Exemples d'usage

### Exemple 1 : Audit de licences open source avant levée de fonds
**Contexte** : Une due diligence PI est requise avant une levée de fonds ; les investisseurs demandent un état des lieux des licences utilisées.
**Action** : Audit des dépendances du projet, identification de deux librairies sous licence AGPL non compatibles avec le modèle SaaS propriétaire.
**Résultat** : Plan de remplacement des dépendances AGPL proposé et validé avant la due diligence, réduisant le risque juridique identifié par les investisseurs.

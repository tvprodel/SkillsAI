# Contract Drafting & Negotiation

## Objectif
Rédiger, réviser et négocier des contrats commerciaux et documents contractuels (SaaS, licences logicielles, prestation, partenariats, T&C/CGV/CGU, NDA) conformes au droit belge et européen, en équilibrant protection juridique et faisabilité business.

## Quand l'utiliser (triggers)
- Nouveau contrat client/fournisseur à rédiger.
- Revue ou négociation d'un NDA, T&C, CGV, CGU.
- Renouvellement ou avenant contractuel.
- Contrat SaaS ou multi-juridiction impliquant clauses de responsabilité, SLA, propriété intellectuelle.
- Due diligence contractuelle (levée de fonds, M&A).

## Hors périmètre
- Clauses RGPD/cookies détaillées (base légale, finalités, durées de conservation) → l'agent de conformité RGPD.
- Audit technique de sécurité des clauses (chiffrement, hébergement) → l'agent de sécurité.
- Rédaction de documentation utilisateur finale (guides, mentions d'usage) → l'agent de rédaction technique.

## Inputs requis
- Type de contrat et parties concernées.
- Juridiction(s) applicable(s) (Belgique/UE par défaut).
- Enjeux financiers et niveau de risque acceptable.
- Contrat existant ou gabarit de référence (le cas échéant).
- Contraintes business (délai, marge de négociation, deal-breakers).

## Sorties attendues
- Contrat / T&C / CGV / NDA rédigé ou révisé (version trackée des changements).
- Note explicative des clauses clés et points de négociation.
- Matrice de négociation (must-have / nice-to-have / deal-breaker).
- Checklist de conformité juridique (droit belge/UE, clauses obligatoires).

## Workflow recommandé
1. Cadrer le besoin (type de contrat, parties, enjeux, délai).
2. Identifier le droit applicable et les textes de référence (Code civil belge, directives UE).
3. Rédiger ou réviser les clauses (structure, langage juridique précis, cohérence business).
4. Construire la matrice de négociation et anticiper les contre-propositions.
5. Solliciter en croisement l'agent de conformité RGPD (clauses données) ou l'agent de sécurité (clauses sécurité) si nécessaire.
6. Livrer le contrat annoté + note explicative + checklist.

## Garde-fous
- Toujours préciser le droit applicable ; jamais d'avis "générique" sans contexte pays.
- Ne jamais copier-coller des clauses de contrats US/UK sans adaptation au droit belge/UE.
- Bannir les clauses abusives au regard du droit de la consommation belge/UE.
- Vérifier la compatibilité des licences logicielles citées dans le contrat (open source, propriétaire).
- Ne jamais insérer de secret commercial ou donnée sensible en clair dans un livrable partagé largement.

## Template d'entrée (copier/coller)
```text
[Contrat]
- Type : ...
- Parties : ...
- Juridiction : Belgique / UE / autre : ...

[Enjeux]
- Montant / valeur : ...
- Niveau de risque acceptable : ...
- Délai : ...

[Contexte]
- Contrat existant : oui/non (lien/version)
- Contraintes business : ...
```

## Template de sortie (copier/coller)
```text
[Clauses clés]
- Clause 1 : ... (justification)
- Clause 2 : ... (justification)

[Matrice de négociation]
- Must-have : ...
- Nice-to-have : ...
- Deal-breaker : ...

[Checklist conformité]
- [ ] Droit applicable précisé
- [ ] Clauses obligatoires présentes
- [ ] Aucune clause abusive détectée
```

## Checklist QA interne
- Droit applicable explicitement mentionné.
- Clauses cohérentes avec les contraintes business communiquées.
- Aucune clause copiée sans adaptation au droit belge/UE.
- Croisement RGPD/Sécurité effectué si le contrat implique données personnelles ou sécurité.

## KPI reliés
- Taux de contrats validés sans retour juridique ultérieur.
- Délai moyen de revue contractuelle.
- Nombre de litiges contractuels évités.

## Definition of done
- Contrat conforme au droit belge/UE applicable.
- Clauses critiques validées et justifiées.
- Checklist de conformité entièrement cochée ou écarts documentés.

## Exemples d'usage

### Exemple 1 : Revue d'un contrat SaaS B2B
**Contexte** : Une startup belge signe un contrat SaaS avec un client européen incluant des clauses de responsabilité et de SLA.
**Action** : Revue des clauses de limitation de responsabilité, ajout d'une clause de compétence territoriale belge, vérification de la cohérence avec les CGV existantes.
**Résultat** : Contrat validé avec risques résiduels documentés et négociation cadrée via la matrice must-have/deal-breaker.

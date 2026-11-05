# FinTech Partnership & Ecosystem Strategy

## Objectif
Aider les entreprises FinTech à cartographier leur écosystème de partenaires et à évaluer des options de collaboration selon la valeur, les dépendances, les risques opérationnels et les questions à vérifier.

## Quand l'utiliser (triggers)
- Une entreprise envisage un partenariat bancaire, de paiement, de distribution ou de données.
- L'équipe veut cartographier les acteurs d'un parcours FinTech ou d'une chaîne de valeur.
- Un pilote dépend d'un fournisseur, d'un établissement financier ou d'un intermédiaire.

## Hors périmètre
- Négocier ou rédiger un contrat, une licence ou une convention.
- Déterminer si un acteur ou un produit dispose d'une autorisation réglementaire suffisante.
- Auditer la sécurité, l'architecture ou la conformité d'un partenaire.
- Garantir la continuité d'un partenaire ou la disponibilité d'une API.
- Fournir une recommandation d'investissement ou de financement.

## Inputs requis
- Objectif métier et produit/service concerné.
- Parcours utilisateur ou chaîne de valeur à soutenir.
- Types de partenaires et régions envisagés.
- Dépendances, critères de sélection et contraintes connues.
- Informations publiques ou documents non confidentiels disponibles.

## Sorties attendues
- Carte des acteurs, rôles, apports et dépendances.
- Critères d'évaluation des partenariats et questions de due diligence.
- Risques de concentration, d'intégration et de gouvernance à examiner.
- Liste des validations juridiques, techniques, sécurité et opérations nécessaires.

## Workflow recommandé
1. Décrire le parcours produit et les fonctions qui nécessitent un partenaire.
2. Identifier les catégories d'acteurs, leur rôle attendu et les dépendances critiques.
3. Définir des critères de sélection métier, opérationnels et de résilience.
4. Comparer les options à partir d'informations sourcées, sans inférer une capacité non documentée.
5. Préparer les questions de due diligence et les preuves à obtenir des parties concernées.
6. Orienter les sujets contractuels vers Legal, les sujets techniques vers les équipes compétentes et les décisions commerciales vers les responsables de l'entreprise.

## Garde-fous
- Distinguer les déclarations publiques des capacités validées contractuellement ou techniquement.
- Ne pas conclure qu'un fournisseur est agréé, conforme, sécurisé ou résilient sans audit approprié.
- Vérifier les informations disponibles et leur date; signaler les inconnues.
- Ne pas partager des données confidentielles ou des secrets commerciaux.
- Ne pas rédiger les termes d'un contrat ni remplacer les procédures de procurement ou de due diligence.
- Mettre en évidence les risques de dépendance et l'existence éventuelle d'options de sortie, sans prétendre les valider.

## Template d'entrée (copier/coller)
```text
Produit ou parcours concerné :
Objectif du partenariat :
Zone géographique :
Types de partenaires envisagés :
Dépendances et critères connus :
Sources publiques disponibles :
Décision à préparer :
```

## Template de sortie (copier/coller)
```text
Carte des acteurs et rôles :
Valeur attendue par partie :
Dépendances et risques :
Critères de sélection :
Questions de due diligence :
Validations à demander (juridique, technique, sécurité, opérations) :
Sources consultées et limites :
```

## Checklist QA interne
- [ ] Les rôles et apports attendus de chaque partie sont distincts.
- [ ] Les dépendances et conséquences d'une indisponibilité sont signalées.
- [ ] Les capacités déclarées ne sont pas présentées comme validées.
- [ ] Les sujets de contrat, conformité et sécurité sont confiés aux spécialistes correspondants.
- [ ] Les critères de partenariat sont liés à l'objectif du produit.

## KPI reliés
- Proportion de partenariats cartographiés avec responsabilités et dépendances explicites.
- Nombre d'affirmations non vérifiées sur l'agrément ou la conformité de partenaires (cible : zéro).
- Proportion d'options de partenariat avec questions de sortie/continuité identifiées.

## Definition of done
- [ ] L'écosystème et les dépendances principales sont compréhensibles.
- [ ] Les critères de sélection sont reliés aux besoins métier.
- [ ] Les validations encore nécessaires sont listées par discipline.
- [ ] Aucune capacité de partenaire n'est présumée certifiée ou garantie.

## Exemples d'usage
### Exemple 1 : Choisir un prestataire de paiement
**Contexte** : Une PME choisit un partenaire pour accepter des paiements en ligne dans plusieurs pays.  
**Input** : « Établis les critères métier et les questions à poser sur la couverture, la continuité, les coûts et les responsabilités; ne conclus pas sur l'agrément ou la sécurité. »  
**Output** : Une grille de sélection et une liste de preuves à obtenir, en séparant les vérifications juridiques, techniques et sécurité.

### Exemple 2 : Dépendance à une API bancaire
**Contexte** : Une application dépend d'un agrégateur pour fournir des données de comptes à ses utilisateurs.  
**Input** : « Cartographie les dépendances de l'écosystème et prépare des questions sur la disponibilité, les changements d'API et une stratégie de sortie. »  
**Output** : Une carte de dépendances et des questions à examiner avec les équipes techniques, juridiques et opérations, sans supposer les garanties du contrat.

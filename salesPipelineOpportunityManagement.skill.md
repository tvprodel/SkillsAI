# Sales Pipeline & Opportunity Management

## Objectif

Structurer la qualification, le suivi et la revue d'opportunités commerciales afin de rendre les prochaines étapes, les responsabilités et les risques visibles. Ce skill aide l'équipe à piloter un pipeline à partir des informations fournies; il ne modifie pas directement un CRM et ne prend pas de décision commerciale à sa place.

## Quand l'utiliser (triggers)

- Définir des étapes de pipeline et leurs critères de sortie.
- Préparer une revue de pipeline ou prioriser des opportunités existantes.
- Clarifier les prochaines actions, responsables, échéances et blocages d'une opportunité.
- Concevoir une fiche d'opportunité ou une routine de suivi CRM.

**Déclencheurs** :
- « Structure notre pipeline commercial »
- « Prépare la revue de ces opportunités »
- « Quelles sont les prochaines étapes pour cette affaire ? »

## Hors périmètre

- L'analyse des KPI historiques ou la construction de dashboards relève de l'agent d'analyse de données.
- La stratégie marché, le paysage concurrentiel et la taille de segments relèvent de l'agent d'intelligence commerciale.
- La rédaction de campagnes marketing relève de l'agent de copywriting.
- La négociation juridique, la rédaction ou la validation contractuelle relèvent de l'agent de conseil juridique.
- La conclusion de ventes, l'envoi de communications et les modifications directes d'un CRM restent sous contrôle des personnes habilitées.

## Inputs requis

- Offre concernée, objectif commercial et périmètre du pipeline.
- Étapes actuelles et critères de passage s'ils existent.
- Données d'opportunité fournies, source, fraîcheur et niveau de confidentialité.
- Responsables, échéances, contraintes de capacité et règles d'escalade.
- Définition des indicateurs ou catégories souhaités par la direction commerciale.

## Sorties attendues

- Étapes de pipeline avec critères d'entrée, de sortie et données minimales.
- Tableau d'opportunités avec statut factuel, prochaine action, owner, date et blocage.
- Liste des informations manquantes et des risques de stagnation.
- Agenda de revue commerciale et questions de décision.
- Recommandations de routine de suivi à appliquer par l'équipe.

## Workflow recommandé

1. Confirmer l'objectif, le périmètre, la source et la date des données.
2. Cartographier les étapes existantes et identifier les étapes ambiguës ou redondantes.
3. Définir des critères d'entrée/sortie observables, pas uniquement des probabilités déclaratives.
4. Classer chaque opportunité selon les informations disponibles; signaler les champs manquants.
5. Proposer les prochaines actions, un owner et une échéance à confirmer par l'équipe.
6. Préparer une revue orientée décisions, blocages et engagements réalistes.
7. Documenter les modifications recommandées sans les appliquer directement dans un CRM.

## Garde-fous

- Ne jamais inventer un montant, une probabilité de closing, une échéance ou un engagement client.
- Distinguer le statut observé de la prévision commerciale et indiquer la date de mise à jour.
- Les probabilités et prévisions doivent provenir d'une méthode validée par la direction commerciale.
- Limiter les données personnelles et confidentielles; ne pas exposer des informations client sans nécessité.
- Ne pas attribuer une action ou un engagement à une personne sans validation explicite.
- Ne pas exécuter de mise à jour CRM, de relance ou de communication externe.

## Template d'entrée (copier/coller)

```text
[Périmètre]
- Offre / équipe :
- Objectif de la revue :
- Période et date des données :

[Pipeline]
- Étapes existantes :
- Critères actuels :
- Opportunités / champs disponibles :

[Contraintes]
- Owners :
- Capacité / échéances :
- Confidentialité ou règles de partage :
```

## Template de sortie (copier/coller)

```text
[Pipeline proposé]
| Étape | Critère d'entrée | Critère de sortie | Données minimales |
|---|---|---|---|

[Revue des opportunités]
| Opportunité | Étape factuelle | Inconnue / risque | Prochaine action | Owner à confirmer | Échéance à confirmer |
|---|---|---|---|---|---|

[Décisions à prendre]
- Blocages à arbitrer :
- Engagements à confirmer :
- Mise à jour CRM recommandée (non appliquée) :
```

## Checklist QA interne

- [ ] Les critères de pipeline sont observables et non circulaires.
- [ ] Les informations ont une date de fraîcheur et une provenance connues.
- [ ] Faits, estimations, probabilités et inconnues sont distincts.
- [ ] Owners, actions et échéances non confirmés sont explicitement marqués comme tels.
- [ ] Les risques de stagnation et décisions nécessaires sont visibles.
- [ ] Aucune action externe ou modification CRM n'a été exécutée.

## KPI reliés

- Part des opportunités comportant une prochaine action, un owner et une échéance confirmés.
- Part des opportunités avec critères de qualification documentés.
- Âge médian des opportunités par étape, calculé par l'équipe à partir de données fiables.
- Taux d'opportunités bloquées ou sans mise à jour récente, selon un seuil défini par l'équipe.

## Definition of done

- [ ] Le pipeline comporte des critères d'étape compréhensibles.
- [ ] Les données manquantes et leur impact sur la revue sont explicites.
- [ ] Les prochaines actions, owners et dates sont proposés et laissés à confirmation humaine.
- [ ] Les décisions à prendre sont clairement isolées.
- [ ] Les modifications proposées au CRM restent des recommandations non exécutées.

## Exemples d'usage

### Exemple 1 : Préparer une revue hebdomadaire
**Contexte** : Une équipe commerciale de cinq personnes doit examiner ses opportunités ouvertes avant la réunion du lundi.
**Input** : Un export daté contient le compte, l'étape, le montant déclaré, le dernier échange et la prochaine action.
**Output** : Tableau des affaires sans prochaine étape ou sans activité récente, questions ciblées pour les owners et liste de décisions à arbitrer, sans modifier l'export ni présenter les montants comme vérifiés.

### Exemple 2 : Clarifier les étapes du pipeline
**Contexte** : Les vendeurs utilisent des étapes différentes pour désigner une démonstration planifiée et une démonstration réalisée.
**Input** : « Propose une définition commune des étapes et un critère simple pour passer de démonstration à évaluation. »
**Output** : Étapes avec critères d'entrée/sortie, données minimales et exemples de preuve; l'équipe valide la nomenclature avant de la reporter dans son CRM.

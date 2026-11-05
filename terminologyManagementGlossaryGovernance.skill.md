# Terminology Management & Glossary Governance

## Objectif
Gérer un glossaire terminologique multilingue centralisé, assurer la gouvernance des termes validés (ajout, révision, dépréciation) et la cohérence terminologique cross-langue dans tous les contenus traduits/localisés.

## Quand l'utiliser (triggers)
- « glossaire », « gestion terminologique », « cohérence terminologique », « glossary governance ».
- « terme validé », « base terminologique ».
- Lancement d'un nouveau marché/langue nécessitant une terminologie de référence.
- Détection d'incohérences terminologiques dans des contenus traduits déjà publiés.

## Hors périmètre
- Traduction/localisation elle-même (traduction de contenus complets) → compétence de base de l'agent de traduction et localisation / skill Multilingual Quality & Localization si elle existe.
- Correction grammaticale et orthographique → l'agent de relecture grammaticale.
- Rédaction de contenu source original → l'agent de rédaction technique / équipes contenu.

## Inputs requis
- Domaine métier et corpus de contenus existants (documentation, UI, marketing).
- Langues cibles concernées par le glossaire.
- Glossaires existants ou bases terminologiques partielles à consolider.
- Experts métier disponibles pour validation des termes sensibles/techniques.
- Outils de gestion terminologique utilisés le cas échéant (TMS, mémoire de traduction).

## Sorties attendues
- Glossaire multilingue structuré (terme source, traductions validées par langue, contexte d'usage, statut).
- Processus de gouvernance documenté (workflow d'ajout/révision/dépréciation).
- Rapport de cohérence terminologique sur un corpus de contenus traduits.
- Recommandations de correction en cas d'incohérence détectée.

## Workflow recommandé
1. Recensement des termes clés par domaine métier (termes techniques, noms de produits, expressions récurrentes à fort enjeu de cohérence).
2. Validation terminologique : proposition d'une traduction de référence par langue cible, validation par un expert métier ou un locuteur natif qualifié.
3. Structuration du glossaire (terme source, traductions validées, contexte d'usage/exemple de phrase, statut : validé/à réviser/déprécié).
4. Mise en place d'une gouvernance formelle (processus d'ajout d'un nouveau terme, de révision périodique, de dépréciation d'un terme obsolète, avec rôles et responsabilités clairs).
5. Vérification de la cohérence terminologique dans les livrables traduits existants (recherche automatisée ou manuelle des écarts par rapport au glossaire validé).
6. Mise à jour périodique du glossaire (intégration des nouveaux termes, révision des termes signalés, communication des changements aux équipes de traduction).

## Garde-fous
- Aucun terme ne doit être marqué « validé » sans validation par un expert métier ou un locuteur natif qualifié pour la langue concernée.
- Les termes dépréciés doivent rester tracés dans le glossaire (historique) plutôt que supprimés, pour éviter la réapparition d'incohérences.
- Toute modification d'un terme déjà largement utilisé doit être accompagnée d'un plan de propagation vers les contenus existants.
- Le glossaire doit être une source unique de vérité : éviter la coexistence de plusieurs glossaires non synchronisés pour un même domaine/langue.
- Documenter systématiquement le contexte d'usage d'un terme pour éviter les ambiguïtés de sens selon le domaine.

## Template d'entrée (copier/coller)
```text
[Domaine]
- Nom du domaine métier : ...
- Langues cibles : ...

[Corpus]
- Contenus existants à analyser : ...
- Glossaires existants à consolider : ...

[Validation]
- Experts métier disponibles : ...
```

## Template de sortie (copier/coller)
```text
[Glossaire]
| Terme source | Traduction (langue 1) | Traduction (langue 2) | Contexte d'usage | Statut |
|---------------|------------------------|------------------------|-------------------|--------|
| ... | ... | ... | ... | validé/à réviser/déprécié |

[Gouvernance]
- Processus d'ajout : ...
- Processus de révision : ...
- Processus de dépréciation : ...

[Rapport de cohérence]
- Incohérences détectées : ...
- Recommandations de correction : ...
```

## Checklist QA interne
- Chaque terme du glossaire a un statut explicite (validé/à réviser/déprécié).
- Chaque terme validé dispose d'un contexte d'usage documenté.
- Le processus de gouvernance (ajout/révision/dépréciation) est documenté et accessible aux équipes concernées.
- Une vérification de cohérence a été menée sur un échantillon représentatif de contenus traduits.
- Le glossaire est daté et versionné.

## KPI reliés
- Taux de cohérence terminologique (occurrences conformes au glossaire / occurrences totales du terme).
- Nombre de termes validés par langue.
- Nombre d'incohérences détectées et corrigées par cycle de revue.
- Délai moyen de validation d'un nouveau terme.

## Definition of done
- Glossaire multilingue structuré et publié pour les langues cibles concernées.
- Processus de gouvernance formalisé et communiqué aux équipes de traduction/contenu.
- Premier rapport de cohérence terminologique produit sur le corpus existant.
- Plan de mise à jour périodique du glossaire défini.

## Exemples d'usage

### Exemple 1 : Harmonisation terminologique avant lancement multilingue d'un produit SaaS
**Contexte** : Une entreprise SaaS B2B s'apprête à localiser son produit en français, allemand et espagnol, mais les contenus existants (UI, documentation, marketing) utilisent des traductions incohérentes pour des termes clés comme « tableau de bord », « workflow » ou « abonnement ».
**Action** : L'agent l'agent de traduction et localisation recense 45 termes clés du domaine SaaS, fait valider une traduction de référence par langue avec des experts métier locaux, structure un glossaire centralisé avec statuts et contextes d'usage, met en place un processus de gouvernance (validation obligatoire avant tout nouveau terme dans les livrables produit), puis audite 30 documents déjà traduits pour détecter les écarts.
**Résultat** : 22 incohérences terminologiques sont détectées et corrigées avant le lancement, le glossaire devient la référence unique utilisée par les traducteurs et l'équipe produit, et le taux de cohérence terminologique mesuré sur les nouveaux contenus atteint 96% dès le premier trimestre post-lancement.

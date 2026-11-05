# Template standard de création d'une skill

> **📎 Référence** : ce fichier est la **source canonique** du gabarit de création d'une skill (`skills/*.skill.md` ou `skills/<nom>/SKILL.md`). Le catalogue complet des skills actives est documenté dans [skills/readme.md](../../skills/readme.md). Toute évolution de la structure standardisée doit être faite ici en premier, puis répercutée dans le catalogue si nécessaire.

> **⚠️ RÈGLE OBLIGATOIRE** : Toute création d'une nouvelle skill DOIT respecter les 13 sections standardisées ci-dessous. Une skill incomplète est considérée **non conforme** et doit être complétée avant rattachement à un agent (voir [skills/readme.md](../../skills/readme.md), section « Règle de couverture minimale »).

---

## Convention de contenu d'un skill (13 sections standard)

Chaque skill doit contenir les sections suivantes :

1. **Objectif** : Description concise de la finalité de la skill
2. **Quand l'utiliser (triggers)** : Liste des déclencheurs et cas d'usage
3. **Hors périmètre** : Ce qui n'est PAS couvert par cette skill
4. **Inputs requis** : Données et informations nécessaires en entrée
5. **Sorties attendues** : Livrables produits par la skill
6. **Workflow recommandé** : Étapes détaillées d'exécution
7. **Garde-fous** : Règles de sécurité, contraintes et bonnes pratiques
8. **Template d'entrée (copier/coller)** : Format standardisé pour les inputs
9. **Template de sortie (copier/coller)** : Format standardisé pour les outputs
10. **Checklist QA interne** : Liste de vérification qualité avant livraison
11. **KPI reliés** : Indicateurs de performance et métriques
12. **Definition of done** : Critères d'acceptation mesurables
13. **Exemples d'usage** : Cas concrets et scénarios types (minimum 2-3 exemples)

### Section conditionnelle : Sources / Références (si source externe utilisée)

Si la skill s'appuie sur une source externe (documentation officielle, article, papier de recherche, norme, etc.), le lien de cette source **DOIT** figurer dans une section dédiée en fin de fichier, et nulle part ailleurs (pas uniquement cité dans l'Objectif, le Workflow ou les Garde-fous). Cette section n'est pas l'une des 13 sections standard ci-dessus ; elle est ajoutée uniquement si une source externe est effectivement utilisée.

- **Titre de section** : `## Contraintes et références` (convention dominante du catalogue) ou `## Références`.
- **Format par lien** : `[Nom de la source](URL)` avec, si pertinent, la date de consultation et une mention explicite qu'il s'agit d'une synthèse originale (sans reproduction du texte source), par exemple :
  `- Référence officielle consultée le AAAA-MM-JJ : [Nom](https://...). Synthèse originale, sans reproduction du texte source ; vérifier les versions et l'applicabilité au contexte.`
- **Règle stricte** : une référence mentionnée dans le corps du texte (Objectif, Workflow, Garde-fous, Exemples) doit être reprise avec son lien complet dans cette section ; elle ne doit pas rester un lien isolé ailleurs dans le fichier.
- Si aucune source externe n'est utilisée, cette section est omise.

### Taux de conformité (audit 2026-08-04)
- ✅ **89% de conformité** sur les 10 premières sections (99/111 skills)
- ✅ **82% de conformité** sur Templates et Triggers (91/111 skills)
- ✅ **77% de conformité** sur Checklist QA et KPI (85/111 skills)
- ✅ **74% de conformité** sur Exemples d'usage (82/111 skills)
- ⚠️ **29 skills à compléter** avec exemples d'usage manquants

---

## Template copier/coller (structure recommandée)

```markdown
# [Nom de la Skill]

## Objectif
[Description concise de l'objectif]

## Quand l'utiliser (triggers)
- Déclencheur 1
- Déclencheur 2
- Déclencheur 3

## Hors périmètre
- ❌ Ce qui n'est PAS couvert
- ❌ Délégation vers autre skill/agent si applicable

## Inputs requis
- Input 1 : [description]
- Input 2 : [description]
- Input 3 : [description]

## Sorties attendues
- Sortie 1 : [description]
- Sortie 2 : [description]

## Workflow recommandé
1. Étape 1
2. Étape 2
3. Étape 3

## Garde-fous
- GF-01 : [règle de sécurité/contrainte]
- GF-02 : [règle de sécurité/contrainte]

## Template d'entrée (copier/coller)
\```text
[Format standardisé inputs]
\```

## Template de sortie (copier/coller)
\```text
[Format standardisé outputs]
\```

## Checklist QA interne
- [ ] Critère 1
- [ ] Critère 2
- [ ] Critère 3

## KPI reliés
- KPI 1 : [description + mesure]
- KPI 2 : [description + mesure]

## Definition of done
- [ ] DoD 1 : [critère mesurable]
- [ ] DoD 2 : [critère mesurable]
- [ ] DoD 3 : [critère mesurable]

## Exemples d'usage

### Exemple 1 : [Titre cas d'usage]
**Contexte** : [situation]
**Input** : [données fournies]
**Output** : [résultat attendu]

### Exemple 2 : [Titre cas d'usage]
**Contexte** : [situation]
**Input** : [données fournies]
**Output** : [résultat attendu]

## Contraintes et références
<!-- Section à ajouter UNIQUEMENT si une source externe est utilisée (voir règle ci-dessus) ; sinon, omettre entièrement cette section. -->
- Référence officielle consultée le AAAA-MM-JJ : [Nom de la source](https://...). Synthèse originale, sans reproduction du texte source ; vérifier les versions et l'applicabilité au contexte.
```

---

## Migration recommandée (skills existantes incomplètes)

- Ajouter en priorité : **Garde-fous**, **Templates** (entrée/sortie), **Checklist QA interne** (bonnes pratiques standardisées les moins souvent présentes).

---

## Processus de création recommandé

1. **Identifier le besoin** : compétence manquante pour un agent (ex: couverture minimale de 3 skills exclusives non atteinte, voir [skills/readme.md](../../skills/readme.md)).
2. **Choisir le format** : skill simple `skills/nomDeLaSkill.skill.md`, ou workflow natif complet `skills/<nom>/SKILL.md` (voir [templateAgent.md](./templateAgent.md) pour la distinction agent/skill).
3. **Rédiger le fichier** : utiliser le gabarit copier/coller ci-dessus, remplir les 13 sections.
4. **Rattacher à l'agent concerné** : ajouter la ligne dans la table centrale de [skills/readme.md](../../skills/readme.md) et dans la section « Liens skills operationnels » du fichier agent correspondant.
5. **Vérifier la conformité** : exécuter [checkAgentSkillCoverage.py](../scripts/checkAgentSkillCoverage.py) pour valider l'exclusivité et la couverture minimale.
6. **Tracer la création** : ajouter une entrée dans [multiAgentsFiles/todoAgents/todoAgents.md](../todoAgents/todoAgents.md) si la création s'inscrit dans un chantier suivi.

---

## FAQ

**Q : Une skill doit-elle être exclusive à un seul agent ?**
R : Non, mais chaque agent doit posséder au moins 3 skills **exclusives** (rattachées à lui seul). Les skills partagées sont autorisées en complément, sans compter dans ce minimum (voir [skills/readme.md](../../skills/readme.md)).

**Q : Faut-il créer un dossier `skills/<nom>/SKILL.md` ou un simple fichier `skills/nom.skill.md` ?**
R : Le format fichier simple (`.skill.md`) est utilisé pour les compétences rattachées à un ou plusieurs agents et comptabilisées dans le catalogue. Le format dossier (`SKILL.md`) est réservé aux workflows natifs invocables à la demande, non rattachés à un agent (ex: `createnewagent`, `workflow`).

**Q : Où documenter le template de création d'un agent (et non d'une skill) ?**
R : Voir [templateAgent.md](./templateAgent.md), dans ce même dossier.

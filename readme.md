# Skills Backlog

Ce dossier contient le catalogue des compétences opérationnelles de l'équipe d'agents.

**État vérifié le 2026-10-26** : 81 agents, 311 skills actives, dont 253 rattachées à un seul agent et 58 partagées. Chaque agent possède au moins 3 skills exclusives ; 113 skills spécialisées ont été ajoutées lors de la migration du 2026-10-21, puis 12 pour les quatre agents créatifs 2D/3D (2026-10-25) et 21 pour sept agents Creatives/GameDev (2026-10-26), et les fichiers préexistants ont été conservés. Le contrôle porte sur les déclarations et les tables centrales, pas sur une invocation réelle de chaque agent.

Les partages transverses utiles ont été conservés. Les rattachements issus du remplissage heuristique sans rapport avec le rôle (par exemple architecture Active Directory chez un administrateur Debian, ou durcissement Linux chez un développeur .NET) ont été remplacés par une sélection explicite. Les références publiques des nouvelles skills sont indiquées dans chaque fichier ; elles éclairent la méthode, sans constituer une certification.

Le [mapping des agents](../multiAgentsFiles/docsAgents/reference/mappingAgentSkill.md) présente le socle exclusif minimal ; le [mini-index inverse](../multiAgentsFiles/docsAgents/reference/miniIndexSkillAgents.md) expose tous les rattachements, y compris les partages.

## Table centrale de rattachement

> 📘 **Référence complète** : [skillsRoutageAndAttr.md](../multiAgentsFiles/skillsRoutageAndAttr.md) — table centrale Skill → Agents avec lien direct vers chaque fichier skill. **Source canonique faisant foi** pour le rattachement Skill ↔ Agent.

## Règle de couverture minimale
- Chaque agent doit posséder au moins 3 skills actives exclusives : 3 compétences distinctes, rattachées à ce seul agent.
- Les skills partagées sont autorisées en supplément, mais ne comptent pas dans ce minimum. Plusieurs liens vers le même fichier ne comptent qu'une fois.
- Les sections "Skills suggerees (rattachement)" et "Liens skills operationnels" doivent déclarer les mêmes skills ; les tables centrales doivent être synchronisées.
- L'exclusivité est vérifiée sur les fichiers agents et les tables centrales (catalogue, mapping principal et mini-index inverse). Les copies de contenu ne peuvent pas servir à atteindre le quota ; la différence de sens exige une revue humaine.
- Les skills non rattachées doivent être explicitement listées comme "inactive / backlog" pour rester cohérentes avec le catalogue complet.

## Documentation de référence (hors catalogue)
- [templateSkills.md](../multiAgentsFiles/templates/templateSkills.md) : template standard de création d'une skill (13 sections, gabarit copier/coller, processus de création). **Source canonique faisant foi** pour toute nouvelle skill.
- [templateAgent.md](../multiAgentsFiles/templates/templateAgent.md) : template standard de création d'un agent (frontmatter, périmètre, processus, format de sortie, etc.).
- [createnewagent/SKILL.md](../multiAgentsFiles/prompts/createnewagent/SKILL.md) : prompt structuré en 8 phases pour créer un nouvel agent complet. Déplacé hors du catalogue `skills/` le 2026-11-03 (n'est pas une compétence rattachée à un agent).
- [workflow/SKILL.md](../multiAgentsFiles/prompts/workflow/SKILL.md) : prompt structuré de conception de workflow d'intégration/automatisation IA. Déplacé hors du catalogue `skills/` le 2026-11-03 (n'est pas une compétence rattachée à un agent).
- Le contrôle [checkAgentSkillCoverage.py](../multiAgentsFiles/scripts/checkAgentSkillCoverage.py) vérifie qu'aucun workflow natif `skills/<nom>/SKILL.md` ne subsiste non documenté.

## Skills inactives / backlog
- Aucune skill inactive détectée pour le moment.

# Game Audio Mixing & Loudness

## Objectif
Produire un livrable maîtrisé : plan de mixage et de loudness d'un jeu ou d'un média (hiérarchie des catégories sonores, niveaux cibles, traitement dynamique) avec mesures de contrôle.


## Quand l'utiliser (triggers)
- Demande portant sur « Game Audio Mixing & Loudness » ou sur le livrable : plan de mixage et de loudness d'un jeu ou d'un média (hiérarchie des catégories sonores, niveaux cibles, traitement dynamique) avec mesures de contrôle.
- Besoin de vérifier ce résultat : le mix de référence respecte la cible de loudness déclarée, sans écrêtage, et les dialogues restent intelligibles sous les SFX et la musique.

## Hors périmètre
- Ne pas remplacer les domaines des agents complémentaires : présenter les interfaces et transmettre les besoins à l'agent rattaché (voir table de routage).
- L'exécution système, les modifications de fichiers, les tests et les publications relèvent de l'agent rattaché (voir table de routage) ; cette skill n'accorde aucun outil supplémentaire.
- Ne pas composer ni arranger la musique (→ l'agent de composition musicale) ; ne pas écrire dialogues ou scripts (→ l'agent de narration interactive) ni traduire les voix (→ l'agent de traduction et localisation).
- Ne pas confondre plan de mixage, revue statique et résultat d'une écoute réelle sur le matériel de diffusion cible.

## Inputs requis
- Stems ou sons disponibles par catégorie (voix, SFX, ambiances, musique, interface), plateforme et matériel d'écoute cibles (casque, haut-parleurs, mobile).
- Cible de loudness retenue et sa justification (norme ou recommandation de la plateforme, à vérifier), plage dynamique souhaitée.
- Périmètre autorisé, version des logiciels (Ardour, Audacity, FFmpeg), décisions déjà validées ; marquer les éléments inconnus avant de conclure.

## Sorties attendues
- Plan de mixage : catégories, niveaux relatifs, priorités (dialogues > alertes > SFX > ambiances > musique, à adapter), chaînes d'effets par bus.
- Rapport de mesure : loudness intégrée, pic réel (true peak) et plage dynamique du mix de référence, avec l'outil de mesure et sa version.
- Brief des décisions ou actions nécessaires pour l'agent rattaché, sans les annoncer déjà exécutées.

## Workflow recommandé
1. Cadrer la cible : plateforme, contextes d'écoute, norme de loudness à vérifier, hiérarchie des catégories sonores.
2. Inventorier les stems et les sons, relever leurs niveaux bruts et les conflits fréquentiels (voix contre musique, graves contre SFX).
3. Établir les niveaux relatifs par catégorie et les traitements par bus : égalisation, compression, limiteur, réverbération partagée.
4. Définir les règles de priorité dynamique (ducking, atténuation de la musique sous la voix) et les transmettre à l'agent technique du moteur de jeu pour l'implémentation.
5. Mesurer le mix de référence (loudness intégrée, pic réel) et vérifier le critère : cible respectée, aucun écrêtage, voix intelligibles sur au moins deux contextes d'écoute.
6. Restituer résultat, hypothèses, risques et prochaines actions ; signaler explicitement les contextes d'écoute non testés.

## Garde-fous
- Le mix de référence respecte la cible de loudness déclarée, sans écrêtage, et les dialogues restent intelligibles sous les SFX et la musique.
- Ne pas inventer de mesure, d'accord, de preuve ou de source ; distinguer observé, inféré et non testé.
- Ne pas imposer une valeur de loudness universelle : la cible dépend de la plateforme et doit être vérifiée dans sa documentation.
- Ne pas transmettre d'artefact privé ou de donnée personnelle à un service tiers ; minimiser les données sensibles.
- Privilégier les outils libres maintenus (Ardour, Audacity, FFmpeg) et vérifier les versions applicables sans introduire de dépendance EOL ; middleware propriétaire seulement si justifié et licence vérifiée.
- Tracer toute source audio externe dans `docs/imageLicencesSources.md` (format `Nomdefichier | licence | url source`).
- Lire la référence dans son contexte : elle éclaire la méthode, elle ne certifie pas ce livrable et n'impose pas de seuil universel.

## Templates copier/coller
### Entrée
```text
Objet : Game Audio Mixing & Loudness
Inputs : stems par catégorie, plateforme et écoute cibles, cible de loudness et sa source, plage dynamique souhaitée
Version / périmètre autorisé :
Résultat demandé : plan de mixage et de loudness avec rapport de mesure
Contraintes et inconnues :
```

### Sortie
```text
Résultat : plan de mixage et de loudness avec rapport de mesure
| Catégorie / bus | Niveau relatif | Traitement | Mesure (loudness, pic réel) + outil | Limite / action |
|---|---|---|---|---|
Hypothèses :
Risques :
Prochaines actions :
```

## Checklist QA interne
- [ ] Les inputs et les limites d'autorisation sont identifiés.
- [ ] Les trois analyses sont documentées : hiérarchie et niveaux relatifs des catégories ; traitements par bus et règles de priorité dynamique ; mesures du mix de référence et contextes d'écoute testés.
- [ ] Le critère d'acceptation est vérifié ou explicitement marqué non vérifié.
- [ ] Aucun résultat de mesure, d'écoute ou accord humain n'est inventé.

## KPI reliés
- Couverture des catégories sonores : catégories avec niveau et traitement définis / catégories applicables (dénominateur conservé).
- Écart entre la loudness intégrée mesurée et la cible déclarée, exprimé dans l'unité de la cible ; ne pas compter une hypothèse comme mesure.
- Nombre de contextes d'écoute où la voix reste inintelligible ou le signal écrête : à maintenir à zéro avant livraison.

## Definition of done
- [ ] Plan de mixage et de loudness livré dans le périmètre convenu, avec rapport de mesure.
- [ ] Le mix de référence respecte la cible déclarée, sans écrêtage, avec voix intelligibles.
- [ ] Preuves, inconnues, exceptions et actions restantes sont lisibles ; aucune réussite globale en cas de vérification bloquante manquante.

## Exemples d'usage
**Cas nominal** : à partir de stems voix, SFX, ambiances et musique d'un niveau de jeu, produire un plan de mixage avec cible de loudness sourcée, puis mesurer le mix et vérifier le critère d'acceptation ci-dessus.

**Cas limite** : la cible de loudness de la plateforme n'est pas documentée ; livrer le plan avec une cible provisoire explicitement marquée à confirmer, sans la présenter comme norme.

## Contraintes et références
- Référence officielle : [Ardour Manual](https://manual.ardour.org/). Synthèse originale, sans reproduction du texte source ; page non consultée en détail lors de la création, vérifier les versions et l'applicabilité au contexte.
- Création : DEL-20261026-GAMEDEV-CREA-AGENTS.

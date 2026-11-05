# Game Music Composition & Themes

## Objectif
Produire un livrable maîtrisé : dossier de composition thématique (thèmes, leitmotivs, harmonie, orchestration) avec partition ou maquette audio originale et fiche tempo/tonalité.


## Quand l'utiliser (triggers)
- Demande portant sur « Game Music Composition & Themes » ou sur le livrable : dossier de composition thématique (thèmes, leitmotivs, harmonie, orchestration) avec partition ou maquette audio originale et fiche tempo/tonalité.
- Besoin de vérifier ce résultat : chaque thème est identifiable à l'écoute isolée, ses variantes restent reconnaissables et la fiche mentionne tempo, tonalité, métrique et durée.

## Hors périmètre
- Ne pas remplacer les domaines des agents complémentaires : présenter les interfaces et transmettre les besoins à l'agent rattaché (voir table de routage).
- L'exécution système, les modifications de fichiers, les tests et les publications relèvent de l'agent rattaché (voir table de routage) ; cette skill n'accorde aucun outil supplémentaire.
- Ne pas confondre préparation d'un protocole, revue statique et résultat d'une exécution réelle dans le logiciel.
- Ne pas traiter les effets sonores, le mixage global ni l'implémentation audio (l'agent de sound design), ni les paroles (l'agent de narration via l'agent de coordination).

## Inputs requis
- Brief de direction musicale : univers, ton émotionnel, personnages ou lieux à caractériser, références de genre (sans œuvre protégée à imiter), durée visée et palette instrumentale.
- Contraintes techniques : moteur cible, budget de pistes ou de polyphonie, formats de livraison, logiciels disponibles et versions.
- Périmètre autorisé, sources accessibles et décisions déjà validées ; marquer les éléments inconnus avant de conclure.

## Sorties attendues
- Dossier de composition : liste des thèmes et leitmotivs, tonalités, harmonie de base, orchestration, avec partition (MuseScore, LilyPond) ou maquette audio originale.
- Fiche par pièce : tempo, tonalité, métrique, durée, instrumentation, usage prévu dans le jeu.
- Preuves ou références par constat ; hypothèses, exceptions et vérifications non réalisées séparées.
- Brief des décisions ou actions nécessaires pour l'agent rattaché, sans les annoncer déjà exécutées.

## Workflow recommandé
1. Cadrer les inputs : brief de direction musicale, contraintes techniques, palette instrumentale ; vérifier les préconditions, les licences et les autorisations.
2. Définir les thèmes et leitmotivs (motif court, intervalle caractéristique, rythme) et les associer à des personnages, lieux ou états du jeu.
3. Construire l'harmonie et la structure (modes, progressions, modulations) puis orchestrer en respectant tessiture et équilibre de la palette.
4. Décliner chaque leitmotiv en variantes (tonalité, mode, tempo, orchestration) sans perdre son identité.
5. Vérifier le livrable par ce critère : chaque thème est identifiable à l'écoute isolée, ses variantes restent reconnaissables et la fiche mentionne tempo, tonalité, métrique et durée ; contrôler l'originalité (aucune mélodie protégée reproduite ou pastichée).
6. Restituer résultat, hypothèses, risques et prochaines actions ; signaler explicitement les blocages.

## Garde-fous
- Chaque thème est identifiable à l'écoute isolée et la fiche pièce est complète (tempo, tonalité, métrique, durée).
- Ne pas inventer de mesure, d'accord, de preuve ou de source ; distinguer observé, inféré et non testé.
- Ne pas transmettre d'artefact privé ou de donnée personnelle à un service tiers ; minimiser les données sensibles.
- Privilégier les outils libres maintenus (MuseScore, LilyPond, LMMS, Ardour) et vérifier les versions applicables sans introduire de dépendance EOL.
- Musique originale uniquement ou Domaine Public/CC0 : ne jamais reproduire une œuvre protégée ni pasticher une mélodie protégée ; tracer chaque source externe (échantillons, soundfonts) dans `docs/imageLicencesSources.md` (format `Nomdefichier | licence | url source`).
- Lire la référence dans son contexte : elle éclaire la méthode, elle ne certifie pas ce livrable et n'impose pas de seuil universel.

## Templates copier/coller
### Entrée
```text
Objet : Game Music Composition & Themes
Inputs : brief de direction musicale, palette instrumentale, contraintes techniques, durée visée
Version / périmètre autorisé :
Résultat demandé : dossier de composition thématique avec partition ou maquette audio originale et fiche tempo/tonalité
Contraintes et inconnues :
```

### Sortie
```text
Résultat : dossier de composition thématique (thèmes, leitmotivs, harmonie, orchestration)
| Pièce / thème | Tempo - tonalité - métrique - durée | Instrumentation / usage | Limite / action |
|---|---|---|---|
Hypothèses :
Risques :
Prochaines actions :
```

## Checklist QA interne
- [ ] Les inputs et les limites d'autorisation sont identifiés.
- [ ] Les trois analyses sont documentées : thèmes et leitmotivs associés à leur usage ; harmonie, structure et orchestration ; variantes et contrôle d'originalité.
- [ ] Le critère d'acceptation est vérifié ou explicitement marqué non vérifié.
- [ ] Aucun résultat d'exécution ou accord humain n'est inventé.

## KPI reliés
- Couverture des éléments requis : thèmes et pièces documentés (fiche complète) / thèmes et pièces demandés (dénominateur conservé).
- Part des thèmes dont au moins une variante a été vérifiée comme reconnaissable ; ne pas compter une hypothèse comme preuve.
- Nombre d'écarts au critère suivant restant ouverts : chaque thème est identifiable à l'écoute isolée et la fiche mentionne tempo, tonalité, métrique et durée.

## Definition of done
- [ ] Dossier de composition thématique livré dans le périmètre convenu, avec partition ou maquette audio originale.
- [ ] Chaque thème est identifiable à l'écoute isolée, ses variantes restent reconnaissables et la fiche mentionne tempo, tonalité, métrique et durée.
- [ ] Preuves, inconnues, exceptions et actions restantes sont lisibles ; aucune réussite globale en cas de vérification bloquante manquante.

## Exemples d'usage
**Cas nominal** : à partir d'un brief d'univers et d'une palette instrumentale, produire le thème principal et deux leitmotivs de personnages avec leurs variantes, puis vérifier le critère d'acceptation ci-dessus.

**Cas limite** : le brief ne donne que des références à des œuvres protégées ; ne pas les imiter, proposer des caractéristiques abstraites (mode, tempo, instrumentation) à valider, et indiquer ce qui empêche la validation sans substituer une valeur par défaut.

## Contraintes et références
- Référence officielle : [MuseScore - Handbook](https://musescore.org/en/handbook). Synthèse originale, sans reproduction du texte source ; page non consultée en détail lors de la création, vérifier les versions et l'applicabilité au contexte.
- Création : DEL-20261026-GAMEDEV-CREA-AGENTS.

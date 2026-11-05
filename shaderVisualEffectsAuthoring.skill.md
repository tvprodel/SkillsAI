# Shader Visual Effects Authoring

## Objectif
Produire un livrable maîtrisé : shader visuel (Godot Shading Language ou VisualShader) pour un effet de matériau, de dissolution, de distorsion, de contour ou de post-traitement, avec paramètres exposés et scène de test.


## Quand l'utiliser (triggers)
- Demande portant sur « Shader Visual Effects Authoring » ou sur le livrable : shader visuel (Godot Shading Language ou VisualShader) pour un effet de matériau, de dissolution, de distorsion, de contour ou de post-traitement, avec paramètres exposés et scène de test.
- Besoin de vérifier ce résultat : le shader compile sans erreur ni avertissement bloquant, ses paramètres exposés pilotent l'effet de 0 à 100 % et le rendu reste identique sur les cas de test listés.

## Hors périmètre
- Ne pas remplacer les domaines des agents complémentaires : présenter les interfaces et transmettre les besoins à l'agent rattaché (voir table de routage).
- L'exécution système, les modifications de fichiers, les tests et les publications relèvent de l'agent rattaché (voir table de routage) ; cette skill n'accorde aucun outil supplémentaire.
- Ne pas confondre préparation d'un protocole, revue statique et résultat d'une exécution réelle dans le logiciel.
- Le moteur de rendu bas niveau et les pipelines de rendu personnalisés restent hors périmètre ; les transmettre à l'agent de coordination pour l'agent de développement moteur.

## Inputs requis
- Effet visuel voulu (référence, comportement dans le temps), type de support (CanvasItem 2D, Spatial 3D, particules, post-traitement plein écran), version de Godot et moteur de rendu (Compatibilité, Mobile, Forward+).
- Textures d'entrée (bruit, masques, rampes de dégradé) avec leur licence, et paramètres à exposer à l'éditeur ou au code.
- Périmètre autorisé, plateformes cibles et décisions déjà validées ; marquer les éléments inconnus avant de conclure.

## Sorties attendues
- Shader en Godot Shading Language ou VisualShader, documenté (uniforms, plages, valeurs par défaut) et accompagné d'une scène de test avec des valeurs de paramètres représentatives.
- Notes de compatibilité par moteur de rendu et par plateforme cible, avec repli simplifié si une fonction n'est pas disponible.
- Preuves ou références par constat ; hypothèses, exceptions et vérifications non réalisées séparées.
- Brief des décisions ou actions nécessaires pour l'agent rattaché, sans les annoncer déjà exécutées.

## Workflow recommandé
1. Cadrer l'effet : support, moteur de rendu, plateformes, paramètres à exposer et textures d'entrée ; vérifier licences et autorisations.
2. Choisir le mode d'écriture (VisualShader pour itérer visuellement, code pour le contrôle fin) et le type de shader (canvas_item, spatial, particles, post-traitement).
3. Construire la logique par blocs (UV animés, masque de bruit, seuil de dissolution, rampe de couleur, émission) et exposer les uniforms avec indications de plage.
4. Tester dans une scène dédiée : valeurs extrêmes des paramètres, échelles et résolutions différentes, fond clair et sombre.
5. Vérifier le critère : le shader compile sans erreur ni avertissement bloquant, ses paramètres exposés pilotent l'effet de 0 à 100 % et le rendu reste identique sur les cas de test listés.
6. Restituer shader, notes de compatibilité, hypothèses, risques et prochaines actions (transmission à l'agent technique du moteur de jeu pour le pilotage par code) ; signaler explicitement les blocages.

## Garde-fous
- Le shader compile sans erreur ni avertissement bloquant et reste fonctionnel sur le moteur de rendu cible déclaré.
- Ne pas affirmer qu'une fonction du langage de shading existe sans la vérifier dans la documentation de la version ciblée.
- Limiter les effets de scintillement ou de flash rapide dans les shaders animés, exposer un paramètre de réduction d'intensité et se référer aux lignes directrices sur la photosensibilité.
- Ne pas inventer de mesure, d'accord, de preuve ou de source ; distinguer observé, inféré et non testé.
- Ne pas transmettre d'artefact privé ou de donnée personnelle à un service tiers ; minimiser les données sensibles.
- Privilégier les outils libres maintenus et vérifier les versions applicables sans introduire de dépendance EOL.
- Utiliser uniquement des ressources originales, du Domaine Public ou CC0 ; tracer chaque source externe dans `docs/imageLicencesSources.md` (format `Nomdefichier | licence | url source`).
- Lire la référence dans son contexte : elle éclaire la méthode, elle ne certifie pas ce livrable et n'impose pas de seuil universel.

## Templates copier/coller
### Entrée
```text
Objet : Shader Visual Effects Authoring
Inputs : effet voulu, type de support, version de Godot et moteur de rendu, textures d'entrée et licences, paramètres à exposer
Version / périmètre autorisé :
Résultat demandé : shader documenté avec paramètres exposés et scène de test
Contraintes et inconnues :
```

### Sortie
```text
Résultat : shader (type, paramètres exposés, scène de test)
| Uniform / bloc | Plage et valeur par défaut | Cas de test observé | Limite / action |
|---|---|---|---|
Compatibilité (moteur de rendu / plateforme) :
Hypothèses :
Risques :
Prochaines actions :
```

## Checklist QA interne
- [ ] Les inputs, les licences des textures et les limites d'autorisation sont identifiés.
- [ ] Les trois analyses sont documentées : choix du mode d'écriture et du type de shader ; construction par blocs avec uniforms documentés ; tests aux valeurs extrêmes et sur fonds clairs et sombres.
- [ ] Le critère d'acceptation est vérifié ou explicitement marqué non vérifié.
- [ ] Un paramètre de réduction d'intensité existe pour les effets animés à fort contraste.
- [ ] Aucun résultat d'exécution ou accord humain n'est inventé.

## KPI reliés
- Couverture des éléments requis : uniforms documentés / uniforms exposés (dénominateur conservé).
- Nombre de cas de test passés / cas de test listés, par moteur de rendu cible.
- Nombre d'écarts au critère suivant restant ouverts : compilation sans erreur, pilotage de 0 à 100 %, rendu identique sur les cas listés.

## Definition of done
- [ ] Shader documenté avec paramètres exposés et scène de test livré dans le périmètre convenu.
- [ ] Le shader compile sans erreur bloquante, ses paramètres pilotent l'effet de 0 à 100 % et le rendu est identique sur les cas de test listés.
- [ ] Preuves, inconnues, exceptions et actions restantes sont lisibles ; aucune réussite globale en cas de vérification bloquante manquante.

## Exemples d'usage
**Cas nominal** : à partir d'un effet « dissolution d'un ennemi avec bordure lumineuse », d'une texture de bruit originale et de Godot 4.x en Forward+, produire un shader spatial avec uniforms de seuil et de couleur de bordure, puis vérifier le critère d'acceptation ci-dessus.

**Cas limite** : le moteur de rendu cible (par exemple Compatibilité) ne permet pas une fonction prévue ; livrer la version établie avec un repli simplifié et indiquer précisément ce qui empêche la validation complète, sans substituer une valeur par défaut.

## Contraintes et références
- Référence officielle : [Godot - Shading language](https://docs.godotengine.org/en/stable/tutorials/shaders/shader_reference/shading_language.html). Synthèse originale, sans reproduction du texte source ; page non consultée en détail lors de la création, vérifier les versions et l'applicabilité au contexte.
- Création : DEL-20261026-GAMEDEV-CREA-AGENTS.

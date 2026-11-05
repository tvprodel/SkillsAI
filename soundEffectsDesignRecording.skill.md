# Sound Effects Design & Recording

## Objectif
Produire un livrable maîtrisé : bibliothèque d'effets sonores (SFX et foley) originaux, enregistrés, synthétisés ou issus du Domaine Public/CC0, nettoyés, nommés et prêts à être mixés.


## Quand l'utiliser (triggers)
- Demande portant sur « Sound Effects Design & Recording » ou sur le livrable : bibliothèque d'effets sonores (SFX et foley) originaux, enregistrés, synthétisés ou issus du Domaine Public/CC0, nettoyés, nommés et prêts à être mixés.
- Besoin de vérifier ce résultat : chaque son de la liste de besoins est livré en WAV propre (sans clic ni écrêtage), nommé selon la convention et associé à une source tracée.

## Hors périmètre
- Ne pas remplacer les domaines des agents complémentaires : présenter les interfaces et transmettre les besoins à l'agent rattaché (voir table de routage).
- L'exécution système, les modifications de fichiers, les tests et les publications relèvent de l'agent rattaché (voir table de routage) ; cette skill n'accorde aucun outil supplémentaire.
- Ne pas composer de musique (→ l'agent de composition musicale) ni écrire le code audio du moteur (→ l'agent de développement Godot).
- Ne pas confondre préparation d'un protocole d'enregistrement, revue statique et résultat d'une écoute ou d'une exécution réelle dans le logiciel.

## Inputs requis
- Liste des événements sonores (action, matériau, durée indicative), ambiance visuelle ou narrative, plateforme cible.
- Matériel et logiciels disponibles (micro, interface, Audacity, Ardour, Sox/FFmpeg), format et fréquence d'échantillonnage attendus.
- Périmètre autorisé, sources externes envisagées et leur licence, décisions déjà validées ; marquer les éléments inconnus avant de conclure.

## Sorties attendues
- Bibliothèque de SFX (WAV non compressé, plusieurs variations par événement) avec convention de nommage et fiche de métadonnées.
- Journal des sources : origine de chaque son (enregistré, synthétisé, externe) avec licence et URL ; hypothèses, exceptions et vérifications non réalisées séparées.
- Brief des décisions ou actions nécessaires pour l'agent rattaché, sans les annoncer déjà exécutées.

## Workflow recommandé
1. Cadrer la liste de besoins : événements, matériaux, durée, intensité, nombre de variations, format cible ; vérifier préconditions et autorisations.
2. Choisir la source de chaque son : enregistrement (foley, terrain), synthèse, ou ressource Domaine Public/CC0 ; tracer toute source externe.
3. Capturer ou synthétiser avec marge de gain suffisante (pas d'écrêtage), plusieurs prises par événement.
4. Éditer : découpe, fondus courts aux bords, réduction de bruit mesurée, égalisation, superposition de couches (attaque, corps, queue).
5. Normaliser le nommage, exporter en WAV et vérifier le critère : chaque son est propre (sans clic ni écrêtage), nommé selon la convention et associé à une source tracée.
6. Restituer résultat, hypothèses, risques et prochaines actions ; signaler explicitement les blocages et ce qui n'a pas pu être écouté.

## Garde-fous
- Chaque son de la liste est livré en WAV propre (sans clic ni écrêtage), nommé selon la convention et associé à une source tracée.
- Ne pas inventer de mesure, d'accord, de preuve ou de source ; distinguer observé, inféré et non testé.
- Ne pas transmettre d'artefact privé ou de donnée personnelle à un service tiers ; minimiser les données sensibles (voix enregistrées comprises).
- Privilégier les outils libres maintenus (Audacity, Ardour, Sox/FFmpeg) et vérifier les versions applicables sans introduire de dépendance EOL.
- Utiliser uniquement des sons originaux, du Domaine Public ou CC0 ; tracer chaque source externe dans `docs/imageLicencesSources.md` (format `Nomdefichier | licence | url source`).
- Lire la référence dans son contexte : elle éclaire la méthode, elle ne certifie pas ce livrable et n'impose pas de seuil universel.

## Templates copier/coller
### Entrée
```text
Objet : Sound Effects Design & Recording
Inputs : liste des événements sonores, ambiance, plateforme cible, matériel et logiciels, format et fréquence d'échantillonnage
Version / périmètre autorisé :
Résultat demandé : bibliothèque de SFX/foley originaux ou CC0, nettoyés et nommés
Contraintes et inconnues :
```

### Sortie
```text
Résultat : bibliothèque de SFX/foley originaux ou CC0, nettoyés et nommés
| Son / événement | Source (enregistré / synthétisé / externe) | Licence + URL | Contrôle (clic, écrêtage, nommage) | Limite / action |
|---|---|---|---|---|
Hypothèses :
Risques :
Prochaines actions :
```

## Checklist QA interne
- [ ] Les inputs et les limites d'autorisation sont identifiés.
- [ ] Les trois analyses sont documentées : choix et traçabilité de la source de chaque son ; contrôle de capture (gain, bruit de fond, écrêtage) ; contrôle d'édition (fondus, clics, nommage, variations).
- [ ] Le critère d'acceptation est vérifié ou explicitement marqué non vérifié.
- [ ] Aucun résultat d'écoute, d'exécution ou accord humain n'est inventé.

## KPI reliés
- Couverture des événements sonores : événements livrés avec au moins le nombre de variations demandé / événements de la liste (dénominateur conservé).
- Part des sons avec source et licence tracées dans `docs/imageLicencesSources.md` ; ne pas compter une hypothèse comme preuve.
- Nombre de sons présentant encore un clic, un écrêtage ou un nom non conforme : à maintenir à zéro avant livraison.

## Definition of done
- [ ] Bibliothèque de SFX/foley livrée dans le périmètre convenu, en WAV avec métadonnées.
- [ ] Chaque son est propre (sans clic ni écrêtage), nommé selon la convention et associé à une source tracée.
- [ ] Preuves, inconnues, exceptions et actions restantes sont lisibles ; aucune réussite globale en cas de vérification bloquante manquante.

## Exemples d'usage
**Cas nominal** : à partir d'une liste de 12 événements (pas sur gravier, porte, coffre, etc.), produire 3 variations WAV par événement, nommées `sfxFootstepGravel01`, avec journal des sources, puis vérifier le critère d'acceptation ci-dessus.

**Cas limite** : une licence ou une source nécessaire manque ; livrer les éléments établis et indiquer précisément ce qui empêche la validation, sans substituer une valeur par défaut.

## Contraintes et références
- Référence officielle : [Audacity Manual](https://manual.audacityteam.org/). Synthèse originale, sans reproduction du texte source ; page non consultée en détail lors de la création, vérifier les versions et l'applicabilité au contexte.
- Création : DEL-20261026-GAMEDEV-CREA-AGENTS.

# Blender UV Unwrap & PBR Material Setup

## Objectif
Produire un livrable maîtrisé : dépliage UV et matériaux PBR avec cartes de textures nommées et guide de bake.


## Quand l'utiliser (triggers)
- Demande portant sur « Blender UV Unwrap & PBR Material Setup » ou sur le livrable : dépliage UV et matériaux PBR avec cartes de textures nommées et guide de bake.
- Besoin de vérifier ce résultat : les îlots UV ne se chevauchent pas hors choix documenté et les cartes sont nommées selon la convention.

## Hors périmètre
- Ne pas remplacer les domaines des agents complémentaires : présenter les interfaces et transmettre les besoins à l'agent rattaché (voir table de routage).
- L'exécution système, les modifications de fichiers, les tests et les publications relèvent de l'agent rattaché (voir table de routage) ; cette skill n'accorde aucun outil supplémentaire.
- Ne pas confondre préparation d'un protocole, revue statique et résultat d'une exécution réelle dans le logiciel.

## Inputs requis
- Modèle, résolution de texture, workflow PBR du moteur cible, textures ou cartes à produire.
- Périmètre autorisé, version des logiciels et des artefacts, sources accessibles et décisions déjà validées.
- Critères d'acceptation et limites d'action ; marquer les éléments inconnus avant de conclure.

## Sorties attendues
- Dépliage UV et matériaux PBR avec cartes de textures nommées et guide de bake.
- Preuves ou références par constat ; hypothèses, exceptions et vérifications non réalisées séparées.
- Brief des décisions ou actions nécessaires pour l'agent rattaché, sans les annoncer déjà exécutées.

## Workflow recommandé
1. Cadrer les inputs : modèle, résolution de texture, workflow PBR du moteur cible, textures ou cartes à produire ; vérifier les préconditions et autorisations.
2. Définir coutures et densité de texels homogène.
3. Préparer les matériaux PBR (albedo, rugosité, métal, normales).
4. Baker les cartes si nécessaire et contrôler les artefacts.
5. Vérifier le livrable par ce critère : les îlots UV ne se chevauchent pas hors choix documenté et les cartes sont nommées selon la convention.
6. Restituer résultat, hypothèses, risques et prochaines actions ; signaler explicitement les blocages.

## Garde-fous
- Les îlots UV ne se chevauchent pas hors choix documenté et les cartes sont nommées selon la convention.
- Ne pas inventer de mesure, d'accord, de preuve ou de source ; distinguer observé, inféré et non testé.
- Ne pas transmettre d'artefact privé ou de donnée personnelle à un service tiers ; minimiser les données sensibles.
- Privilégier les outils libres maintenus et vérifier les versions applicables sans introduire de dépendance EOL.
- Utiliser uniquement des ressources originales, du Domaine Public ou CC0 ; tracer chaque source externe dans `docs/imageLicencesSources.md` (format `Nomdefichier | licence | url source`).
- Lire la référence dans son contexte : elle éclaire la méthode, elle ne certifie pas ce livrable et n'impose pas de seuil universel.

## Templates copier/coller
### Entrée
```text
Objet : Blender UV Unwrap & PBR Material Setup
Inputs : modèle, résolution de texture, workflow PBR du moteur cible, textures ou cartes à produire
Version / périmètre autorisé :
Résultat demandé : dépliage UV et matériaux PBR avec cartes de textures nommées et guide de bake
Contraintes et inconnues :
```

### Sortie
```text
Résultat : dépliage UV et matériaux PBR avec cartes de textures nommées et guide de bake
| Élément examiné | Preuve / source / version | Conclusion | Limite / action |
|---|---|---|---|
Hypothèses :
Risques :
Prochaines actions :
```

## Checklist QA interne
- [ ] Les inputs et les limites d'autorisation sont identifiés.
- [ ] Les trois analyses sont documentées : définir coutures et densité de texels homogène ; préparer les matériaux PBR (albedo, rugosité, métal, normales) ; baker les cartes si nécessaire et contrôler les artefacts.
- [ ] Le critère d'acceptation est vérifié ou explicitement marqué non vérifié.
- [ ] Aucun résultat d'exécution ou accord humain n'est inventé.

## KPI reliés
- Couverture des éléments requis : éléments documentés / éléments applicables de ce livrable (dénominateur conservé).
- Part des conclusions appuyées par une preuve ou une source datée ; ne pas compter une hypothèse comme preuve.
- Nombre d'écarts au critère suivant restant ouverts : les îlots UV ne se chevauchent pas hors choix documenté et les cartes sont nommées selon la convention.

## Definition of done
- [ ] Dépliage UV et matériaux PBR avec cartes de textures nommées et guide de bake livré dans le périmètre convenu.
- [ ] Les îlots UV ne se chevauchent pas hors choix documenté et les cartes sont nommées selon la convention.
- [ ] Preuves, inconnues, exceptions et actions restantes sont lisibles ; aucune réussite globale en cas de vérification bloquante manquante.

## Exemples d'usage
**Cas nominal** : à partir de modèle, résolution de texture, workflow PBR du moteur cible, textures ou cartes à produire, produire dépliage UV et matériaux PBR avec cartes de textures nommées et guide de bake puis vérifier le critère d'acceptation ci-dessus.

**Cas limite** : une preuve ou autorisation nécessaire manque ; livrer les éléments établis et indiquer précisément ce qui empêche la validation, sans substituer une valeur par défaut.

## Contraintes et références
- Référence officielle : [Blender - Manuel officiel](https://docs.blender.org/manual/en/latest/). Synthèse originale, sans reproduction du texte source ; page non consultée en détail lors de la création, vérifier les versions et l'applicabilité au contexte.
- Création : DEL-20261025-CREA-3D-AGENTS.

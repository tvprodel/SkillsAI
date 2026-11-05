# UI Tone-of-Voice Specification

## Objectif
Définir des règles de ton produit applicables aux états d'interface sans sacrifier la clarté.


## Quand l'utiliser (triggers)
- Demande portant sur « UI Tone-of-Voice Specification » ou sur le livrable : guide de microcopie avec variantes et exemples conformes/non conformes.
- Besoin de vérifier ce résultat : le ton n'introduit ni culpabilisation ni ambiguïté dans une action critique.

## Hors périmètre
- Ne pas remplacer les domaines des agents complémentaires : présenter les interfaces et transmettre les besoins à l'agent rattaché (voir table de routage).
- L'exécution système, les modifications de fichiers, les tests et les publications relèvent de l'agent rattaché (voir table de routage) ; cette skill n'accorde aucun outil supplémentaire.
- Ne pas confondre préparation d'un protocole, revue statique et résultat d'une exécution réelle.

## Inputs requis
- Voix de marque, publics, contextes sensibles et corpus existant.
- Périmètre autorisé, version des artefacts, sources accessibles et décisions déjà validées.
- Critères d'acceptation et limites d'action ; marquer les éléments inconnus avant de conclure.

## Sorties attendues
- Guide de microcopie avec variantes et exemples conformes/non conformes.
- Preuves ou références par constat ; hypothèses, exceptions et vérifications non réalisées séparées.
- Brief des décisions ou actions nécessaires pour l'agent rattaché, sans les annoncer déjà exécutées.

## Workflow recommandé
1. Cadrer les inputs : voix de marque, publics, contextes sensibles et corpus existant ; vérifier les préconditions et autorisations.
2. Distinguer voix constante et ton contextuel.
3. Définir règles par succès/erreur/attente.
4. Fournir contre-exemples et critères de choix.
5. Vérifier le livrable par ce critère : le ton n'introduit ni culpabilisation ni ambiguïté dans une action critique.
6. Restituer résultat, hypothèses, risques et prochaines actions ; signaler explicitement les blocages.

## Garde-fous
- Le ton n'introduit ni culpabilisation ni ambiguïté dans une action critique.
- Ne pas inventer de mesure, d'accord, de preuve ou de source ; distinguer observé, inféré et non testé.
- Ne pas transmettre d'artefact privé ou de donnée personnelle à un service tiers ; minimiser les données sensibles.
- Privilégier les outils libres maintenus et vérifier les versions applicables sans introduire de dépendance EOL.
- Lire la référence dans son contexte : elle éclaire la méthode, elle ne certifie pas ce livrable et n'impose pas de seuil universel.

## Templates copier/coller
### Entrée
```text
Objet : UI Tone-of-Voice Specification
Inputs : Voix de marque, publics, contextes sensibles et corpus existant
Version / périmètre autorisé :
Résultat demandé : Guide de microcopie avec variantes et exemples conformes/non conformes
Contraintes et inconnues :
```

### Sortie
```text
Résultat : Guide de microcopie avec variantes et exemples conformes/non conformes
| Élément examiné | Preuve / source / version | Conclusion | Limite / action |
|---|---|---|---|
Hypothèses :
Risques :
Prochaines actions :
```

## Checklist QA interne
- [ ] Les inputs et les limites d'autorisation sont identifiés.
- [ ] Les trois analyses sont documentées : distinguer voix constante et ton contextuel ; définir règles par succès/erreur/attente ; fournir contre-exemples et critères de choix.
- [ ] Le critère d'acceptation est vérifié ou explicitement marqué non vérifié.
- [ ] Aucun résultat d'exécution ou accord humain n'est inventé.

## KPI reliés
- Couverture des éléments requis : éléments documentés / éléments applicables de ce livrable (dénominateur conservé).
- Part des conclusions appuyées par une preuve ou une source datée ; ne pas compter une hypothèse comme preuve.
- Nombre d'écarts au critère suivant restant ouverts : le ton n'introduit ni culpabilisation ni ambiguïté dans une action critique.

## Definition of done
- [ ] Guide de microcopie avec variantes et exemples conformes/non conformes livré dans le périmètre convenu.
- [ ] Le ton n'introduit ni culpabilisation ni ambiguïté dans une action critique.
- [ ] Preuves, inconnues, exceptions et actions restantes sont lisibles ; aucune réussite globale en cas de vérification bloquante manquante.

## Exemples d'usage
**Cas nominal** : à partir de voix de marque, publics, contextes sensibles et corpus existant, produire guide de microcopie avec variantes et exemples conformes/non conformes puis vérifier le critère d'acceptation ci-dessus.

**Cas limite** : une preuve ou autorisation nécessaire manque ; livrer les éléments établis et indiquer précisément ce qui empêche la validation, sans substituer une valeur par défaut.

## Contraintes et références
- Référence officielle consultée le 2026-10-21 : [GOV.UK - Writing to GOV.UK standards](https://www.gov.uk/guidance/content-design). Synthèse originale, sans reproduction du texte source ; vérifier les versions et l'applicabilité au contexte.
- Migration : DEL-20261021-EXCLUSIVE-SKILLS-MIGRATION.

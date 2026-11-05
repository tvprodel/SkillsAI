# APT and Pacman Recovery Planning

## Objectif
Préparer une récupération cohérente après une transaction de paquets Debian ou Arch interrompue.


## Quand l'utiliser (triggers)
- Demande portant sur « APT and Pacman Recovery Planning » ou sur le livrable : plan de reprise par gestionnaire avec vérifications avant/après.
- Besoin de vérifier ce résultat : le plan n'efface aucun verrou actif et précise les preuves de cohérence requises.

## Hors périmètre
- Ne pas remplacer les domaines des agents complémentaires : présenter les interfaces et transmettre les besoins à l'agent rattaché (voir table de routage).
- L'exécution système, les modifications de fichiers, les tests et les publications relèvent de l'agent rattaché (voir table de routage) ; cette skill n'accorde aucun outil supplémentaire.
- Ne pas confondre préparation d'un protocole, revue statique et résultat d'une exécution réelle.

## Inputs requis
- Distribution et version, journal de transaction, état des verrous et dépôts.
- Périmètre autorisé, version des artefacts, sources accessibles et décisions déjà validées.
- Critères d'acceptation et limites d'action ; marquer les éléments inconnus avant de conclure.

## Sorties attendues
- Plan de reprise par gestionnaire avec vérifications avant/après.
- Preuves ou références par constat ; hypothèses, exceptions et vérifications non réalisées séparées.
- Brief des décisions ou actions nécessaires pour l'agent rattaché, sans les annoncer déjà exécutées.

## Workflow recommandé
1. Cadrer les inputs : distribution et version, journal de transaction, état des verrous et dépôts ; vérifier les préconditions et autorisations.
2. Distinguer verrou actif et transaction interrompue.
3. Contrôler cohérence des dépôts et métadonnées.
4. Préparer des étapes de récupération et leurs points d'arrêt.
5. Vérifier le livrable par ce critère : le plan n'efface aucun verrou actif et précise les preuves de cohérence requises.
6. Restituer résultat, hypothèses, risques et prochaines actions ; signaler explicitement les blocages.

## Garde-fous
- Le plan n'efface aucun verrou actif et précise les preuves de cohérence requises.
- Ne pas inventer de mesure, d'accord, de preuve ou de source ; distinguer observé, inféré et non testé.
- Ne pas transmettre d'artefact privé ou de donnée personnelle à un service tiers ; minimiser les données sensibles.
- Privilégier les outils libres maintenus et vérifier les versions applicables sans introduire de dépendance EOL.
- Lire la référence dans son contexte : elle éclaire la méthode, elle ne certifie pas ce livrable et n'impose pas de seuil universel.

## Templates copier/coller
### Entrée
```text
Objet : APT and Pacman Recovery Planning
Inputs : Distribution et version, journal de transaction, état des verrous et dépôts
Version / périmètre autorisé :
Résultat demandé : Plan de reprise par gestionnaire avec vérifications avant/après
Contraintes et inconnues :
```

### Sortie
```text
Résultat : Plan de reprise par gestionnaire avec vérifications avant/après
| Élément examiné | Preuve / source / version | Conclusion | Limite / action |
|---|---|---|---|
Hypothèses :
Risques :
Prochaines actions :
```

## Checklist QA interne
- [ ] Les inputs et les limites d'autorisation sont identifiés.
- [ ] Les trois analyses sont documentées : distinguer verrou actif et transaction interrompue ; contrôler cohérence des dépôts et métadonnées ; préparer des étapes de récupération et leurs points d'arrêt.
- [ ] Le critère d'acceptation est vérifié ou explicitement marqué non vérifié.
- [ ] Aucun résultat d'exécution ou accord humain n'est inventé.

## KPI reliés
- Couverture des éléments requis : éléments documentés / éléments applicables de ce livrable (dénominateur conservé).
- Part des conclusions appuyées par une preuve ou une source datée ; ne pas compter une hypothèse comme preuve.
- Nombre d'écarts au critère suivant restant ouverts : le plan n'efface aucun verrou actif et précise les preuves de cohérence requises.

## Definition of done
- [ ] Plan de reprise par gestionnaire avec vérifications avant/après livré dans le périmètre convenu.
- [ ] Le plan n'efface aucun verrou actif et précise les preuves de cohérence requises.
- [ ] Preuves, inconnues, exceptions et actions restantes sont lisibles ; aucune réussite globale en cas de vérification bloquante manquante.

## Exemples d'usage
**Cas nominal** : à partir de distribution et version, journal de transaction, état des verrous et dépôts, produire plan de reprise par gestionnaire avec vérifications avant/après puis vérifier le critère d'acceptation ci-dessus.

**Cas limite** : une preuve ou autorisation nécessaire manque ; livrer les éléments établis et indiquer précisément ce qui empêche la validation, sans substituer une valeur par défaut.

## Contraintes et références
- Référence officielle consultée le 2026-10-21 : [Debian Reference - Package management](https://www.debian.org/doc/manuals/debian-reference/ch02.en.html). Synthèse originale, sans reproduction du texte source ; vérifier les versions et l'applicabilité au contexte.
- Migration : DEL-20261021-EXCLUSIVE-SKILLS-MIGRATION.

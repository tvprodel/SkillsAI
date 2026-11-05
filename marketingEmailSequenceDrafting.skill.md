# Marketing Email Sequence Drafting

## Objectif
Rédiger une séquence marketing cohérente sans envoyer de messages ni décider de la base de prospection.


## Quand l'utiliser (triggers)
- Demande portant sur « Marketing Email Sequence Drafting » ou sur le livrable : brouillons ordonnés avec objectif et preuves utilisées.
- Besoin de vérifier ce résultat : les brouillons restent non envoyés et n'impliquent ni profilage sensible ni faux contact antérieur.

## Hors périmètre
- Ne pas remplacer les domaines des agents complémentaires : présenter les interfaces et transmettre les besoins à l'agent rattaché (voir table de routage).
- L'exécution système, les modifications de fichiers, les tests et les publications relèvent de l'agent rattaché (voir table de routage) ; cette skill n'accorde aucun outil supplémentaire.
- Ne pas confondre préparation d'un protocole, revue statique et résultat d'une exécution réelle.

## Inputs requis
- Audience autorisée, offre, ton, objectif et contraintes de contact validées.
- Périmètre autorisé, version des artefacts, sources accessibles et décisions déjà validées.
- Critères d'acceptation et limites d'action ; marquer les éléments inconnus avant de conclure.

## Sorties attendues
- Brouillons ordonnés avec objectif et preuves utilisées.
- Preuves ou références par constat ; hypothèses, exceptions et vérifications non réalisées séparées.
- Brief des décisions ou actions nécessaires pour l'agent rattaché, sans les annoncer déjà exécutées.

## Workflow recommandé
1. Cadrer les inputs : audience autorisée, offre, ton, objectif et contraintes de contact validées ; vérifier les préconditions et autorisations.
2. Définir rôle de chaque message.
3. Écrire objets et corps sans promesse infondée.
4. Prévoir sortie de séquence et validation humaine.
5. Vérifier le livrable par ce critère : les brouillons restent non envoyés et n'impliquent ni profilage sensible ni faux contact antérieur.
6. Restituer résultat, hypothèses, risques et prochaines actions ; signaler explicitement les blocages.

## Garde-fous
- Les brouillons restent non envoyés et n'impliquent ni profilage sensible ni faux contact antérieur.
- Ne pas inventer de mesure, d'accord, de preuve ou de source ; distinguer observé, inféré et non testé.
- Ne pas transmettre d'artefact privé ou de donnée personnelle à un service tiers ; minimiser les données sensibles.
- Privilégier les outils libres maintenus et vérifier les versions applicables sans introduire de dépendance EOL.
- Lire la référence dans son contexte : elle éclaire la méthode, elle ne certifie pas ce livrable et n'impose pas de seuil universel.

## Templates copier/coller
### Entrée
```text
Objet : Marketing Email Sequence Drafting
Inputs : Audience autorisée, offre, ton, objectif et contraintes de contact validées
Version / périmètre autorisé :
Résultat demandé : Brouillons ordonnés avec objectif et preuves utilisées
Contraintes et inconnues :
```

### Sortie
```text
Résultat : Brouillons ordonnés avec objectif et preuves utilisées
| Élément examiné | Preuve / source / version | Conclusion | Limite / action |
|---|---|---|---|
Hypothèses :
Risques :
Prochaines actions :
```

## Checklist QA interne
- [ ] Les inputs et les limites d'autorisation sont identifiés.
- [ ] Les trois analyses sont documentées : définir rôle de chaque message ; écrire objets et corps sans promesse infondée ; prévoir sortie de séquence et validation humaine.
- [ ] Le critère d'acceptation est vérifié ou explicitement marqué non vérifié.
- [ ] Aucun résultat d'exécution ou accord humain n'est inventé.

## KPI reliés
- Couverture des éléments requis : éléments documentés / éléments applicables de ce livrable (dénominateur conservé).
- Part des conclusions appuyées par une preuve ou une source datée ; ne pas compter une hypothèse comme preuve.
- Nombre d'écarts au critère suivant restant ouverts : les brouillons restent non envoyés et n'impliquent ni profilage sensible ni faux contact antérieur.

## Definition of done
- [ ] Brouillons ordonnés avec objectif et preuves utilisées livré dans le périmètre convenu.
- [ ] Les brouillons restent non envoyés et n'impliquent ni profilage sensible ni faux contact antérieur.
- [ ] Preuves, inconnues, exceptions et actions restantes sont lisibles ; aucune réussite globale en cas de vérification bloquante manquante.

## Exemples d'usage
**Cas nominal** : à partir de audience autorisée, offre, ton, objectif et contraintes de contact validées, produire brouillons ordonnés avec objectif et preuves utilisées puis vérifier le critère d'acceptation ci-dessus.

**Cas limite** : une preuve ou autorisation nécessaire manque ; livrer les éléments établis et indiquer précisément ce qui empêche la validation, sans substituer une valeur par défaut.

## Contraintes et références
- Référence officielle consultée le 2026-10-21 : [GOV.UK - Writing to GOV.UK standards](https://www.gov.uk/guidance/content-design). Synthèse originale, sans reproduction du texte source ; vérifier les versions et l'applicabilité au contexte.
- Migration : DEL-20261021-EXCLUSIVE-SKILLS-MIGRATION.

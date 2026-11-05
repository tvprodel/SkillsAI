# Source Authority Comparison

## Objectif
Comparer des sources générales selon autorité, actualité et proximité avec le fait recherché.


## Quand l'utiliser (triggers)
- Demande portant sur « Source Authority Comparison » ou sur le livrable : table de sources classées avec justification.
- Besoin de vérifier ce résultat : une source populaire ne remplace pas une preuve primaire et aucune recherche spécialisée n'est usurpée.

## Hors périmètre
- Usage de secours uniquement après qualification qu'aucun agent spécialisé ne couvre la demande.
- Ne pas traiter de fond juridique, médical, financier, sécurité ou développement spécialisé ; remettre le brief pour routage.
- L'exécution système, les modifications de fichiers, les tests et les publications relèvent de l'agent rattaché (voir table de routage) ; cette skill n'accorde aucun outil supplémentaire.
- Ne pas confondre préparation d'un protocole, revue statique et résultat d'une exécution réelle.

## Inputs requis
- Question générale, sources publiques autorisées, dates et critères.
- Périmètre autorisé, version des artefacts, sources accessibles et décisions déjà validées.
- Critères d'acceptation et limites d'action ; marquer les éléments inconnus avant de conclure.

## Sorties attendues
- Table de sources classées avec justification.
- Preuves ou références par constat ; hypothèses, exceptions et vérifications non réalisées séparées.
- Brief des décisions ou actions nécessaires pour l'agent rattaché, sans les annoncer déjà exécutées.

## Workflow recommandé
1. Cadrer les inputs : question générale, sources publiques autorisées, dates et critères ; vérifier les préconditions et autorisations.
2. Identifier source primaire et reprises.
3. Comparer dates, responsabilité et portée.
4. Noter conflits et informations invérifiables.
5. Vérifier le livrable par ce critère : une source populaire ne remplace pas une preuve primaire et aucune recherche spécialisée n'est usurpée.
6. Restituer résultat, hypothèses, risques et prochaines actions ; signaler explicitement les blocages.

## Garde-fous
- Une source populaire ne remplace pas une preuve primaire et aucune recherche spécialisée n'est usurpée.
- Ne pas inventer de mesure, d'accord, de preuve ou de source ; distinguer observé, inféré et non testé.
- Ne pas transmettre d'artefact privé ou de donnée personnelle à un service tiers ; minimiser les données sensibles.
- Privilégier les outils libres maintenus et vérifier les versions applicables sans introduire de dépendance EOL.
- Lire la référence dans son contexte : elle éclaire la méthode, elle ne certifie pas ce livrable et n'impose pas de seuil universel.

## Templates copier/coller
### Entrée
```text
Objet : Source Authority Comparison
Inputs : Question générale, sources publiques autorisées, dates et critères
Version / périmètre autorisé :
Résultat demandé : Table de sources classées avec justification
Contraintes et inconnues :
```

### Sortie
```text
Résultat : Table de sources classées avec justification
| Élément examiné | Preuve / source / version | Conclusion | Limite / action |
|---|---|---|---|
Hypothèses :
Risques :
Prochaines actions :
```

## Checklist QA interne
- [ ] Les inputs et les limites d'autorisation sont identifiés.
- [ ] Les trois analyses sont documentées : identifier source primaire et reprises ; comparer dates, responsabilité et portée ; noter conflits et informations invérifiables.
- [ ] Le critère d'acceptation est vérifié ou explicitement marqué non vérifié.
- [ ] Aucun résultat d'exécution ou accord humain n'est inventé.

## KPI reliés
- Couverture des éléments requis : éléments documentés / éléments applicables de ce livrable (dénominateur conservé).
- Part des conclusions appuyées par une preuve ou une source datée ; ne pas compter une hypothèse comme preuve.
- Nombre d'écarts au critère suivant restant ouverts : une source populaire ne remplace pas une preuve primaire et aucune recherche spécialisée n'est usurpée.

## Definition of done
- [ ] Table de sources classées avec justification livré dans le périmètre convenu.
- [ ] Une source populaire ne remplace pas une preuve primaire et aucune recherche spécialisée n'est usurpée.
- [ ] Preuves, inconnues, exceptions et actions restantes sont lisibles ; aucune réussite globale en cas de vérification bloquante manquante.

## Exemples d'usage
**Cas nominal** : à partir de question générale, sources publiques autorisées, dates et critères, produire table de sources classées avec justification puis vérifier le critère d'acceptation ci-dessus.

**Cas limite** : une preuve ou autorisation nécessaire manque ; livrer les éléments établis et indiquer précisément ce qui empêche la validation, sans substituer une valeur par défaut.

## Contraintes et références
- Référence officielle consultée le 2026-10-21 : [W3C PROV Overview](https://www.w3.org/TR/prov-overview/). Synthèse originale, sans reproduction du texte source ; vérifier les versions et l'applicabilité au contexte.
- Migration : DEL-20261021-EXCLUSIVE-SKILLS-MIGRATION.

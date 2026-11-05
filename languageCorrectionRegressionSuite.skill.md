# Language Correction Regression Suite

## Objectif
Empêcher qu'une nouvelle révision réintroduise des fautes déjà corrigées.


## Quand l'utiliser (triggers)
- Demande portant sur « Language Correction Regression Suite » ou sur le livrable : jeu de cas phrase/règle/attendu avec rapport de régression.
- Besoin de vérifier ce résultat : chaque échec renvoie à une règle linguistique et une occurrence vérifiable.

## Hors périmètre
- Ne pas remplacer les domaines des agents complémentaires : présenter les interfaces et transmettre les besoins à l'agent rattaché (voir table de routage).
- L'exécution système, les modifications de fichiers, les tests et les publications relèvent de l'agent rattaché (voir table de routage) ; cette skill n'accorde aucun outil supplémentaire.
- Ne pas confondre préparation d'un protocole, revue statique et résultat d'une exécution réelle.

## Inputs requis
- Texte de référence, corrections validées, version nouvelle.
- Périmètre autorisé, version des artefacts, sources accessibles et décisions déjà validées.
- Critères d'acceptation et limites d'action ; marquer les éléments inconnus avant de conclure.

## Sorties attendues
- Jeu de cas phrase/règle/attendu avec rapport de régression.
- Preuves ou références par constat ; hypothèses, exceptions et vérifications non réalisées séparées.
- Brief des décisions ou actions nécessaires pour l'agent rattaché, sans les annoncer déjà exécutées.

## Workflow recommandé
1. Cadrer les inputs : texte de référence, corrections validées, version nouvelle ; vérifier les préconditions et autorisations.
2. Créer des cas minimaux pour les fautes récurrentes.
3. Comparer les occurrences nouvelles aux corrections validées.
4. Isoler faux positifs et exceptions linguistiques.
5. Vérifier le livrable par ce critère : chaque échec renvoie à une règle linguistique et une occurrence vérifiable.
6. Restituer résultat, hypothèses, risques et prochaines actions ; signaler explicitement les blocages.

## Garde-fous
- Chaque échec renvoie à une règle linguistique et une occurrence vérifiable.
- Ne pas inventer de mesure, d'accord, de preuve ou de source ; distinguer observé, inféré et non testé.
- Ne pas transmettre d'artefact privé ou de donnée personnelle à un service tiers ; minimiser les données sensibles.
- Privilégier les outils libres maintenus et vérifier les versions applicables sans introduire de dépendance EOL.
- Lire la référence dans son contexte : elle éclaire la méthode, elle ne certifie pas ce livrable et n'impose pas de seuil universel.

## Templates copier/coller
### Entrée
```text
Objet : Language Correction Regression Suite
Inputs : Texte de référence, corrections validées, version nouvelle
Version / périmètre autorisé :
Résultat demandé : Jeu de cas phrase/règle/attendu avec rapport de régression
Contraintes et inconnues :
```

### Sortie
```text
Résultat : Jeu de cas phrase/règle/attendu avec rapport de régression
| Élément examiné | Preuve / source / version | Conclusion | Limite / action |
|---|---|---|---|
Hypothèses :
Risques :
Prochaines actions :
```

## Checklist QA interne
- [ ] Les inputs et les limites d'autorisation sont identifiés.
- [ ] Les trois analyses sont documentées : créer des cas minimaux pour les fautes récurrentes ; comparer les occurrences nouvelles aux corrections validées ; isoler faux positifs et exceptions linguistiques.
- [ ] Le critère d'acceptation est vérifié ou explicitement marqué non vérifié.
- [ ] Aucun résultat d'exécution ou accord humain n'est inventé.

## KPI reliés
- Couverture des éléments requis : éléments documentés / éléments applicables de ce livrable (dénominateur conservé).
- Part des conclusions appuyées par une preuve ou une source datée ; ne pas compter une hypothèse comme preuve.
- Nombre d'écarts au critère suivant restant ouverts : chaque échec renvoie à une règle linguistique et une occurrence vérifiable.

## Definition of done
- [ ] Jeu de cas phrase/règle/attendu avec rapport de régression livré dans le périmètre convenu.
- [ ] Chaque échec renvoie à une règle linguistique et une occurrence vérifiable.
- [ ] Preuves, inconnues, exceptions et actions restantes sont lisibles ; aucune réussite globale en cas de vérification bloquante manquante.

## Exemples d'usage
**Cas nominal** : à partir de texte de référence, corrections validées, version nouvelle, produire jeu de cas phrase/règle/attendu avec rapport de régression puis vérifier le critère d'acceptation ci-dessus.

**Cas limite** : une preuve ou autorisation nécessaire manque ; livrer les éléments établis et indiquer précisément ce qui empêche la validation, sans substituer une valeur par défaut.

## Contraintes et références
- Référence officielle consultée le 2026-10-21 : [Python unittest](https://docs.python.org/3/library/unittest.html). Synthèse originale, sans reproduction du texte source ; vérifier les versions et l'applicabilité au contexte.
- Migration : DEL-20261021-EXCLUSIVE-SKILLS-MIGRATION.

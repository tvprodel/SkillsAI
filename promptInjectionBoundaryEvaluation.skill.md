# Prompt Injection Boundary Evaluation

## Objectif
Évaluer défensivement les frontières de confiance d'un agent IA autorisé.


## Quand l'utiliser (triggers)
- Demande portant sur « Prompt Injection Boundary Evaluation » ou sur le livrable : matrice scénario/frontière/attendu/observé/preuve.
- Besoin de vérifier ce résultat : aucun test ne vise un tiers ni ne nécessite un secret réel ou un effet destructeur.

## Hors périmètre
- Ne pas remplacer les domaines des agents complémentaires : présenter les interfaces et transmettre les besoins à l'agent rattaché (voir table de routage).
- L'exécution système, les modifications de fichiers, les tests et les publications relèvent de l'agent rattaché (voir table de routage) ; cette skill n'accorde aucun outil supplémentaire.
- Ne pas confondre préparation d'un protocole, revue statique et résultat d'une exécution réelle.

## Inputs requis
- Agent cible autorisé, outils, données de test synthétiques et règles attendues.
- Périmètre autorisé, version des artefacts, sources accessibles et décisions déjà validées.
- Critères d'acceptation et limites d'action ; marquer les éléments inconnus avant de conclure.

## Sorties attendues
- Matrice scénario/frontière/attendu/observé/preuve.
- Preuves ou références par constat ; hypothèses, exceptions et vérifications non réalisées séparées.
- Brief des décisions ou actions nécessaires pour l'agent rattaché, sans les annoncer déjà exécutées.

## Workflow recommandé
1. Cadrer les inputs : agent cible autorisé, outils, données de test synthétiques et règles attendues ; vérifier les préconditions et autorisations.
2. Définir entrées non fiables et actions interdites.
3. Construire scénarios contrôlés sans accès réel sensible.
4. Comparer refus, escalade et effets observés.
5. Vérifier le livrable par ce critère : aucun test ne vise un tiers ni ne nécessite un secret réel ou un effet destructeur.
6. Restituer résultat, hypothèses, risques et prochaines actions ; signaler explicitement les blocages.

## Garde-fous
- Aucun test ne vise un tiers ni ne nécessite un secret réel ou un effet destructeur.
- Ne pas inventer de mesure, d'accord, de preuve ou de source ; distinguer observé, inféré et non testé.
- Ne pas transmettre d'artefact privé ou de donnée personnelle à un service tiers ; minimiser les données sensibles.
- Privilégier les outils libres maintenus et vérifier les versions applicables sans introduire de dépendance EOL.
- Lire la référence dans son contexte : elle éclaire la méthode, elle ne certifie pas ce livrable et n'impose pas de seuil universel.

## Templates copier/coller
### Entrée
```text
Objet : Prompt Injection Boundary Evaluation
Inputs : Agent cible autorisé, outils, données de test synthétiques et règles attendues
Version / périmètre autorisé :
Résultat demandé : Matrice scénario/frontière/attendu/observé/preuve
Contraintes et inconnues :
```

### Sortie
```text
Résultat : Matrice scénario/frontière/attendu/observé/preuve
| Élément examiné | Preuve / source / version | Conclusion | Limite / action |
|---|---|---|---|
Hypothèses :
Risques :
Prochaines actions :
```

## Checklist QA interne
- [ ] Les inputs et les limites d'autorisation sont identifiés.
- [ ] Les trois analyses sont documentées : définir entrées non fiables et actions interdites ; construire scénarios contrôlés sans accès réel sensible ; comparer refus, escalade et effets observés.
- [ ] Le critère d'acceptation est vérifié ou explicitement marqué non vérifié.
- [ ] Aucun résultat d'exécution ou accord humain n'est inventé.

## KPI reliés
- Couverture des éléments requis : éléments documentés / éléments applicables de ce livrable (dénominateur conservé).
- Part des conclusions appuyées par une preuve ou une source datée ; ne pas compter une hypothèse comme preuve.
- Nombre d'écarts au critère suivant restant ouverts : aucun test ne vise un tiers ni ne nécessite un secret réel ou un effet destructeur.

## Definition of done
- [ ] Matrice scénario/frontière/attendu/observé/preuve livré dans le périmètre convenu.
- [ ] Aucun test ne vise un tiers ni ne nécessite un secret réel ou un effet destructeur.
- [ ] Preuves, inconnues, exceptions et actions restantes sont lisibles ; aucune réussite globale en cas de vérification bloquante manquante.

## Exemples d'usage
**Cas nominal** : à partir de agent cible autorisé, outils, données de test synthétiques et règles attendues, produire matrice scénario/frontière/attendu/observé/preuve puis vérifier le critère d'acceptation ci-dessus.

**Cas limite** : une preuve ou autorisation nécessaire manque ; livrer les éléments établis et indiquer précisément ce qui empêche la validation, sans substituer une valeur par défaut.

## Contraintes et références
- Référence officielle consultée le 2026-10-21 : [NIST AI Risk Management Framework](https://www.nist.gov/itl/ai-risk-management-framework). Synthèse originale, sans reproduction du texte source ; vérifier les versions et l'applicabilité au contexte.
- Migration : DEL-20261021-EXCLUSIVE-SKILLS-MIGRATION.

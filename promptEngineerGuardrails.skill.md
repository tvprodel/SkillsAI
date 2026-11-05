# Prompt Engineer & Guardrails

## Objectif
Ameliorer robustesse, qualite, cout et latence des prompts agents.

## Quand l'utiliser (triggers)
- Reponses hors perimetre frequentes.
- Cout tokens en derive.
- Variabilite de format de sortie.

## Hors périmètre
- Refonte architecture complete.
- Probleme purement metier sans lien prompt.

## Inputs requis
- Prompt actuel.
- Exemples d'echecs/reussites.
- Contraintes cout/latence/qualite.

## Sorties attendues
- Prompt revise.
- Guardrails de sortie (structure, refus, limites).
- Protocole de test adversarial.
- Comparatif avant/apres.

## Workflow recommandé
1. Etablir baseline.
2. Reviser instructions et format.
3. Tester sur jeux de cas normaux + adversariaux.
4. Mesurer et iterrer.

## Garde-fous
- Ne pas sacrifier fiabilite pour cout minimum.
- Garder un format de sortie strict.
- Integrer politique de refus explicite.

## Template d'entrée (copier/coller)
```text
[Prompt actuel]
...

[Problemes observes]
- ...

[Contraintes]
- Cout max : ...
- Latence max : ...
```

## Template de sortie (copier/coller)
```text
[Prompt revise]
...

[Guardrails]
- Format de sortie : ...
- Conditions de refus : ...

[Mesures]
- Qualite avant/apres : ...
- Cout avant/apres : ...
```

## Checklist QA interne
- Cas limites couverts.
- Refus corrects verifies.
- Format de sortie stable.

## KPI reliés
- Taux hors perimetre.
- Cout token/requete.
- Taux de relance.

## Definition of done
- Gain mesurable qualite/cout/latence.
- Diminution des echecs critiques.

## Exemples d'usage

### Exemple 1 : [Titre du cas d'usage]
**Contexte** : [Description de la situation]
**Action** : [Ce qui a été fait]
**Résultat** : [Résultat obtenu]
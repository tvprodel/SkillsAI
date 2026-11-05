# I Have ADHD (Output Mode Neurodivergent)

## Distinction avec les autres skills
Cette skill n'est **pas** une méthode de clarification (cf. [Grill Me](./grillMe.skill.md)) ni une critique (cf. [Roast My Idea](./roastMyIdea.skill.md)). C'est un **mode de formatage de réponse** : les mêmes idées, mais restructurées pour une cognition TDAH — action d'abord, étapes claires, dopamine visible.

## Origine
Source : [ayghri/i-have-adhd](https://github.com/ayghri/i-have-adhd) (Matt Pocock, DevTools, 2026).

## Objectif
Reformater les réponses pour un lecteur TDAH : action immédiate en premier, étapes numérotées et bornées, estimations de temps précises, progrès visibles, pas de tangentes. Reste actif **toute la session** jusqu'à « stop adhd mode » explicite.

## Neurosciences derrière (les 5 faits)
1. **Mémoire de travail courte** — Tout ce qui n'est pas visible sur l'écran disparaît.
2. **Écart comprendre ≠ faire** — La friction entre « j'ai compris » et « c'est fait » est où s'effondre le travail.
3. **Démarrer est le plus dur** — La première action doit être : évidente, petite, faisable maintenant.
4. **Estimations floues ne passent pas** — « Ça prend un peu » et « quelques heures » se ressentent identiquement. Il faut du concret.
5. **Dopamine scarce** — Progrès visibles = dopamine. Victoires cachées = nulles.

## Quand l'utiliser (triggers)
- « /i-have-adhd », « mode ADHD », « adhd mode ».
- « ultra clair, étape par étape », « donne-moi l'action d'abord ».
- « rends ça actionnable », « structure-moi la réponse ».

## Hors périmètre
- Ne remplace pas une revue technique / audit formel (renvoyer vers l'agent spécialisé).
- N'est pas une excuse pour perte de précision technique : le contenu reste intact, juste reformaté.
- Doit rester activé même sur changement de sujet — user doit dire « stop adhd mode » explicitement.

## Inputs requis
- N'importe quelle réponse, question ou livrable à reformater.
- Contexte : tâche en cours, dépendances, état actuel (utile pour rappel d'état à chaque tour).

## Sorties attendues
- **Action immédiate** en première ligne (commande, chemin, snippet).
- Étapes numérotées, une par action bornée (pas de « et ensuite »).
- Prochaine action concrète nommée et bornée en ~2 min.
- Estimations de temps précises (« 15 min si Y couvre ça ; 2h sinon »).
- État rappelé explicitement chaque tour (« Étape 3/5 : X fait. Prochaine : Y »).
- Progrès visibles énoncés en concret (« Login fonctionne maintenant via magic links »).

## Workflow recommandé
1. **Commencer par l'action** : si c'est une commande, un chemin, un snippet → en premier.
2. **Numéroter si multi-étape** : une étape = une action bornée, pas de liste nested.
3. **Donner un temps concret** : « 15 min si tests couvrent ça ; 2h après-midi sinon ».
4. **Rappeler l'état** : « On est Étape 3/5 : schéma à jour. Prochaine : remplir colonne ».
5. **Une seule tangente** : si autre question surgit, finir d'abord la courante, proposer la 2e après.
6. **Terminer par une action** : 1 truc faisable <2 min avant clôture (« run test, paste error »).
7. **Rendre les wins visibles** : pas « j'ai changé l'auth » → « Login fonctionne avec magic links ».

## Garde-fous
- **Jamais de liste floue** : chaque item doit être exécutable.
- **Action d'abord** : contexte/histoire vient **après**, jamais avant.
- **Une seule tangente à la fois** : si plusieurs pop up, les proposer en séquence.
- **Estimations toujours** : vague (« un peu de travail ») = mort du projet.
- **État rappelé sans demande** : le lecteur ne retient rien entre messages.
- **Pas de bavardage** : l'objectif est l'exécution, pas l'explication riche.

## Template d'entrée (copier/coller)
```text
/i-have-adhd

[Question / Tâche à reformater]
- Contexte (si long) : ...
```

## Template de sortie (copier/coller)
```text
[Action immédiate]
> Exécute X, puis Y.

[Étapes (si besoin)]
1. Ouvre ...
2. Remplace ...
3. Lance ...

[Estimations]
~ 15 min si Z couvre; 2h après-midi sinon

[État]
Étape 2/5 : SQL migré. Prochaine : backfill colonne.

[Prochaine action]
> Lance test, colle error line.
```

## Checklist QA interne
- Première ligne = action exécutable (pas intro/contexte).
- Étapes numérotées, bornées, une per étape (pas de « et ensuite »).
- Estimations précises (unités concrètes, pas flou).
- État rappelé (« Étape N/M : X. Prochaine : Y »).
- Progrès énoncés concrètement (« Login fonctionne » pas « j'ai modifié »).
- Une tangente max à la fois ; autres proposées après.
- Clôture : 1 action <2 min nommée.

## KPI reliés
- Taux d'actions lancées après passage ADHD mode vs mode standard.
- Temps moyen pour exécution première étape (doit ↓).
- Satisfaction utilisateur TDAH vs neurotypique.

## Definition of done
- Réponse est exploitable immédiatement (action d'abord).
- Utilisateur sait ce qu'il fait ensuite sans relire.
- Chaque étape est faisable en <10 min.
- Estimations et état explicites, pas implicites.

## Exemples d'usage

### Exemple 1 : Setup Django sans ADHD mode
**Input** : « Je veux bootstrapper un projet Django avec auth et API REST, je sais pas par où commencer. »
**Output standard** : « Oui, Django est un framework complet. Avant de coder, il faut penser à plusieurs éléments : structure, dépendances... »

**Output ADHD mode** :
```
> pip install django djangorestframework django-cors-headers
> django-admin startproject myproject . && cd myproject

1. python manage.py startapp accounts
2. Ajoute 'rest_framework' + 'corsheaders' à INSTALLED_APPS
3. Lance python manage.py runserver sur http://127.0.0.1:8000/

~ 10 min pour ce bloc ; 30 min pour le JWT config

Prochaine : crée un modèle User, ajoute une API list simple.
```

### Exemple 2 : Reformater une réponse long text
**Input** : Réponse technique standard de 500+ mots sur migrations SQL.
**Output ADHD mode** : Même contenu, mais : action (migration command) en premier, étapes claires, estimations précises, rappel d'état à chaque turn.

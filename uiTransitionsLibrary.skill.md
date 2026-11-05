# UI Transitions Library (Transitions.dev)

## Objectif
Concevoir et intégrer des transitions/micro-interactions UI web (CSS et Vue) performantes et prêtes à l'emploi, en s'appuyant sur la collection de référence [Transitions.dev](https://transitions.dev/) ("UI transitions for AI agents" — collection de transitions essentielles copier/coller pour applications web).

## Contraintes et références
- [Transitions.dev](https://transitions.dev/) — collection de transitions/micro-interactions CSS pensée pour être copiée-collée ou utilisée directement par un agent de code.
- [Animate.css](https://animate.style/) — bibliothèque d'animations CSS prêtes à l'emploi, cross-browser (`animate__animated` + classe d'animation, ex. `animate__bounce`), personnalisable via CSS Custom Properties (`--animate-duration`, `--animate-delay`). Installation : `npm install animate.css` ou CDN (`https://cdnjs.cloudflare.com/ajax/libs/animate.css/4.1.1/animate.min.css`). Utile pour des animations d'emphase/attention (home pages, sliders, hints) en complément des patterns Transitions.dev plus taillés pour les micro-interactions d'état.
- Toujours vérifier la version la plus récente sur le site avant intégration (bibliothèques évolutives).

## Quand l'utiliser (triggers)
- « transition », « micro-interaction », « animation d'interface », « effet de survol », « transition d'entrée/sortie », « UI polish », « Transitions.dev », « Animate.css », « CSS transition copy-paste ».
- Ajout de transitions d'état (hover, focus, apparition/disparition, changement de route) sur un composant Vue.js.
- Recherche d'une transition performante (compositing GPU) plutôt qu'une animation coûteuse en repaint.

## Hors périmètre
- Animations complexes de scénarisation/storytelling (timelines avancées) → GSAP dédié, hors périmètre de cette skill (rester sur les patterns Transitions.dev + CSS/Vue Transition).
- Logique métier des composants Vue (state management, props) → compétence de base de l'agent front-end / l'agent de développement TypeScript/JavaScript.
- Performance runtime globale d'un moteur de jeu → Game Engine Performance & Profiling.

## Inputs requis
- Élément(s) UI concerné(s) (bouton, carte, modal, liste, route/page).
- Déclencheur de la transition (hover, focus, montage/démontage, changement de route, changement d'état).
- Contraintes de performance (cible mobile, accessibilité `prefers-reduced-motion`).

## Sorties attendues
- Snippet CSS ou Vue (`<Transition>`, classes `enter-active`/`leave-active`) prêt à intégrer, basé sur un pattern Transitions.dev adapté au besoin.
- Explication du choix de propriété animée (privilégier `transform`/`opacity` qui compositent, éviter `filter`/`mask-position`/propriétés qui forcent un repaint).
- Fallback `prefers-reduced-motion` si pertinent.

## Workflow recommandé
1. Identifier le déclencheur et l'effet recherché (fade, slide, scale, curtain, stagger, etc.).
2. Consulter [Transitions.dev](https://transitions.dev/) pour le pattern le plus proche du besoin.
3. Adapter le snippet au contexte du projet (variables CSS existantes, classes Tailwind/SCSS, ou `<Transition>` Vue 3).
4. Vérifier que la propriété animée composite (transform, opacity) plutôt que de forcer un repaint (mask-position, filter, top/left) — séparer la cause si un lag est constaté (repaint répété vs relance du filtre à chaque frame).
5. Ajouter un fallback `@media (prefers-reduced-motion: reduce)` pour l'accessibilité.
6. Tester sur mobile/desktop et vérifier l'absence de jank (DevTools > Performance).

## Garde-fous
- Toujours préférer les propriétés qui compositent (`transform`, `opacity`) aux propriétés qui repeignent (`mask-position`, `filter`, `width`/`height`, `top`/`left`).
- Isoler la cause d'un lag avant d'ajuster un paramètre (ex. rayon de flou) : distinguer un recalcul par frame d'un repaint forcé par la chaîne de rendu (masque/filtre).
- Respecter `prefers-reduced-motion` pour l'accessibilité.
- Ne pas dupliquer une transition déjà standardisée dans le design system du projet ; centraliser les patterns réutilisés.

## Template d'entrée (copier/coller)
```text
[Élément UI]
- Composant : ...
- Déclencheur : hover / focus / montage-démontage / changement de route / changement d'état

[Effet recherché]
- Type : fade / slide / scale / curtain / stagger / autre
- Contrainte perf : mobile ciblé ? reduced-motion requis ?
```

## Template de sortie (copier/coller)
```text
[Snippet]
- Code CSS/Vue : ...
- Propriété(s) animée(s) : transform/opacity (compositing) — justification

[Accessibilité]
- Fallback prefers-reduced-motion : oui/non

[Vérification perf]
- Repaint évité : oui/non
- Testé sur : desktop/mobile
```

## Checklist QA interne
- Propriété animée compositée (transform/opacity), pas de repaint inutile.
- Fallback `prefers-reduced-motion` présent si transition non essentielle.
- Snippet testé visuellement sur le composant cible.
- Cohérence avec le design system existant (durées, easings).

## KPI reliés
- Absence de jank perçu (fluidité 60fps).
- Nombre de transitions standardisées réutilisées vs créées ad hoc.
- Taux de conformité `prefers-reduced-motion`.

## Definition of done
- Transition intégrée et fonctionnelle sur le composant cible.
- Propriété animée conforme aux garde-fous (compositing).
- Fallback accessibilité présent si nécessaire.

## Exemples d'usage

### Exemple 1 : Transition d'apparition d'une carte au montage
**Contexte** : Une liste de cartes Vue doit apparaître avec un léger fade + slide au montage, sans jank sur mobile.
**Action** : Pattern Transitions.dev adapté en `<Transition>` Vue 3 animant `opacity` et `transform: translateY(...)`, avec fallback `prefers-reduced-motion` désactivant le slide.
**Résultat** : Apparition fluide à 60fps sur mobile, dégradée en fade simple pour les utilisateurs sensibles au mouvement.

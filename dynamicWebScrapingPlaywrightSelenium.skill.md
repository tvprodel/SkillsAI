# Dynamic Web Scraping (Playwright/Selenium)

## Objectif
Extraire des données depuis des sites dont le contenu est généré ou chargé dynamiquement via JavaScript (SPA, infinite scroll, contenu post-XHR), en pilotant un navigateur headless (Playwright ou Selenium).

## Quand l'utiliser (triggers)
- « site JS-rendered », « Playwright », « Selenium », « scraper une SPA », « contenu chargé en JavaScript ».
- Données absentes du HTML brut (vue source) mais visibles après exécution du JS.
- Interactions nécessaires (clics, scroll infini, formulaires, authentification par session).

## Hors périmètre
- Sites purement statiques (HTML brut suffisant) → skill Static Web Scraping (BeautifulSoup/lxml/Requests).
- Écriture/exécution du code de production (scripts Playwright/Selenium) → **l'agent de développement back-end**.
- Stockage/orchestration des données extraites → **l'agent d'ingénierie des données**.

## Inputs requis
- URL(s) cible(s) et description du comportement dynamique (scroll, clics, attente réseau).
- Volumétrie et fréquence de collecte (impact direct sur coût/latence navigateur headless).
- Besoin d'authentification (session, cookies, login).
- Contraintes de détection anti-bot connues (captcha, fingerprinting).

## Sorties attendues
- Choix outil justifié (Playwright vs Selenium) selon performance, maintenabilité, écosystème.
- Stratégie d'attente (wait strategies : sélecteur visible, réseau idle, timeout).
- Stratégie de gestion des ressources (headless, parallélisation, pool de navigateurs).
- Points de vigilance (consommation mémoire/CPU, coût infra, fragilité UI).

## Workflow recommandé
1. Confirmer le besoin de rendu JS (inspecter le DOM après chargement vs HTML brut).
2. Choisir l'outil : Playwright (recommandé par défaut : plus rapide, API moderne, multi-navigateurs) ou Selenium (si écosystème existant/legacy).
3. Définir la stratégie d'attente explicite (éviter les `sleep()` fixes, préférer `wait_for_selector`/réseau idle).
4. Spécifier la gestion des interactions (scroll infini, pagination JS, formulaires).
5. Définir la stratégie de parallélisation raisonnable et de gestion des ressources (fermeture des contextes navigateur).
6. Transmettre la spécification technique à **l'agent de développement back-end** pour implémentation.

## Garde-fous
- Respecter `robots.txt`/CGU (voir skill Scraping Ethics & Legal Awareness) même si le site est dynamique.
- Limiter la parallélisation pour éviter la surcharge du site cible et le blocage IP (voir skill Anti-Bot Evasion).
- Ne jamais contourner un CAPTCHA/mécanisme de sécurité explicite du site cible sans validation légale préalable → **l'agent de conseil juridique**.
- Fermer proprement les contextes/navigateurs headless pour éviter les fuites mémoire en production.

## Template d'entrée (copier/coller)
```text
[Site cible]
- URL(s) : ...
- Comportement dynamique : scroll infini / clics / attente réseau / formulaire

[Volumétrie]
- Nombre de pages/items : ...
- Fréquence : one-shot / périodique

[Contraintes]
- Authentification requise : oui/non
- CAPTCHA détecté : oui/non
```

## Template de sortie (copier/coller)
```text
[Outil recommandé]
- Playwright ou Selenium : ... (justification)

[Stratégie d'attente]
- Sélecteurs/conditions réseau : ...

[Interactions]
- Scroll/clics/formulaire : ...

[Ressources]
- Parallélisation max : ...
- Gestion mémoire : ...
```

## Checklist QA interne
- Besoin de rendu JS confirmé (pas de sur-ingénierie si HTML statique suffit).
- Stratégie d'attente explicite (pas de sleep fixe).
- Gestion des ressources navigateur définie (fermeture contextes).
- robots.txt/CGU vérifiés.
- Frontière de délégation vers l'agent de développement back-end explicite.

## KPI reliés
- Temps moyen d'extraction par page (latence navigateur headless).
- Taux d'échec (timeout, élément non trouvé).
- Consommation mémoire/CPU par instance navigateur.

## Definition of done
- Choix d'outil justifié et documenté.
- Stratégie d'attente et d'interaction spécifiée.
- Spécification technique transmise à l'agent de développement back-end.

## Exemples d'usage

### Exemple 1 : Extraction d'une SPA avec scroll infini
**Contexte** : Récupérer des annonces chargées progressivement au scroll sur une SPA React.
**Action** : Playwright choisi, stratégie de scroll + attente réseau idle jusqu'à stabilisation du nombre d'éléments DOM.
**Résultat** : Spécification transmise à l'agent de développement back-end avec script Playwright type.

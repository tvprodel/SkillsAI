# Static Web Scraping (BeautifulSoup/lxml/Requests)

## Objectif
Extraire des données depuis des pages HTML statiques (rendues côté serveur) via des bibliothèques Python légères (Requests, BeautifulSoup, lxml, httpx), sans moteur de rendu JavaScript.

## Quand l'utiliser (triggers)
- « scraper un site statique », « parser du HTML », « BeautifulSoup », « lxml », « requests + scraping ».
- Site dont le contenu cible est présent dans le HTML brut (vue source = données visibles).
- Volumétrie modérée, pas de rendu JS nécessaire pour accéder aux données.

## Hors périmètre
- Sites nécessitant l'exécution de JavaScript pour afficher les données cibles → skill Dynamic Web Scraping (Playwright/Selenium).
- Écriture/exécution du code de production → **l'agent de développement back-end**.
- Stockage/orchestration des données extraites → **l'agent d'ingénierie des données**.

## Inputs requis
- URL(s) cible(s) et structure HTML (sélecteurs CSS/XPath candidats).
- Fréquence de collecte souhaitée (one-shot, périodique).
- Champs de données à extraire (schéma cible).
- Contraintes connues (robots.txt, CGU, authentification).

## Sorties attendues
- Stratégie de sélection (CSS selectors / XPath) documentée.
- Recommandation de bibliothèques (requests/httpx + BeautifulSoup ou lxml) et justification.
- Schéma de données extrait (champs, types).
- Points de vigilance techniques (pagination, encodage, structure instable).

## Workflow recommandé
1. Vérifier que le site est statique (vue source contient les données ; sinon rediriger vers scraping dynamique).
2. Identifier les sélecteurs CSS/XPath stables (éviter les classes générées dynamiquement).
3. Définir la stratégie de pagination/crawl (liens suivants, paramètres d'URL).
4. Spécifier la gestion des erreurs HTTP (retries, backoff, codes 403/429).
5. Définir le format de sortie structuré (voir skill Web Data Extraction & Structuring).
6. Transmettre la spécification technique à **l'agent de développement back-end** pour implémentation.

## Garde-fous
- Vérifier `robots.txt` et les CGU avant de définir la stratégie (voir skill Scraping Ethics & Legal Awareness).
- Respecter un rate limiting raisonnable (voir skill Anti-Bot Evasion & Scraping Best Practices).
- Ne jamais extraire de données personnelles sans validation préalable **l'agent de conformité RGPD**.
- Documenter la fragilité des sélecteurs (risque de rupture si le site change de structure).

## Template d'entrée (copier/coller)
```text
[Site cible]
- URL(s) : ...
- Contenu HTML statique confirmé : oui/non

[Données à extraire]
- Champs : ...
- Format cible : CSV/JSON/BDD

[Contraintes]
- robots.txt vérifié : oui/non
- Authentification requise : oui/non
```

## Template de sortie (copier/coller)
```text
[Stratégie de sélection]
- Sélecteurs CSS/XPath : ...
- Bibliothèque recommandée : ...

[Pagination/Crawl]
- Stratégie : ...

[Gestion erreurs]
- Retries/backoff : ...

[Schéma de données]
- Champs : type
```

## Checklist QA interne
- Sélecteurs testés sur un échantillon de pages représentatif.
- Gestion des erreurs HTTP définie.
- robots.txt et CGU vérifiés.
- Schéma de données validé avec le demandeur.
- Frontière de délégation vers l'agent de développement back-end explicite.

## KPI reliés
- Taux de succès d'extraction (% pages correctement parsées).
- Taux d'erreur HTTP (403/429/5xx).
- Stabilité des sélecteurs dans le temps (fréquence de rupture).

## Definition of done
- Stratégie de sélection documentée et validée.
- Spécification technique transmise à l'agent de développement back-end.
- Garde-fous éthiques/légaux vérifiés.

## Exemples d'usage

### Exemple 1 : Extraction de fiches produits e-commerce
**Contexte** : Extraire nom, prix, disponibilité depuis un catalogue e-commerce statique.
**Action** : Sélecteurs CSS identifiés sur la structure des fiches produits, pagination par paramètre `?page=N`.
**Résultat** : Spécification transmise à l'agent de développement back-end pour implémentation avec BeautifulSoup.

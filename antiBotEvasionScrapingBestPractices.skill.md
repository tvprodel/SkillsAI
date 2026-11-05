# Anti-Bot Evasion & Scraping Best Practices

## Objectif
Définir les bonnes pratiques techniques pour réaliser du scraping web de manière robuste, respectueuse des serveurs cibles et durable dans le temps : rate limiting, rotation, en-têtes HTTP, respect de `robots.txt`.

## Quand l'utiliser (triggers)
- « anti-bot », « rate limiting », « rotation proxy/user-agent », « respect robots.txt », « éviter le blocage IP », « scraping responsable ».
- Avant toute mise en production d'un scraper (statique ou dynamique) à volumétrie non négligeable.

## Hors périmètre
- Contournement actif de mesures de sécurité explicites (CAPTCHA, WAF) dans un but malveillant ou contraire aux CGU → hors périmètre, à proscrire ; escalade **l'agent de conseil juridique** si doute.
- Implémentation du code (rate limiter, gestion de proxies) → **l'agent de développement back-end**.
- Analyse légale de la conformité CGU/RGPD → skill Scraping Ethics & Legal Awareness + **l'agent de conseil juridique** / **l'agent de conformité RGPD**.

## Inputs requis
- Volumétrie de requêtes prévue (nombre de pages, fréquence).
- Politique `robots.txt` du site cible.
- Contraintes d'infrastructure (proxies disponibles, budget).
- Criticité du site cible (petit site vs plateforme à fort trafic).

## Sorties attendues
- Politique de rate limiting recommandée (délai entre requêtes, requêtes/seconde max).
- Stratégie d'en-têtes HTTP réalistes (User-Agent identifiable, Accept-Language).
- Stratégie de rotation (IP/proxy, User-Agent) si justifiée par la volumétrie.
- Politique de respect de `robots.txt` (Disallow, Crawl-delay).

## Workflow recommandé
1. Lire et documenter `robots.txt` du site cible (Disallow, Crawl-delay, sitemap).
2. Définir un rate limiting conservateur par défaut (ex : 1 requête/seconde/domaine, ajustable selon Crawl-delay).
3. Utiliser un User-Agent identifiable (nom du projet/contact) plutôt qu'un User-Agent usurpé, sauf besoin technique justifié et validé.
4. Prévoir une stratégie de retry avec backoff exponentiel sur erreurs 429/503 (respecter l'en-tête `Retry-After`).
5. N'envisager une rotation de proxies/IP que si strictement nécessaire (forte volumétrie légitime) et documenter la justification.
6. Transmettre la spécification à **l'agent de développement back-end** pour implémentation (rate limiter, gestion des en-têtes/retries).

## Garde-fous
- Respect strict de `robots.txt` par défaut ; toute dérogation doit être justifiée et validée par **l'agent de conseil juridique**.
- Ne jamais usurper l'identité d'un autre outil/navigateur dans un but de dissimulation malveillante.
- Ne jamais scraper à un débit susceptible de dégrader le service du site cible (déni de service involontaire).
- Documenter systématiquement les choix de rate limiting/rotation pour audit ultérieur.

## Template d'entrée (copier/coller)
```text
[Site cible]
- robots.txt analysé : oui/non
- Crawl-delay spécifié : ...

[Volumétrie]
- Pages/requêtes prévues : ...
- Fréquence : ...

[Infrastructure]
- Proxies disponibles : oui/non
```

## Template de sortie (copier/coller)
```text
[Rate limiting]
- Délai entre requêtes : ...
- Requêtes/seconde max : ...

[En-têtes HTTP]
- User-Agent : ...

[Retry/Backoff]
- Stratégie : ...

[Rotation]
- Justifiée : oui/non — raison : ...
```

## Checklist QA interne
- robots.txt lu et respecté.
- Rate limiting défini et documenté.
- User-Agent identifiable choisi (sauf justification contraire validée).
- Stratégie de retry/backoff spécifiée.
- Rotation proxy/UA justifiée par écrit si utilisée.

## KPI reliés
- Taux d'erreurs 429/403 observées (indicateur de blocage).
- Nombre de plaintes/signalements du site cible (idéalement 0).
- Débit moyen respecté vs Crawl-delay recommandé.

## Definition of done
- Politique de rate limiting et d'en-têtes documentée.
- robots.txt vérifié et respecté.
- Spécification transmise à l'agent de développement back-end.

## Exemples d'usage

### Exemple 1 : Scraping respectueux d'un site à fort trafic
**Contexte** : Extraction périodique de données publiques sur un site e-commerce à fort trafic.
**Action** : Crawl-delay de 2s respecté, User-Agent identifiable avec contact, retry avec backoff exponentiel sur 429.
**Résultat** : 0 blocage IP observé sur 3 mois de collecte.

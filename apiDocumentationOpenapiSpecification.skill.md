# API Documentation & OpenAPI Specification

## Objectif
Rédiger et maintenir une documentation d'API publique conforme à la spécification OpenAPI/Swagger (endpoints, schémas de requête/réponse, exemples, codes d'erreur, authentification).

## Quand l'utiliser (triggers)
- « documentation API », « OpenAPI », « Swagger », « spec API publique », « référence API », « API publique ».
- Publication d'une nouvelle version d'API destinée à des consommateurs externes ou internes.
- Demande de portail développeur ou de documentation self-service pour une API.

## Hors périmètre
- Conception de l'architecture API (choix REST/GraphQL, découpage des ressources, versionnement) → l'agent d'architecture.
- Implémentation technique de l'API (code des endpoints, logique métier) → l'agent de développement back-end / l'agent de développement TypeScript/JavaScript.
- Tests de charge et de sécurité de l'API → l'agent qualité / l'agent de sécurité.

## Inputs requis
- Liste des endpoints existants ou prévus (méthode HTTP, chemin, description fonctionnelle).
- Schémas de données (modèles de requête et de réponse, types, contraintes).
- Mécanisme d'authentification utilisé (API key, OAuth2, JWT, Basic Auth).
- Codes d'erreur standards et messages associés.
- Environnements disponibles (sandbox, production) et URLs de base correspondantes.

## Sorties attendues
- Fichier de spécification OpenAPI 3.x (YAML ou JSON) validé.
- Documentation interactive publiée (Swagger UI ou Redoc).
- Exemples d'appels prêts à l'emploi (curl, extraits SDK).
- Guide d'authentification et de gestion des erreurs.

## Workflow recommandé
1. Recensement des endpoints (méthode HTTP, chemin, description fonctionnelle, paramètres).
2. Définition des schémas request/response au format OpenAPI 3.x, en centralisant les modèles réutilisables dans `components/schemas`.
3. Documentation des codes d'erreur (structure des réponses d'erreur, codes HTTP, messages) et de l'authentification (API key, OAuth2, JWT) dans les sections `components/securitySchemes`.
4. Génération d'exemples d'appels concrets pour chaque endpoint (curl, extraits SDK dans un ou plusieurs langages selon l'audience cible).
5. Validation du fichier OpenAPI via un linter (Spectral, Swagger Editor) pour détecter les incohérences de schéma ou de syntaxe.
6. Publication de la documentation interactive (Swagger UI ou Redoc) et mise à disposition sur le portail développeur.

## Garde-fous
- Le fichier OpenAPI doit être syntaxiquement valide (validation Spectral/Swagger Editor sans erreur bloquante).
- Chaque endpoint documenté doit avoir au moins un exemple de requête et un exemple de réponse (succès et erreur).
- Ne jamais inclure de clés d'API réelles ou de secrets dans les exemples ; utiliser des valeurs factices explicitement identifiées comme telles.
- La documentation doit rester synchronisée avec le comportement réel de l'API (processus de revue à chaque changement d'endpoint).
- Les breaking changes doivent être signalés explicitement (changelog, versionnement de l'API).

## Template d'entrée (copier/coller)
```text
[API]
- Nom : ...
- Version : ...
- URL de base (sandbox/prod) : ...

[Endpoints]
- Liste (méthode, chemin, description) : ...

[Authentification]
- Mécanisme : ...

[Erreurs]
- Codes standards et structure : ...
```

## Template de sortie (copier/coller)
```text
[Spécification OpenAPI]
- Fichier : openapi.yaml
- Version OpenAPI : 3.x
- Statut validation linter : ...

[Documentation publiée]
- URL Swagger UI/Redoc : ...

[Exemples d'appels]
- Endpoint 1 : curl ...
- Endpoint 2 : curl ...

[Anomalies]
- Liste des incohérences détectées : ...
```

## Checklist QA interne
- Fichier OpenAPI validé sans erreur par le linter.
- Tous les endpoints ont un schéma de requête et de réponse documenté.
- Authentification et codes d'erreur documentés de façon exhaustive.
- Exemples d'appels testés et fonctionnels (au moins en sandbox).
- Documentation interactive accessible et à jour par rapport au fichier source.

## KPI reliés
- Taux de couverture des endpoints documentés (endpoints documentés / endpoints existants).
- Nombre d'erreurs de linting détectées avant publication.
- Nombre de tickets support liés à une documentation API incomplète ou obsolète.
- Délai entre mise en production d'un changement d'API et mise à jour de la documentation.

## Definition of done
- Fichier OpenAPI complet, validé et versionné dans le dépôt source.
- Documentation interactive publiée et accessible aux consommateurs de l'API.
- Exemples d'appels vérifiés fonctionnels.
- Processus de mise à jour documenté pour les futures évolutions de l'API.

## Exemples d'usage

### Exemple 1 : Documentation d'une API publique de gestion de commandes
**Contexte** : Une entreprise e-commerce ouvre une API publique permettant à des partenaires externes de créer et consulter des commandes, mais ne dispose d'aucune documentation formalisée, uniquement du code source.
**Action** : L'agent l'agent de rédaction technique recense les 9 endpoints existants (création commande, consultation, annulation, statut, etc.), formalise les schémas de requête/réponse en OpenAPI 3.1, documente l'authentification par API key en header et les 6 codes d'erreur standards, ajoute des exemples curl pour chaque endpoint, valide le fichier via Spectral (0 erreur bloquante), puis publie la documentation via Redoc sur le portail partenaires.
**Résultat** : Le temps d'intégration moyen des nouveaux partenaires passe de 3 semaines à 4 jours, et le nombre de tickets support liés à des questions d'usage de l'API diminue de 60% le mois suivant la publication.

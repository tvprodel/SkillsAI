# Docker Compose Orchestration

## Objectif
Orchestrer multi-conteneurs localement avec docker-compose (services, networks, volumes, healthchecks).

## Quand l'utiliser (triggers)
- « docker-compose », « orchestration locale », « multi-conteneurs », « stack dev/test ».
- App multi-services (frontend + backend + BDD).
- Environnements dev/test reproductibles.

## Hors périmètre
- Production orchestration (Swarm, Kubernetes) → l'agent d'architecture cloud ou containersExpert (Swarm basique).
- Dockerfile creation → skill Dockerfile Best Practices.
- CI/CD → l'agent d'intégration et d'automatisation.

## Inputs requis
- Services à orchestrer (app, BDD, cache, reverse proxy).
- Dépendances entre services (depends_on).
- Volumes persistants (data BDD, uploads).
- Networks isolation (frontend, backend).

## Sorties attendues
- docker-compose.yml avec services, networks, volumes.
- .env.example (variables env documentées).
- README avec docker-compose up, down, logs.

## Workflow recommandé
1. Définir services (app, db, redis, nginx) :
   ```yaml
   version: '3.8'
   services:
     app:
       build: .
       ports: ["3000:3000"]
       depends_on:
         db:
           condition: service_healthy
       env_file: .env
     db:
       image: postgres:15-alpine
       volumes: ["db-data:/var/lib/postgresql/data"]
       healthcheck:
         test: ["CMD", "pg_isready"]
         interval: 10s
   volumes:
     db-data:
   ```
2. Networks (frontend, backend) si isolation nécessaire.
3. Healthchecks (depends_on condition: service_healthy).
4. Tester : docker-compose up -d, docker-compose logs -f, docker-compose down.

## Garde-fous
- Healthchecks obligatoires (depends_on avec condition).
- Volumes nommés (persistance data BDD).
- .env.example fourni (secrets jamais en dur compose.yml).
- Restart policies (restart: unless-stopped pour services critiques).

## Template d'entrée (copier/coller)
```text
[Services]
- Liste : ...
- Dépendances : ...

[Volumes]
- Persistants : ...

[Networks]
- Isolation : ...
```

## Template de sortie (copier/coller)
```text
[docker-compose.yml]
- Services : ...
- Networks : ...
- Volumes : ...

[Tests]
- docker-compose up : ...
- Healthchecks : ...
```

## Checklist QA interne
- Healthchecks définis (services critiques).
- Volumes nommés (data BDD).
- .env.example fourni.
- README avec commandes up/down/logs.

## KPI reliés
- Temps startup stack (secondes).
- Taux succès healthchecks (%).
- Nb services stack (complexité).

## Definition of done
- docker-compose.yml créé et testé.
- Stack up/down réussis.
- README publié.

## Exemples d'usage

### Exemple 1 : [Titre du cas d'usage]
**Contexte** : [Description de la situation]
**Action** : [Ce qui a été fait]
**Résultat** : [Résultat obtenu]
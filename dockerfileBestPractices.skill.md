# Dockerfile Best Practices

## Objectif
Créer Dockerfiles optimisés (multi-stage builds, minimisation layers, sécurité, taille image).

## Quand l'utiliser (triggers)
- « crée Dockerfile », « optimise image Docker », « multi-stage builds », « sécurise image ».
- Containerisation application.
- Réduction taille images ou amélioration sécurité.

## Hors périmètre
- docker-compose orchestration → skill Docker Compose Orchestration.
- Kubernetes deployment → l'agent d'architecture cloud.
- Podman Quadlet → l'agent de scripting système.

## Inputs requis
- Application à containeriser (runtime, dépendances).
- Base image préférée (Alpine, Debian slim, distroless, scratch).
- Contraintes (taille image, sécurité, performance build).

## Sorties attendues
- Dockerfile multi-stage avec commentaires.
- .dockerignore.
- Taille finale image (docker images).
- Rapport scan sécurité (Trivy, Snyk).

## Workflow recommandé
1. Analyser app (runtime, dépendances build vs runtime).
2. Choisir base images :
   - Builder stage : image complète (node:18, python:3.11, golang:1.21).
   - Runtime stage : image minimale (alpine, slim, distroless).
3. Multi-stage Dockerfile :
   ```
   FROM node:18 AS builder
   WORKDIR /app
   COPY package*.json ./
   RUN npm ci
   COPY . .
   RUN npm run build
   
   FROM node:18-alpine AS runtime
   WORKDIR /app
   COPY --from=builder /app/dist ./dist
   COPY --from=builder /app/node_modules ./node_modules
   USER node
   CMD ["node", "dist/index.js"]
   ```
4. .dockerignore : node_modules, .git, tests/, *.md (sauf README).
5. Build : docker build -t myapp:latest .
6. Scan sécurité : trivy image myapp:latest.

## Garde-fous
- Multi-stage obligatoire (réduction taille 50-80%).
- USER non-root (sécurité).
- Base images officielles ou distroless (pas images random Docker Hub).
- HEALTHCHECK défini (monitoring liveness).
- Pas de secrets hardcodés (ARG secrets build-time invalide, env vars runtime).

## Template d'entrée (copier/coller)
```text
[Application]
- Runtime : ...
- Dépendances build : ...
- Dépendances runtime : ...

[Contraintes]
- Taille cible : ...
- Base image : ...
```

## Template de sortie (copier/coller)
```text
[Dockerfile]
- Contenu : ...
- Stages : ...

[Image]
- Taille : ...
- Scan Trivy : ...

[Optimisations]
- Layer caching : ...
```

## Checklist QA interne
- Multi-stage builds utilisé.
- USER non-root.
- .dockerignore créé.
- Image < 500 MB (apps standard).
- Scan Trivy : 0 vulnérabilités HIGH/CRITICAL.

## KPI reliés
- Taille image (MB).
- Nb vulnérabilités (Trivy HIGH/CRITICAL).
- Temps build (minutes).

## Definition of done
- Dockerfile créé et testé.
- Image buildée < taille cible.
- Scan sécurité passé.

## Exemples d'usage

### Exemple 1 : [Titre du cas d'usage]
**Contexte** : [Description de la situation]
**Action** : [Ce qui a été fait]
**Résultat** : [Résultat obtenu]
# Container Registry Management

## Objectif
Gérer registries conteneurs (Docker Hub, Harbor, GitLab CR, AWS ECR, Azure ACR, GCP GCR) : push/pull, tags, scanning, cleanup.

## Quand l'utiliser (triggers)
- « push image registry », « configure Harbor », « ECR policies », « cleanup images ».
- Publication images conteneurs.
- Gestion lifecycle images (retention, cleanup old tags).

## Hors périmètre
- Build images → skill Dockerfile Best Practices.
- Orchestration Kubernetes → l'agent d'architecture cloud.
- CI/CD pipelines → l'agent d'intégration et d'automatisation.

## Inputs requis
- Registry cible (Docker Hub, Harbor private, cloud ECR/ACR/GCR).
- Images à publier (tags versionnés).
- Policies retention (cleanup tags > 30j, keep latest 10).

## Sorties attendues
- Images poussées vers registry (docker push).
- Policies retention configurées (Harbor/ECR/ACR lifecycle).
- Documentation authentication registry (credentials, tokens).

## Workflow recommandé
1. Authentication registry :
   - Docker Hub : docker login.
   - Harbor : docker login harbor.example.com.
   - ECR : aws ecr get-login-password | docker login.
   - ACR : az acr login --name myregistry.
   - GCR : gcloud auth configure-docker.
2. Tag image : docker tag myapp:latest registry.example.com/myapp:v1.0.0.
3. Push : docker push registry.example.com/myapp:v1.0.0.
4. Scan sécurité registry (Harbor built-in Trivy, ECR scanning).
5. Policies retention (Harbor : cleanup tags > 30j, ECR lifecycle : expire untagged after 7d).

## Garde-fous
- Tags versionnés (semver v1.0.0, pas latest seul en prod).
- Scan sécurité automatique (Harbor Trivy, ECR enhanced scanning).
- Policies retention (éviter registry bloat, cleanup old tags).
- Authentication sécurisée (tokens limités temps/scope, pas passwords hardcodés).

## Template d'entrée (copier/coller)
```text
[Registry]
- Type : ...
- Images : ...

[Policies]
- Retention : ...
- Scanning : ...
```

## Template de sortie (copier/coller)
```text
[Push]
- Images publiées : ...
- Tags : ...

[Policies]
- Retention configurée : ...
- Scanning : ...

[Authentication]
- Credentials : ...
```

## Checklist QA interne
- Images poussées avec tags versionnés.
- Scan sécurité automatique enabled.
- Policies retention configurées (cleanup vieux tags).
- Authentication sécurisée (tokens, pas passwords).

## KPI reliés
- Nb images registry (taille totale GB).
- Nb tags par image (moyenne).
- Nb vulnérabilités HIGH/CRITICAL (scan registry).

## Definition of done
- Images publiées vers registry.
- Policies retention configurées.
- Documentation authentication publiée.

## Exemples d'usage

### Exemple 1 : [Titre du cas d'usage]
**Contexte** : [Description de la situation]
**Action** : [Ce qui a été fait]
**Résultat** : [Résultat obtenu]
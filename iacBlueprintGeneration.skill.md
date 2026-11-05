# IaC Blueprint Generation

## Objectif
Générer des squelettes d'Infrastructure as Code (Terraform, Bicep, CloudFormation) alignés sur une architecture validée, paramétrables et documentés.

## Quand l'utiliser (triggers)
- « génère le Terraform/IaC », « template d'infra », « provisionne ».
- Industrialisation d'une architecture cible déjà validée.
- Standardisation de modules réutilisables.

## Hors périmètre
- Conception de l'architecture cible → skill Cloud Architecture Design.
- Exécution/déploiement en production → l'agent de coordination (exécution directe, sous supervision).
- Pipelines CI/CD applicatifs → l'agent d'intégration et d'automatisation.

## Inputs requis
- Architecture cible validée.
- Provider et région(s).
- Conventions de nommage et de tagging.
- Contraintes de sécurité (chiffrement, réseau, IAM).

## Sorties attendues
- Fichiers IaC commentés et modulaires.
- Variables paramétrables et valeurs par défaut sûres.
- README d'usage (prérequis, commandes, ordre d'application).
- Aucun secret en dur (variables d'environnement / gestionnaire de secrets).

## Workflow recommandé
1. Traduire l'architecture cible en modules IaC.
2. Externaliser les paramètres variables et secrets.
3. Ajouter tags, chiffrement et contrôles réseau par défaut.
4. Documenter l'usage et l'ordre d'application.

## Garde-fous
- Jamais de secret en dur.
- Versions de providers/modules épinglées, stables et supportées (pas d'EOL).
- Valeurs par défaut sécurisées (moindre privilège, chiffrement activé).

## Template d'entrée (copier/coller)
```text
[Contexte]
- Architecture cible : ...
- Provider/région : ...

[Objectif]
- Outil IaC : Terraform | Bicep | CloudFormation
- Contraintes sécurité : ...
```

## Template de sortie (copier/coller)
```text
[Modules IaC]
- Module 1 : ...
- Variables : ...

[Usage]
- Prérequis : ...
- Commandes : ...
```

## Checklist QA interne
- Aucun secret en dur.
- Versions épinglées et supportées.
- README d'usage complet.

## KPI reliés
- Taux de ressources chiffrées par défaut.
- Nombre de secrets détectés en dur (cible : 0).
- Réutilisabilité des modules.

## Definition of done
- Squelette IaC complet, paramétrable et commenté.
- README d'usage fourni.
- Prêt pour revue sécurité avant exécution.

## Exemples d'usage

### Exemple 1 : [Titre du cas d'usage]
**Contexte** : [Description de la situation]
**Action** : [Ce qui a été fait]
**Résultat** : [Résultat obtenu]
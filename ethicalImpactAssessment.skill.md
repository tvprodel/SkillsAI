# Skill: Ethical Impact Assessment

## Objectif
Évaluer l'impact éthique et sociétal des systèmes d'intelligence artificielle : conséquences sur les individus, groupes et société, risques discriminatoires, questions AI Act et recommandations d'ethics by design.

## Agents principaux
- L'agent d'éthique des données
- L'agent de stratégie produit
- L'agent de conformité RGPD
- L'agent d'architecture IA

## Quand l'utiliser (triggers)
- Évaluer les impacts éthiques ou sociétaux d'un système IA avant son lancement ou une évolution importante.
- Identifier les parties prenantes affectées, risques, mesures de mitigation et recours.
- Préparer une analyse à coordonner avec les responsables de conformité et les décideurs.

## Hors périmètre
- Ne constitue pas un avis juridique ni une détermination définitive de conformité AI Act.
- Ne remplace pas une analyse d'impact RGPD, une évaluation réglementaire formelle ou une décision humaine.
- Les arbitrages de lancement, d'appétence au risque et d'allocation des moyens appartiennent aux responsables humains.

## Inputs requis
- Cas d'usage, cycle de vie, contexte de déploiement et population concernée.
- Parties prenantes, bénéfices attendus, processus décisionnel et solutions alternatives.
- Données, fournisseurs, contrôles existants, incertitudes et incidents connus.
- Juridictions, calendrier, contraintes et responsables décisionnaires.

## Sorties attendues
- Analyse des impacts positifs/négatifs et groupes concernés.
- Registre des risques avec gravité, probabilité, preuves et incertitudes.
- Mesures de prévention, mitigation, supervision, recours et owners.
- Questions à faire valider par les responsables juridiques, conformité et métier.

## Workflow recommandé
1. Cadrer le système, ses usages prévus et raisonnablement prévisibles, son contexte et ses parties prenantes.
2. Examiner bénéfices, impacts négatifs, vulnérabilités et répartition des conséquences.
3. Coter les risques avec critères explicités et distinguer faits des hypothèses.
4. Définir les mesures de réduction, les recours et le suivi avec des owners.
5. Faire valider les points réglementaires et décisionnels par les responsables compétents.
6. Réviser l'évaluation aux jalons du cycle de vie ou lors d'un changement significatif.

## Garde-fous
- Ne pas confondre cette évaluation avec une certification légale ou une DPIA.
- Ne pas présenter les critères de risque comme universels; justifier la méthode et les seuils.
- Inclure les personnes affectées, y compris les groupes minoritaires et vulnérables.
- Conserver les désaccords, inconnues et risques résiduels plutôt que les masquer.

## Template d'entrée (copier/coller)
```text
[Système, usages et contexte] ...
[Parties prenantes/populations] ...
[Bénéfices, dommages, données et contrôles existants] ...
[Juridictions, incertitudes et décision attendue] ...
```

## Template de sortie (copier/coller)
```text
[Périmètre et méthode] ...
[Impacts/risques] Groupe concerné, preuve, probabilité, impact, incertitude : ...
[Mitigations/recours] Mesure, owner, échéance/jalon et preuve de suivi : ...
[Validations requises et risques résiduels] ...
```

## Checklist QA interne
- Le périmètre, les usages et populations affectées sont-ils explicites?
- Les bénéfices et dommages sont-ils examinés par partie prenante?
- Les niveaux de confiance, inconnues et risques résiduels sont-ils visibles?
- Les mitigations ont-elles un owner et une méthode de vérification?
- Les conclusions réglementaires sont-elles laissées aux responsables compétents?

## KPI reliés
- Part des risques prioritaires avec mesure, owner et preuve de suivi.
- Délai de traitement des risques éthiques ouverts.
- Nombre d'incidents ou retours des personnes affectées suivis par période.

## Definition of done
- Impacts et risques sont reliés au contexte et aux parties prenantes.
- Les mitigations, owners et risques résiduels sont documentés.
- Les validations juridiques/conformité et décisions humaines nécessaires sont identifiées.

## Compétences détaillées

### 1. Framework d'évaluation éthique
**Objectif** : Structurer l'analyse d'impact éthique selon une méthodologie reproductible et complète.

#### Étapes du framework

**Étape 1 : Cadrage et contexte**
- Identifier le système IA cible et son cas d'usage
- Cartographier les parties prenantes (stakeholders)
- Définir le périmètre d'analyse (fonctionnalités évaluées)
- Établir critères d'acceptation éthique

**Étape 2 : Identification des risques éthiques**
- Risques discriminatoires (biais, fairness)
- Risques de vie privée (surveillance, profiling)
- Risques d'autonomie (manipulation, nudging)
- Risques de sécurité (dual use, weaponization)
- Risques sociétaux (emploi, inégalités, cohésion sociale)

**Étape 3 : Évaluation de la gravité**
- Probabilité d'occurrence (Faible/Moyenne/Élevée)
- Impact si réalisé (Mineur/Modéré/Majeur/Critique)
- Matrice risque = Probabilité × Impact
- Priorisation par criticité

**Étape 4 : Analyse parties prenantes**
- Qui bénéficie du système IA ?
- Qui subit les risques/coûts ?
- Distribution équitable ou asymétrique ?
- Groupes vulnérables identifiés ?

**Étape 5 : Recommandations et mitigation**
- Mesures préventives (design éthique)
- Mesures correctives (monitoring, supervision humaine)
- Mesures compensatoires (recours, indemnisation)
- Roadmap implémentation

**Template Ethical Impact Assessment** :
```markdown
# Ethical Impact Assessment : [Nom Système IA]

## 1. Contexte
- **Système** : [Description]
- **Cas d'usage** : [Application concrète]
- **Parties prenantes** : [Utilisateurs, impactés, fournisseurs, régulateurs]
- **Périmètre** : [Fonctionnalités évaluées]
- **Date** : [YYYY-MM-DD]

## 2. Risques éthiques identifiés

| ID | Risque | Catégorie | Probabilité | Impact | Criticité |
|----|--------|-----------|-------------|--------|-----------|
| R1 | Biais de genre dans recommandations | Discrimination | Élevée | Majeur | CRITIQUE |
| R2 | Surveillance excessive utilisateurs | Vie privée | Moyenne | Modéré | MOYEN |
| R3 | Manipulation comportementale (dark patterns) | Autonomie | Faible | Majeur | MOYEN |

### R1 : Biais de genre (détail)
- **Description** : Système recommande emplois tech 60% moins fréquemment aux femmes
- **Population impactée** : Femmes 18-55 ans cherchant emploi (≈ 2M personnes/an)
- **Conséquence** : Perpétuation inégalités de genre dans secteur tech
- **Cause probable** : Biais historique données entraînement (70% candidats hommes)

## 3. Analyse parties prenantes

### Bénéficiaires
- **Employeurs** : Gain efficacité recrutement (30% temps économisé)
- **Candidats qualifiés homme** : Visibilité accrue offres pertinentes

### Impactés négativement
- **Candidates femmes qualifiées** : Opportunités réduites de 60%
- **Secteur tech** : Perte diversité, talents non détectés

### Distribution asymétrique
⚠️ Bénéfices concentrés sur groupe majoritaire, coûts supportés par groupe minoritaire → **INÉQUITABLE**

## 4. Conformité AI Act européen

### Classification niveau risque
- **Niveau** : RISQUE ÉLEVÉ (High-Risk AI System)
- **Justification** : Emploi et gestion travailleurs (Annexe III point 4)
- **Exigences applicables** :
  - Système de gestion risques (Art. 9)
  - Gouvernance données (Art. 10)
  - Documentation technique (Art. 11)
  - Transparence et information utilisateurs (Art. 13)
  - Supervision humaine (Art. 14)

### Conformité actuelle
| Exigence | Status | Gap |
|----------|--------|-----|
| Gestion risques | ⚠️ Partiel | Pas de monitoring fairness continu |
| Gouvernance données | ❌ Non conforme | Biais historique non mitigé |
| Documentation | ✅ Conforme | Model card complétée |
| Transparence | ⚠️ Partiel | Explications disponibles mais opt-in |
| Supervision humaine | ❌ Non conforme | Décisions 100% automatisées |

## 5. Recommandations

### Priorité CRITIQUE (0-3 mois)
1. **Implémenter supervision humaine obligatoire**
   - Impact : Réduction risque discrimination de 80%
   - Effort : Moyen (refonte workflow validation)
   - Owner : l'agent produit

2. **Mitiger biais genre données**
   - Impact : Réduction écart 60% → 10% (cible demographic parity)
   - Effort : Élevé (rebalancing dataset + retraining)
   - Owner : ML Engineer

### Priorité ÉLEVÉE (3-6 mois)
3. **Monitoring fairness continu**
   - Impact : Détection précoce dérives
   - Effort : Faible (dashboard + alertes)
   - Owner : l'agent d'éthique des données

4. **Opt-out explicabilité → Opt-in par défaut**
   - Impact : Transparence accrue (compliance RGPD Art. 22)
   - Effort : Faible (config interface)
   - Owner : l'agent produit

### Priorité NORMALE (6-12 mois)
5. **Audit externe indépendant**
   - Impact : Validation conformité tierce partie
   - Effort : Moyen (coût audit ≈ 20k EUR)
   - Owner : Legal & Compliance

## 6. Conclusion
- **Verdict éthique** : ❌ **NON DÉPLOYABLE EN L'ÉTAT**
- **Justification** : Risques discriminatoires critiques non mitigés
- **Prochaine étape** : Implémenter recommandations priorité CRITIQUE avant reconsidération
```


### 2. Analyse d'impact sociétal
**Objectif** : Évaluer les conséquences macroscopiques du déploiement d'un système IA à grande échelle.

#### Dimensions d'analyse

**Impact économique**
- Destruction/création emplois (automation)
- Redistribution valeur créée (qui capture bénéfices ?)
- Concentration pouvoir économique (effets monopolistiques)
- Coût infrastructure/énergie (empreinte carbone)

**Impact social**
- Cohésion sociale (polarisation, filtres bulles)
- Inégalités (accès technologie, fracture numérique)
- Discrimination structurelle (perpétuation biais systémiques)
- Qualité de vie (bien-être, santé mentale)

**Impact démocratique**
- Manipulation politique (deepfakes, désinformation)
- Surveillance étatique (authoritarisme numérique)
- Concentration pouvoir informationnel (data monopolies)
- Droit à la vie privée (tracking, profiling)

**Impact environnemental**
- Empreinte carbone entraînement/inférence
- Consommation ressources (eau, terres rares)
- E-waste (obsolescence matériel)

**Méthode d'évaluation** :
1. **Définir scénarios déploiement** (optimiste, réaliste, pessimiste)
2. **Modéliser effets directs** (1er ordre) et **indirects** (2e/3e ordre)
3. **Identifier gagnants/perdants** par dimension
4. **Quantifier quand possible** (emplois détruits, émissions CO2, etc.)
5. **Proposer mesures compensation** pour perdants

**Exemple** :
```markdown
## Impact Sociétal : ChatBot Service Client IA (déploiement national)

### Scénario réaliste (5 ans)
- **Adoption** : 60% entreprises >50 employés
- **Substitution emplois** : 40% agents call-center (≈ 80k emplois)

### Impact économique
- **Gains productivité** : +30% efficacité, -25% coûts opérationnels (bénéfice entreprises)
- **Pertes emploi** : -80k emplois direct, -30k emplois indirect (secteur formation agents)
- **Redistribution** : Valeur capturée par entreprises tech (fournisseurs IA) + grandes entreprises clientes
  → Asymétrie : Bénéfices concentrés, coûts diffus (chômage agents)

### Impact social
- **Inégalités** : Aggravation précarité travailleurs peu qualifiés
- **Qualité service** : Amélioration temps réponse (+20%) mais baisse satisfaction interactions complexes (-15%)
- **Fracture numérique** : Exclusion populations peu à l'aise tech (seniors, handicaps)

### Recommandations compensation
1. Programme reconversion agents (financement mixte État + entreprises bénéficiaires)
2. Taxe automation pour financer filet sécurité sociale
3. Maintien option humaine obligatoire (loi) pour interactions complexes/sensibles
```


### 3. Conformité éthique AI Act européen
**Objectif** : Évaluer conformité système IA aux exigences éthiques de l'AI Act (Règlement UE 2024/1689).

#### Classification niveau de risque

**Pratiques interdites (Inacceptable)**
- Manipulation comportementale (subliminal)
- Exploitation vulnérabilités (âge, handicap)
- Social scoring gouvernemental
- Biométrie temps réel espaces publics (sauf exceptions)

**Risque élevé (High-Risk)**
Systèmes listés Annexe III :
- Identification biométrique
- Infrastructure critique
- Éducation/formation (admission, évaluation)
- **Emploi** (recrutement, promotion, licenciement)
- Services essentiels (crédit, assurance, urgences)
- Application de la loi (prédiction criminalité, évaluation fiabilité preuves)
- Migration/asile
- Justice (aide décisions judiciaires)

**Risque limité (Transparence)**
- Chatbots (obligation information utilisateur)
- Deepfakes (obligation marquage)
- Systèmes recommandation contenu
- Systèmes catégorisation biométrique

**Risque minimal**
- Filtres anti-spam
- Correcteurs orthographiques
- Jeux vidéo IA

#### Exigences systèmes haut risque

**Art. 9 : Système de gestion des risques**
- [ ] Identifier risques raisonnablement prévisibles
- [ ] Estimer/évaluer risques émergents (usage + données)
- [ ] Évaluer risques sur base tests
- [ ] Adopter mesures de gestion risques appropriées
- [ ] Tester mesures gestion risques
- [ ] Réviser/mettre à jour système de manière itérative

**Art. 10 : Gouvernance des données**
- [ ] Pratiques gouvernance données appropriées (qualité, pertinence, représentativité)
- [ ] Examen données pour biais possibles
- [ ] Détection lacunes/insuffisances
- [ ] Mesures atténuation biais identifiés

**Art. 13 : Transparence et information**
- [ ] Instructions d'utilisation compréhensibles
- [ ] Capacités et limitations système
- [ ] Niveau de performance (exactitude, robustesse)
- [ ] Mesures supervision humaine requises
- [ ] Durée de vie attendue

**Art. 14 : Supervision humaine**
- [ ] Conception permettant surveillance humaine
- [ ] Mesures techniques garantissant :
  - Compréhension capacités/limites
  - Sensibilisation biais automation
  - Capacité interpréter sorties correctement
  - Capacité décider ne pas utiliser ou outrepasser sortie
  - Capacité intervention/interruption système

**Checklist conformité** :
```markdown
## Conformité AI Act : [Nom Système]

### Classification
- [x] Risque évalué : HAUT (Emploi - Recrutement)
- [ ] Pratique interdite : Non
- [x] Annexe III applicable : Oui (point 4a)

### Exigences obligatoires

#### Gestion des risques (Art. 9)
- [x] Risques identifiés et documentés
- [ ] Tests risques émergents (données biaisées) → GAP
- [x] Mesures mitigation adoptées (threshold optimization)
- [ ] Tests mesures mitigation → GAP
- [ ] Révision itérative → GAP (pas de process défini)

#### Gouvernance données (Art. 10)
- [x] Pratiques gouvernance documentées
- [ ] Biais examinés systématiquement → GAP
- [ ] Détection lacunes automatisée → GAP
- [ ] Mesures mitigation biais implémentées → GAP (partiel)

**Score conformité : 40% (4/10 exigences)**
**Verdict : NON CONFORME** ❌

### Actions correctives prioritaires
1. Implémenter tests automatisés biais (Art. 10)
2. Définir processus révision itérative risques (Art. 9)
3. Déployer monitoring continu fairness (Art. 10)
```


### 4. Design éthique (Ethics by Design)
**Objectif** : Intégrer principes éthiques dès la conception du système IA plutôt qu'en audit post-hoc.

#### Principes Ethics by Design

**1. Fairness by Design**
- Audit biais données AVANT entraînement
- Contraintes fairness dans fonction objectif
- Validation fairness comme critère arrêt entraînement
- Monitoring fairness continu post-déploiement

**2. Privacy by Design**
- Minimisation données collectées (RGPD principe)
- Anonymisation/pseudonymisation par défaut
- Chiffrement end-to-end
- Federated learning (données restent locales)

**3. Transparency by Design**
- Modèles interprétables par défaut (ou explications LIME/SHAP intégrées)
- Documentation automatique (model cards générées)
- Audit trails décisions algorithmiques
- Communication proactive limitations

**4. Accountability by Design**
- Traçabilité versioning (modèles, données, hyperparamètres)
- Responsabilités claires (RACI)
- Mécanismes recours humain (human-in-the-loop)
- Procédure gestion incidents éthiques

**5. Safety & Security by Design**
- Red teaming dès phase conception
- Adversarial testing automatisé (CI/CD)
- Fail-safes (fallback vers humain si incertitude > seuil)
- Isolation composants critiques

**Checklist Ethics by Design** :
```markdown
## Ethics by Design : [Projet IA]

### Phase Conception
- [ ] Ethical Impact Assessment réalisé AVANT développement
- [ ] Parties prenantes consultées (utilisateurs finaux, groupes impactés)
- [ ] Métriques fairness définies comme exigences fonctionnelles
- [ ] Architecture incluant human oversight points

### Phase Développement
- [ ] Dataset audité pour biais (pre-processing)
- [ ] Contraintes fairness intégrées entraînement (in-processing)
- [ ] Tests A/B fairness avant chaque release
- [ ] Explications (LIME/SHAP) générées automatiquement

### Phase Déploiement
- [ ] Monitoring fairness temps réel (dashboards)
- [ ] Alertes automatiques si drift détecté
- [ ] Procédure escalade incidents éthiques définie
- [ ] Audit externe programmé (fréquence : trimestrielle)

### Phase Maintenance
- [ ] Révision périodique métriques éthiques (mensuelle)
- [ ] Mises à jour modèle testées fairness (non-régression)
- [ ] Feedback utilisateurs intégré (biais signalés)
- [ ] Documentation mise à jour (model card + datasheet)
```


### 5. Consultation stakeholders
**Objectif** : Impliquer parties prenantes dans évaluation éthique pour perspectives multiples.

#### Méthode participative

**Étape 1 : Identifier stakeholders**
- Utilisateurs finaux (bénéficiaires directs)
- Personnes impactées (cibles décisions IA)
- Groupes vulnérables (risques disproportionnés)
- Experts domaine (contexte métier)
- Régulateurs/société civile

**Étape 2 : Organiser consultation**
- Ateliers participatifs (focus groups)
- Enquêtes en ligne (échantillon représentatif)
- Interviews approfondies (groupes marginalisés)
- Panels citoyens (délibération)

**Étape 3 : Analyser retours**
- Thèmes récurrents (préoccupations majoritaires)
- Préoccupations minoritaires (groupes vulnérables)
- Trade-offs identifiés (tensions valeurs)
- Recommandations co-construites

**Étape 4 : Intégrer dans design**
- Prioriser recommandations consensuelles
- Arbitrer tensions (l'agent produit)
- Documenter décisions (ADR)
- Communiquer retour stakeholders (transparence)

**Template rapport consultation** :
```markdown
## Consultation Stakeholders : [Projet IA]

### Participants (N=150)
- Utilisateurs finaux : 60% (n=90)
- Impactés : 25% (n=38)
- Experts : 10% (n=15)
- Régulateurs/ONG : 5% (n=7)

### Méthodes
- Ateliers participatifs : 3 sessions (30 pers/session)
- Enquête en ligne : 150 réponses
- Interviews : 15 personnes (groupes marginalisés)

### Préoccupations identifiées (top 5)
1. **Transparence décisions** : 85% préoccupés (demande explications obligatoires)
2. **Biais discrimination** : 78% préoccupés (demande audits indépendants)
3. **Vie privée** : 72% préoccupés (demande minimisation données)
4. **Recours humain** : 68% préoccupés (demande option human review)
5. **Responsabilité erreurs** : 65% préoccupés (demande indemnisation si préjudice)

### Recommandations co-construites
1. Implémenter explications opt-in par défaut (consensus 90%)
2. Audit fairness trimestriel par organisme indépendant (consensus 85%)
3. Option recours humain TOUJOURS disponible (consensus 95%)

### Décisions design intégrées
✅ Recommandation 1 : Intégrée (release v2.0)
✅ Recommandation 3 : Intégrée (release v2.0)
⚠️ Recommandation 2 : Partiellement (audit interne mensuel, externe annuel, compromis coût)
```


## Cas d'usage typiques

### Système de crédit scoring
- **Risques** : Discrimination indirecte (proxies), exclusion financière groupes vulnérables
- **AI Act** : Haut risque (services essentiels)
- **Recommandations** : Fairness metrics (predictive parity), supervision humaine décisions limites, droit recours

### Reconnaissance faciale sécurité publique
- **Risques** : Surveillance de masse, biais raciaux, chilling effect libertés
- **AI Act** : Pratique interdite (biométrie temps réel) sauf exceptions strictes
- **Recommandations** : Évaluation nécessité/proportionnalité, audit indépendant, transparence usage

### IA générative (LLM chatbot)
- **Risques** : Désinformation, toxicité, biais culturels, plagiat
- **AI Act** : Risque limité (transparence obligatoire)
- **Recommandations** : Guardrails toxicité, modération humaine, disclaimer IA générative


## Frameworks éthiques de référence
- **EU AI Ethics Guidelines** (High-Level Expert Group on AI)
- **IEEE Ethically Aligned Design**
- **OECD AI Principles**
- **UNESCO Recommendation on Ethics of AI**
- **Montreal Declaration for Responsible AI**


## Contraintes et références
- [AI Act (Règlement UE 2024/1689)](https://artificialintelligenceact.eu/)
- [EU AI Ethics Guidelines](https://digital-strategy.ec.europa.eu/en/library/ethics-guidelines-trustworthy-ai)
- [IEEE Ethically Aligned Design](https://ethicsinaction.ieee.org/)
- [Algorithmic Impact Assessment (Canada)](https://www.canada.ca/en/government/system/digital-government/digital-government-innovations/responsible-use-ai/algorithmic-impact-assessment.html)

## Exemples d'usage

### Exemple 1 : Évaluer un outil de présélection de candidatures
**Contexte** : Un employeur envisage d'utiliser un système IA pour classer les candidatures avant examen humain.  
**Input** : Cas d'usage et population concernée, données/proxies employés, étapes de décision, mécanismes de recours, contrôles humains et éléments de conformité disponibles.  
**Output** : Parties prenantes et groupes potentiellement affectés, risques éthiques classés avec preuves/incertitudes, mitigations et validations juridiques nécessaires; pas de conclusion légale automatique.

### Exemple 2 : Examiner un assistant IA d'aide aux étudiants
**Contexte** : Un établissement veut proposer un assistant qui recommande des ressources pédagogiques selon les difficultés déclarées.  
**Input** : Publics visés, données collectées, types de recommandations, modalités de consentement, options d'escalade vers un conseiller et critères d'évaluation.  
**Output** : Analyse des risques de vie privée, d'étiquetage et d'accès inéquitable, mesures de minimisation/supervision et plan de suivi impliquant les parties prenantes.

# Scraping Ethics & Legal Awareness

## Objectif
Sensibiliser aux enjeux éthiques et légaux du web scraping (CGU, propriété intellectuelle, RGPD, robots.txt) et déclencher systématiquement l'escalade vers les agents juridiques compétents. Ce skill couvre uniquement la **sensibilisation technique**, pas le conseil juridique définitif.

## Quand l'utiliser (triggers)
- « le scraping est-il légal ? », « CGU », « robots.txt légal », « propriété intellectuelle contenu scrapé », « données personnelles scraping », « RGPD scraping ».
- Systématiquement en amont de tout projet de scraping, avant conception technique.

## Hors périmètre
- Avis juridique définitif et rédaction de clauses contractuelles → **l'agent de conseil juridique**.
- Analyse RGPD complète (base légale, DPIA, registre des traitements) → **l'agent de conformité RGPD**.
- Mise en œuvre technique du respect de `robots.txt`/rate limiting → skill Anti-Bot Evasion & Scraping Best Practices.

## Inputs requis
- Nature du site cible (public, nécessitant authentification, CGU spécifiques).
- Nature des données visées (publiques, personnelles, protégées par droit d'auteur/bases de données).
- Usage prévu des données (interne, recherche, revente, IA/entraînement de modèle).
- Juridiction concernée (Belgique/UE par défaut).

## Sorties attendues
- Liste des points de vigilance identifiés (CGU, robots.txt, PI, RGPD).
- Recommandation d'escalade explicite vers l'agent juridique compétent avant tout développement.
- Rappel des principes de minimisation et de finalité si données personnelles suspectées.
- Aucune validation juridique définitive émise par cet agent.

## Workflow recommandé
1. Identifier si le site cible a des CGU interdisant explicitement le scraping automatisé.
2. Vérifier `robots.txt` (indicateur d'intention, non contraignant juridiquement en soi mais signal fort).
3. Identifier si les données visées incluent des données à caractère personnel (noms, emails, profils).
4. Identifier si le contenu est protégé (droit d'auteur, droit sui generis des bases de données).
5. Documenter les points de vigilance et **escalader systématiquement** :
   - CGU / contrat / propriété intellectuelle → **l'agent de conseil juridique**.
   - Données personnelles / RGPD → **l'agent de conformité RGPD**.
6. Ne jamais donner un feu vert juridique définitif ; formuler uniquement des points de vigilance et rediriger.

## Garde-fous
- Ne jamais affirmer qu'un scraping est « légal » ou « illégal » de manière définitive : rediriger systématiquement vers l'agent juridique compétent.
- Toujours signaler la présence potentielle de données personnelles pour déclenchement RGPD.
- Ne jamais recommander de contourner des CGU explicitement restrictives sans validation légale préalable.
- Documenter la source et la date de consultation des CGU/robots.txt pour traçabilité.

## Template d'entrée (copier/coller)
```text
[Site cible]
- CGU consultées : oui/non — restriction scraping mentionnée : oui/non
- robots.txt : Disallow pertinent : oui/non

[Données visées]
- Données personnelles suspectées : oui/non
- Contenu protégé (PI) suspecté : oui/non

[Usage prévu]
- Interne / recherche / revente / entraînement IA
```

## Template de sortie (copier/coller)
```text
[Points de vigilance identifiés]
- ...

[Escalade recommandée]
- L'agent de conseil juridique : oui/non — motif : ...
- L'agent de conformité RGPD : oui/non — motif : ...

[Statut]
- Feu vert technique conditionnel à validation juridique : oui
```

## Checklist QA interne
- CGU et robots.txt consultés et documentés.
- Présence de données personnelles évaluée.
- Escalade juridique explicite proposée (pas d'avis définitif émis).
- Aucune recommandation de contournement de restriction explicite.

## KPI reliés
- Taux de projets scraping ayant fait l'objet d'une escalade juridique avant développement (%).
- Nombre d'incidents de conformité évités grâce à l'escalade précoce.

## Definition of done
- Points de vigilance documentés.
- Escalade vers l'agent juridique compétent effectuée ou explicitement recommandée à l'utilisateur.
- Aucune validation juridique définitive émise par cet agent.

## Exemples d'usage

### Exemple 1 : Scraping d'un annuaire professionnel public
**Contexte** : Extraction de noms et emails professionnels publics pour une base de prospection commerciale.
**Action** : Données personnelles identifiées (noms, emails) → escalade immédiate vers **l'agent de conformité RGPD** avant toute conception technique.
**Résultat** : Projet suspendu en attente de validation de la base légale (intérêt légitime) par l'agent juridique compétent.

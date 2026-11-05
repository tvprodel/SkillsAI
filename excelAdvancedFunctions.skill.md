# Excel Advanced Functions

**Compétence** : Maîtriser les formules Excel avancées (XLOOKUP, LAMBDA, LET, tableaux dynamiques), Power Query, Power Pivot, DAX basique et automatisation VBA.

**Agents utilisateurs** : l'agent Microsoft 365 (principal)

## Quand l'utiliser (triggers)
- Créer des formules complexes (XLOOKUP, INDEX/MATCH, tableaux dynamiques)
- Transformer et nettoyer des données avec Power Query
- Construire des modèles de données relationnels avec Power Pivot
- Automatiser des tâches répétitives avec VBA basique
- Optimiser les performances de classeurs volumineux

## Hors périmètre
- Analyse de données métier/BI → l'agent d'analyse de données
- Modélisation de base de données → l'agent bases de données
- Développement .NET/COM add-ins → l'agent de développement .NET
- Pipelines ETL complexes → l'agent d'ingénierie des données

---

## Compétences

### 1. Formules avancées (XLOOKUP, LAMBDA, LET, tableaux dynamiques)

**Description** : Utiliser les formules Excel modernes pour des calculs complexes, dynamiques et maintenables.

**Formules clés** :

**XLOOKUP** (remplace VLOOKUP/HLOOKUP/INDEX/MATCH) :
```excel
=XLOOKUP(valeur_recherchée, plage_recherche, plage_retour, [si_non_trouvé], [mode_correspondance], [mode_recherche])

Exemple : Rechercher le prix d'un produit
=XLOOKUP(A2, Produits[Code], Produits[Prix], "Produit introuvable", 0)

Avantages :
- Recherche verticale ET horizontale
- Valeur par défaut si non trouvé
- Recherche approximative ou exacte
- Recherche de gauche à droite ou inversée
```

**LET** (variables nommées pour lisibilité) :
```excel
=LET(var1, expression1, var2, expression2, ..., calcul_final)

Exemple : Calcul complexe réutilisable
=LET(
    prix, B2,
    quantité, C2,
    remise, D2,
    sousTotal, prix * quantité,
    montantRemise, sousTotal * remise,
    sousTotal - montantRemise
)

Avantages :
- Pas de recalcul multiple (performances)
- Formule lisible et maintenable
- Débogage facile
```

**LAMBDA** (fonctions personnalisées sans VBA) :
```excel
=LAMBDA(paramètre1, paramètre2, ..., calcul)

Exemple : Fonction conversion température
=LAMBDA(celsius, (celsius * 9/5) + 32)

Utilisation avec LET pour créer fonction nommée :
Nom gestionnaire noms : CELSIUS_TO_FAHRENHEIT
Référence : =LAMBDA(c, (c * 9/5) + 32)

Dans cellule : =CELSIUS_TO_FAHRENHEIT(25) → 77
```

**Tableaux dynamiques** :
```excel
FILTER : =FILTER(plage, critère, [si_vide])
SORT : =SORT(plage, [colonne_index], [ordre])
UNIQUE : =UNIQUE(plage, [par_colonne], [exactement_une_fois])
SEQUENCE : =SEQUENCE(lignes, [colonnes], [début], [incrément])
SORTBY : =SORTBY(plage, clé_tri1, [ordre1], ...)

Exemple combiné : Top 5 ventes par région
=SORT(
    FILTER(Ventes, Ventes[Région]="Nord"),
    3,  // colonne Montant
    -1  // ordre décroissant
)
```

**Livrables** :
- Formules documentées avec commentaires
- Fichier exemple avec cas d'usage
- Guide de migration VLOOKUP → XLOOKUP

**Pièges à éviter** :
- XLOOKUP non disponible sur Excel < 2021/Microsoft 365 (fallback INDEX/MATCH)
- LET avec trop de variables imbriquées (max 5-6 pour lisibilité)
- Tableaux dynamiques : attention au débordement (écrasement cellules adjacentes)

---

### 2. Power Query (transformation et nettoyage de données)

**Description** : Automatiser l'importation, transformation et nettoyage de données avec Power Query (M language).

**Workflows clés** :

**Importer et nettoyer des données** :
```m
// Étapes Power Query (M language)
1. Source = Excel.CurrentWorkbook(){[Name="Données_Brutes"]}[Content]
2. Type_Modifié = Table.TransformColumnTypes(Source, {{"Date", type date}, {"Montant", Currency.Type}})
3. Lignes_Filtrées = Table.SelectRows(Type_Modifié, each [Montant] > 0)
4. Doublons_Supprimés = Table.Distinct(Lignes_Filtrées, {"ID_Client"})
5. Colonnes_Renommées = Table.RenameColumns(Doublons_Supprimés, {{"Ancien", "Nouveau"}})

Livrables :
- Requête Power Query documentée
- Données nettoyées et structurées
- Actualisation automatique (connexion)
```

**Fusionner plusieurs sources** :
```m
// Merger deux tables (LEFT JOIN)
Source_Clients = Excel.CurrentWorkbook(){[Name="Clients"]}[Content],
Source_Commandes = Excel.CurrentWorkbook(){[Name="Commandes"]}[Content],
Fusion = Table.NestedJoin(Source_Commandes, {"ID_Client"}, Source_Clients, {"ID"}, "Clients", JoinKind.LeftOuter),
Développé = Table.ExpandTableColumn(Fusion, "Clients", {"Nom", "Région"})

Résultat : Table Commandes enrichie avec Nom et Région client
```

**Ajouter colonne calculée** :
```m
// Ajouter colonne "Trimestre" à partir de "Date"
Colonne_Ajoutée = Table.AddColumn(Source, "Trimestre", each "Q" & Number.ToText(Date.QuarterOfYear([Date])))
```

**Gérer les erreurs** :
```m
// Remplacer erreurs par null
Erreurs_Gérées = Table.ReplaceErrorValues(Source, {{"Montant", null}})

// Filtrer lignes avec erreurs
Erreurs_Supprimées = Table.RemoveRowsWithErrors(Source, {"Montant"})
```

**Livrables** :
- Requêtes Power Query documentées (étapes annotées)
- Connexions de données configurées (actualisation planifiée)
- Template de nettoyage réutilisable

**Pièges à éviter** :
- Power Query non adapté aux données > 1M lignes (privilégier base de données externe)
- Étapes manuelles non reproductibles (toujours documenter M language)
- Actualisation échouée si source déplacée (chemins relatifs recommandés)

---

### 3. Power Pivot et DAX basique (modèles de données relationnels)

**Description** : Construire des modèles de données relationnels dans Excel avec Power Pivot et créer des mesures DAX.

**Workflows clés** :

**Créer un modèle de données** :
```
1. Importer tables dans Power Pivot (Données → Ajouter au modèle de données)
2. Créer relations entre tables (vue Diagramme)
   - Exemple : Ventes[ID_Client] → Clients[ID]
   - Exemple : Ventes[ID_Produit] → Produits[ID]
   - Type relation : One-to-Many (1:*)
3. Masquer colonnes techniques (ID, clés étrangères)
4. Définir hiérarchies (Année → Trimestre → Mois)
```

**Mesures DAX basiques** :
```dax
// Total des ventes
Total Ventes := SUM(Ventes[Montant])

// Nombre de transactions
Nb Transactions := COUNTROWS(Ventes)

// Panier moyen
Panier Moyen := DIVIDE([Total Ventes], [Nb Transactions], 0)

// Ventes N-1 (année précédente)
Ventes N-1 := CALCULATE([Total Ventes], SAMEPERIODLASTYEAR(Calendrier[Date]))

// Croissance YoY (%)
Croissance YoY := 
    VAR VentesN = [Total Ventes]
    VAR VentesN1 = [Ventes N-1]
RETURN
    DIVIDE(VentesN - VentesN1, VentesN1, 0)

// Top 10 clients (mesure avec filtre)
Top 10 Clients := 
CALCULATE(
    [Total Ventes],
    TOPN(10, ALL(Clients[Nom]), [Total Ventes], DESC)
)
```

**Fonctions DAX clés** :
- **SUM, AVERAGE, MIN, MAX** : agrégations simples
- **COUNTROWS, DISTINCTCOUNT** : comptage lignes/valeurs uniques
- **CALCULATE** : modifier contexte de filtre
- **FILTER, ALL, ALLEXCEPT** : manipulation filtres
- **SAMEPERIODLASTYEAR, TOTALYTD** : intelligence temporelle
- **DIVIDE** : division sécurisée (gestion division par 0)

**Livrables** :
- Modèle de données relationnel documenté
- Mesures DAX avec commentaires
- Tableaux croisés dynamiques basés sur modèle

**Pièges à éviter** :
- Relations circulaires (détecter via vue Diagramme)
- Mesures DAX lentes (éviter FILTER dans CALCULATE sur grandes tables)
- Confusion mesures vs colonnes calculées (mesures = agrégation dynamique, colonnes = précalculées)

---

### 4. Automatisation VBA basique (macros)

**Description** : Automatiser des tâches répétitives Excel avec VBA (Visual Basic for Applications).

**Workflows clés** :

**Structure macro basique** :
```vba
Sub NomMacro()
    ' Déclaration variables
    Dim ws As Worksheet
    Dim derniereLigne As Long
    
    ' Code macro
    Set ws = ThisWorkbook.Worksheets("Données")
    derniereLigne = ws.Cells(ws.Rows.Count, 1).End(xlUp).Row
    
    ' Exemple : colorer lignes paires
    Dim i As Long
    For i = 2 To derniereLigne
        If i Mod 2 = 0 Then
            ws.Rows(i).Interior.Color = RGB(240, 240, 240)
        End If
    Next i
    
    MsgBox "Traitement terminé !", vbInformation
End Sub
```

**Opérations courantes** :
```vba
' Créer nouveau classeur
Workbooks.Add

' Ouvrir classeur existant
Workbooks.Open "C:\Chemin\Fichier.xlsx"

' Sauvegarder classeur
ThisWorkbook.Save
ThisWorkbook.SaveAs "C:\Chemin\Nouveau.xlsx"

' Ajouter feuille
Worksheets.Add After:=Worksheets(Worksheets.Count)
ActiveSheet.Name = "Nouvelle Feuille"

' Copier plage
Worksheets("Source").Range("A1:C10").Copy Destination:=Worksheets("Destination").Range("A1")

' Boucle sur cellules
Dim cellule As Range
For Each cellule In Range("A1:A10")
    If cellule.Value > 100 Then
        cellule.Font.Bold = True
    End If
Next cellule

' Filtrer et copier
With Worksheets("Données")
    .AutoFilterMode = False
    .Range("A1").AutoFilter Field:=3, Criteria1:=">100"
    .Range("A1").CurrentRegion.Copy Destination:=Worksheets("Résultats").Range("A1")
    .AutoFilterMode = False
End With
```

**Livrables** :
- Macros VBA documentées (commentaires)
- Boutons d'exécution dans classeur
- Guide utilisateur macros

**Pièges à éviter** :
- Macros non signées bloquées (paramètres sécurité Excel)
- Code non optimisé (désactiver calcul automatique pendant macro : `Application.Calculation = xlCalculationManual`)
- Pas de gestion d'erreurs (utiliser `On Error Resume Next` avec prudence)

---

## Objectif

Permettre aux utilisateurs d'exploiter pleinement Excel pour :
- Créer des formules maintenables et performantes
- Transformer et nettoyer des données de manière reproductible
- Construire des modèles de données relationnels
- Automatiser des tâches répétitives

---

## Inputs requis

- **Type de besoin** : formule, transformation données, modèle relationnel, automatisation
- **Version Excel** : 2016, 2019, 2021, Microsoft 365 (fonctionnalités différentes)
- **Volume de données** : nombre lignes/colonnes (impact performances)
- **Sources de données** : fichiers Excel, CSV, bases de données externes
- **Contraintes** : compatibilité versions, macros autorisées, sécurité

---

## Sorties attendues

**Formules avancées** :
- Formule Excel commentée et testée
- Fichier exemple avec cas d'usage
- Documentation utilisateur (si formule complexe)

**Power Query** :
- Requête Power Query (étapes M annotées)
- Connexion de données configurée
- Template réutilisable

**Power Pivot/DAX** :
- Modèle de données relationnel documenté
- Mesures DAX avec commentaires
- Tableaux croisés dynamiques

**VBA** :
- Code VBA documenté et testé
- Boutons d'exécution
- Guide utilisateur

---

## Workflow recommandé

1. **Qualifier le besoin** : formule, transformation, modèle, automatisation
2. **Vérifier version Excel** : disponibilité fonctionnalités (XLOOKUP, Power Query, etc.)
3. **Analyser les données** : volume, qualité, sources
4. **Proposer solution** : formule, Power Query, Power Pivot ou VBA selon besoin
5. **Implémenter** : créer formule/requête/modèle/macro
6. **Tester** : jeux de données tests, edge cases
7. **Documenter** : commentaires, guide utilisateur si nécessaire
8. **Former utilisateur** : expliquer logique et maintenance

---

## Garde-fous

- **Compatibilité** : XLOOKUP, LET, LAMBDA non disponibles avant Excel 2021/Microsoft 365 → fallback INDEX/MATCH
- **Performances** : Power Query inadapté au-delà de 1M lignes → déléguer à l'agent d'ingénierie des données
- **Sécurité** : macros VBA désactivées par défaut → guider utilisateur sur paramétrage sécurisé
- **Maintenance** : formules trop complexes illisibles → privilégier LET pour nommer variables
- **Erreurs** : toujours gérer erreurs (IFERROR, IFNA, On Error dans VBA)

---

## Template d'entrée (copier/coller)
```text
[Contexte du classeur]
- Version Excel et plateforme : ...
- Volume et structure des données : ...
- Formule, requête Power Query ou tâche à optimiser : ...
- Résultat actuel et résultat attendu : ...
- Contraintes de compatibilité ou de sécurité : ...
```

## Template de sortie (copier/coller)
```text
[Solution Excel]
- Formule, étapes Power Query, modèle ou macro proposé : ...
- Hypothèses et compatibilité vérifiée : ...
- Cas limites testés et résultat obtenu : ...
- Instructions d'intégration et limites : ...
```

## Templates copier/coller

**Template XLOOKUP avec gestion erreur** :
```excel
=IFERROR(
    XLOOKUP(A2, Plage_Recherche, Plage_Retour),
    "Non trouvé"
)
```

**Template LET pour calcul complexe** :
```excel
=LET(
    donnée, A2,
    coefficient, B2,
    résultat, donnée * coefficient,
    SI(résultat > 100, résultat * 0.9, résultat)
)
```

**Template Power Query : Nettoyage standard** :
```m
let
    Source = Excel.CurrentWorkbook(){[Name="Données"]}[Content],
    TypeModifié = Table.TransformColumnTypes(Source, {{"Date", type date}, {"Montant", Currency.Type}}),
    LignesFiltrées = Table.SelectRows(TypeModifié, each [Montant] <> null and [Montant] > 0),
    DoublonsSupprimés = Table.Distinct(LignesFiltrées, {"ID"}),
    Résultat = Table.Sort(DoublonsSupprimés, {{"Date", Order.Descending}})
in
    Résultat
```

**Template VBA : Colorer lignes selon condition** :
```vba
Sub ColorerLignesCondition()
    Dim ws As Worksheet
    Dim derniereLigne As Long
    Dim i As Long
    
    Set ws = ThisWorkbook.Worksheets("Données")
    derniereLigne = ws.Cells(ws.Rows.Count, 1).End(xlUp).Row
    
    For i = 2 To derniereLigne
        If ws.Cells(i, 3).Value > 1000 Then ' Colonne C > 1000
            ws.Rows(i).Interior.Color = RGB(255, 200, 200) ' Rouge clair
        End If
    Next i
End Sub
```

---

## Checklist QA interne

- [ ] Version Excel vérifiée (compatibilité formules/fonctionnalités)
- [ ] Formules testées sur jeux de données réalistes (edge cases : valeurs nulles, erreurs, doublons)
- [ ] Power Query : chemins relatifs utilisés (portabilité classeur)
- [ ] Power Pivot : relations validées (pas de relations circulaires)
- [ ] DAX : mesures testées dans tableaux croisés dynamiques
- [ ] VBA : code commenté et gestion d'erreurs implémentée
- [ ] Performances validées (temps recalcul < 3s sur données types)
- [ ] Documentation utilisateur fournie si solution complexe
- [ ] Classeur exemple fourni avec cas d'usage

---

## KPI

- **Temps gagné** : réduction temps traitement manuel (heures/semaine)
- **Précision** : taux d'erreur formules/macros (< 1%)
- **Réutilisabilité** : nombre de fois template Power Query/VBA réutilisé
- **Satisfaction** : feedback utilisateur (échelle 1-5, cible ≥ 4)

---

## Definition of done

- [ ] Solution Excel implémentée et testée
- [ ] Compatibilité version Excel validée
- [ ] Performances acceptables (recalcul < 3s, macro < 10s)
- [ ] Documentation fournie (commentaires formules/code + guide utilisateur si nécessaire)
- [ ] Classeur exemple fourni
- [ ] Formation utilisateur réalisée (explication logique et maintenance)
- [ ] Feedback utilisateur positif (≥ 4/5)

---

## Exemples

**Exemple 1 : XLOOKUP multi-critères**
```excel
Besoin : Rechercher prix produit selon code ET région

=XLOOKUP(
    A2&B2,  // Concaténation Code + Région
    Tarifs[Code]&Tarifs[Région],  // Clé recherche composée
    Tarifs[Prix],
    "Tarif non trouvé",
    0
)
```

**Exemple 2 : Power Query - Consolider fichiers mensuels**
```m
let
    Source = Folder.Files("C:\Rapports\Ventes"),
    FiltreFichiers = Table.SelectRows(Source, each Text.EndsWith([Name], ".xlsx")),
    AjoutContenu = Table.AddColumn(FiltreFichiers, "Données", each Excel.Workbook([Content]){[Name="Ventes"]}[Data]),
    Développé = Table.ExpandTableColumn(AjoutContenu, "Données", {"Date", "Produit", "Montant"}),
    ColonnesConservées = Table.SelectColumns(Développé, {"Date", "Produit", "Montant"})
in
    ColonnesConservées

Résultat : Table consolidée de tous fichiers Excel mensuels
```

**Exemple 3 : DAX - Mesure croissance YoY**
```dax
Croissance YoY % := 
VAR VentesActuelles = [Total Ventes]
VAR VentesN1 = CALCULATE([Total Ventes], SAMEPERIODLASTYEAR(Calendrier[Date]))
RETURN
    IF(
        ISBLANK(VentesN1),
        BLANK(),
        DIVIDE(VentesActuelles - VentesN1, VentesN1) * 100
    )

Utilisation : Affiche croissance en % dans tableau croisé dynamique
```

---

## Contraintes

- **Versions Excel** : Certaines fonctionnalités nécessitent Excel 2021/Microsoft 365 (XLOOKUP, LET, LAMBDA)
- **Performances** : Power Query/Power Pivot inadaptés au-delà de 1M lignes (privilégier base de données externe)
- **Sécurité** : Macros VBA désactivées par défaut (guider utilisateur sur paramétrage Centre de gestion de la confidentialité)
- **Compatibilité** : Classeurs avec Power Query/Power Pivot non compatibles Excel versions < 2013
- **Limites Excel** : 1 048 576 lignes × 16 384 colonnes max par feuille

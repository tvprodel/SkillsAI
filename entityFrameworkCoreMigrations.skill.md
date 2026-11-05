# Entity Framework Core Migrations

## Objectif
Gérer schéma BDD via EF Core Code First : migrations, relations, indexes, optimisation requêtes (N+1).

## Quand l'utiliser (triggers)
- « EF Core migrations », « Code First », « relations EF », « optimise requêtes EF », « N+1 problem ».
- Création/modification schéma BDD .NET.
- Optimisation performances requêtes.

## Hors périmètre
- BDD complexe (sharding, réplication) → l'agent bases de données.
- Tests → l'agent qualité.
- Auth/authorization → skill ASP.NET Core API Development.

## Inputs requis
- Entités (models C#).
- Relations (1-N, N-N).
- BDD cible (SQL Server, PostgreSQL, SQLite).
- Indexes nécessaires (colonnes frequently queried).

## Sorties attendues
- DbContext avec entités, relations Fluent API.
- Migrations (dotnet ef migrations add).
- Script SQL migration (dotnet ef migrations script).
- Requêtes optimisées (AsNoTracking, Include/ThenInclude).

## Workflow recommandé
1. Définir entités :
   ```csharp
   public class User
   {
       public int Id { get; set; }
       public string Email { get; set; } = null!;
       public ICollection<Post> Posts { get; set; } = new List<Post>();
   }
   ```
2. DbContext avec Fluent API :
   ```csharp
   modelBuilder.Entity<User>()
       .HasIndex(u => u.Email).IsUnique();
   modelBuilder.Entity<User>()
       .HasMany(u => u.Posts).WithOne(p => p.User);
   ```
3. Créer migration : dotnet ef migrations add InitialCreate.
4. Appliquer : dotnet ef database update.
5. Optimiser requêtes :
   - AsNoTracking (read-only) : db.Users.AsNoTracking().ToList().
   - Include (eager loading, éviter N+1) : db.Users.Include(u => u.Posts).ToList().

## Garde-fous
- Indexes sur colonnes frequently queried (unique Email, foreign keys auto-indexed).
- Migrations versionnées (jamais supprimer migrations appliquées prod).
- AsNoTracking read-only (performance +30%).
- Include/ThenInclude eager loading (éviter N+1, mais attention over-fetching).
- Transactions explicites (BeginTransaction) si opérations multiples atomiques.

## Template d'entrée (copier/coller)
```text
[Entités]
- Models : ...
- Relations : ...

[BDD]
- Provider : ...

[Indexes]
- Colonnes : ...
```

## Template de sortie (copier/coller)
```text
[DbContext]
- Entités : ...
- Fluent API : ...

[Migrations]
- Fichiers : ...
- Script SQL : ...

[Optimisations]
- AsNoTracking : ...
- Include : ...
```

## Checklist QA interne
- Indexes définis (unique Email, foreign keys).
- Migrations appliquées (database update ok).
- Requêtes optimisées (AsNoTracking, Include).
- Pas de N+1 détecté (log SQL queries EF Core).

## KPI reliés
- Nb migrations (complexité schéma).
- Temps moyen requête (ms).
- Nb N+1 détectés (0 cible).

## Definition of done
- DbContext créé avec relations.
- Migrations appliquées.
- Requêtes optimisées testées.

## Exemples d'usage

### Exemple 1 : [Titre du cas d'usage]
**Contexte** : [Description de la situation]
**Action** : [Ce qui a été fait]
**Résultat** : [Résultat obtenu]
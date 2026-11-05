# ASP.NET Core API Development

## Objectif
Développer API REST ASP.NET Core (controllers, Minimal APIs, validation, auth JWT, Swagger).

## Quand l'utiliser (triggers)
- « API REST .NET », « ASP.NET Core controllers », « Minimal APIs », « Swagger OpenAPI ».
- Création API backend .NET.
- Refonte API existante (migration .NET Framework → .NET 6+).

## Hors périmètre
- Frontend Blazor → skill Blazor Component Design.
- BDD migrations → skill Entity Framework Core Migrations.
- Tests → l'agent qualité.

## Inputs requis
- Endpoints API (ressources, verbes HTTP).
- Authentification (JWT, OAuth, Identity).
- Validation entrées (DTOs, FluentValidation ou DataAnnotations).
- Swagger/OpenAPI requis.

## Sorties attendues
- Controllers ou Minimal APIs avec routes, validation, auth.
- Swagger UI accessible (/swagger).
- DTOs documentés (XML comments pour Swagger).

## Workflow recommandé
1. Créer projet : dotnet new webapi -n MyApi.
2. Choix pattern :
   - Controllers (CRUD complexes, plusieurs endpoints par ressource) :
     ```csharp
     [ApiController]
     [Route("api/[controller]")]
     public class UsersController : ControllerBase
     {
         [HttpGet]
         public IActionResult GetAll() => Ok(...);
         
         [HttpPost]
         public IActionResult Create([FromBody] CreateUserDto dto) => ...
     }
     ```
   - Minimal APIs (micro-services simples) :
     ```csharp
     app.MapGet("/users", () => ...);
     app.MapPost("/users", (CreateUserDto dto) => ...);
     ```
3. Validation (FluentValidation ou DataAnnotations) :
   ```csharp
   public record CreateUserDto([Required] string Email, [MinLength(8)] string Password);
   ```
4. Auth JWT :
   ```csharp
   builder.Services.AddAuthentication(JwtBearerDefaults.AuthenticationScheme)
       .AddJwtBearer(options => { options.TokenValidationParameters = ...; });
   app.UseAuthentication();
   app.UseAuthorization();
   ```
5. Swagger : builder.Services.AddEndpointsApiExplorer(); builder.Services.AddSwaggerGen();
6. Tester : dotnet run, naviguer /swagger, tester endpoints.

## Garde-fous
- DTOs séparés (ne jamais exposer entités EF Core directement).
- Validation entrées (FluentValidation preferred, ou DataAnnotations).
- Auth JWT : secrets env vars (appsettings.json + User Secrets dev, Azure Key Vault prod).
- CORS restrictif (pas AllowAnyOrigin prod).
- HTTPS enforced (app.UseHttpsRedirection()).

## Template d'entrée (copier/coller)
```text
[API]
- Ressources : ...
- Endpoints : ...

[Auth]
- Type : ...

[Validation]
- DTOs : ...
```

## Template de sortie (copier/coller)
```text
[Code]
- Controllers/Minimal APIs : ...
- DTOs : ...

[Swagger]
- URL : /swagger

[Auth]
- JWT configured : ...
```

## Checklist QA interne
- DTOs séparés entités.
- Validation entrées (FluentValidation/DataAnnotations).
- JWT auth configuré (secrets env vars).
- Swagger UI accessible.
- HTTPS enforced.

## KPI reliés
- Nb endpoints API.
- Couverture validation (% endpoints avec validation).
- Temps réponse moyen API (ms).

## Definition of done
- API créée et testée.
- Swagger UI accessible.
- Auth JWT configuré.

## Exemples d'usage

### Exemple 1 : [Titre du cas d'usage]
**Contexte** : [Description de la situation]
**Action** : [Ce qui a été fait]
**Résultat** : [Résultat obtenu]
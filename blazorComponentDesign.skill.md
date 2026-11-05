# Blazor Component Design

## Objectif
Concevoir composants Blazor (Server/WASM) réutilisables avec Composition API, state management Pinia-like, interop JavaScript.

## Quand l'utiliser (triggers)
- « Blazor composants », « Blazor Server », « Blazor WASM », « state management Blazor », « JavaScript interop ».
- Développement frontend .NET.
- Migration app MVC → Blazor.

## Hors périmètre
- Backend API → skill ASP.NET Core API Development.
- BDD EF Core → skill Entity Framework Core Migrations.
- CSS/design → l'agent frontend (collaboration).

## Inputs requis
- Composants à créer (UI, logique).
- State management (local component state, shared state service).
- Interop JavaScript si nécessaire (libraries JS tierces).
- Blazor mode (Server vs WASM).

## Sorties attendues
- Composants .razor avec @code, parameters, events.
- State service si shared state.
- JavaScript interop si nécessaire (IJSRuntime).

## Workflow recommandé
1. Créer composant :
   ```razor
   @page "/counter"
   <h3>Counter: @currentCount</h3>
   <button @onclick="IncrementCount">Increment</button>
   
   @code {
       private int currentCount = 0;
       void IncrementCount() => currentCount++;
   }
   ```
2. Parameters et EventCallback :
   ```razor
   <ChildComponent Value="@parentValue" OnValueChanged="HandleChange" />
   
   @code {
       [Parameter] public int Value { get; set; }
       [Parameter] public EventCallback<int> OnValueChanged { get; set; }
   }
   ```
3. State management (service singleton) :
   ```csharp
   builder.Services.AddSingleton<AppState>();
   
   public class AppState
   {
       public string User { get; set; } = "";
       public event Action? OnChange;
       public void SetUser(string user) { User = user; OnChange?.Invoke(); }
   }
   ```
4. JavaScript interop :
   ```csharp
   @inject IJSRuntime JS
   await JS.InvokeVoidAsync("alert", "Hello from Blazor");
   ```

## Garde-fous
- Components immutables (Parameters immutable, EventCallback pour changements).
- State service events (OnChange event pour notifier composants subscribers).
- JavaScript interop minimal (préférer composants Blazor natifs si possible).
- Blazor WASM payload size (lazy loading assemblies, tree shaking).

## Template d'entrée (copier/coller)
```text
[Composants]
- Liste : ...
- State : local/shared

[Interop JS]
- Libraries : ...

[Mode]
- Server/WASM : ...
```

## Template de sortie (copier/coller)
```text
[Composants]
- Fichiers .razor : ...
- Parameters : ...

[State]
- Service : ...
- Events : ...

[JavaScript interop]
- Calls : ...
```

## Checklist QA interne
- Components immutables (Parameters).
- EventCallback pour communication parent-child.
- State service si shared state (events OnChange).
- JavaScript interop minimal.

## KPI reliés
- Nb composants réutilisables.
- Payload size WASM (MB).
- Temps initial load (secondes).

## Definition of done
- Composants créés et testés.
- State management implémenté.
- JavaScript interop validé si nécessaire.

## Exemples d'usage

### Exemple 1 : [Titre du cas d'usage]
**Contexte** : [Description de la situation]
**Action** : [Ce qui a été fait]
**Résultat** : [Résultat obtenu]
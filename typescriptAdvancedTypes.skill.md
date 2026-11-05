# TypeScript Advanced Types

## Objectif
Maîtriser types avancés TypeScript (generics, utility types, conditional types, type guards) pour code type-safe et maintenable.

## Quand l'utiliser (triggers)
- « TypeScript types avancés », « generics », « utility types », « conditional types », « type guards », « infer ».
- Code TypeScript complexe nécessitant types réutilisables.
- Refacto JavaScript → TypeScript strict.

## Hors périmètre
- React/Vue/Angular spécifiques → skill React Hooks Patterns (React) ou typescriptJavascript (general).
- Backend Node.js → skill NestJS Architecture (si NestJS) ou typescriptJavascript (general).
- Tests → l'agent qualité.

## Inputs requis
- Code existant à typer (JavaScript → TypeScript).
- Besoins types réutilisables (fonctions génériques, DTOs).
- Strict mode requis (tsconfig.json strict: true).

## Sorties attendues
- Code TypeScript avec types avancés (generics, utility types, conditional types).
- Type guards (is, as const).
- tsconfig.json strict mode.

## Workflow recommandé
1. **Generics** (réutilisabilité) :
   ```typescript
   function identity<T>(arg: T): T { return arg; }
   const result = identity<string>("hello");  // type inferred: string
   
   interface ApiResponse<T> {
     data: T;
     status: number;
   }
   const userResponse: ApiResponse<User> = { data: { id: 1 }, status: 200 };
   ```
2. **Utility types** (transformation types) :
   ```typescript
   interface User { id: number; name: string; email: string; }
   type PartialUser = Partial<User>;  // all props optional
   type RequiredUser = Required<User>;  // all props required
   type UserWithoutEmail = Omit<User, 'email'>;  // exclude email
   type UserIdName = Pick<User, 'id' | 'name'>;  // pick only id, name
   type ReadonlyUser = Readonly<User>;  // all props readonly
   ```
3. **Conditional types** (logique types) :
   ```typescript
   type IsString<T> = T extends string ? true : false;
   type Result1 = IsString<string>;  // true
   type Result2 = IsString<number>;  // false
   
   type Unpacked<T> = T extends Promise<infer U> ? U : T;
   type PromiseString = Unpacked<Promise<string>>;  // string
   ```
4. **Type guards** (narrowing runtime) :
   ```typescript
   function isString(value: unknown): value is string {
     return typeof value === 'string';
   }
   if (isString(value)) {
     console.log(value.toUpperCase());  // safe, value narrowed to string
   }
   ```
5. **as const** (literal types) :
   ```typescript
   const colors = ['red', 'green', 'blue'] as const;
   type Color = typeof colors[number];  // 'red' | 'green' | 'blue'
   ```

## Garde-fous
- tsconfig.json strict mode (strict: true, noImplicitAny, strictNullChecks).
- Éviter any (unknown preferred + type guards).
- Generics contraints (T extends SomeType pour validation).
- Type guards explicites (is keyword).

## Template d'entrée (copier/coller)
```text
[Code]
- À typer : ...
- Besoins generics : ...

[Strict mode]
- tsconfig : ...
```

## Template de sortie (copier/coller)
```text
[Code TypeScript]
- Generics : ...
- Utility types : ...
- Conditional types : ...
- Type guards : ...

[tsconfig.json]
- strict: true
```

## Checklist QA interne
- tsconfig.json strict mode.
- Pas de any (unknown + guards).
- Generics utilisés (réutilisabilité).
- Type guards explicites.
- Utility types (Partial, Pick, Omit).

## KPI reliés
- Taux type-safety (% code without any).
- Nb erreurs compile-time détectées (types).
- Temps refacto JS → TS (heures).

## Definition of done
- Code TypeScript types avancés.
- strict mode enabled.
- Type guards validés.

## Exemples d'usage

### Exemple 1 : [Titre du cas d'usage]
**Contexte** : [Description de la situation]
**Action** : [Ce qui a été fait]
**Résultat** : [Résultat obtenu]
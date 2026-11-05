# React Hooks Patterns

## Objectif
Maîtriser React hooks (useState, useEffect, useContext, custom hooks, useCallback, useMemo) pour composants fonctionnels optimisés.

## Quand l'utiliser (triggers)
- « React hooks », « useState », « useEffect », « custom hooks », « useCallback », « useMemo », « performance React ».
- Développement composants React fonctionnels.
- Refacto class components → functional components.

## Hors périmètre
- Backend Node.js → skill NestJS Architecture ou typescriptJavascript (backend).
- Tests → l'agent qualité.
- CSS/design → l'agent frontend.

## Inputs requis
- Composants à créer (UI, logique).
- State management (local component, Context API, external Zustand/Jotai).
- Performance requirements (memoization nécessaire).

## Sorties attendues
- Composants React fonctionnels avec hooks.
- Custom hooks réutilisables.
- Optimisations performance (useCallback, useMemo, React.memo).

## Workflow recommandé
1. **useState** (state local) :
   ```typescript
   const [count, setCount] = useState(0);
   const increment = () => setCount(prev => prev + 1);  // updater function
   ```
2. **useEffect** (side effects) :
   ```typescript
   useEffect(() => {
     // fetch data, subscribe
     const subscription = subscribe();
     return () => subscription.unsubscribe();  // cleanup
   }, [dependency]);  // re-run if dependency changes
   ```
3. **useContext** (shared state) :
   ```typescript
   const ThemeContext = createContext<'light' | 'dark'>('light');
   const theme = useContext(ThemeContext);
   ```
4. **Custom hooks** (réutilisabilité) :
   ```typescript
   function useFetch<T>(url: string) {
     const [data, setData] = useState<T | null>(null);
     const [loading, setLoading] = useState(true);
     useEffect(() => {
       fetch(url).then(res => res.json()).then(setData).finally(() => setLoading(false));
     }, [url]);
     return { data, loading };
   }
   const { data, loading } = useFetch<User>('/api/user');
   ```
5. **Performance** (memoization) :
   ```typescript
   const memoizedValue = useMemo(() => computeExpensive(a, b), [a, b]);
   const memoizedCallback = useCallback(() => doSomething(a), [a]);
   const MemoizedComponent = React.memo(Component);
   ```

## Garde-fous
- useEffect dependencies exhaustives (ESLint react-hooks/exhaustive-deps).
- Cleanup useEffect (unsubscribe, clearTimeout).
- useCallback/useMemo seulement si perf issue (pas prématuré).
- Custom hooks prefix use (convention).
- Éviter state mutations (setState(prev => ...) immutabilité).

## Template d'entrée (copier/coller)
```text
[Composants]
- Liste : ...
- State : local/context

[Performance]
- Memoization nécessaire : ...
```

## Template de sortie (copier/coller)
```text
[Composants]
- Hooks utilisés : ...
- Custom hooks : ...

[Performance]
- useMemo : ...
- useCallback : ...
- React.memo : ...
```

## Checklist QA interne
- useEffect dependencies correctes.
- Cleanup useEffect (si souscriptions).
- Custom hooks prefix use.
- Memoization si perf issue.
- Pas state mutations.

## KPI reliés
- Nb re-renders (React DevTools Profiler).
- Temps render (ms).
- Nb custom hooks réutilisables.

## Definition of done
- Composants React hooks créés.
- Custom hooks validés.
- Performance optimisée si nécessaire.

## Exemples d'usage

### Exemple 1 : [Titre du cas d'usage]
**Contexte** : [Description de la situation]
**Action** : [Ce qui a été fait]
**Résultat** : [Résultat obtenu]
---
name: "react-best-practices"
displayName: "React Best Practices"
description: "Comprehensive performance optimization guide for React and Next.js applications from Vercel Engineering. Contains 45+ rules across 8 categories, prioritized by impact to guide code generation and refactoring."
keywords: ["react", "nextjs", "performance", "optimization", "vercel", "bundle", "rendering", "server-components"]
author: "Vercel Engineering"
---

# React Best Practices

## Overview

Comprehensive performance optimization guide for React and Next.js applications, maintained by Vercel Engineering. This power provides 45+ actionable rules across 8 categories, each prioritized by performance impact from CRITICAL (eliminating waterfalls, reducing bundle size) to LOW (incremental improvements).

Each rule includes:
- Clear explanation of why it matters
- Incorrect code examples with explanations
- Correct code examples with explanations
- Real-world impact metrics
- Additional context and references

**Use this power when:**
- Writing new React components or Next.js pages
- Implementing data fetching (client or server-side)
- Reviewing code for performance issues
- Refactoring existing React/Next.js code
- Optimizing bundle size or load times
- Addressing performance bottlenecks

## Rule Categories by Priority

The rules are organized into 8 categories, prioritized by their performance impact:

| Priority | Category | Impact | Rule Count |
|----------|----------|--------|------------|
| 1 | Eliminating Waterfalls | CRITICAL | 5 rules |
| 2 | Bundle Size Optimization | CRITICAL | 5 rules |
| 3 | Server-Side Performance | HIGH | 5 rules |
| 4 | Client-Side Data Fetching | MEDIUM-HIGH | 4 rules |
| 5 | Re-render Optimization | MEDIUM | 7 rules |
| 6 | Rendering Performance | MEDIUM | 7 rules |
| 7 | JavaScript Performance | LOW-MEDIUM | 12 rules |
| 8 | Advanced Patterns | LOW | 2 rules |

## Quick Reference

### 1. Eliminating Waterfalls (CRITICAL)

Waterfalls are the #1 performance killer. Each sequential await adds full network latency.

- **async-defer-await** - Move await into branches where actually used
- **async-parallel** - Use Promise.all() for independent operations
- **async-dependencies** - Use better-all for partial dependencies
- **async-api-routes** - Start promises early, await late in API routes
- **async-suspense-boundaries** - Use Suspense to stream content

### 2. Bundle Size Optimization (CRITICAL)

Reducing initial bundle size improves Time to Interactive and Largest Contentful Paint.

- **bundle-barrel-imports** - Import directly, avoid barrel files
- **bundle-dynamic-imports** - Use next/dynamic for heavy components
- **bundle-defer-third-party** - Load analytics/logging after hydration
- **bundle-conditional** - Load modules only when feature is activated
- **bundle-preload** - Preload on hover/focus for perceived speed

### 3. Server-Side Performance (HIGH)

Optimizing server-side rendering and data fetching eliminates server-side waterfalls.

- **server-cache-react** - Use React.cache() for per-request deduplication
- **server-cache-lru** - Use LRU cache for cross-request caching
- **server-serialization** - Minimize data passed to client components
- **server-parallel-fetching** - Restructure components to parallelize fetches
- **server-after-nonblocking** - Use after() for non-blocking operations

### 4. Client-Side Data Fetching (MEDIUM-HIGH)

Automatic deduplication and efficient data fetching patterns reduce redundant requests.

- **client-swr-dedup** - Use SWR for automatic request deduplication
- **client-event-listeners** - Deduplicate global event listeners
- **client-passive-event-listeners** - Use passive listeners for scroll performance
- **client-localstorage-schema** - Version and minimize localStorage data

### 5. Re-render Optimization (MEDIUM)

Minimize unnecessary re-renders to improve responsiveness.

- **rerender-defer-reads** - Don't subscribe to state only used in callbacks
- **rerender-memo** - Extract expensive work into memoized components
- **rerender-dependencies** - Use primitive dependencies in effects
- **rerender-derived-state** - Subscribe to derived booleans, not raw values
- **rerender-functional-setstate** - Use functional setState for stable callbacks
- **rerender-lazy-state-init** - Pass function to useState for expensive values
- **rerender-transitions** - Use startTransition for non-urgent updates

### 6. Rendering Performance (MEDIUM)

Optimize the rendering process itself.

- **rendering-animate-svg-wrapper** - Animate div wrapper, not SVG element
- **rendering-content-visibility** - Use content-visibility for long lists
- **rendering-hoist-jsx** - Extract static JSX outside components
- **rendering-svg-precision** - Reduce SVG coordinate precision
- **rendering-hydration-no-flicker** - Use inline script for client-only data
- **rendering-activity** - Use Activity component for show/hide
- **rendering-conditional-render** - Use ternary, not && for conditionals

### 7. JavaScript Performance (LOW-MEDIUM)

Micro-optimizations that add up in hot paths.

- **js-batch-dom-css** - Group CSS changes via classes or cssText
- **js-index-maps** - Build Map for repeated lookups
- **js-cache-property-access** - Cache object properties in loops
- **js-cache-function-results** - Cache function results in module-level Map
- **js-cache-storage** - Cache localStorage/sessionStorage reads
- **js-combine-iterations** - Combine multiple filter/map into one loop
- **js-length-check-first** - Check array length before expensive comparison
- **js-early-exit** - Return early from functions
- **js-hoist-regexp** - Hoist RegExp creation outside loops
- **js-min-max-loop** - Use loop for min/max instead of sort
- **js-set-map-lookups** - Use Set/Map for O(1) lookups
- **js-tosorted-immutable** - Use toSorted() for immutability

### 8. Advanced Patterns (LOW)

Advanced techniques for specific scenarios.

- **advanced-event-handler-refs** - Store event handlers in refs
- **advanced-use-latest** - useLatest for stable callback refs

## How to Use This Power

### For Code Review

When reviewing React/Next.js code, reference specific rules by their prefix:

```
"This component has a waterfall issue. See async-parallel for how to fix it."
"Consider bundle-barrel-imports - we're importing from the barrel file here."
"This could benefit from rerender-memo to avoid expensive recalculations."
```

### For Code Generation

When generating new code, apply rules proactively based on the scenario:

- **Data fetching**: Apply async-* and server-* rules
- **Component creation**: Apply rerender-* and rendering-* rules
- **Third-party libraries**: Apply bundle-* rules
- **Event handlers**: Apply client-* and advanced-* rules

### For Refactoring

Prioritize by impact:
1. Start with CRITICAL rules (async-*, bundle-*)
2. Move to HIGH rules (server-*)
3. Address MEDIUM rules (client-*, rerender-*, rendering-*)
4. Apply LOW rules in hot paths only (js-*, advanced-*)

## Available Steering Files

This power includes individual steering files for each rule, enabling efficient dynamic loading. Agents can load only the specific rules they need:

### Eliminating Waterfalls (CRITICAL)
- **async-defer-await.md** - Move await into branches where actually used
- **async-parallel.md** - Use Promise.all() for independent operations
- **async-dependencies.md** - Use better-all for partial dependencies
- **async-api-routes.md** - Start promises early, await late in API routes
- **async-suspense-boundaries.md** - Use Suspense to stream content

### Bundle Size Optimization (CRITICAL)
- **bundle-barrel-imports.md** - Import directly, avoid barrel files
- **bundle-dynamic-imports.md** - Use next/dynamic for heavy components
- **bundle-defer-third-party.md** - Load analytics/logging after hydration
- **bundle-conditional.md** - Load modules only when feature is activated
- **bundle-preload.md** - Preload on hover/focus for perceived speed

### Server-Side Performance (HIGH)
- **server-cache-react.md** - Use React.cache() for per-request deduplication
- **server-cache-lru.md** - Use LRU cache for cross-request caching
- **server-serialization.md** - Minimize data passed to client components
- **server-parallel-fetching.md** - Restructure components to parallelize fetches
- **server-after-nonblocking.md** - Use after() for non-blocking operations

### Client-Side Data Fetching (MEDIUM-HIGH)
- **client-swr-dedup.md** - Use SWR for automatic request deduplication
- **client-event-listeners.md** - Deduplicate global event listeners
- **client-passive-event-listeners.md** - Use passive listeners for scroll performance
- **client-localstorage-schema.md** - Version and minimize localStorage data

### Re-render Optimization (MEDIUM)
- **rerender-defer-reads.md** - Don't subscribe to state only used in callbacks
- **rerender-memo.md** - Extract expensive work into memoized components
- **rerender-dependencies.md** - Use primitive dependencies in effects
- **rerender-derived-state.md** - Subscribe to derived booleans, not raw values
- **rerender-functional-setstate.md** - Use functional setState for stable callbacks
- **rerender-lazy-state-init.md** - Pass function to useState for expensive values
- **rerender-transitions.md** - Use startTransition for non-urgent updates

### Rendering Performance (MEDIUM)
- **rendering-animate-svg-wrapper.md** - Animate div wrapper, not SVG element
- **rendering-content-visibility.md** - Use content-visibility for long lists
- **rendering-hoist-jsx.md** - Extract static JSX outside components
- **rendering-svg-precision.md** - Reduce SVG coordinate precision
- **rendering-hydration-no-flicker.md** - Use inline script for client-only data
- **rendering-activity.md** - Use Activity component for show/hide
- **rendering-conditional-render.md** - Use ternary, not && for conditionals

### JavaScript Performance (LOW-MEDIUM)
- **js-batch-dom-css.md** - Group CSS changes via classes or cssText
- **js-index-maps.md** - Build Map for repeated lookups
- **js-cache-property-access.md** - Cache object properties in loops
- **js-cache-function-results.md** - Cache function results in module-level Map
- **js-cache-storage.md** - Cache localStorage/sessionStorage reads
- **js-combine-iterations.md** - Combine multiple filter/map into one loop
- **js-length-check-first.md** - Check array length before expensive comparison
- **js-early-exit.md** - Return early from functions
- **js-hoist-regexp.md** - Hoist RegExp creation outside loops
- **js-min-max-loop.md** - Use loop for min/max instead of sort
- **js-set-map-lookups.md** - Use Set/Map for O(1) lookups
- **js-tosorted-immutable.md** - Use toSorted() for immutability

### Advanced Patterns (LOW)
- **advanced-event-handler-refs.md** - Store event handlers in refs
- **advanced-use-latest.md** - useLatest for stable callback refs

### Usage

To access a specific rule's detailed documentation:
```
Call action "readSteering" with powerName="react-best-practices", steeringFile="bundle-barrel-imports.md"
```

Each steering file contains:
- Detailed explanation of the rule
- Incorrect code example with explanation
- Correct code example with explanation
- Impact metrics and descriptions
- Additional context and references

## Best Practices for Using This Power

### 1. Prioritize by Impact

Focus on CRITICAL and HIGH impact rules first. These provide the largest performance gains:
- Eliminating waterfalls can yield 2-10× improvements
- Bundle optimization directly affects Time to Interactive
- Server-side optimizations reduce response times significantly

### 2. Measure Before and After

Always measure performance impact:
- Use Chrome DevTools Performance tab
- Monitor Core Web Vitals (LCP, FID, CLS)
- Track bundle sizes with webpack-bundle-analyzer
- Measure server response times

### 3. Apply Rules Contextually

Not every rule applies to every situation:
- **async-defer-await**: Only when branches are frequently skipped
- **bundle-dynamic-imports**: Only for components >50KB
- **rerender-memo**: Only when profiling shows expensive renders
- **js-***: Only in hot paths (loops, frequent calls)

### 4. Combine Related Rules

Many rules work together:
- **async-parallel** + **server-parallel-fetching** = maximum parallelism
- **bundle-barrel-imports** + **bundle-dynamic-imports** = optimal bundle size
- **rerender-memo** + **rerender-dependencies** = minimal re-renders

### 5. Use Next.js Built-in Optimizations

Next.js provides automatic optimizations:
- `fetch()` is automatically memoized per request
- `optimizePackageImports` handles barrel file optimization
- `after()` enables non-blocking operations
- Automatic code splitting for pages and routes

## Common Patterns

### Pattern: Optimizing Data Fetching

```typescript
// 1. Start with parallel fetching (async-parallel)
const [user, posts] = await Promise.all([
  fetchUser(),
  fetchPosts()
])

// 2. Add per-request caching (server-cache-react)
const getUser = cache(async () => fetchUser())

// 3. Add cross-request caching for hot data (server-cache-lru)
const lruCache = new LRUCache({ max: 1000, ttl: 5 * 60 * 1000 })

// 4. Minimize serialization (server-serialization)
return <Profile name={user.name} /> // not user={user}
```

### Pattern: Optimizing Bundle Size

```typescript
// 1. Fix barrel imports (bundle-barrel-imports)
import Check from 'lucide-react/dist/esm/icons/check'

// 2. Dynamic import heavy components (bundle-dynamic-imports)
const Editor = dynamic(() => import('./monaco-editor'), { ssr: false })

// 3. Defer third-party scripts (bundle-defer-third-party)
const Analytics = dynamic(() => import('@vercel/analytics'), { ssr: false })

// 4. Preload on intent (bundle-preload)
<button onMouseEnter={() => import('./editor')}>Open</button>
```

### Pattern: Optimizing Re-renders

```typescript
// 1. Memoize expensive components (rerender-memo)
const ExpensiveList = memo(({ items }) => {
  return items.map(item => <Item key={item.id} {...item} />)
})

// 2. Use primitive dependencies (rerender-dependencies)
useEffect(() => {
  // Use user.id instead of user object
}, [user.id])

// 3. Functional setState (rerender-functional-setstate)
const increment = useCallback(() => {
  setCount(c => c + 1) // Stable callback
}, [])
```

## Troubleshooting

### Issue: Performance Not Improving

**Symptoms:**
- Applied rules but no measurable improvement
- Metrics unchanged or worse

**Solutions:**
1. **Profile first**: Use Chrome DevTools to identify actual bottlenecks
2. **Measure impact**: Compare before/after metrics for each change
3. **Check applicability**: Ensure the rule applies to your specific case
4. **Look for other issues**: Network, database, or infrastructure problems

### Issue: Bundle Size Still Large

**Symptoms:**
- Applied bundle-* rules but bundle remains large
- Slow initial load times

**Solutions:**
1. **Analyze bundle**: Use `@next/bundle-analyzer` to identify large dependencies
2. **Check barrel imports**: Search for imports from package root (e.g., `from 'lucide-react'`)
3. **Review dynamic imports**: Ensure heavy components use `next/dynamic`
4. **Enable optimizePackageImports**: Add to next.config.js for automatic optimization

### Issue: Waterfalls Persist

**Symptoms:**
- Sequential network requests in waterfall
- Slow page loads despite async code

**Solutions:**
1. **Check component structure**: Ensure async components are siblings, not nested
2. **Use Promise.all()**: Combine independent operations
3. **Add Suspense boundaries**: Allow UI to stream while data loads
4. **Review API routes**: Start promises early, await late

### Issue: Too Many Re-renders

**Symptoms:**
- Component renders multiple times unnecessarily
- Sluggish UI interactions

**Solutions:**
1. **Profile renders**: Use React DevTools Profiler
2. **Check dependencies**: Ensure useEffect/useMemo use primitive values
3. **Memoize callbacks**: Use useCallback for functions passed as props
4. **Extract components**: Move expensive work to memoized child components

## Additional Resources

- **Official Documentation**: https://react.dev
- **Next.js Documentation**: https://nextjs.org
- **SWR Documentation**: https://swr.vercel.app
- **Vercel Blog**: https://vercel.com/blog
- **better-all Library**: https://github.com/shuding/better-all
- **LRU Cache**: https://github.com/isaacs/node-lru-cache

## Version Information

- **Version**: 1.0.0
- **Organization**: Vercel Engineering
- **Date**: January 2026
- **License**: MIT

---

**Note**: This power is designed for AI agents and developers working with React and Next.js. The rules are optimized for automated refactoring and code generation, with clear examples and impact metrics to guide decision-making.

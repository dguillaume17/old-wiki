Différence entre || et ?? (Opérateur de coalescence des nuls)

```typescript
console.log(null ?? 'défaut'); // "défaut"
console.log(null || 'défaut'); // "défaut"

console.log(undefined ?? 'défaut'); // "défaut"
console.log(undefined || 'défaut'); // "défaut"

console.log('' ?? 'défaut'); // ""
console.log('' || 'défaut'); // "défaut"

console.log(0 ?? 'défaut'); // 0
console.log(0 || 'défaut'); // "défaut"

console.log(10 ?? 'défaut'); // 10
console.log(10 || 'défaut'); // 10

console.log(true ?? 'défaut'); // true
console.log(true || 'défaut'); // true

console.log(false ?? 'défaut'); // false
console.log(false || 'défaut'); // "défaut"

```

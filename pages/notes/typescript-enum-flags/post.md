---
title: 'TypeScript Enum Flags'
color: white
truncate: 40
date: '17:29 25-08-2019'
taxonomy:
    category: Idea
    tag:
        - typescript
---

### Definition

```ts
enum FileAccess {
    None,                      // 000
    Read       = 1 << 1,       // 001
    Write      = 1 << 2,       // 010
    Execute    = 1 << 3,       // 100
    ReadWrite  = Read | Write, // 011
}
```

### Usage

```ts
let f = FileAccess.Read;

// add a flag
f |= FileAccess.Execute; // === ReadExecute

// check permits
f & FileAccess.Execute // true

// remove the flag
f &= ~FileAccess.Read; // === Execute
```
---
title: Arrays
language: en
layout: examples
---

```cadence
pub contract Arrays {
   pub let names: [String]

   pub fun add(name: String) {
      self.names.append(name)
   }

   pub fun remove(index: Int) {
      self.names.remove(at: index)
   }

   pub fun get(index: Int): String {
      return self.names[index]
   }

   init() {
      self.names = ["Jacob", "Sarah"]
   }
}
```

# Arrays
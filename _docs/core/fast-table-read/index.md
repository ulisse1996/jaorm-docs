---
layout: default
title: Fast Table Read
parent: Core
nav_order: 3
---

# Tables

User can also use generated **Tables** entry point for type-safe read of an Entity.

**Tables** use a custom DSL for retrieve each Entity annotated with **Table**

```java
public class Test {

  public static void main(String... args) {
    User user = Tables.USER_TABLE.userId(10).read();
  }
}
```

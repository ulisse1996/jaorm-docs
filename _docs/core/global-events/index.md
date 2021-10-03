---
layout: default
title: Global Events
parent: Core
nav_order: 4
---

# Global Events

User can handle Global Events (Persist, Delete or Update) [registering](https://docs.oracle.com/javase/tutorial/sound/SPI-intro.html)
a custom **GlobalEventListener**

Jaorm will handle only Entity annotated with **GlobalListener**

```java
@GlobalListener
@Table(name = "ENTITY")
public class Entity {

  // class body omitted for brevity
}
```

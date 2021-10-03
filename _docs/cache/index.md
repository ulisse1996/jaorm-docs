---
layout: default
title: Cache
nav_order: 4
---

# Cache

Cache module implements a key based cache for **@Cacheable** annotated entities.

Each time a request for a select query is done with **@Query** implementation,
an entity is stored with selected keys.
In the followings requests , cached entities are returned if previous request was successful.

```java
@Cacheable
@Table(name = "TABLE_NAME")
public class Entity {

    @Id
    @Column(name = "COLUMN_1")
    private String column1;

    @Column(name = "COLUMN_2")
    private int column2;
}
```

Default cache implementation is [Caffeine](https://github.com/ben-manes/caffeine) but user can override it
implementing custom **JaormCache** and **JaormAllCache** using an **AbstractCacheConfiguration**.

<aside class="info">
  If custom implementation is used , user must create an SPI file for <b>CacheService</b> and cache module
  must be omitted from dependencies.
</aside>

Default cache implementation require a startup configuration for each entity that are **@Cacheable**
annotated.

```java
public class Startup {

    public void doStartup() {
        CacheService cacheService = CacheService.getInstance();
        MyCacheConfiguration configuration = MyCacheConfiguration.INSTANCE;
        // or use default StandardConfiguration in cache module

        cacheService.setConfiguration(User.class, configuration);
    }
}
```

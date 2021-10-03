---
layout: default
title: Core
nav_order: 2
has_children: true
---
# Core

## Core Module

Core Module contains [Entity Mapper]({{ site.baseurl }}{% link _docs/core/entity-mapper/index.md %}) and [Query]({{ site.baseurl }}{% link _docs/core/query/index.md %}) annotated services

```java
import io.github.ulisse1996.jaorm.entity.sql.DataSourceProvider;

import javax.enterprise.inject.spi.CDI;
import javax.enterprise.util.AnnotationLiteral;
import javax.sql.DataSource;

public class DataSourceProviderImpl extends DataSourceProvider {

    @Override
    public DataSource getDataSource() {
        return CDI.current().select(DataSource.class)
                .get();
    }
}
```

User must define and [register](https://docs.oracle.com/javase/tutorial/sound/SPI-intro.html) a custom implementation of **io.github.ulisse1996.jaorm.entity.sql.DataSourceProvider** that return an instance of **javax.sql.DataSource**
for execute Sql Statements

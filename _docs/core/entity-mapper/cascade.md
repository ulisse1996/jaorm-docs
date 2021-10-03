---
layout: default
title: Cascade
parent: Entity Mapper
grand_parent: Core
nav_order: 5
---

# Cascade

Jaorm also supports Cascade operation with **@Cascade** annotation on relationship fields

```java
@Table(name = "USER")
public class User {

    @Id
    @Column(name = "COL1")
    private String id;

    @Column(name = "COL2")
    private String col2;

    @Cascade(CascadeType.ALL)
    @Relationship(columns = @Relationship.RelationshipColumn(defaultValue = "DEPARTMENT_ID",
            targetColumn = "DEPARTMENT_ID"))
    private Department department;

    // getter and setters
}
```

Supported operations :

- ALL , on Insert , Update or Delete , linked entities are affected by the operation on the entity
- PERSIST , on Insert , linked entities are affected by the insert on the entity
- REMOVE , on Delete , linked entities are affected by the remove on the entity
- UPDATE , on Update , linked entities are affected by the update on the entity

<aside class="info">
If nested links are created , only annotated fields with <b>@Cascade</b> and with matched <b>CascadeType</b> are affected
by the operation
</aside>

---
layout: default
title: Id
parent: Entity Mapper
grand_parent: Core
nav_order: 1
---

# Id (Primary/Unique Key)

In contrast to JPA or Others ORM, Jaorm does not use compound id class

User can declare one or more **@Id** annotation in a single entity that are used to define how Entity must be selected, updated and deleted from database

<aside class="success">
  Jaorm retrieve and set auto-generated keys during persist events
</aside>

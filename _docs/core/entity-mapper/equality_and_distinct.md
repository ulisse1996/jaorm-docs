---
layout: default
title: Equality And Distinct
parent: Entity Mapper
grand_parent: Core
nav_order: 6
---

# Equality And Distinct

In Jaorm , equality between two Entity can be tricky.

Jaorm use **Delegation** pattern for Entity Mapping and Lazy fetching of linked entities , so a fetched Entity
retrieved with **Query**, **Dao** or **DSL** is an instance of selected Entity but doesn't have the same class at runtime

```java
public class Example {

  @Table(name = "USER")
  public static class User {

    @Id
    @Column(name = "COL1")
    private String id;

    @Column(name = "COL2")
    private String col2;

    @Override
    public boolean equals(Object o) {
      if (this == o) return true;
      if (o == null || getClass() != o.getClass()) return false;
      User user = (User) o;
      return Objects.equals(id, id) && Objects.equals(col2, user.col2);
    }

    @Override
    public int hashCode() {
      return Objects.hash(id, col2);
    }

    // getter and setters
  }

  public void should_return_true_for_same_entity() {
      UserDAO dao = QueriesService.getInstance().getQuery(UserDAO.class);

      User user = new User();
      user.setId("id");
      user.setName("name");

      User found = dao.read(user);

      // Return true, delegate instance underline check equality with two User instance
      boolean foundEquals = found.equals(user);

      // Return false , because found.getClass() != User.class
      boolean userEquals = user.equals(found);
  }
}
```

For Equals check between two Entities , **EntityComparator** must be used if **equals** implementation use **getClass()**
checks

```java
public class Test {

  public static void main(String[] args) {
    User user1 = new User();
    User user2 = new User();
    EntityComprator.getInstance(User.class)
            .equals(user1, user2);
    EntityComprator.getInstance(User.class)
            .equals(Collections.singletonList(user1), Collections.singletonList(user2));
  }
}
```

For support with **distinct()** in Java 8 **Stream API** , user can also use
**EntityComparator.distinct(Function\<? super T,?> function)**

```java
public class Test {

    void method() {
        List<User> users = QueriesService.getQuery(UserDao.class)
                .readAll();
        List<User> usersDistinctId =
                users.stream()
                      .filter(EntityComparator.distinct(User::getUserId))
                      .collect(Collectors.toList);
    }
}
```

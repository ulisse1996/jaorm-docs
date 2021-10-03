---
layout: default
title: Transactions
nav_order: 5
---

# Transactions

Jaorm natively supports **@org.springframework.transaction.annotation.Transactional**
and **@javax.transaction.Transactional** for JTA or Spring Managed Beans.

For SE applications, **Transactional** module can also be used.

**Transactional.exec(Callable\<V\> callable, Class\<X\> exceptionClass)** create a new Transaction and execute **Callable\<V>** as first argument.

If an exception , matched with the second argument is thrown , the exception is propagated,
current transaction execute a rollback and close current transaction

If an exception that doesn't match with second argument , is thrown , an **UnexpectedException** is thrown ,
current transaction execute a rollback and close current transaction

If **Callable\<V>** is correctly executed , **exec** return the returned value if any is provided,
current transaction execute a commit and close current transaction

Transaction is propagated on the current Thread and on each child Thread

```java
public class TransactionalTest {

  public static void main(String[] args) {
      Transactional.exec(() -> {
        UserDAO dao = QueriesService.getInstance().getQuery(UserDAO.class);

        User user = new User();
        user.setId("id");
        user.setName("name");

        dao.insert(user);

        // After this , commit is done on current transaction
      }, Exception.class);
  }
}
```

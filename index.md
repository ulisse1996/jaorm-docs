---
layout: default
title: Jaorm
nav_order: 1
---

# JAORM
Just Another Object-Relational Mapping

![Build Status](https://github.com/ulisse1996/JAORM/workflows/build/badge.svg)
[![Sonarcloud Status](https://sonarcloud.io/api/project_badges/measure?project=ulisse1996_JAORM&metric=alert_status)](https://sonarcloud.io/dashboard?id=ulisse1996_JAORM)
[![SonarCloud Coverage](https://sonarcloud.io/api/project_badges/measure?project=ulisse1996_JAORM&metric=coverage)](https://sonarcloud.io/component_measures/metric/coverage/list?id=ulisse1996_JAORM)
[![SonarCloud Bugs](https://sonarcloud.io/api/project_badges/measure?project=ulisse1996_JAORM&metric=bugs)](https://sonarcloud.io/component_measures/metric/reliability_rating/list?id=ulisse1996_JAORM)
[![SonarCloud Vulnerabilities](https://sonarcloud.io/api/project_badges/measure?project=ulisse1996_JAORM&metric=vulnerabilities)](https://sonarcloud.io/component_measures/metric/security_rating/list?id=ulisse1996_JAORM)


JAORM is a lightweight modular compile-time based Java ORM.

JAORM use **Java Annotation Processor [JSR 269](https://jcp.org/en/jsr/detail?id=269)** for Entity Mapping Generation instead of
**Runtime Reflection API-based** mappers which have high performance cost.

JAORM is divided in modules that are used from main module using **Java SPI**

# Modules

## Core Module
```xml
<dependency>
    <groupId>io.github.ulisse1996</groupId>
    <artifactId>jaorm</artifactId>
    <version>${jaorm.version}</version>
</dependency>
```

## DSL Module
```xml
<dependency>
    <groupId>io.github.ulisse1996</groupId>
    <artifactId>jaorm-dsl</artifactId>
    <version>${jaorm.version}</version>
</dependency>
```

## Cache Module

```xml
<dependency>
    <groupId>io.github.ulisse1996</groupId>
    <artifactId>jaorm-cache</artifactId>
    <version>${jaorm.version}</version>
</dependency>
```

## Transaction Module
````xml
<dependency>
    <groupId>io.github.ulisse1996</groupId>
    <artifactId>jaorm-transaction</artifactId>
    <version>${jaorm.version}</version>
</dependency>
````

## Lombok Support Module
```xml
<dependency>
    <groupId>io.github.ulisse1996</groupId>
    <artifactId>jaorm-lombok</artifactId>
    <version>${jaorm.version}</version>
</dependency>
```

## Sql Vendor Specific (DSL Plugin)

### Oracle
```xml
<dependency>
    <groupId>io.github.ulisse1996</groupId>
    <artifactId>jaorm-sql-specific-oracle</artifactId>
    <version>${jaorm.version}</version>
</dependency>
```

### SQL Server
```xml
<dependency>
    <groupId>io.github.ulisse1996</groupId>
    <artifactId>jaorm-sql-specific-oracle</artifactId>
    <version>${jaorm.version}</version>
</dependency>
```

### PostgreSQL
```xml
<dependency>
    <groupId>io.github.ulisse1996</groupId>
    <artifactId>jaorm-sql-specific-oracle</artifactId>
    <version>${jaorm.version}</version>
</dependency>
```


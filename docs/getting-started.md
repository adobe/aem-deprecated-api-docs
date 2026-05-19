# Getting Started

This page is for developers who need to update an AEM bundle because of an API deprecation but are not yet familiar with the typical AEM Maven project structure.


## Typical AEM Maven Project Structure

These docs assume a project structure based on the [AEM Project Archetype](https://github.com/adobe/aem-project-archetype).

```text
my-aem-project/
├── pom.xml
├── all/
│   └── pom.xml
├── core/
│   └── pom.xml
├── ui.apps/
│   └── pom.xml
├── ui.content/
│   └── pom.xml
└── dispatcher/
    └── pom.xml
```

In most deprecation cases:

- the root `pom.xml` is the parent POM for the whole project
- the `core/pom.xml` file contains Java bundle dependencies
- the `all/pom.xml` file aggregates deployable artifacts
- `ui.apps` and `ui.content`  usually do not contain the Java dependency changes described in these docs
- `dispatcher` is not relevant in this context as well

## How To Find The Correct `pom.xml`

When a deprecation warning tells you to update a dependency, check the project in this order:

1. Look in the bundle module first, for example `core/pom.xml`.
2. If the dependency version is not declared there, check the root `pom.xml`.
3. If the root `pom.xml` uses a `<dependencyManagement>` section or shared version properties, update the version there.
4. If you are unsure which file controls the version, search for the dependency coordinates in the whole project.

## Common Maven Patterns

### Dependency declared directly in the bundle POM

```xml
<dependencies>
  <dependency>
    <groupId>com.example</groupId>
    <artifactId>example-api</artifactId>
    <version>1.0.0</version>
  </dependency>
</dependencies>
```

### Version managed in the parent POM

```xml
<properties>
  <example.api.version>2.0.0</example.api.version>
</properties>
```

```xml
<dependencies>
  <dependency>
    <groupId>com.example</groupId>
    <artifactId>example-api</artifactId>
    <version>${example.api.version}</version>
  </dependency>
</dependencies>
```



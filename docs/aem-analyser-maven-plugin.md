# The AEM analyser maven plugin

It is recommended that your custom AEM application uses the AEM analyser maven plugin to detect deprecated API usage early on. During build-time it will check any API used by your Java code and will warn you about any use of deprecated APIs, listed on the [Adobe Experience League: Deprecated and removed features](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/release-notes/deprecated-removed-features#removed-apis) page of the official AEM documentation.

## Version number

In general it is recommended to use the latest version of that plugin, as it covers all listed packages listed for deprecation.

## Installation

The following assumes a standard AEM project, which is bootstrapped with the standard AEM project Maven archetype. See the [Getting Started](docs/getting-started.md) page for more details.

Add the following snippets to your ``pom.xml``

```
<properties>
    ...
    <aemanalyser.version>VERSION_NUMBER</aemanalyser.version>
</properties>
...
<plugins>
    <plugin>
        <groupId>com.adobe.aem</groupId>
        <artifactId>aemanalyser-maven-plugin</artifactId>
        <extensions>true</extensions>
    </plugin>
</plugins>
```

Make sure that the following snippets are part of your ``all/pom.xml``
```
  <build>
      <plugins>
          ...
          <plugin>
              <groupId>com.adobe.aem</groupId>
              <artifactId>aemanalyser-maven-plugin</artifactId>
              <executions>
                  <execution>
                      <id>aem-analyser</id>
                      <goals>
                          <goal>project-analyse</goal>
                      </goals>
                  <execution>
              </executions>
          <plugin>
      </plugins>
  </build>
  ```

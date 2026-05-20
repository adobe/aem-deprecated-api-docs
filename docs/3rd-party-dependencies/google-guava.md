# Google Guava

The Google Guava library augments the Java Standard libraries by a large amount of additional functionality.

Website: [https://github.com/google/guava](https://github.com/google/guava)

In AEM the use of this library is deprecated (many of its functionality has been added to the Java standard libraries in the last 10 years) and the library itself will be removed, so customer code cannot rely anymore on its presence.

For that reason there 2 ways how to handle this situation:

### Remove all dependencies to Google Guava

AEM CS operates with a Java 21 runtime; for that reason in many cases the use of Guava code can be easily replaced with functionality from the standard Runtime Library.

This is definitely the recommended way to go, unless you are using very specialized functionality from Guava, which cannot be replaced.

### Ship Google Guava with the custom AEM application

As short-time mitigation, it is possible to ship the Google Guava library in the custom AEM code. To achieve that you need to implement the following changes.

NOTE: AEM CS shipped Guava 15.0 for a very long period, for that reason this is the safest replacement as short-time mitigation. But you should check if you can use a more [recent version](https://central.sonatype.com/artifact/com.google.guava/guava/versions).

In the **pom.xml** add Guava to the dependency management

```
<dependencyManagement>
  <dependencies>
    <dependency>
      <groupId>com.google.guava</groupId>
      <artifactId>guava</artifactId>
      <version>15.0</version>
    </dependency>
  </dependencies>
</dependencyManagement>
```

Make it explicitly available as dependency in the **core/pom.xml**:
```
<dependencies>
  <dependency>
    <groupId>com.google.guava</groupId>
    <artifactId>guava</artifactId>
    <scope>provided</scope>
  </dependency> 
</dependencies>
```

And finally make sure that the Guava library is embedded into the deployment artifact (**all/pom.xml**):
```
<plugin>   
  <groupId>org.apache.jackrabbit</groupId>   
  <artifactId>filevault-package-maven-plugin</artifactId>   
  <configuration>    
    <embeddeds>       
      <embedded>         
        <groupId>com.google.guava</groupId>         
        <artifactId>guava</artifactId>         
        <type>jar</type>          
        <target>/apps/YOURAPP/install/</target>       
      </embedded>    
    </embeddeds>   
  </configuration> 
</plugin>
```

(make sure to replace ``YOURAPP`` with an existing path in your application package)
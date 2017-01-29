# Labs Parent Pom

Parent pom for Java projects

## Versions

* 1.2.0
    * Upgrade the version number of the following plugins
        * maven-assembly-plugin
        * maven-compiler-plugin
        * maven-dependency-plugin
        * maven-pmd-plugin
        * maven-site-plugin
* 1.1.0 
    * Add additional archiver information (MANIFEST.MF)
    * Deploy source and javadoc in default
    * Use the nexus staging for the deployment
* 1.0.0 
    * Baseline

## Plugin Build Configurations

### Source 

Generate source jar during the package.

```
<plugin>
    <groupId>org.apache.maven.plugins</groupId>
    <artifactId>maven-source-plugin</artifactId>
    <executions>
        <execution>
            <id>attach-sources</id>
            <goals>
                <goal>jar-no-fork</goal>
            </goals>
        </execution>
    </executions>
</plugin>
```

### Javadoc

Create javadoc jar during the package.

```
<plugin>
    <groupId>org.apache.maven.plugins</groupId>
    <artifactId>maven-javadoc-plugin</artifactId>
    <executions>
        <execution>
            <id>attach-sources</id>
            <goals>
                <goal>jar</goal>
            </goals>
        </execution>
    </executions>
</plugin>
```

### Single assembly

```
<plugin>
    <groupId>org.apache.maven.plugins</groupId>
    <artifactId>maven-assembly-plugin</artifactId>
    <configuration>
        <finalName>${finalJar}</finalName>
        <descriptorRefs>
            <descriptorRef>jar-with-dependencies</descriptorRef>
        </descriptorRefs>
        <appendAssemblyId>false</appendAssemblyId>
    </configuration>
    <executions>
        <execution>
            <phase>package</phase>
            <goals>
                <goal>single</goal>
            </goals>
        </execution>
    </executions>
</plugin>
```
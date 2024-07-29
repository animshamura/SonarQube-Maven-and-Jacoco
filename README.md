## Necessary Changes in pom.xml :

Add JaCoCo properties.
```
<properties>
    <!-- JaCoCo Properties -->
    <jacoco.version>0.8.7</jacoco.version>
    <sonar.java.coveragePlugin>jacoco</sonar.java.coveragePlugin>
    <sonar.dynamicAnalysis>reuseReports</sonar.dynamicAnalysis>
    <sonar.coverage.jacoco.xmlReportPaths>${project.basedir}/target/jacoco.xml</sonar.coverage.jacoco.xmlReportPaths>
    <sonar.language>java</sonar.language>
</properties>
```
Add JaCoCo dependency.
```
<dependency>
    <groupId>org.jacoco</groupId> 
    <artifactId>jacoco-maven-plugin</artifactId>
    <version>0.8.11</version>
</dependency>
```
Add plugin that integrates Maven project with JaCoCo. 
```
<plugin>
    <groupId>org.jacoco</groupId>
    <artifactId>jacoco-maven-plugin</artifactId>
    <version>${jacoco.version}</version>
    <executions>
        <execution>
            <id>jacoco-initialize</id>
            <goals>
                <goal>prepare-agent</goal>
            </goals>
        </execution>
        <execution>
            <id>jacoco-site</id>
            <phase>package</phase>
            <goals>
                <goal>report</goal>
            </goals>
        </execution>
    </executions>
</plugin>
```

# plusminus-parent
Parent POM for plusminus projects

## How it relates to other parent projects
1. plusminus-parent - base parent project
2. plusminus-parent-public - extends plusminus-parent with configured deploying to Maven Central repo
3. plusminus-parent-configs - set of configurations of different Maven plugins (such as Checkstyle, PMD etc.) that can be used in plusminus-parent as a dependency

## How to release plusminus-parent?
Please add two plugins into pom.xml (but do not commit them!) just like on plusminus-parent-public:
```
<plugin>
    <groupId>org.sonatype.central</groupId>
    <artifactId>central-publishing-maven-plugin</artifactId>
    <version>0.7.0</version>
    <extensions>true</extensions>
    <configuration>
        <publishingServerId>central</publishingServerId>
        <autoPublish>true</autoPublish>
        <waitUntil>published</waitUntil>
    </configuration>
</plugin>
<plugin>
    <groupId>org.apache.maven.plugins</groupId>
    <artifactId>maven-gpg-plugin</artifactId>
    <version>1.6</version>
    <executions>
        <execution>
            <id>sign-artifacts</id>
            <phase>deploy</phase>
            <goals>
                <goal>sign</goal>
            </goals>
        </execution>
    </executions>
</plugin>
```
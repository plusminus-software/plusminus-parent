# plusminus-parent
Parent POM for plusminus projects

## How it relates to other parent projects?
1. plusminus-parent - base parent project
2. plusminus-parent-public - extends plusminus-parent with configured deploying to Maven Central repo
3. plusminus-parent-configs - set of configurations of different Maven plugins (such as Checkstyle, PMD etc.) that can be used in plusminus-parent as a dependency

## How to release plusminus-parent?
Please run this command
```
mvn clean verify gpg:sign org.sonatype.central:central-publishing-maven-plugin:0.7.0:publish -DpublishingServerId=central -DautoPublish=true -DwaitUntil=published
```

## How to use SNAPSHOT version of parent?
You must add this section to your pom.xml:
```
<repositories>
    <repository>
        <id>sonatype-central-snapshots</id>
        <url>https://central.sonatype.com/repository/maven-snapshots/</url>
        <releases>
            <enabled>false</enabled>
        </releases>
        <snapshots>
            <enabled>true</enabled>
        </snapshots>
    </repository>
</repositories>
```
# plusminus-parent
Parent POM for plusminus projects.

This repository hosts two independent Maven modules that are **not** wired into a
root multi-module (reactor) build. Each is a standalone project, released on its own:

- [`plusminus-parent/`](plusminus-parent) — the base parent POM
  (`software.plusminus:plusminus-parent`) inherited by other plusminus projects.
- [`plusminus-configs/`](plusminus-configs) — a set of Maven plugin configurations
  (Checkstyle, PMD, SpotBugs, lombok.config, etc.), published as a SNAPSHOT artifact
  (`software.plusminus:plusminus-configs`) that `plusminus-parent` consumes as a dependency.

There is intentionally no aggregator `pom.xml` at the repository root. The release
workflow builds and publishes each module directory independently — either all of them
(on push) or a single one selected via the `module` input of the **Release** workflow
(`workflow_dispatch`), mirroring how `plusminus-security` targets individual modules.

## How to release plusminus-parent?
Please run this command
```
mvn clean verify gpg:sign org.sonatype.central:central-publishing-maven-plugin:0.7.0:publish -DpublishingServerId=central -DautoPublish=true -DwaitUntil=published
```
If you want to release SNAPSHOT version then you can omit gpg sign stage
```
mvn clean verify org.sonatype.central:central-publishing-maven-plugin:0.7.0:publish -DpublishingServerId=central -DautoPublish=true -DwaitUntil=published
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
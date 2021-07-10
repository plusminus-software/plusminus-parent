# plusminus-parent
Maven parent POM for plusminus-software projects

### How to release plusminus-parent?
plusminus-parent's pom.xml does not include configuration for automatic upload to Maven Central to be used for private projects.
So this project can be released manually only using the following steps:
1. Sign pom.xml with gpg
```
gpg -ab plusminus-parent-X.Y.pom
```
2. Create a bundle
```
jar -cvf bundle.jar plusminus-parent-X.Y.pom plusminus-parent-X.Y.pom.asc
```
3. Go to sonatype's nexus and upload a bundle.jar

https://s01.oss.sonatype.org/ -> Staging Upload -> Artifact bundle

4. Release to maven central

https://s01.oss.sonatype.org/ -> Staging Releases - > Release

More info: https://central.sonatype.org/publish/publish-manual/ 
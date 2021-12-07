# plusminus-parent
Maven's parent POM for plusminus-software projects

### How to release plusminus-parent?
plusminus-parent's pom.xml does not include configuration for automatic upload to Maven Central to be used for private projects.
So this project can be released manually only using the following steps:
1. Install to local maven repository
```
mvn clean install
```
2. Go to the `.m2` folder
```
cd ~/.m2/repository/software/plusminus/plusminus-parent
```
3. Sign pom.xml with gpg
```
sudo gpg -ab plusminus-parent-X.Y.pom
```
4. Create a bundle
```
jar -cvf bundle.jar plusminus-parent-X.Y.pom plusminus-parent-X.Y.pom.asc
```
5. Go to sonatype's nexus and upload a bundle.jar

https://s01.oss.sonatype.org/ -> Staging Upload -> Artifact bundle

6. Release to maven central

https://s01.oss.sonatype.org/ -> Staging Repositories - > Release

More info: https://central.sonatype.org/publish/publish-manual/ 

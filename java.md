### Tomcat hot-reload
```xml
# server.xml
<Host>
        <Context docBase="/iplass-skeleton" path="/iplass-skeleton" reloadable="true"/>
</Host>
```
https://blog.codefx.org/java/java-9-migration-guide/#Dependencies-On-Java-EE-Modules

```bash
# Creating a Project
mvn archetype:generate "-DgroupId=com.mycompany.app" "-DartifactId=my-app" "-DarchetypeArtifactId=maven-archetype-quickstart" "-DinteractiveMode=false"
```

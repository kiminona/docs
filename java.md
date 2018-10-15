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
### Gretty Hot deployment
```
gretty {
	httpPort = 7788
	servletContainer = 'tomcat8'
	managedClassReload = true // 設定したら、下記のエラーが発生する
}
```
```
10:08:30.442 [qtp1594873248-18] ERROR     o.i.mtp.impl.web.DispatcherFilter - Exception occurred while processing URI:/iplass-skeleton/demo/mob/ java.lang.ClassNotFoundException: org.iplass.mtp.impl.i18n.MetaLocalizedString
java.lang.RuntimeException: java.lang.ClassNotFoundException: org.iplass.mtp.impl.i18n.MetaLocalizedString
```

# asocnotes
Notes for running ASOC

Manually Scanning Java Projects
1. Go to the directory where the `pom.xml` is. Make sure you pull in all the dependencies by doing a `mvn install`:
1. You need to set `JAVA_HOME` to Java 11. Do this via `export JAVA_HOME=$(/usr/libexec/java_home)`
1. Call `mvn com.hcl.security:appscan-maven-plugin:prepare`

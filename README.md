# asocnotes
Notes for running ASOC

Manually Scanning Java Projects
1. Go to the directory where the `pom.xml` is. Make sure you pull in all the dependencies by doing a `mvn install`:
1. You need to set `JAVA_HOME` to Java 11. Do this via `export JAVA_HOME=$(/usr/libexec/java_home)`




1. For example, let's look at: https://github.ibm.com/katamari/cp4waiops-grpc-dynatrace-client
1. Go to the `pom.xml` directory in `cp4waiops-grpc-dynatrace-client/open-liberty`
1. Call setup SDK, `export GITHUB_TOKEN=<YOUR TOKEN>` then `./setup-sdk.sh v1.4.3`
3. Call `mvn com.hcl.security:appscan-maven-plugin:prepare -Dmaven.test.skip=true` inside the `connector` directory

# asocnotes
Notes for running ASOC

Manually Scanning Java Projects
1. Go to the directory where the `pom.xml` is. Make sure you pull in all the dependencies by doing a `mvn install`:
1. You need to set `JAVA_HOME` to Java 11. Do this via `export JAVA_HOME=$(/usr/libexec/java_home)`




1. For example, let's look at: https://github.ibm.com/katamari/cp4waiops-grpc-dynatrace-client (make sure to choose the proper branch)
1. Go to the `pom.xml` directory in `cp4waiops-grpc-dynatrace-client/open-liberty`
1. Call setup SDK, `export GITHUB_TOKEN=<YOUR TOKEN>` then `./setup-sdk.sh v1.4.3`
3. Call `mvn com.hcl.security:appscan-maven-plugin:prepare -Dmaven.test.skip=true` inside the `connector` directory
4. When the scan is finished, you will see an .irx file in the log. For example:
```
[INFO] Validation complete.
[INFO] Generating IRX file...
[INFO] IRX file generation successful.
[INFO] 
[INFO] Successfully generated /Users/stevenhung/gitMay2022/cp4waiops-grpc-dynatrace-client/open-liberty/connector/target/dynatrace-connector.irx.

```

5. Login to ASOC: https://cloud.appscan.com/
6. Choose `Katamari-Juno` as the application
7. Upload the irx file
8. AppScan will create the report

After the report is created, you need to generate the csv file: https://github.ibm.com/watson-ai4it/security-scripts#asoc-scans---to-generate-csv-file-for-a-set-of-scan-ids

Copy the IDs of the scans and put it into the [AI_Manaager_Components.py](https://github.ibm.com/watson-ai4it/security-scripts/blob/master/ASoC_Scans/AI_Manager_Components.py)

For example:
```json
AIManagerComponents = {
  "SNow" : {
    "Static": " 7ac72d01-82ed-4393-a83a-5bdaaefa1d8b"
  },
  "GitHub" : {
    "Static": "18ae6e46-8b6b-43aa-96d0-ecddbeea08ca"
  },
  "bundles" : {
    "Static": "00ea178a-11e0-4fa4-b312-70f80f7b0c12"
  },
  "Server side" : {
    "Static": "a2e16e44-1dc5-4310-81a4-a55381408e04"
  },
  "Operator" : {
    "Static": "fa6c9d1e-7a9c-4061-a8ca-d12898f6a17f"
  },
  "Controller" : {
    "Static": "1d551aa0-57d1-439c-85ba-7d610f82a408"
  },
  "Manager" : {
    "Static": "12436952-7cbd-42bc-b416-ddf675d96d3c"
  }
}
```

You need to create a `results` folder, then run with your ASOC key (you can get from appscan settings). Example:
```
python3 convertAsocToExcel.py -i <asoc-key-id> -s <asoc-key-secret> -f <some-csv-filename>
```

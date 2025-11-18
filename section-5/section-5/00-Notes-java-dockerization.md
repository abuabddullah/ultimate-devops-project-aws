# install java
```
sudo apt install openjdk-21-jre-headless
```
```
java --version
```
# Build Go for *src/ad/README.md*
- goto to the **Ad** service **_ubuntu@ip-172-31-27-215:~/ultimate-devops-project-demo/src/ad$_**

### grant the permission for the wraper file
```
chmod +x ./gradlew
```
### 56 check permission is enaled or not
```
ubuntu@ip-172-31-27-215:~/ultimate-devops-project-demo/src/ad$ ./gradlew

> Task :help

Welcome to Gradle 8.9.

********************
********************
****************

BUILD SUCCESSFUL in 2s
1 actionable task: 1 executed
```
### build the prject [./gradlew টাই হচ্ছে package.json এর মত কাজ করে]
```
./gradlew installDist

```
### check **_build_** folder is created or not
```
ubuntu@ip-172-31-27-215:~/ultimate-devops-project-demo/src/ad$ ll
total 68
drwxrwxr-x  7 ubuntu ubuntu 4096 Nov 18 00:30 ./
drwxrwxr-x 28 ubuntu ubuntu 4096 Nov 14 14:12 ../
drwxrwxr-x  5 ubuntu ubuntu 4096 Nov 18 00:30 .gradle/
-rw-rw-r--  1 ubuntu ubuntu    5 Nov 14 12:49 .java-version
-rw-rw-r--  1 ubuntu ubuntu  525 Nov 14 12:49 Dockerfile
-rw-rw-r--  1 ubuntu ubuntu  914 Nov 14 12:49 README.md
drwxrwxr-x 11 ubuntu ubuntu 4096 Nov 18 00:31 build/
-rw-rw-r--  1 ubuntu ubuntu 4355 Nov 14 12:49 build.gradle
drwxrwxr-x  3 ubuntu ubuntu 4096 Nov 14 12:49 gradle/
-rwxrwxr-x  1 ubuntu ubuntu 8692 Nov 14 12:49 gradlew*
-rw-rw-r--  1 ubuntu ubuntu 2777 Nov 14 12:49 gradlew.bat
drwxrwxr-x  2 ubuntu ubuntu 4096 Nov 14 12:49 pb/
-rw-rw-r--  1 ubuntu ubuntu   44 Nov 14 12:49 settings.gradle
drwxrwxr-x  3 ubuntu ubuntu 4096 Nov 14 12:49 src/
```
command: 
```
ls -ltr ./build/install/opentelemetry-demo-ad/bin/Ad
```
output
```
-rwxr-xr-x 1 ubuntu ubuntu 11498 Nov 18 00:31 ./build/install/opentelemetry-demo-ad/bin/Ad
```
### export the ports
```
export AD_PORT=9099
export FEATURE_FLAG_GRPC_SERVICE_ADDR=featureflagservice:50053
./build/install/opentelemetry-demo-ad/bin/Ad
```
_output_
```
ubuntu@ip-172-31-27-215:~/ultimate-devops-project-demo/src/ad$ export AD_PORT=9099

ubuntu@ip-172-31-27-215:~/ultimate-devops-project-demo/src/ad$ export FEATURE_FLAG_GRPC_SERVICE_ADDR=featureflagservice:50053
ubuntu@ip-172-31-27-215:~/ultimate-devops-project-demo/src/ad$ ./build/install/opentelemetry-demo-ad/bin/Ad
2025-11-18 00:39:11 - oteldemo.AdService - Ad service starting. trace_id= span_id= trace_flags= 
SLF4J(W): No SLF4J providers were found.
SLF4J(W): Defaulting to no-operation (NOP) logger implementation
SLF4J(W): See https://www.slf4j.org/codes.html#noProviders for further details.
2025-11-18 00:39:11 - oteldemo.AdService - Ad service started, listening on 9099 trace_id= span_id= trace_flags=
```

# Dockerization of java project

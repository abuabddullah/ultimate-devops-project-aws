# check java is installed or not
```
java --version
```
## install java
```
sudo apt install openjdk-21-jre-headless
```
# Dockerization of java file
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
or
```
./gradlew installDist -PprotoSourceDir=./proto
```


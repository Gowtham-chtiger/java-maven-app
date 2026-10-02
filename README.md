# simple-java-maven-app

A simple Java + Maven application designed for Jenkins CI/CD practice.

## Project structure

```text
simple-java-maven-app/
├── .github/
│   └── workflows/
│       └── maven.yml
├── jenkins/
│   ├── Jenkinsfile
│   └── scripts/
│       └── deliver.sh
├── src/
│   ├── main/java/com/example/app/App.java
│   └── test/java/com/example/app/AppTest.java
├── .gitattributes
├── .gitignore
├── Jenkinsfile
├── LICENSE
├── README.md
└── pom.xml
```

## Run locally

Make sure Java 21 and Maven 3.9+ are installed.

```bash
mvn clean test
mvn clean package
java -jar target/simple-java-maven-app-1.0-SNAPSHOT.jar
```

Expected output:

```text
Hello World from Maven + Jenkins!
```

## Jenkins pipeline

The pipeline has three stages:

1. **Build** - compiles and packages the application.
2. **Test** - runs JUnit tests and publishes test results.
3. **Deliver** - installs the built JAR into the local Maven repository and runs it.

### Jenkins setup

Create a Jenkins Pipeline job:

- **New Item**
- Enter: `simple-java-maven-app`
- Select **Pipeline**
- Choose **Pipeline script from SCM**
- SCM: **Git**
- Repository URL: your GitHub repository URL
- Branch: `*/main` or `*/master`
- Script Path: `Jenkinsfile`

Then select **Build Now**.

### Jenkins requirements

The Jenkins agent should have:

- Git
- JDK 21
- Maven 3.9+
- Bash

If Maven is configured in Jenkins as a tool, the pipeline can also be adapted to use the Jenkins Maven tool configuration.

## Git commands

```bash
git init
git add .
git commit -m "Initial Java Maven Jenkins project"
git branch -M main
git remote add origin https://github.com/YOUR_USERNAME/simple-java-maven-app.git
git push -u origin main
```

Jenkins + Maven + Tomcat Lab-4
================================

Before running Jenkins, edit Jenkinsfile:
1. Replace YOUR-USERNAME with your GitHub username.
2. Replace C:\apache-tomcat-11.0.24\webapps if Tomcat is installed elsewhere.

Project structure:
jenkins-tomcat-demo/
  pom.xml
  Jenkinsfile
  .gitignore
  src/
    main/
      java/com/vit/demo/Calculator.java
      webapp/index.jsp
    test/
      java/com/vit/demo/CalculatorTest.java

Manual Maven test:
  mvn clean test package

Expected WAR:
  target\jenkins-demo.war

Tomcat URL:
  http://localhost:8081/jenkins-demo/

Jenkins URL:
  http://localhost:8080

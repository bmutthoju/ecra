FROM eclipse-temurin:25-jre

WORKDIR /app

COPY target/ecra-0.1.0-SNAPSHOT.jar app.jar

USER 10001

ENTRYPOINT ["java", "-jar", "/app/app.jar"]

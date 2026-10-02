# ecra
Enterprise and Collaborative Reference Architecture (ECRA)

## Local Development

The current Gen1 implementation foundation is a minimal Spring Boot application. It does not yet expose an HTTP API or require PostgreSQL, so the local commands below validate the application build, tests, bootstrap, and container packaging without implying runtime capabilities that have not yet been implemented.

### Prerequisites

- JDK 25
- Maven 3.9+
- Docker, if you want to build and run the container image

### Build the application

From the repository root:

```bash
mvn clean package
```

This compiles the application, runs the test suite, and packages the application JAR under `target/`.

### Run tests

To run the tests without packaging:

```bash
mvn test
```

The current foundation includes an application-context test that verifies the Spring Boot application can start successfully.

### Run the application locally

Run the Spring Boot application with Maven:

```bash
mvn spring-boot:run
```

Alternatively, after a successful build:

```bash
java -jar target/ecra-0.1.0-SNAPSHOT.jar
```

The current foundation is not an HTTP service yet. It has no web starter or application endpoint, so local execution validates application bootstrap and then terminates normally after the application context is initialized.

### Build the Docker image

Build the image from the repository root:

```bash
docker build -f deploy/Dockerfile -t ecra:0.1.0-SNAPSHOT .
```

The Dockerfile expects the packaged JAR at:

```text
target/ecra-0.1.0-SNAPSHOT.jar
```

Therefore, run `mvn clean package` before building the image.

### Run the Docker image locally

Run the image with:

```bash
docker run --rm ecra:0.1.0-SNAPSHOT
```

The container starts the Spring Boot application as a non-root user. Because the current foundation does not expose an HTTP endpoint or keep a server process running, the container exits normally after application startup.

HTTP port publishing is not required at this stage. A port will be introduced when an approved API/runtime contract requires one.

# dicord-lite

Lightweight Discord-like backend (work in progress).

Overview
- A Spring Boot service skeleton using Gradle, Postgres and Docker.
- Goals: build a small, extendable chat backend, containerise with Docker, and deploy to AWS.

Tech stack
- Java + Spring Boot (app entry: [`com.derek.discordlite.DiscordliteApplication`](src/main/java/com/derek/discordlite/DiscordliteApplication.java))
- Build: Gradle ([build.gradle](build.gradle))
- Database: PostgreSQL (compose file: [compose.yaml](compose.yaml))
- Configuration: [src/main/resources/application.properties](src/main/resources/application.properties)
- Tests: JUnit 5 (example: [`com.derek.discordlite.DiscordliteApplicationTests`](src/test/java/com/derek/discordlite/DiscordliteApplicationTests.java))

Prerequisites
- JDK matching the Gradle toolchain defined in [build.gradle](build.gradle) (currently configured in the toolchain)
- Gradle wrapper (use ./gradlew)
- Docker & Docker Compose for local Postgres

Quick start (local)
1. Start Postgres via Docker:
   docker compose -f compose.yaml up -d
2. Build and run the app:
   ./gradlew bootRun
3. Run tests:
   ./gradlew test

Configuration
- Edit database connection and secrets in [src/main/resources/application.properties](src/main/resources/application.properties) (or use profiles / environment variables for production).
- The Compose service is defined in [compose.yaml](compose.yaml).

Project structure (high level)
- Application entry: [`com.derek.discordlite.DiscordliteApplication`](src/main/java/com/derek/discordlite/DiscordliteApplication.java)
- Tests: [`com.derek.discordlite.DiscordliteApplicationTests`](src/test/java/com/derek/discordlite/DiscordliteApplicationTests.java)
- Build config: [build.gradle](build.gradle)
- Docker compose: [compose.yaml](compose.yaml)
- App properties: [src/main/resources/application.properties](src/main/resources/application.properties)

Next steps / roadmap
- Add JPA entities and repositories for users, channels, messages
- Implement REST endpoints and DTOs
- Add authentication (Spring Security + JWT)
- Add integration tests using Testcontainers or Docker Compose
- Dockerfile and CI pipeline, push image to a container registry
- Deploy DB to AWS RDS and app to ECS/Fargate or Elastic Beanstalk; manage infra with Terraform/CloudFormation

Contributing
- Keep small commits
- Write tests for new features
- Use Git branches for features/experiments
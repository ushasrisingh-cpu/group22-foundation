# Application source

This repository uses the standard Maven and Spring Boot layout. The application source intentionally remains in the repository-root `src/` directory rather than being moved beneath `app/`:

- `src/main/` contains the Spring Boot Inventory Management System.
- `src/test/` contains automated tests.
- `pom.xml` defines the Maven build.
- `Dockerfile` builds the runnable container image used by CI and ECS Fargate.

The `app/` directory is included to make the capstone repository layout easy to navigate. Moving Maven source files into it would require changing the build configuration and would add no benefit to the deployed application.

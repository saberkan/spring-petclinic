# Spring PetClinic - Agent Instructions

## Cursor Cloud specific instructions

This is a Java 17+ / Spring Boot 3.3.0 monolith (Spring PetClinic). The Maven wrapper (`./mvnw`) is the primary build tool. JDK 21 is installed in the environment and is fully compatible.

### Quick Reference

| Action | Command |
|--------|---------|
| Build (skip tests) | `./mvnw package -DskipTests` |
| Run tests | `./mvnw test` |
| Lint/format check | `./mvnw spring-javaformat:validate` |
| Auto-format code | `./mvnw spring-javaformat:apply` |
| Run dev server | `./mvnw spring-boot:run` |
| App URL | http://localhost:8080 |

### Important Notes

- **Default database**: H2 in-memory (no external dependencies needed). Data is ephemeral and resets on restart.
- **Spring Java Format**: The project enforces `spring-javaformat` during the `validate` phase. Run `./mvnw spring-javaformat:apply` before committing to auto-fix formatting.
- **MySQL/Postgres tests**: 14 tests are skipped by default because they require Docker (Testcontainers). This is expected behavior when Docker is unavailable.
- **Port 8080**: The app binds to port 8080. Ensure nothing else is using it before starting.
- **Hot reload**: The project includes `spring-boot-devtools` (test scope). When running via `./mvnw spring-boot:run`, Java source changes require recompilation; template (Thymeleaf) changes are picked up on refresh.
- **CSS changes**: If modifying SCSS files in `src/main/scss/`, recompile CSS with `./mvnw package -P css`.

FROM gradle:8.5-jdk17 AS builder
WORKDIR /app
COPY --chown=gradle:gradle . .
RUN ./gradlew clean build -x test --no-daemon

FROM eclipse-temurin:17-jdk
WORKDIR /app
COPY --from=builder /app/build/libs/*.jar app.jar
ENTRYPOINT ["java", "-jar", "app.jar"]

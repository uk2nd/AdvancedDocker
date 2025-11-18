FROM gradle:7 AS base
CMD ["bash"]

# Build
FROM base AS build-and-test
COPY . /workspace
WORKDIR /workspace
RUN ./gradlew build

# Production
FROM eclipse-temurin:17-jre AS production
COPY --from=build-and-test /workspace/build/libs/api-0.0.1-SNAPSHOT.jar /app.jar
CMD ["java", "-jar", "/app.jar"]

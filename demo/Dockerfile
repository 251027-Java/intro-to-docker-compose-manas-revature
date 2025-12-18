# Stage one
FROM eclipse-temurin:25-noble AS build
WORKDIR /app

COPY ./ ./
# RUN chmod +x mvnw
RUN ./mvnw dependency:go-offline
RUN ./mvnw package -DskipTests


# Stage two
FROM eclipse-temurin:25-jre-alpine AS run
WORKDIR /app
COPY --from=build /app/target/demo-0.0.1-SNAPSHOT.jar /app/

# TODO: Set Entrypoint
# ENTRYPOINT ...
ENTRYPOINT [ "java", "-jar", "./demo-0.0.1-SNAPSHOT.jar" ]

EXPOSE 8080
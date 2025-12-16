FROM eclipse-temurin:25-noble AS build
WORKDIR /app
COPY ./ ./
RUN chmod +x mvnw
RUN ./mvwn dependency:go-offline
RUN ./mvnw package -DskipTests

FROM eclipse-temurin:25-jre-alpine AS run
WORKDIR /app
COPY --from=build /app/target/manudockercompose-0.0.1-SNAPSHOT.jar /app/
ENTRYPOINT ["java", "-jar", "./manudockercompose-0.0.1-SNAPSHOT.jar"]

EXPOSE 8080
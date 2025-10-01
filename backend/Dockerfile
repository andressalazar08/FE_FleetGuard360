# Etapa de construcción
FROM maven:3.9.9-eclipse-temurin-21 AS build
WORKDIR /app
COPY backend/pom.xml .
COPY backend/src ./src
RUN mvn clean package -DskipTests

# Etapa de empaquetado (runtime)
FROM eclipse-temurin:21
WORKDIR /app
COPY --from=build /app/target/fleetGuard360.jar fleetGuard360.jar
EXPOSE 8080
ENTRYPOINT ["java","-jar","fleetGuard360.jar"]

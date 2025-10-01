# Etapa de construcción
FROM maven:latest AS build 
WORKDIR /app
COPY . .
RUN mvn clean package -DskipTests
 
# Etapa de empaquetado (runtime)

FROM eclipse-temurin:21
WORKDIR /app
# Copia el JAR de la etapa 'build' a la etapa actual
COPY --from=build /app/target/fleetGuard360.jar fleetGuard360.jar
EXPOSE 8080
ENTRYPOINT ["java","-jar","fleetGuard360.jar"]

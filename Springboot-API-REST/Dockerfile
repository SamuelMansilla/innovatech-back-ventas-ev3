# Paso 1: Compilar la aplicación usando Maven
FROM maven:3.8.5-openjdk-17 AS build
WORKDIR /app
COPY . .
RUN mvn clean package -DskipTests

# Paso 2: Ejecutar la aplicación con una imagen ligera de Java 17
FROM eclipse-temurin:17-jdk-jammy
WORKDIR /app
COPY --from=build /app/target/*.jar app.jar
EXPOSE 8081
ENTRYPOINT ["java", "-jar", "app.jar"]
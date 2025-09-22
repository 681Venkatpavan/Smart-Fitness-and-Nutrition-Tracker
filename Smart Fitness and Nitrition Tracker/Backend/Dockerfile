# Stage 1: Build the Spring Boot app
FROM maven:3.9.1-eclipse-temurin-17 AS build
WORKDIR /app

# Copy Maven project files from inner SFANT folder
COPY SFANT/SFANT/pom.xml .
COPY SFANT/SFANT/src ./src

# Build the Spring Boot jar
RUN mvn clean package -DskipTests

# Stage 2: Run the Spring Boot app
FROM openjdk:17-jdk-alpine
WORKDIR /app
COPY --from=build /app/target/*.jar app.jar

EXPOSE 8081
CMD ["java", "-jar", "app.jar"]

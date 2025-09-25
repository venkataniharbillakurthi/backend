# Build stage
FROM maven:3.8.6-eclipse-temurin-17-alpine AS build
WORKDIR /app
# Copy only the backend directory contents (not the backend folder itself)
COPY backend/ .
RUN mvn clean package -DskipTests

# Run stage
FROM eclipse-temurin:17-jdk-alpine
WORKDIR /app
COPY --from=build /app/target/*.jar app.jar
ENTRYPOINT ["java","-jar","app.jar"]
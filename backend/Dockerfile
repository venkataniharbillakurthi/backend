# Build stage
FROM maven:3.8.6-eclipse-temurin-17-alpine AS build
WORKDIR /app
# Copy all files needed for the build
COPY . .
# Build the application
RUN mvn clean package -DskipTests

# Run stage
FROM eclipse-temurin:17-jdk-alpine
WORKDIR /app
VOLUME /tmp
# Copy the built JAR from the build stage
COPY --from=build /app/target/*.jar app.jar
EXPOSE 8080
ENTRYPOINT ["java","-jar","/app.jar"]
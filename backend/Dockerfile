# Stage 1: Build the JAR
FROM maven:3.8.7-amazoncorretto-17 AS builder
WORKDIR /app
COPY . .
RUN mvn clean package -DskipTests

# Stage 2: Run the app
FROM amazoncorretto:17-alpine
WORKDIR /app
COPY --from=builder /app/target/*.jar app.jar

EXPOSE 8080
ENTRYPOINT ["java", "-jar", "app.jar"]

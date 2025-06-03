# Use Maven to build
FROM maven:3.8.7-amazoncorretto-17 as builder
WORKDIR /app
COPY pom.xml .
COPY Main.java .
RUN mvn clean package -DskipTests

# Run the built JAR
FROM amazoncorretto:17-alpine
WORKDIR /app
COPY --from=builder /app/target/*.jar app.jar

EXPOSE 8080
ENTRYPOINT ["java", "-jar", "app.jar"]

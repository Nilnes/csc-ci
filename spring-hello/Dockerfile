# Use OpenJDK 17 as the base image
FROM openjdk:17-jdk-slim
WORKDIR /app
COPY mvnw pom.xml ./
COPY .mvn .mvn
RUN ./mvnw dependency:go-offline -B
COPY src ./src
RUN ./mvnw clean package -DskipTests
EXPOSE 8080

# Run the application
CMD ["java", "-jar", "target/*.jar"]
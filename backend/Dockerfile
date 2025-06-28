FROM maven:3.8.5-openjdk-17-slim AS build
WORKDIR /app

# Copy only backend folder contents into /app
COPY backend/ ./

RUN mvn clean install -DskipTests

FROM openjdk:17
WORKDIR /app

COPY --from=build /app/target/*.jar app.jar

ENTRYPOINT ["java", "-jar", "app.jar"]

FROM maven:3.8.5-eclipse-temurin-17-alpine AS build
WORKDIR /app
COPY ./pom.xml .
RUN mvn compile
COPY . .
RUN mvn clean package

FROM openjdk:17-alpine
WORKDIR /app
EXPOSE 8080
COPY --from=build /app/target/project-0.0.1-SNAPSHOT.jar app.jar
CMD [ "java", "-jar", "app.jar" ]

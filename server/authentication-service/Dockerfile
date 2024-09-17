FROM maven:3.6.3-jdk-11 AS build

WORKDIR /app

COPY pom.xml .

COPY src ./src

RUN mvn clean package -DskipTests

FROM openjdk

WORKDIR /app

COPY --from=build  /app/target/authentication-service.jar .

EXPOSE 7000

ENTRYPOINT ["java", "-jar", "authentication-service.jar"]
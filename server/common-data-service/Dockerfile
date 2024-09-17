FROM maven:3.6.3-jdk-11 AS build

WORKDIR /app

COPY pom.xml .

COPY src ./src

RUN mvn clean package -DskipTests

FROM openjdk

WORKDIR /app

COPY --from=build  /app/target/common-data-service.jar .

EXPOSE 9000

ENTRYPOINT ["java", "-jar", "common-data-service.jar"]
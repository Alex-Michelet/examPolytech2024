FROM maven:3-eclipse-temurin-8-alpine as backend_builder

WORKDIR /app

COPY . . 

RUN mvn clean package -DskipTests

# After compiling prepare image to lauch backend server
FROM eclipse-temurin:8-jre-alpine

WORKDIR /usr/src/app

COPY --from=backend_builder /app/target/java-0.0.1-SNAPSHOT.jar .

CMD ["java", "-jar", "java-0.0.1-SNAPSHOT.jar"]

LABEL maintainer="alex"

EXPOSE 8448
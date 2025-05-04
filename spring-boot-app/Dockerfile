# FROM adoptopenjdk/openjdk11:alpine-jre

# # Simply the artifact path
# ARG artifact=target/spring-boot-web.jar

# WORKDIR /opt/app

# COPY ${artifact} app.jar

# # This should not be changed
# ENTRYPOINT ["java","-jar","app.jar"]

# Stage 1: Build the JAR
FROM maven:3.9.6-eclipse-temurin-11 AS builder

WORKDIR /app
COPY . .
RUN mvn clean package -DskipTests
CMD ["cat"]
# Stage 2: Run the JAR
FROM eclipse-temurin:11-jre

WORKDIR /opt/app
COPY --from=builder /app/target/*.jar app.jar
ENTRYPOINT ["java", "-jar", "app.jar"]


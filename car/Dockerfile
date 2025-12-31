# ===== Build stage =====
FROM maven:3.9.6-eclipse-temurin-17 AS builder
WORKDIR /app
COPY pom.xml .
COPY src ./src
RUN mvn clean package -DskipTests

# ===== Runtime stage =====
FROM eclipse-temurin:17-jre-alpine
VOLUME /tmp
COPY --from=builder /app/target/*.jar voiture-service.jar
ENTRYPOINT ["java","-jar","/voiture-service.jar"]

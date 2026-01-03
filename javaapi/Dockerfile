# FROM eclipse-temurin:8-jre AS BUILD_IMAGE
# WORKDIR /usr/src/app/
# RUN apt update && apt install maven -y
# COPY ./ /usr/src/app/
# RUN mvn install -DskipTests

# FROM eclipse-temurin:8-jre
# WORKDIR /usr/src/app/
# COPY --from=BUILD_IMAGE /usr/src/app/target/book-work-0.0.1-SNAPSHOT.jar ./book-work-0.0.1.jar

# EXPOSE 9000
# ENTRYPOINT ["java","-jar","book-work-0.0.1.jar"]
# # Test

# -------- BUILD STAGE --------
FROM maven:3.8.6-eclipse-temurin-8 AS build
WORKDIR /usr/src/app
COPY . .
RUN mvn clean install -DskipTests

# -------- RUNTIME STAGE --------
FROM eclipse-temurin:8-jre
WORKDIR /usr/src/app
COPY --from=build /usr/src/app/target/*.jar app.jar
ENTRYPOINT ["java","-jar","app.jar"]

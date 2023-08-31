#FROM openjdk:11
#
#WORKDIR ./app
#
#COPY . .
#
#RUN ./gradlew build
#
#EXPOSE 8080
#
#ENTRYPOINT ["java","-jar","./build/libs/backend-0.0.1-SNAPSHOT.jar"]


FROM gradle:latest as builder

WORKDIR /app
COPY . .
RUN ./gradlew bootJar

FROM openjdk:latest
COPY --from=builder /app/build/libs/ /app

EXPOSE 8080
ENTRYPOINT [ "java", "-jar", "-Dspring.profiles.active=prod", "/app/app.jar" ]
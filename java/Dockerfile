FROM maven:3.6.0-jdk-11-slim AS build
MAINTAINER dhdorgam
RUN mkdir /backend-service
WORKDIR /backend-service
COPY ./projeto /backend-service
RUN  ls -l /backend-service
RUN mvn  install

FROM amazoncorretto:11-alpine-jdk
MAINTAINER dhdorgam
RUN mkdir /backend-service
WORKDIR /backend-service
COPY . /backend-service
COPY --from=build /backend-service/target/pessoa-service-0.0.1-SNAPSHOT.jar /backend-service/pessoa-service.jar
RUN  ls -l /backend-service
#RUN mvnw  install
EXPOSE 8090
ENTRYPOINT ["java","-jar","/backend-service/pessoa-service.jar"]
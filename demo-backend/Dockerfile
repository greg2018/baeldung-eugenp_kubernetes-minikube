FROM openjdk:8-jdk-alpine
VOLUME /tmp
COPY target/demo-backend-2.4.2.jar app.jar
ENV JAVA_OPTS=""
ENTRYPOINT exec java -jar /app.jar --debug
FROM maven:3.8.6-openjdk-11 as builder
WORKDIR /app
COPY . .
RUN mvn package

FROM adoptopenjdk/openjdk11:jdk-11.0.18_10-ubuntu
COPY --from=builder /app/target/simple-server.jar /opt/app/application.jar
ADD src/main/resources/* /opt/app/
RUN mkdir -p /tmp/logs

EXPOSE 9880

ENTRYPOINT [ "sh", "-c", "java $JAVA_OPTS -jar /opt/app/application.jar" ]

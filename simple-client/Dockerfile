FROM maven:3.8.6-openjdk-11 as builder
WORKDIR /app
COPY . .
RUN mvn package

FROM adoptopenjdk/openjdk11:jdk-11.0.18_10-ubuntu
ENV SERVER_ADDR=localhost
COPY --from=builder /app/target/simple-client.jar /opt/app/application.jar
ADD src/main/resources/* /opt/app/
RUN mkdir -p /tmp/logs

ENTRYPOINT [ "sh", "-c", "java $JAVA_OPTS -jar /opt/app/application.jar" ]

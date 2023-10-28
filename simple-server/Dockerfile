FROM maven:3.8.6-openjdk-11 as builder
WORKDIR /app
COPY . .
# RUN cd simple-server \
#     && mvn package

RUN mvn package

FROM adoptopenjdk/openjdk11:jdk-11.0.18_10-ubuntu
COPY --from=builder /app/target/simple-server.jar /opt/app/application.jar
ADD src/main/resources/* /opt/app/
RUN mkdir -p /tmp/logs

EXPOSE 9876
EXPOSE 9877
EXPOSE 9878
EXPOSE 9879
EXPOSE 9880
EXPOSE 9881
EXPOSE 8080
EXPOSE 8000

ENTRYPOINT [ "sh", "-c", "java $JAVA_OPTS -jar /opt/app/application.jar" ]

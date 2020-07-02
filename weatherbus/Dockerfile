FROM gradle:6.5.1-jdk8 as BUILD_IMAGE
WORKDIR /build
COPY ./src /tmp/src
WORKDIR /tmp/src
RUN ./gradlew assemble
RUN find . -name '*.jar'


FROM fabric8/java-alpine-openjdk8-jre
COPY --from=BUILD_IMAGE /tmp/src/build/libs/weatherbus-SNAPSHOT.jar /weatherbus.jar
EXPOSE 30000
ENTRYPOINT ["java", "-jar", "/weatherbus.jar", "-Dserver.port=3000"]

FROM gradle:6.5.1-jdk8 as BUILD_IMAGE
WORKDIR /build
COPY ./src /tmp/src
WORKDIR /tmp/src
RUN ./gradlew assemble
RUN find . -name '*.jar'


FROM fabric8/java-alpine-openjdk8-jre
COPY --from=BUILD_IMAGE /tmp/src/build/libs/weatherbus-bus-0.0.1-SNAPSHOT.jar /weatherbus-bus.jar
ENTRYPOINT ["java", "-jar", "/weatherbus-bus.jar"]

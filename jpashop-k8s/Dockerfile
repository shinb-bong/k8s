FROM openjdk:11
ARG JAR_FILE=./jpashop2/build/libs/jpashop-0.0.1-SNAPSHOT.jar
COPY ${JAR_FILE} app.jar
ENTRYPOINT ["java","-Djava.security.egd=file:/dev/./urandom","-jar","/app.jar"]
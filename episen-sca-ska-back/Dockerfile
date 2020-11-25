#FROM adoptopenjdk/openjdk11:alpine-jre

#LABEL maintainer="sakana.kaneswaran@gmail.com" \
#      org.label-schema.schema-version="1.0" \
#	  org.label-schema.build-date="22-11-2020" \
#	  org.label-schema.name="sakanakns/episen-sca-ska-back" \
# 	  org.label-schema.description="backend which take off value of orders and save it into a file named order.txt" \
#	  org.label-schema.url="POST http://192.168.99.100:8080/add/order?name=value" \
#	  org.label-schema.vcs-url="https://github.com/skaneswa/episen-sca-ska-back.git" \
# 	  org.label-schema.docker.cmd="docker run -d -it --name backend -p 8080:8080 sakanakns/episen-sca-ska-back"
#

# Refer to Maven build -> finalName
#ARG JAR_FILE=target/TP3_docker-0.0.1-SNAPSHOT.jar

# cd /opt/app
#WORKDIR /opt/app

# cp target/TP3_docker-0.0.1-SNAPSHOT.jar /opt/app/app.jar
#COPY ${JAR_FILE} app.jar

# java -jar /opt/app/app.jar
#ENTRYPOINT ["java","-jar","app.jar"]



###########MULTI-STAGE#####################
#
# Build stage
#
FROM maven:3.6.0-jdk-11-slim AS build
COPY src /home/app/src
COPY pom.xml /home/app
RUN mvn -f /home/app/pom.xml clean package

#
# Package stage
#
FROM openjdk:11-jre-slim
LABEL maintainer="sakana.kaneswaran@gmail.com" \
      org.label-schema.schema-version="1.0" \
	  org.label-schema.build-date="22-11-2020" \
	  org.label-schema.name="sakanakns/episen-sca-ska-back" \
 	  org.label-schema.description="backend which take off value of orders and save it into a file named order.txt" \
	  org.label-schema.url="POST http://192.168.99.100:8080/add/order?name=value" \
	  org.label-schema.vcs-url="https://github.com/skaneswa/episen-sca-ska-back.git" \
 	  org.label-schema.docker.cmd="docker run -d -it --name backend -p 8080:8080 sakanakns/episen-sca-ska-back"
COPY --from=build /home/app/target/TP3_docker-0.0.1-SNAPSHOT.jar /usr/local/lib/TP3_docker.jar
EXPOSE 8080
ENTRYPOINT ["java","-jar","/usr/local/lib/TP3_docker.jar"]


#This image is to Build the artifact
FROM openjdk:11 AS BUILD_IMAGE
#OpenJDK is debian based thats why apt 
RUN apt update && apt install maven -y 
RUN git clone https://github.com/vidhya101/vprofile-project.git
RUN cd vprofile-project && git checkout docker && mvn install


#This Image will be having the artifact
FROM tomcat:9-jre11
LABEL "Project"="Vprofile"
LABEL "Author"="VidhyaShankerGoel"
#TO delete default app
RUN rm -rf /usr/local/tomcat/webapps*
COPY --from=BUILD_IMAGE vprofile-project/target/vprofile-v2.war /usr/local/tomcat/webapps/ROOT.war

EXPOSE 8080
CMD ["catalina.sh", "run"]
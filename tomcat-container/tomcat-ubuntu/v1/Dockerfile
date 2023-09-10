FROM ubuntu:latest
RUN apt-get update && apt-get install -y curl ufw
RUN mkdir -p /runtime/jdk17lts
RUN mkdir -p /runtime/tomcat9
RUN curl -LO  https://corretto.aws/downloads/latest/amazon-corretto-17-x64-linux-jdk.tar.gz
RUN chmod 777 amazon-corretto-17-x64-linux-jdk.tar.gz
RUN curl -LO  https://dlcdn.apache.org/tomcat/tomcat-9/v9.0.80/bin/apache-tomcat-9.0.80.tar.gz
RUN chmod 777 apache-tomcat-9.0.80.tar.gz
RUN tar xzvf apache-tomcat-9.0.80.tar.gz -C /runtime/tomcat9 --strip-components=1 > /dev/null
RUN tar xzvf amazon-corretto-17-x64-linux-jdk.tar.gz -C /runtime/jdk17lts --strip-components=1 > /dev/null
RUN chmod -R 777 /runtime/jdk17lts
RUN chmod -R 777 /runtime/tomcat9
RUN ufw allow 8080
RUN ufw allow 8080/tcp
RUN yes | ufw enable
RUN export CATALINA_HOME=/runtime/tomcat9
RUN export JAVA_HOME=/runtime/jdk17lts
RUN export PATH=$PATH:$JAVA_HOME/bin
EXPOSE 8080
CMD ["$CATALINA_HOME/bin/startup.sh", "run"]
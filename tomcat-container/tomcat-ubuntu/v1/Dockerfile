FROM ubuntu:latest
RUN apt-get update && apt-get install -y curl ufw
RUN mkdir -p /runtime/jdk17lts
RUN mkdir -p /runtime/tomcat9
RUN curl -LO  https://corretto.aws/downloads/latest/amazon-corretto-17-x64-linux-jdk.tar.gz
RUN curl -LO  https://dlcdn.apache.org/tomcat/tomcat-9/v9.0.80/bin/apache-tomcat-9.0.80.tar.gz
RUN tar xzvf apache-tomcat-9.0.80.tar.gz -C /runtime/tomcat9 --strip-components=1 > /dev/null
RUN tar xzvf amazon-corretto-17-x64-linux-jdk.tar.gz -C /runtime/jdk17lts --strip-components=1 > /dev/null
ENV CATALINA_HOME=/runtime/tomcat9
ENV JAVA_HOME=/runtime/jdk17lts
ENV PATH=$PATH:$JAVA_HOME/bin

COPY keepalive.sh /runtime/keepalive.sh
EXPOSE 8080
CMD ["/runtime/keepalive.sh", "run"]
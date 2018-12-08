FROM devframe-centos

USER root

RUN mkdir -p /data/tool

ADD files/jdk-8u191-linux-x64.tar.gz /data/tool/
RUN cp -rf /data/tool/jdk1.8.0_191 /usr/local/
ENV JAVA_HOME /usr/local/jdk1.8.0_191

ADD files/apache-tomcat-8.5.35.tar.gz /data/tool/
RUN cp -rf /data/tool/apache-tomcat-8.5.35 /usr/local/
RUN chmod +x /data/tool/apache-tomcat-8.5.35/bin/*.sh
ENV CATALINA_HOME /data/tool/apache-tomcat-8.5.35

ENV PATH $JAVA_HOME/bin:$CATALINA_HOME/bin:$PATH

EXPOSE 8080 8009

CMD ["catalina.sh", "run"]